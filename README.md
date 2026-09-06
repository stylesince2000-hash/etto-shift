# 食・酒・楽 笑っと（ETTO） シフトアプリ

居酒屋「食・酒・楽 笑っと」のスマホ用シフト管理アプリ。**単一ファイル `index.html`**（素のHTML/CSS/JS）に全機能を内包。データ同期は Firebase Realtime Database、ホスティングは **GitHub Pages 自動デプロイ**。

- 本番URL: https://stylesince2000-hash.github.io/etto-shift/
- リポジトリ（Public）: https://github.com/stylesince2000-hash/etto-shift

> この README は公開リポジトリに入るため、パスワード等の秘密は書きません。詳細な運用メモは、各自のPCローカルにある `CLAUDE.md`（gitignore・非公開）を参照してください。

## 他PCで続きを始める手順
```bash
gh auth login          # 初回のみ：GitHubにログイン
git clone https://github.com/stylesince2000-hash/etto-shift
cd etto-shift
claude                 # このフォルダで Claude Code を起動し、まず CLAUDE.md を読ませる
```
- **作業前**に必ず `git pull`、**作業後**は下記手順で `git push`。
- シフトの入力データは Firebase 上にあるので、どのPCで編集しても本番データは共通。

## ファイル構成
| ファイル | 役割 | Git |
|---|---|---|
| `index.html` | 本体（唯一の実装ファイル） | ✅ 追跡 |
| `logo-dark.png` / `logo-light.png` | ログイン画面／上部バーのロゴ | ✅ 追跡 |
| `icon.png` | ホーム画面追加時のアプリアイコン（512×512） | ✅ 追跡 |
| `manifest.json` | PWAマニフェスト（**Androidのホーム画面アイコンに必須**） | ✅ 追跡 |
| `version.json` | 自動アップデート用の版番号 | ✅ 追跡 |
| `.nojekyll` | GitHub PagesのJekyll処理を無効化（**無いとビルド失敗し画像等が404**） | ✅ 追跡 |
| `CLAUDE.md` / `セットアップ手順.md` | 運用メモ・利用者マニュアル（パスワード記載） | 🚫 非公開(gitignore) |

## 主な機能
- **従業員**: 名前を選んで、月カレンダー／週リストで ○希望・△調整可能・×休み ＋ 備考を入力。「確定シフト」タブで自分／みんなの予定を確認。
- **管理者**: 集計、シフト編成（日付をタップして出勤者を選択）、店休日の設定、⚙️設定（スタッフ管理・パスワード変更・伝達事項）。
- **全体**: 伝達事項バナー、日ごとのイベント・予約メモ、全端末リアルタイム同期、ホーム画面追加（PWA）、開きっぱなし端末の自動アップデート。

**定休日は月曜**（自動）。祝日は営業扱い。臨時の店休・例外営業は「🚫 店休」タブで日付をタップして切り替えます。

## 変更のデプロイ
1. `index.html` を編集。
2. 動作に影響する変更なら `index.html` の `APP_VERSION` と `version.json` の `version` を**同じ新しい値**に上げる。
3. `git add -A && git commit -m "..." && git push` → 1〜2分で本番反映。
