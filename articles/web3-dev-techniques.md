---
title: "Web3開発テクニック50選を紹介"
emoji: "🐶"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["NFT", "Solidity","Firebase","nextjs","ethersjs"]
published: true
---

Web3開発テクを片っ端から紹介します。
30以上のWeb3プロジェクトの開発を牽引する中で会得しました。
多種多様な要件を求められてきましたが、ここで紹介するテクを組み合わせることで全て対応できました。

*この記事はこんな方にお勧め*👇
🐶「Web3プロジェクトの開発リーダー」
🦉「Web3プロダクトの機能追加を担当するエンジニア」

## 前提

- 主にNFT領域等のアプリケーションレイヤーの開発を想定しています(dAppsの中でもエンドユーザーに近いポジション)
- ブロックチェーンそのものの開発や、複雑なDeFiプロトコルの開発は対象としていません
- 主にスタートアップによる開発を想定しています

## Web3開発テクニック一覧

:::message
本当は一つ一つについて詳しく解説したいところですが、手が回らなさそうです。
(やることが..やることが多い..!!)
ただ、Web3開発の現場で働いている方なら本記事の項目をヒントに自走できるかなと思います。
:::

### ✅ リレートランザクション
### ✅ メタトランザクション
### ✅ オラクル
### ✅ スマホからウォレット接続(WalletConnect)
### ✅ SNSログインでウォレット自動生成(Torus Wallet)
### ✅ ウォレットの接続状態をキャッシュ化してUX向上
### ✅ Firebase AuthとMetaMask連携
### ✅ Moralisでウォレットの保有NFTを一覧取得　
### ✅ MoralisでNFT所有者限定のページを実装
### ✅ クローンベースの開発でdApps最速リリース
### ✅ Bunzzの登録スマコンを使ってCode Audit省略
### ✅ Bunzzの登録スマコンを使ってスマートコントラクトエンジニアの採用を省略
### ✅ オンチェーンデータをWeb2DBに重複保持
### ✅ オンチェーンから直接取得することでDBをスリム化
### ✅ OpenSea APIでNFTコレクションのVTやFloor Priceを取得
### ✅ contractAddress&tokenIdからOpenSeaやLooksRareへの遷移ボタンを自動表示
### ✅ QuickNodeの最強RPCで高負荷のTXを通す
### ✅ StripeとFirebaseでNFTのクレカ購入機能を実装
### ✅ NFTプロダクトでStripe審査をパスする裏技
### ✅ Stripeがリジェクトされた時の決済APIの代替
### ✅ Pinataでフォルダ単位のIPFS化
### ✅ InfuraでクライアントからIPFS化制御
### ✅ メタデータのリフレッシュボタンの実装
### ✅ IPFSを脱却してArweaveにメタデータホスティング
### ✅ ERC-721とERC-1155の使い分け
### ✅ トランザクションベースと署名ベースの使い分け
### ✅ 独自コントラクトと共用コントラクトの使い分け
### ✅ コントラクトを生成するコントラクトで独コン実装
### ✅ WLをマークルツリーで実装してガス代節約 
### ✅ Bulk関数でGAS代を節約
### ✅ ERC-721AでGAS代を節約
### ✅ Low GASなL1/L2チェーンを選定することでGAS代を考慮した実装を省略
### ✅ require文を一行足してbot対策
### ✅ publicMintにも上限を設定してbot対策
### ✅ The Graphで高機能なIndexerを作成
### ✅ FirestoreやMoralisでThe Graphを代替
### ✅ Firebase Cloud FunctionsでMint周りをAPI化
### ✅ エンドユーザーがTXを発行する際のガス代を制御
### ✅ Bunzz SDKでWeb3.jsやウォレット周りの実装を代替
### ✅ Notionで爆速で要件定義書を作成&開発スケジュールの遡行を防ぐ
### ✅ Thirdwebでミンティング機能を既存サイトに埋め込み
### ✅ スマコンのコメント部分や関数名を工夫してグロースハック
### ✅ 自作APIでDiscordのNFT認証をカスタマイズ
### ✅ Chakra UIでwalletAddressのコピペ機能を簡単実装
### ✅ Chakra UIでTXやウォレット周りのToastメッセージを簡単実装
### ✅ 各チェーンのBlockchain Explorerへのリンクを自動表示
### ✅ walletAddressから各NFTマケプレへのユーザーページのリンクを自動表示(OpenSea等)
### ✅ collectionAddressから各NFTマケプレ上のNFT詳細ページのリンクを自動表示(OpenSea等)
### ✅ collectionAddressとtokenIdから各NFTマケプレへのNFT詳細ページのリンクを自動表示(OpenSea等)
### ✅ NFTのメタデータでSEOハック
### ✅ フッターからEthereumや金融庁への発リンクを行うことでドメインパワー向上


## 紹介した開発ツール
https://www.quicknode.com?tap_a=67226-09396e&tap_s=3027894-be8de5&utm_source=affiliate&utm_campaign=generic&utm_content=affiliate_landing_page&utm_medium=generic
https://notion.grsm.io/0udc86nsqz1d
https://www.bunzz.dev/
https://moralis.io/
https://infura.io/
https://www.alchemy.com/
https://www.pinata.cloud/


## 終わりに

~~これ数えたら20個以上あるな？？？。~~
「50選」にタイトル修正しました。

本記事が、Bizからの無茶振りや思い付きと戦うWeb3エンジニアの助けになれば幸いです。
皆さんのお勧めテクやご意見も、ぜひコメントで教えてください。

また、各種開発/PMの相談もお気軽にどうぞ🙆
こんなことできます👇
- Web3プロジェクトの企画-開発-運用まで一気通貫で伴走
- Web3開発の内製化支援/研修実施
- Web3開発チームをゼロから採用・組成
- NFTマーケットプレイス開発
- ミンティングサイト開発
- ジェネラティブNFTの企画・開発
- NFTの配布を活用したプロモーション企画の実施
- Web3リサーチ
  
(お問い合わせは[Twitter](https://twitter.com/kyohei_nft)または[こちら](https://business.leadedge-c.com/#contact)からどうぞ)

僕の各種プロダクトもよろしくお願いします🙏
https://nft-hhkun.leadedge-c.com/
https://nori.leadedge-c.com/
https://media.leadedge-c.com/

## 参考資料

[Web2/Web3スタートアップにお勧めの書籍・学習リソース](https://www.notion.so/kyohei-nft/7707ba5b13e24814881d50f032934db7)


