---
title: "DApps/Web3開発の技術構成の紹介"
emoji: "👻"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Solidity","Ethereum","DApps","NFT", "ethersjs"]
published: true
---

DApps/Web3開発を行う際の技術構成がFIXしたので共有させて頂きます💪

*この記事はこんな方にお勧め*👇
🐶「Web3プロジェクトの開発リーダー」
🐱「技術構成を模索している個人開発者」
🦉「Web3企業の開発体制に興味がある」

## 想定

開発するプロダクトや開発体制の想定としては下記となります👇
- Web2側の実装(認証処理やDB連動, UX等)の開発工数が重く、その上でWeb3側の実装がある
- 少数精鋭&最速リリース&リソースが限られている中での開発体制
- よりアプリケーションレイヤーに近いDAppsの開発(例えばNFTマケプレやWeb3ツールの開発等。一方でBunzz等のWeb3インフラならGolang等採用した方が良いと思います)
## 技術構成
### アプリケーション開発

| | |
| ---- | ---- |
|`Language`|TypeScript| 
|`Frame work`|Next.js(React.js)| 
|`Directory Structure`|bulletproof-react | 
|`Styling Library`|Chakra UI| 
|`State Management`|Recoil| 
|`Backend`|Firebase(Firebase Auth, Firestore, Cloud Functions)| 
|`Web2-Web3 Bridge`|Ethers.js, Bunzz SDK, Moralis | 
|`Wallet Library`|Web3Modal, WalletConnect, Torus|
|`Fiat Payments API`|Stripe|
|`Linter/Formatter`|ESLint, Prettier, VSCode|
|`Testing`|Cypress|
|`UI Tool`|Storybook|


TypeScript + Next.js + Firebaseという、スタートアップの典型的な技術構成ですね。
また、「ディレクトリ構成はbulletproof-reactを踏襲」「状態管理はRecoilを使用」等モダンな技術スタックを採用するように努めています。

