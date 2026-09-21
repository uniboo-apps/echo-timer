# echo-timer（全画面カウントダウンタイマー）

本文中のコードパスは repo ルート基準（Markdownリンクは文書位置基準）。
スマホを置いて使う、シンプルな全画面カウントダウンタイマー。料理・運動などの分単位タイマー用途。

## 構成・技術
- **`index.html` 1枚で完結**（静的・外部依存なし）。
- プリセット 1〜10分ボタン、±1分調整、スタート/一時停止/リセット。
- 残り30秒で黄・10秒で赤に変色。0でビープ（Web Audio Oscillator）＋画面フラッシュ。
- `requestAnimationFrame` で計時、`navigator.wakeLock` で画面スリープ防止。

## デプロイ
- `main` に push → GitHub Actions で Cloudflare Pages へ自動デプロイ。
- リポジトリは **public**（`uniboo-apps` の組織シークレット `CLOUDFLARE_API_TOKEN` を使用）。
- Notion コミットログの実装は `.github/workflows/deploy.yml` を参照する。

## ルール
- **public なので秘密をコードに置かない**（現状ゼロ依存で問題なし）。
- モバイル前提（全画面・タップUI・`viewport-fit=cover`）。
