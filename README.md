# pome-fixture

Pome の proxy，sumdb，`emela pome` を確かめるための Pome．中身に意味はない．

tag は検査のケースを並べたもので，付け替えも削除もしない（proxy に一度取り込まれた版は変わらないため）．

| tag | 中身 | 期待する結果 |
|---|---|---|
| `v0.1.0` | 正しい Pome（軽量 tag） | 取り込める |
| `v0.1.1` | 正しい Pome（注釈付き tag） | 取り込める．`@latest` はこれ |
| `v0.2.0-rc.1` | prerelease | `@v/list` に出るが `@latest` に選ばれない |
| `v0.3.0` | `[pome].version` が `0.2.9` | `manifest_version_mismatch` で 410 |
| `v0.4.0` | シンボリックリンクを含む | `symlink` で 410 |
| `latest` | semver でない tag | `@v/list` に出ない |

`main` は `v0.2.0-rc.1` を指す．`v0.3.0` と `v0.4.0` の commit は tag からしかたどれない．