さて、スマートコントラクトの印象が先行するDApps開発ですが、実は**開発タスクの中でスマコンが占める割合は1~2割程度**です。
**DApps開発においてはむしろWeb2開発の体制構築・最適化の方が重要**だと思います。
(Web2部分についてはほぼ[os-shun](https://zenn.dev/os_hun)の提案です。神)

また、Linter/Formatterについては最強の設定で運用できている自負があります([os-shun](https://zenn.dev/os_hun))がほぼ一人で作り切ってくれました。神を超えた神)
また、VSCodeの共用設定を `.vscode` に入れていて、非常に便利です。
VSCodeの共用設定については別記事で解説予定です。脳死で入れるべき拡張機能とか。

ユーザー認証周りはFirebase AuthのCustom Token, Ethers.jsの署名, Web3Modal等を併用しています。
これだけで重いテーマなので、詳しくは別記事で取り上げます。

:::message
🤔「Indexerについての記載がない?」
と思った方はつよくて信頼できるDApps開発者です。
通常、The GraphのようなIndexerを使用することが多いと思います。
しかし、弊社ではIndexer的役割をFirestore+Ethers.js+Moralisで代替しています。
The Graphを扱えるエンジニアがいないわけではないのですが、弊社の諸要件から考えた結論になります。
詳しくは別途記事で解説予定。
:::

### スマートコントラクト開発

| | |
| ---- | ---- |
| `Language` | Solidity, TypeScript |
| `Framework` | Hardhat |
| `Web2-Web3 Bridge` |  Ethers.js |
| `RPC URL` | Alchemy, QuickNode |
| `Linter/Formatter` | Prettier, VSCode |


元々[Truffle](https://trufflesuite.com/)+[Web3.js](https://web3js.readthedocs.io/en/v1.7.4/)だったんですが、最近[Hardhat](https://hardhat.org/)+[Ethers.js](https://docs.ethers.io/v5/)に移行しました。
Ethers.jsへの移行は元々予定されていたのですが、Hardhatのきっかけは[てんでんさん](https://twitter.com/ytenden)に「HardhatならコントラクトのVerifyがワンタッチでできる」と教えてもらったからです。
ちなみにWeb3.jsとEthers.jsの比較は[こちらの記事](https://zenn.dev/nft/books/410be300912936)を参照ください。

またRPCは基本的にInfuraや[Alchemy](https://alchemy.com/?r=53d41f5c8165b493)で十分かと思いますが、WebSocket Serverを立てたり、高負荷のTXを発行する場合は[QuickNode](https://www.quicknode.com?tap_a=67226-09396e&tap_s=3027894-be8de5&utm_source=affiliate&utm_campaign=generic&utm_content=affiliate_landing_page&utm_medium=generic)を使用しています。
有償のサービスではありますが、「世界で最速のRPC Node」の謳い文句通りに非常に強固なRPCです。

SolidityはLinter/Formatterの設定を模索中です。
TSと違って、ピンとくるベストプラクティスを見出せずにいます。
solhintも試したんですが、うーんという感じでした。
今はVSCode側の設定でPrettierを効かせるようにしています。

:::message
Bunzz CTOの[hitsujiさん](https://twitter.com/hitsuji_haneta_)にも相談させて頂いたんですが、そもそもスマコンはチーム開発というよりほぼ個人開発の延長です。また、デプロイ後の保守もありません(できない)。
短期間にほぼ一人きりでコードを書き切ることを踏まえると、Linter/Formatterの設定をしっかりと用意する必要がそもそもないのかもしれません。
:::

### ツール

| | |
| ---- | ---- |
|`Chat Tool`|Slack|
|`Sprint Manager`|Notion |
|`Source Code`|Github|
|`Code Editor`|VSCode|
|`DB Editor`|dbdiagram|
|`Design Tool`|Figma|
|`JS Tool Manager`|Volta|
|`IPFS Hosting`|Pinata|

こちらもよくあるスタートアップの使用ツール群です。
違いとしてはIPFS管理ツールの存在でしょうか。Infuraが最も有名ですが、[Pinata](https://www.pinata.cloud/)が便利です。Bizメンバーでも扱いやすいです。
また、弊社の特徴としてはNotionを使い倒しています。企画書/要件定義/スプリント管理etc.ドキュメント関連は全てNotionです。
DB設計も元々はNotion上で作成していましたが、最近はdbdiagramを使用することも増えてきました。

## おわりに

皆さんの参考になれば幸いです💪
是非皆さんのお勧めの技術構成やご意見もコメントで教えてください🙏

また、弊社では各種開発・コンサルティングを承っております。

- NFTマーケットプレイス開発
- ミンティングサイト開発
- ジェネラティブNFT開発
- Web3開発の内製化支援
- Web3新規事業の立ち上げ/コンサルティング
- Discordコミュニティ運用/SNSマーケティング

ご相談は[Twitter](https://twitter.com/kyohei_nft)または[こちら](https://business.leadedge-c.com/#contact)までお気軽に💪

-----
## 参考資料

▼記事
[DAppを構成する技術レイヤーと各サービスのカオスマップ](https://lastrust.notion.site/DApp-9a862bc707624d5eb94e09705486552d)
[Ethereum JavaScript Libraries: web3.js vs. ethers.js (Part I)[邦訳]](https://zenn.dev/nft/books/410be300912936)
[Reactベストプラクティスの宝庫！「bulletproof-react」が勉強になりすぎる件](https://zenn.dev/meijin/articles/bulletproof-react-is-best-architecture)
[hardhatからEtherscanにコードを登録する方法](https://zenn.dev/ryo_takahashi/articles/77f4eeb3f9f52b)
[Node.jsのバージョン管理にVoltaを推したい](https://zenn.dev/taichifukumoto/articles/how-to-use-volta)

▼書籍
[プログラミングTypeScript ―スケールするJavaScriptアプリケーション開発](https://amzn.to/3z9FHYJ)
[Reactハンズオンラーニング 第2版 ―Webアプリケーション開発のベストプラクティス ](https://amzn.to/3IN7Doz)
[プロダクトマネジメントのすべて 事業戦略・IT開発・UXデザイン・マーケティングからチーム・組織運営まで](https://amzn.to/3zd7bfY)