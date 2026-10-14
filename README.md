<div id="top"></div>

## 使用技術一覧

<p style="display: inline">
  <img src="https://img.shields.io/badge/-HTML5-E34F26.svg?logo=html5&style=for-the-badge&logoColor=white">
  <img src="https://img.shields.io/badge/-CSS3-1572B6.svg?logo=css3&style=for-the-badge&logoColor=white">
  <img src="https://img.shields.io/badge/-JavaScript-F7DF1E.svg?logo=javascript&style=for-the-badge&logoColor=black">
  <img src="https://img.shields.io/badge/-SVG-FFB13B.svg?logo=svg&style=for-the-badge&logoColor=black">
  <img src="https://img.shields.io/badge/-Web%20Audio%20API-4B4B4B.svg?style=for-the-badge">
  <img src="https://img.shields.io/badge/-Google%20Colab-F9AB00.svg?logo=googlecolab&style=for-the-badge&logoColor=white">
  <img src="https://img.shields.io/badge/-GitHub%20Pages-222222.svg?logo=githubpages&style=for-the-badge&logoColor=white">
</p>

## 目次

1. [プロジェクトについて](#プロジェクトについて)
2. [環境](#環境)
3. [ディレクトリ構成](#ディレクトリ構成)
4. [遊び方](#遊び方)
5. [ゲームの仕組み](#ゲームの仕組み)
6. [実行方法](#実行方法)
7. [カスタマイズ](#カスタマイズ)
8. [トラブルシューティング](#トラブルシューティング)
9. [注記](#注記)

<!-- プロジェクト名を記載 -->

## プロジェクト名

謝罪会見

▶ **今すぐ遊ぶ：https://aoihirata.github.io/shazai-kaiken/**

<!-- プロジェクトについて -->

## プロジェクトについて

「謝罪会見」は、不祥事を起こした架空の会社の社長になり、記者会見で頭を下げて世間の怒りを 0 にするブラウザゲームである。

記者の質問の言い回しから「ちょうどいい角度」と「ちょうどいい長さ」を読み取り、ボタン（またはスペースキー）を押している間だけ頭を下げる。離した瞬間に判定され、ぴったりなら怒りゲージが下がり、浅すぎても深すぎても怒りが上がる。

- 🙇 **長押しで頭を下げる**：押している時間で角度が深くなり、離した瞬間に角度と長さを判定する
- 🎤 **個性的な記者 9 人**：しつこい粘田記者、なぜか褒めてくる褒川記者、全然関係ない質問をする的外記者など、記者ごとに怒りやすさが違う
- ❓ **69 種類の質問**：「深く・長く」「中くらい」「浅く・短く」「すぐ上げる」「あえて下げない」の 5 系統。1 ゲーム中に同じ質問は出ない
- 🔥 **コンボ**：ドンピシャが続くと怒りの下がり幅が最大 +60% まで増える
- 🎚️ **3 段階の難易度**：やさしい／ふつう／鬼
- 🏆 **6 種類の結末**：完全勝利、誠実な社長、薄氷の会見、炎上、謝罪の怪物、終わらない会見
- 💾 **自己ベスト保存**：難易度ごとの記録をブラウザに保存する

HTML 1 ファイルだけで動き、外部ライブラリ・画像・音声ファイルは使っていない。絵は SVG、効果音は Web Audio API で合成している。スマホでは縦長、PC では横長のレイアウトに自動で切り替わる。

<p align="right">(<a href="#top">トップへ</a>)</p>

## 環境

| 言語・技術 | 用途 |
| ---------- | ---- |
| HTML / CSS / JavaScript | ゲーム本体（ビルド不要、外部ライブラリなし） |
| SVG | 社長・会見場などのグラフィック |
| Web Audio API | 効果音・カメラのシャッター音の合成 |
| localStorage | 難易度と自己ベストの保存 |
| Google Colab（Python / IPython.display） | ノートブック上でゲームを表示 |
| GitHub Pages | Web 版の公開（`.nojekyll` 同梱） |

動作確認の目安：最新の Chrome / Edge / Safari / Firefox。

<p align="right">(<a href="#top">トップへ</a>)</p>

## ディレクトリ構成

```
❯ tree -a -I ".git"
.
├── .nojekyll
├── README.md
├── index.html
└── shazai_kaiken_colab.ipynb
```

| ファイル | 内容 |
| -------- | ---- |
| [index.html](index.html) | ゲーム本体。HTML / CSS / JavaScript をすべてこの 1 ファイルに収めている |
| [shazai_kaiken_colab.ipynb](shazai_kaiken_colab.ipynb) | Google Colab 版。セルを実行するとノートブック上でゲームが始まる |
| `.nojekyll` | GitHub Pages で Jekyll の処理を無効にするための空ファイル |

<p align="right">(<a href="#top">トップへ</a>)</p>

## 遊び方

1. タイトル画面で難易度を選び、「会見を始める」を押す
2. 記者の質問を読み、求められている角度と長さを考える
3. ボタン（またはスペースキー）を押している間だけ頭が下がる。離した瞬間に判定される
4. 怒りゲージが **0** になれば勝利、**100** になると炎上してゲームオーバー

| 操作 | キー / ボタン |
| ---- | ------------- |
| 頭を下げる | 画面のボタンを長押し / `Space` 長押し |
| オープニングを進める | `Space` / `Enter` |
| 全画面の切り替え | `F`（タイトル画面などで、使える環境のみ） |

「頭は下げずに、まず私の質問に答えてください」のような質問では、**あえて頭を下げずに待つ**のが正解になる。何も操作しないまま一定時間が過ぎると質問が流れ、怒りが上がる。

<p align="right">(<a href="#top">トップへ</a>)</p>

## ゲームの仕組み

### 難易度

| 難易度 | 特徴 |
| ------ | ---- |
| やさしい | 怒りの上昇ゆるめ・誤差に寛大・ヒント多め（最初の 6 問） |
| ふつう | ちょうどいい難しさ（ヒントは最初の 3 問） |
| 鬼 | 怒り急上昇・誤差シビア・ヒントなし |

### 判定

- 質問ごとに正解の **角度の範囲** と **秒数の範囲** が決まっている
- 秒数のズレは角度のズレに換算され（1 秒 ≒ 25 度）、合計のズレが小さいほど怒りが大きく下がる
- 正解の中心にとても近いと「ピカーン！」（ドンピシャ）になり、コンボが続く
- 記者ごとに「成功時の下がりやすさ」「失敗時の上がりやすさ」の倍率が違う
- 時間がたつだけでも怒りは少しずつ上がる

### 結末

| 結末 | 条件のイメージ |
| ---- | -------------- |
| 🏆 完全勝利：伝説の謝罪会見 | ほぼミスなく怒りを 0 にした |
| 🙆 勝利：誠実な社長 | 危ない場面もあったが勝利 |
| 😅 ギリギリ勝利：薄氷の会見 | 炎上寸前から逃げ切った |
| 🔥 炎上エンド：謝る気、あるんですか | 浅い礼が多く、怒りが 100 に達した |
| 🌀 やりすぎエンド：謝罪の怪物 | 深すぎる礼が多く、怒りが 100 に達した |
| 🌙 質問が尽きたエンド：終わらない会見 | 全質問に答えても怒りが残った |

<p align="right">(<a href="#top">トップへ</a>)</p>

## 実行方法

### ローカルで遊ぶ

[index.html](index.html) をブラウザで開くだけで遊べる。サーバーもビルドも必要ない。

```bash
git clone https://github.com/aoiHirata/shazai-kaiken.git
cd shazai-kaiken
start index.html
```

（macOS は `open index.html`、Linux は `xdg-open index.html`）

### GitHub Pages で公開する

1. リポジトリの **Settings → Pages** を開く
2. **Source** を「Deploy from a branch」、ブランチを `main`、フォルダを `/ (root)` にして保存する
3. 数分後に `https://aoiHirata.github.io/shazai-kaiken/` で遊べるようになる

### Google Colab で遊ぶ

1. [shazai_kaiken_colab.ipynb](shazai_kaiken_colab.ipynb) を Colab で開く（Colab の「ファイル → ノートブックを開く → GitHub」からも開ける）
2. セルの ▶ を押す（初回は数秒かかる）
3. 画面を大きくしたいときは、セルの「画面の高さ」スライダーを上げてもう一度実行する

<p align="right">(<a href="#top">トップへ</a>)</p>

## カスタマイズ

ゲームの調整は [index.html](index.html) の `<script>` 内の定数を書き換えるだけでできる。

| 定数 | 内容 |
| ---- | ---- |
| `CFG` | 怒りの初期値・上昇速度・誤差の許容範囲・コンボの倍率などの基本設定 |
| `DIFFS` | 難易度ごとに `CFG` を上書きする値 |
| `REPORTERS` | 記者の名前・性格・怒りやすさの倍率 |
| `QUESTIONS` | 質問文（`t`）、正解の角度範囲（`a`）、秒数範囲（`s`）、担当記者（`r`） |
| `STORY` | 会社名（`company`）などの設定 |
| `ENDINGS` | 結末のタイトルと文章（`{社名}` はゲーム中の会社名に置き換わる） |

<p align="right">(<a href="#top">トップへ</a>)</p>

## トラブルシューティング

### 音が出ない

ブラウザの仕様で、ページを一度クリック（タップ）するまで音は鳴らない。ゲーム画面を一度クリックしてから遊ぶこと。Colab 版でも同様である。

### スペースキーで頭が下がらない

ゲーム画面にフォーカスが当たっていない可能性がある。ゲーム画面を一度クリックしてからスペースキーを押すこと。Colab 版ではセルの出力部分をクリックする。

### 自己ベストや難易度が保存されない

プライベートブラウズ（シークレットモード）や、サイトデータを保存しない設定では `localStorage` が使えないため記録が残らない。ゲーム自体は問題なく遊べる。

### GitHub Pages の URL が 404 になる

Pages の設定直後や更新直後は、反映に数分かかる。少し待ってから再読み込みすること。

<p align="right">(<a href="#top">トップへ</a>)</p>

## 注記

- 登場する会社・人物・出来事はすべて架空である
- 実在の企業・人物・事件とは関係ない

<p align="right">(<a href="#top">トップへ</a>)</p>
