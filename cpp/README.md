# C++（Arduino フレームワーク）

PlatformIO のプロジェクトを番号つきで置く（例: `01-blink-r4/`）。

```sh
pio project init --board uno_r4_minima   # R4 Minima
pio project init --board nodemcuv2       # ESP8266（ボードに合わせて変える）
pio run -t upload
pio device monitor
```
