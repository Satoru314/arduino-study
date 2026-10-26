# arduino-study

Arduino UNO R4 Minima と ESP8266 を組み合わせて、マイコンの仕組みを学ぶリポジトリ。
Arduino IDE は使わず、CLI で進める。

## 学びたいこと

- Arduino の使い方とエコシステム（コア、ボード定義、ライブラリ、ツールチェーン）
- コードがマイコンで動くまでの仕組み（コンパイル、リンク、書き込み、ブートローダ、起動）
- C++ 以外の言語での組み込み（Rust、Ruby、emela）

## 目標

R4 Minima と ESP8266 を UART でつなぎ、ESP8266 経由で HTTP 通信する。

```
[センサー等] ─ R4 Minima (5V) ─UART─ ESP8266 (3.3V) ─Wi-Fi─ HTTP
```

## ロードマップ

### C++（`cpp/`）
- [ ] 環境構築（PlatformIO CLI）
- [ ] R4 Minima で L チカ。ビルド成果物（.elf / .bin）とアップロードの中身を見る
- [ ] シリアル出力。USB CDC とは何か
- [ ] ESP8266 で L チカ
- [ ] ESP8266 で Wi-Fi 接続 → HTTP GET
- [ ] R4 ⇄ ESP8266 の UART 通信（分圧配線）
- [ ] R4 のデータを ESP8266 経由で HTTP 送信

### Rust（`rust/`）
- [ ] R4 Minima（RA4M1 / Cortex-M4）で `no_std` の L チカ

### Ruby（`ruby/`）
- [ ] mruby/c をマイコンで動かす

### emela（`emela/`）
- [ ] emela の C バックエンドで生成した C をマイコンで動かす

## ディレクトリ

| パス | 内容 |
|---|---|
| `cpp/` | C++（Arduino フレームワーク） |
| `rust/` | Rust |
| `ruby/` | Ruby（mruby/c） |
| `emela/` | emela |
| `notes/` | 学習ログ |
| `docs/hardware.md` | ボード・配線・電圧のメモ |
