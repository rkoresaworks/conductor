# Conductor - Monokey Split Keyboard Firmware

Monokey 左右分割キーボードの ZMK ファームウェア設定。
ボード: Seeeduino XIAO BLE / シールド: monokey_L, monokey_R (RGB LED adapter 付き)

## 主要ファイル

| ファイル | 役割 |
|----------|------|
| `config/monokey.keymap` | **メインキーマップ（編集対象）** - レイヤー、コンボ、マクロ、behaviors すべてここ |
| `config/monokey.json` | ZMK Studio 用レイアウト定義 |
| `config/boards/shields/monokey/monokey.dtsi` | 物理レイアウト・マトリクス定義 |
| `config/boards/shields/monokey/monokey_L.overlay` | 左手側ハードウェア定義 |
| `config/boards/shields/monokey/monokey_R.overlay` | 右手側ハードウェア定義 |
| `config/boards/shields/monokey/monokey.keymap` | シールド側キーマップ（未使用・config 側が優先） |
| `build.yaml` | GitHub Actions ビルドマトリクス |

## キーポジションマップ

```
Row 0:  Q(0)    W(1)    E(2)    R(3)    T(4)         Y(5)    U(6)    I(7)    O(8)    P(9)
Row 1:  A(10)   S(11)   D(12)   F(13)   G(14)        H(15)   J(16)   K(17)   L(18)   -(19)
Row 2:  Z(20)   X(21)   C(22)   V(23)   B(24)        N(25)   M(26)   ,(27)   .(28)   /(29)
Thumb:  Esc(30)  Alt(31) Tab(32) Cmd(33) Space(34) BS(35)  Enter(36) Cmd(37) RShift(38) RCtrl(39)
```

## レイヤー構成

| # | 名前 | 用途 |
|---|------|------|
| 0 | default | ベースレイヤー (QWERTY) |
| 1 | FUNCTION | F1-F12 + テンキー (Space ホールドで発動) |
| 2 | NUM | 記号 (BS ホールドで発動) |
| 3 | ARROW | 矢印・メディア (Enter ホールドで発動) |
| 4 | MOUSE | マウスボタン |
| 5 | SCROLL | 未使用 |
| 6 | Bluetooth | BT 接続管理 (Tab ホールドで発動) |

## コンボ一覧

| 位置 | キー | バインド |
|------|------|---------|
| 17+18 | K+L | Space (Nvim リーダーキー用) |
| 18+19 | L+- | MB3 (ミドルクリック) |
| 11+12 | S+D | Ctrl |
| 12+13 | D+F | Alt |

## ビルド

GitHub Actions で自動ビルド。push すると `.uf2` ファームウェアが生成される。
