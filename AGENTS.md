# arduino-study

マイコン（Arduino UNO R4 Minima + ESP8266）を触って学ぶためのリポジトリ。
**一番の目的はユーザーの学習。** 動くものを作るより、仕組みを理解することを優先する。

## エージェントへのお願い

- 代わりに全部書かない。ユーザーが書く前提で、ヒント・説明・レビューを中心にする。頼まれたら書く
- 「なぜそう動くか」を説明する（ビルド → リンク → 書き込み → ブートローダ → `setup()`/`loop()` の流れなど）
- 配線の指示では電圧に必ず触れる。**ESP8266 は 3.3V で 5V 非対応**。R4 → ESP8266 の線は分圧が必須
- Wi-Fi のパスワード等は `secrets.h`（gitignore 済み）に置き、コミットしない
- 学んだことは `notes/` に日付つきで短く残す（ユーザーの言葉で書けるよう手伝う）

## ハードウェア

詳細は `docs/hardware.md`。

| ボード | MCU | 電圧 | 役割 |
|---|---|---|---|
| Arduino UNO R4 Minima | Renesas RA4M1 (Arm Cortex-M4, 48MHz) | 5V | メイン処理 |
| ESP8266 (ESP8266MOD) | Tensilica L106 (80/160MHz) | 3.3V | Wi-Fi / HTTP |

## ディレクトリ

- `cpp/` — C++（Arduino フレームワーク, PlatformIO）。最初はここ
- `rust/` — Rust の組み込み
- `ruby/` — mruby/c など Ruby の組み込み
- `emela/` — emela の C バックエンドでマイコンを動かす実験（`~/programF/emela`）
- `notes/` — 学習ログ
- `docs/` — ハードウェア・配線のメモ

## 開発環境

Arduino IDE は使わない。PlatformIO CLI（`pio`）か `arduino-cli` を使う。
ボードはサーバーの USB に挿し、開発用 CT に渡して書き込む（homeserver-controller 側で管理）。
