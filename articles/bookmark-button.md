---
title: "【簡単】好きなページに飛ぶだけのChrome拡張機能をつくる"
emoji: "🏰"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [chrome, chromeextension, javascript, 初心者]
published: true
published_at: 2023-03-03 10:00
---

## 作成するもの

好きなページに飛ぶだけのChrome拡張機能をつくる方法を紹介します！

![Chrome拡張機能の作成](/images/bookmark-button/demodemo.gif)
*拡張機能の位置にブックマークが作れるということですね*

## 作成手順

### フォルダを作成

Chrome拡張機能のフォルダを作成します。

`bookmark-button` フォルダの中に以下を作りましょう。

- `background.js` Chrome拡張機能の処理を書きます。
- `icon.png` Chrome拡張機能のアイコンになります。
  - 今回使用したのはこれ。![Chrome拡張機能のアイコン](/images/bookmark-button/extensions-icon.png =32x)
- `manifest.json` 基本情報を書きます。

![Chrome拡張機能のファイル](/images/bookmark-button/files.png =231x)
*これで準備完了！*

### 基本情報を入力

作成するChrome拡張機能の基本情報を入力します。

```json:manifest.json
{
  "name": "Bookmark dg4",
  "version": "1.0.0",
  "manifest_version": 3,

  "action": {
    "default_title": "Bookmark dg4",
    "default_icon": "icon.png"
  },
  "permissions": ["activeTab", "scripting"],
  "background": {
    "service_worker": "background.js"
  }
}
```

### ページ遷移の処理を書く

- ページ遷移の処理を書きます。

  - 今回は、`https://www.dgdgdgdg.com/` に飛ぶようにします。

```js:background.js
chrome.action.onClicked.addListener((tab) => {
  chrome.tabs.create({ url: "https://www.dgdgdgdg.com" });
});
```

### Chrome拡張機能をインストール

- Chrome拡張機能ページ(`chrome://extensions/`)へ行ったら、右上にある「デベロッパーモード」をオンにしたあと「パッケージ化されていない拡張機能を読み込む」をクリック。

  ![Chrome拡張機能のインストール](/images/bookmark-button/install.png)

- 作成したフォルダを選択して、Chrome拡張機能をインストールします。

  ![フォルダ選択](/images/bookmark-button/install2.png)

- ブラウザ右上の拡張機能マークをクリックし、ピン留めしておきます。

  ![ピン留め](/images/bookmark-button/pin.png =321x)

- これで、好きなページに飛ぶだけのChrome拡張機能が完成しました！

  ![Chrome拡張機能の作成](/images/bookmark-button/demodemo.gif)
*スマートなブックマークだなあ*

## 参考

- [2. 実践編 - Chrome 拡張機能を作ろう](https://www2.kobe-u.ac.jp/~tnishida/programming/ChromeExtension-02.html)

- [Manifest file format - Chrome Developers](https://developer.chrome.com/docs/extensions/mv3/manifest/)

- [chrome.action - Chrome Developers](https://developer.chrome.com/docs/extensions/reference/action/)

- [chrome.tabs - Chrome Developers](https://developer.chrome.com/docs/extensions/reference/tabs/)

## 最後までお読みいただきありがとうございます

この記事のいいねや SNS のフォローなど、励みになります！

- Web

  dgdgdgdg についての基本情報はこちら！

  @[card](https://www.dgdgdgdg.com/)

- Twitter

  - メイン

    基本的にこちらにいます

    @[card](https://twitter.com/dg4_design)

  - 豆知識

    毎平日更新。便利な OS の機能やソフトの情報、最新ニュースなどを投稿しています！

    @[card](https://twitter.com/RenRenTipsTree)

- Instagram

  写真の作品を投稿しています

  @[card](https://instagram.com/dg4_design)

- YouTube

  ドラムの演奏動画がほとんどです。たまに映像作品的なものも。

  @[card](https://www.youtube.com/@dg4_design)

- note

  技術的でない、日常的な記事はこちら！

  @[card](https://note.com/dg4_design)
