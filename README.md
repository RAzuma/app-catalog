# app-catalog

アプリ内「関連アプリ」画面が読みにいくクロスプロモ用の静的 JSON。
GitHub Pages (`https://razuma.github.io/app-catalog/`) で配信され、**push だけで反映される**
（アプリの再リリース不要）。

## ファイル名の規則

`{Android パッケージ名の末尾}.json`。資格アプリは `jp.razuma.{appid}study` なので
`{appid}study.json`（例: `kenki1study.json`）。appid ではなくパッケージ末尾に合わせること。

形式は `self`（自分の情報）+ `apps`（自分以外・同カテゴリのみ）。
各エントリは `{name, icon, android_package, ios_id}`。ストアリンクは **Google Play のみ**。

## 消していいファイル / ダメなファイル

**未参照に見えても消さないこと。** どのアプリからも参照されていないように見える JSON には、
消すと本番が壊れるものが混ざっている。

| ファイル | 状態 | 理由 |
|---|---|---|
| `shoubouotu6study.json` | **消さない** | 公開済みの消防設備士乙6が、綴り誤りのこの URL を叩いている（`shoubouot`**`s`**`u` の s が抜け）。更新しないユーザーの端末は永久にここを見にくるので恒久措置 |
| `shoubouotu7study.json` | **消さない** | 同上（乙7） |
| `shoubouotsu6study.json` | **消さない** | アプリ側のソースは綴りを修正済み。次回リリース以降はこちらを見にくる |
| `shoubouotsu7study.json` | **消さない** | 同上（乙7） |

つまり乙6・乙7 は正誤2つの名前を両方置いておく必要がある。片方だけにしないこと。

`boilerstudy.json` / `sample.json` はテンプレート・サンプル用。

## 未公開アプリの扱い

Play 未公開のアプリを `apps` に入れるとストアで「見つかりません」になる。
公開されてから追記する運用にする（カタログは push で即反映されるので後追いで問題ない）。
