---
title: 用 systemd slice 限制 docker 使用的資源上限
date: 2025-03-11 23:13:27
categories:
  - docker
tags:
  - docker
  - cgroup
  - systemd
---

最近伺服器開的docker服務是越來越多了

我的tinker board 2s小板子資源開始越來越不穩定, 經常資源耗盡後重新開機

docker嘛, 容器技術, `--memory`, `--cpu` 參數甚麼的多少也是了解一點的

可是這只能對單一容器限制, 其他容器是不知道自己以外的容器用了多少資源, 這就會導致當你開/關一個新服務時需要調整舊服務的配額, 服務一多後可不好管

加上要保證沒有資源超額分配情況, 還會導致所有容器只能用平均的方式分配資源, 當某個服務高負載時, 不能挪用其他有空閒的服務的資源

那有沒有甚麼方法可以讓所有容器共用一個資源限制的規則呢?

有的

docker engine 有個設定`cgroup-parent`, 可以讓所有容器在同一control group下, 這樣可以免去替每個容器設定資源限制, 又避免掉單一容器高負載時無法使用更多資源

當然, 我們不可能在每次重新開機後手動設定control group, 所以搭配systemd slice自動設定cgroup

新增檔案 `/etc/systemd/system/docker_limit.slice` 並編輯:
```ini
[Unit]
Description=Slice that limits docker resources
Before=slices.target

[Slice]
# 計算cpu用量
CPUAccounting=true
# 限制cpu用量 100% 為 1 cpu
CPUQuota=500%
# 計算記憶體用量
MemoryAccounting=true 
# 限制記憶體用量 1.75GB, 這裡不允許浮點數
MemoryMax=1792M
```

編輯`/etc/docker/daemon.json`
```json
{
  "cgroup-parent": "docker_limit.slice"
}
```

輸入指令, 用root操作或前面加上`sudo`
```sh
systemctl daemon-reload
systemctl restart docker
```

收工

如果想追蹤用量, 除了用`docker stats`外, 你還可以用

```sh
systemd-cgtop docker_limit.slice
```

缺點就是不知道那個服務就是了...

## 後記

設定完後那個會把server搞掛的服務就不作怪了= =, 感覺就像某遊戲開工作管理員後反而變順的樣子

## 參考:
- https://unix.stackexchange.com/questions/537645/how-to-limit-docker-total-resources
- https://docs.docker.com/reference/cli/dockerd/#default-cgroup-parent
- https://www.freedesktop.org/software/systemd/man/latest/systemd.resource-control.html#
