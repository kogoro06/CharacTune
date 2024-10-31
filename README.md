# CharacTune

## ■ サービス概要
CharacTuneは、楽曲を軸に、キャラクターや作品、実在の人物といったさまざまな要素を結びつけるレコメンデーションサービスです。ユーザーが楽曲名を入力すると、その曲のテーマや雰囲気に合ったキャラクターや作品、著名な人物を提案し、新たな関連性を発見する手助けをします。また、キャラクター名や作品名を入力することで、そのイメージに合う楽曲の提案も可能です。提案結果には関連リンクが付いており、楽曲の視聴やキャラクターの詳細確認が簡単にでき、音楽とエンタメが交わる新しい体験を提供します。

## ■ このサービスへの思い・作りたい理由
アニメやゲームのキャラクター、作品、実在の人物には独自の個性や背景があり、ファンがその世界観に浸るために音楽を通じてさらに楽しんでもらいたいという思いから、CharacTuneを考案しました。キャラクターや作品が持つ雰囲気に合う音楽を提案することで、ユーザーが新しい楽曲や関連キャラクターとの出会いを楽しめるサービスを目指しています。特に、日本文化の一部であるアニメや音楽のつながりを深めることで、より多くの人に日本のエンタメを楽しんでもらいたいと考えています。

## ■ ユーザー層について
- **エンタメファン:** キャラクターや作品のイメージに沿った音楽を提案することで、アニメやゲームといったエンタメ作品が好きな人に音楽を楽しんでもらえます。
- **音楽好き:** 音楽好きなユーザーにも、その楽曲のイメージに合うキャラクターや作品を紹介し、新しい楽しみを提供します。
- **日本文化に興味のある海外ユーザー:** アニメや日本の音楽に関心があり、日本のエンタメを深く理解したいユーザー層に向けても、日本のエンタメに触れるきっかけを提供します。

## ■ サービスの利用イメージ
ユーザーは好きな楽曲名を入力するだけで、その曲に合ったキャラクターや作品、実在の人物の提案を受けられます。提案されたキャラクターや作品には関連リンクも提示され、簡単にコンテンツを楽しむことが可能です。逆にキャラクターや実在の人物、作品を入力することでも、関連する楽曲の提案を受けることができ、新しい楽曲との出会いも期待できます。

## ■ ユーザーの獲得について
- **SNSでの拡散:** TwitterやInstagramなどのSNSで、提案結果を簡単に共有してもらうことを促進します。ユーザーが自身の体験を投稿することで、アプリの楽しみ方を広め、認知度を向上させる狙いがあります。
- **コミュニティでの拡散:** シェアハウスやRUNTEQのコミュニティ内で宣伝を行い、様々な人にアプリを触ってもらい、拡散していくことを目指します。

## ■ サービスの差別化ポイント・推しポイント
CharacTuneは、他のレコメンデーションサービスとは異なり、楽曲とアニメやゲームのキャラクター、作品、実在の人物の「イメージ」に合わせた提案に特化しており、キャラクターの性格やストーリーに基づく楽曲を提案することで、ユーザーにとって新鮮でユニークな体験を提供します。これにより、アニメやゲームのファンがキャラクターの世界観を音楽を通じてさらに楽しめる場となります。

## ■ 機能候補

### MVPリリース時に作っておきたい機能
1. **検索機能:** キャラクター、作品、楽曲名を入力して、myGPTs APIを用いた楽曲提案を取得。
2. **提案結果の表示:** 提案された楽曲やキャラクターの説明、関連リンクの表示。
3. **逆提案機能:** ユーザーがキャラクター名や作品名を入力することで、そのイメージに合う楽曲を提案する。

### 本リリースまでに作りたい機能
1. **フィードバック機能(完全版):** 提案内容に対してチャットで会話できる機能を追加し、ユーザー自身で提案できる機能も追加。
2. **パーソナライズ提案:** ユーザー履歴に基づいた提案の精度向上。
3. **SNSシェア機能:** 提案楽曲やお気に入りキャラクターをSNSでシェア可能に。
4. **テーマ別提案:** 「元気が出る」「切ない」など特定テーマに沿った楽曲やキャラクターの提案。
5. **キャラクターや作品の情報リンク:** 提案されたキャラクターや作品の詳細ページへのリンクを自動的に取得して表示。
6. **ユーザーアカウント機能:** ユーザー登録と検索履歴の保存、ユーザーごとに検索結果を管理。

## ■ 機能の実装方針予定

1. **myGPTs API連携（検索機能）**
   - ユーザーが入力したキャラクター名や作品名、楽曲名を受け取るフォームを作成。RailsのNet::HTTPやHTTPartyを使用して、myGPTs APIにリクエストを送信し、受け取ったレスポンスから提案された楽曲やキャラクター情報を抽出して表示。

2. **楽曲視聴リンク表示**
   - 提案された楽曲の情報に基づいて、YouTube APIを用いて視聴リンクを取得。楽曲名をAPIにクエリとして送信し、得られたレスポンスから視聴リンクを抽出して表示。

3. **提案履歴保存**
   - RailsのActiveRecordを使用して、ユーザーの検索履歴やお気に入りをデータベースに保存。ユーザーが検索した内容や提案結果をHistoryモデルとして管理し、user_idでユーザーと関連付けて保存。

4. **ユーザー提案機能**
   - 提案された楽曲やキャラクターの下に「このキャラクターに合う楽曲を提案」や「この曲に合うキャラクターを提案」といったボックスを設け、ユーザーが自分の提案を入力できるフォームを作成。入力された提案はデータベースに保存し、他のユーザーが閲覧できるようにする。

## myGPTs APIの使用方法:

APIリクエスト: ユーザーが入力したキャラクター名、作品名、または楽曲名を取得し、リクエストをmyGPTs APIに送信します。この際、Net::HTTPやHTTPartyを使用し、JSONフォーマットでリクエスト内容を整形します。
レスポンス処理: APIのレスポンスから、提案された楽曲やキャラクター情報を抽出し、表示用データを生成します。

## YouTube APIの使用方法:

楽曲視聴リンク取得: 提案された楽曲の名前をYouTube APIにクエリとして送信し、視聴リンクを取得します。
結果の表示: 得られたレスポンスからURLを抽出し、提案楽曲の視聴リンクとしてユーザーに表示します。
