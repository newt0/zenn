---
title: "DApps/Web3開発の技術構成の紹介"
emoji: "👻"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["NFT", "Web3", "dapps","react", "nextjs", ]
published: true
---

DApps/Web3開発を行う際の技術構成が自分の中でFIXしたので共有。

*この記事はこんな方にお勧め*👇
🐶「Web3プロジェクトの開発リーダー」
🐱「技術構成を模索している個人開発者」
🦉「これからWeb3にキャッチアップしたいWeb2エンジニア」

## 技術構成

- 「アプリケーション開発」
- 「スマートコントラクトコントラクト開発」
- 「ツール」
に分けます。

### アプリケーション開発

- `言語`: TypeScript 
- `フレームワーク`: Next.js(React.js)
- `ディレクトリ構成`: bulletproof-react
- `CSSライブラリ`: Chakra UI
- `状態管理`: Recoil
- `Web2バックエンド`: Firebase(Firebase Auth, Firestore, Cloud Functions)
- `Web2-Web3ブリッジ`: Ethers.js, Bunzz SDK, Moralis 
- `Web3ライブラリ`: Web3Modal, WalletConnect, Torus
- `フィアット決済`: Stripe
- `Linter/Formatter`: ESLint, Prettier, VSCode
- `Testing`: Cypress
- `UIツール`: Storybook

TypeScript + Next.js + Firebaseという、スタートアップの典型的な技術構成ですね。
また、「ディレクトリ構成はbulletproof-reactを踏襲」「状態管理はRecoilを使用」等モダンな技術スタックを採用するように努めています。
スマートコントラクトの印象が先行するDApps開発ですが、実は開発タスクの中でスマコンが占める割合は1~2割です。
DApps開発においてはむしろWeb2開発の体制構築・最適化の方が大事です。
(Web2部分についてはほぼ[os-shun](https://zenn.dev/os_hun))が提案してくれました。神)

また、Linter/Formatterについては最強の設定で運用できている自負があります([os-shun](https://zenn.dev/os_hun))がほぼ一人で作り切ってくれました。神を超えた神)
また、VSCodeの共用設定を `.vscode` に入れていて、非常に便利です。
VSCodeの共用設定については別記事で解説予定です。脳死で入れるべき拡張機能とか。

Firebaseの使い方もちょっとクセがあり、Firebase AuthのCustom Tokenとウォレットの署名を併用しています。
これも詳しくは別記事で取り上げます。

:::message
🤔「Indexerについての記載がない...?」
と思った方はつよくて信頼できるDApps開発者です。
通常、The GraphのようなIndexerを使用することが多いと思います。
しかし、弊社ではIndexer的役割をFirestore+Ethers.js+Moralisで代替しています。
The Graphを扱えるエンジニアがいないわけではなく、諸要件から考えてベストであると考えるからです。
詳しくは別途記事で解説予定。
:::

### スマートコントラクト開発

- `言語`: Solidity, TypeScript
- `フレームワーク`: hardhat
- `Web2-Web3ブリッジ`: Ethers.js
- `インフラ`: Alchemy
- `Linter/Formatter`: Prettier, VSCode

元々Truffle+Web3.jsだったんですが、最近Hardhat+Ethers.jsに移行しました。
Ethers.jsへの移行は元々予定されていたのですが、Hardhatのきっかけは[てんでんさん](https://twitter.com/ytenden)に「HardhatならコントラクトのVerifyがワンタッチでできる」と教えてもらったからです。
ちなみにWeb3.jsとEthers.jsの比較は[こちらの記事](https://zenn.dev/nft/books/410be300912936)を参照ください。

SolidityはLinter/Formatterの設定を模索中です。
TSと違って、ピンとくるベストプラクティスを見出せずにいます。
solhintも試したんですが、うーんという感じでした。
今はVSCode側の設定でPrettierを効かせるようにしています。

:::message
Bunzz CTOの[hitsujiさん](https://twitter.com/hitsuji_haneta_)にも相談させて頂いたんですが、そもそもスマコンはチーム開発というよりほぼ個人開発の延長です。また、デプロイ後の保守もありません(できない)。
短期間にほぼ一人きりでコードを書き切ることを踏まえると、Linter/Formatterの設定をしっかりと用意する必要がそもそもないのかもしれません。
:::

### ツール

- `連絡ツール`: Slack
- `バージョン管理`: Github
- `コードエディタ`: VSCode
- `デザイン`: Figma
- `プロジェクト管理`: Notion 
- `DB設計エディタ`: dbdiagram
- `Node.jsバージョン管理`: Volta 
- `IPFS管理`: Pinata
- `RPC`: QuickNode  

こちらもよくあるスタートアップの使用ツール群です。
違いとしてはIPFS管理ツールの存在でしょうか。Infuraが最も有名ですが、Pinataが便利です。
またRPCは基本的にInfuraやAlchemyで十分かと思いますが、WebSocket Serverを立てたり、長時間TXを発行し続ける場合の負荷には耐えられないと思います。そのような場合は有償ではありますが[QuickNode](https://www.quicknode.com?tap_a=67226-09396e&tap_s=3027894-be8de5&utm_source=affiliate&utm_campaign=generic&utm_content=affiliate_landing_page&utm_medium=generic)がお勧めです。
また、弊社の特徴としてはNotionを使い倒しています。企画書/要件定義/スプリント管理etc.ドキュメントは全てNotion。
DB設計も元々はNotion上で作成していましたが、最近はdbdiagramを使用することも増えてきました。

## おわりに

是非皆さんのお勧めの技術構成やご意見もコメントで教えてください🙏

### お知らせ

主に法人向けに各種開発・コンサルティングを承っております。

- NFTマーケットプレイス開発
- ミンティングサイト開発
- ジェネラティブNFT開発
- Web3開発の内製化支援
- Web3新規事業の立ち上げ/コンサルティング
- Discordコミュニティ運用/SNSマーケティング

ご連絡は[Twitter](https://twitter.com/kyohei_nft)または[フォーム](https://business.leadedge-c.com/#contact)までお気軽に✌️


## 参考

[Reactベストプラクティスの宝庫！「bulletproof-react」が勉強になりすぎる件](https://zenn.dev/meijin/articles/bulletproof-react-is-best-architecture)
[hardhatからEtherscanにコードを登録する方法](https://zenn.dev/ryo_takahashi/articles/77f4eeb3f9f52b)
[プログラミングTypeScript ―スケールするJavaScriptアプリケーション開発](https://amzn.to/3z9FHYJ)
[Node.jsのバージョン管理にVoltaを推したい](https://zenn.dev/taichifukumoto/articles/how-to-use-volta)
[Reactハンズオンラーニング 第2版 ―Webアプリケーション開発のベストプラクティス ](https://amzn.to/3IN7Doz)
[プロダクトマネジメントのすべて 事業戦略・IT開発・UXデザイン・マーケティングからチーム・組織運営まで](https://amzn.to/3zd7bfY)