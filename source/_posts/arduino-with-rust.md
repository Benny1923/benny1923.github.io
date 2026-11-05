---
title: 用rust寫arduino操作lcd
date: 2023-10-28 12:15:58
categories: 
    - rust
tags:
    - rust
    - lcd
    - hd44780
---

在零件包找到 20x4 的 lcd 顯示器，想要測試還能不能用

手上還有一片 arduino uno，就用它好了

用arduino IDE嗎，感覺沒什麼意思(沒有，我沒有看不起用arduino IDE的人的意思

聽說 rust 可以寫很多開發版的程式了，來玩玩看好了

接線表:

| uno 板 | LCD |
|---|---|
| 12 | RS |
| 11 | RW |
| 10 | EN |
| 4 | D7 |
| 5 | D6 |
| 6 | D5 |
| 7 | D4 |
| GND | VSS, Vo, K |
| 5v | VCC, A |

資料腳反順序接，這什麼反人類接法...

正來來說Vo用來控制對比度, 實際上要接一個可變電阻

但手邊沒有，直接接地

## 安裝avr工具

除了rust官方的編譯器外，你還需要 avr 相關的工具

下面是從 avr-hal 的 readme 節錄:

安裝scoop(windows 的包管理器):

開啟 powershell ，輸入以下指令:

```ps1
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser # 線上腳本執行權限
irm get.scoop.sh | iex # 安裝 scoop
scoop install avr-gcc # 安裝 avr-gcc
scoop install avrdude # avr 燒錄工具
```

接下來要用cargo安裝整合工具:

用可以跑 cargo 的終端就行:

```sh
cargo +stable install ravedude
cargo install cargo-generate
```

## 寫一個簡單程式

要先產生一個專案:

```sh
cargo generate --git https://github.com/Rahix/avr-hal-template.git
```

過程讓你輸入專案名稱和目標開發版

完成後用你習慣的編輯器打開資料夾就行

接下來安裝lcd的library

```sh
# 先確定你是在專案資料夾下
cargo add hd44780-driver
```

然後就可以愉快寫程式拉

```rust
// src/main.rs
#![no_std]
#![no_main]

use hd44780_driver::{HD44780, Cursor, CursorBlink};
use panic_halt as _;

#[arduino_hal::entry]
fn main() -> ! {
    let dp = arduino_hal::Peripherals::take().unwrap();
    let pins = arduino_hal::pins!(dp);
    let mut delay = arduino_hal::Delay::new();

    let mut led = pins.d13.into_output();
    let rs = pins.d12.into_output();
    // 沒用到, 但你不宣告他不會動
    let rw = pins.d11.into_output();
    let en = pins.d10.into_output();

    let d4 = pins.d5.into_output();
    let d5 = pins.d4.into_output();
    let d6 = pins.d3.into_output();
    let d7 = pins.d2.into_output();
    // 定義輸出腳位
    let mut lcd = HD44780::new_4bit(rs, en, d4, d5, d6, d7, &mut delay).unwrap();

    // 初始化
    lcd.reset(&mut delay);
    lcd.clear(&mut delay);


    // 不要游標
    lcd.set_cursor_visibility(Cursor::Invisible, &mut delay);
    // 不要閃爍
    lcd.set_cursor_blink(CursorBlink::Off, &mut delay);

    // 輸出
    lcd.write_str("Hello World!", &mut delay);
    // 定位到第二行
    lcd.set_cursor_pos(40, &mut delay);
    lcd.write_str("greeting from rust", &mut delay);

    loop {
        led.toggle();
        arduino_hal::delay_ms(1000);
    }
}
```

執行程式也很簡單:

```sh
# arduino on COM3
RAVEDUDE_PORT=COM3 cargo run
```

![](2023/10/uno-lcd.png)

embedded-hal 十分強大，基於該抽象層的功能都能輕易移植到有實作的平台

下次來玩玩看一起被翻出來的8266好了...

## 參考:
- https://github.com/Rahix/avr-hal
- https://github.com/johndoneth/hd44780-driver