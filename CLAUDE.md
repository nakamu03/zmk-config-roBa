ユーザーはmacOSを使用しています。
pcには、キーボードをus配列として認識させています

## ZMK バージョン管理

ZMKはバージョンピンニングが必要。以下の3ファイルを常に同じバージョンに揃えること：

| ファイル | 設定箇所 | 現在の値 |
|---|---|---|
| `.github/workflows/build.yml` | `uses: zmkfirmware/zmk/.github/workflows/build-user-config.yml@v0.3` | `@v0.3` |
| `config/west.yml` | `revision: v0.3` | `v0.3` |
| `build.yaml` | `board: seeeduino_xiao_ble` | `seeeduino_xiao_ble` |

### バージョンアップ時の注意

ZMKのリリースタグ一覧: https://github.com/zmkfirmware/zmk/tags

バージョンを上げる場合は3ファイル同時に更新する。例えば `v0.4` が出たら：
1. `build.yml` → `@v0.4`
2. `west.yml` → `revision: v0.4`
3. `build.yaml` → ボード名が変わっている可能性があるので確認する

### Zephyr 4.1以降のボード名変更について

ZMK main ブランチ（Zephyr 4.1以降）では `seeeduino_xiao_ble` → `xiao_ble//zmk` にリネームされた。
`v0.3` タグはZephyr 4.1以前のため `seeeduino_xiao_ble` のまま。

参考ドキュメント:
- ZMKバージョンピンニング: https://zmk.dev/blog/2025/06/20/pinned-zmk#west-manifest
- Zephyr 4.1対応: https://zmk.dev/blog/2025/12/09/zephyr-4-1#zmk-board-variant
