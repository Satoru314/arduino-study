# ハードウェア

## Arduino UNO R4 Minima

- MCU: Renesas RA4M1（Arm Cortex-M4F, 48MHz, Flash 256KB, SRAM 32KB）
- ロジック電圧: **5V**
- USB-C（MCU の USB を直接使う。USB シリアル変換チップなし）
- 書き込み: ブートローダ経由（DFU）。リセットのダブルタップでブートローダに入る
- UART: `Serial` = USB, `Serial1` = D0(RX) / D1(TX)

## ESP8266（ESP8266MOD = ESP-12E/F モジュール）

- MCU: Tensilica L106（80/160MHz）, Wi-Fi 2.4GHz のみ, WPA2
- ロジック電圧: **3.3V（5V 非対応）**
- ボード: **NodeMCU**（裏面の印字で確認, 2026-10-26）。USB シリアル変換チップ（CH340 / CP2102）は未確認
- PlatformIO のボード名: `nodemcuv2`
- UART0 は USB と共有。`Serial.swap()` で GPIO13(RX) / GPIO15(TX) に移せる
- GPIO15 は起動時 LOW、GPIO0 / GPIO2 は起動時 HIGH が必要（ブートモードに関係）

## R4 ⇄ ESP8266 の配線（予定）

```
R4 D1(TX, 5V) ──[1kΩ]──┬── ESP8266 GPIO13 (RX)
                       [2kΩ]
                        GND
R4 D0(RX)     ────────────── ESP8266 GPIO15 (TX)   ※3.3V→5V入力は直結で壊れない
R4 5V         ────────────── ESP8266 VIN/5V        ※ボードにレギュレータがある場合のみ
R4 GND        ────────────── ESP8266 GND           ※必ず共通
```

- 分圧: 5V × 2k/(1k+2k) ≒ 3.3V。10kΩ / 20kΩ でもよい
- レベル変換モジュール（BSS138）があればそちらが確実

## ネットワーク

- 家の Wi-Fi でもスマホのテザリングでもよい（2.4GHz / WPA2）
  - iPhone は「互換性を優先」を ON
- テザリング中は自宅 LAN（192.168.40.x）に直接届かない
