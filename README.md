# devcontaners-presentation

プレゼン資料を作成する。

スライドの作成は Marp を利用し、内部で使用する図は draw.io で作成する。
Marp は VSCode 拡張機能、draw.io は Web 版を用いる。

出力は Marp CLI を用いて pptx や pdf に変換する。
そのために各種設定などを最適化した Docker コンテナを利用する。

## 手順

###　作業

1. VSCode で当フォルダを開く
2. 左下の「><」から「コンテナーで再度開く(Reopen in Contaner)」
3. 通常の markdown と同様にプレビュー表示

### 出力

```bash
marp ./documents/slides.md -o outputs/slides.pdf --allow-local-files
marp ./documents/slides.md -o outputs/slides.pptx --allow-local-files
```

## memo

- marp で図のサイズ調整が難しい
  html を有効化して css を利用する必要あり
  "markdown.marp.html": "all"
  ただし出力時にどういう影響がでるか...
