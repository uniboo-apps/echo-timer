# echo-timer（全画面カウントダウンタイマー）

スマホを置いて使う、シンプルな全画面カウントダウンタイマー。料理・運動などの分単位タイマー用途。

## 構成・技術
- **`index.html` 1枚で完結**（静的・外部依存なし）。
- プリセット 1〜10分ボタン、±1分調整、スタート/一時停止/リセット。
- 残り30秒で黄・10秒で赤に変色。0でビープ（Web Audio Oscillator）＋画面フラッシュ。
- `requestAnimationFrame` で計時、`navigator.wakeLock` で画面スリープ防止。

## デプロイ
- `main` に push → GitHub Actions で Cloudflare Pages へ自動デプロイ。
- 旧 URL（廃止）: `tubular-pie-d74799.netlify.app`（Netlify Drop）。
- リポジトリは **public**（`uniboo-apps` の組織シークレット `CLOUDFLARE_API_TOKEN` を使用）。
- push 時に `notion-commit.yml` が NotionのコミットDBへコミットを記録（AI DB「エコータイマー」行に紐づけ）。

## ルール
- **public なので秘密をコードに置かない**（現状ゼロ依存で問題なし）。
- モバイル前提（全画面・タップUI・`viewport-fit=cover`）。
