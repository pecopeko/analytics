# `answer.md` の評価と次の一週間の改善案

作業ログと結果を見る限り、`answer.md` は方向性としては半分正しいですが、結論を強く出しすぎています。特に問題なのは、サンプル数が少ないのに因果を断定している点と、規約リスクの高い施策が混ざっている点です。

前提データ:
- `done.md` で確認できる実施施策は 4 本
- `result.md` で確認できるインストールは `2/28 GoGoBombs 1件`, `3/3 Gymty 1件`, `3/5 GoGoBombs 1件`
- ストアインプレッションは `Gymty 42`, `GoGoBombs 29`

## 総評

評価は `60/100` です。

良い点:
- 「露骨な宣伝より、コンテンツとして先に価値や面白さを出す」という方向は妥当
- GoGoBombs と Gymty で勝ち方を分けるべき、という視点も妥当
- ストア発見性が弱いという問題提起も概ね正しい

弱い点:
- `1件` のインストールを特定施策の成果とみなしている
- `3/5` の GoGoBombs インストールがあるのに、引用RTを「効いていない」と切っている
- Reddit、Discord、Google Maps コメントなど、規約やコミュニティ反応を踏まえると再現性が低い施策が混ざっている
- 「YouTube Shorts は TikTok より伸びやすい」など、今のデータでは言えない仮説がある

## 仮説ごとの評価

### 1. 「宣伝色の薄いバズコンテンツ + コメ欄誘導」が最もCVRが高い
評価: `一部正しいが、言い切りすぎ`

理由:
- TikTok の公式クリエイティブ資料では、最初の数秒のフック、自然な文脈、クリエイターらしい語り口が重要とされている。つまり「広告っぽさを薄くする」方向は合っている
- ただし、今回のデータでは `2/26` の動画と `2/28` のインストールが本当に因果でつながっているかは確定できない
- しかも「コメ欄誘導」が効いたのか、「動画を見たあと検索された」のかも分からない

修正後の仮説:
- `宣伝色の薄い動画` は有望
- ただし `コメント欄誘導が最適` まではまだ証明できていない
- 次週は `動画ごとに別リンク` を発行して計測すべき

### 2. 「他人のコンテンツへの寄生型マーケはリーチが限定的」
評価: `方向性は理解できるが、現時点では結論が早い`

理由:
- 引用RTやコメント営業は、自分で表示面をコントロールできないので、再現性が低いのはその通り
- ただし `3/5` に GoGoBombs のインストールが発生しているため、`3/5` 実施の引用RTが全く効かなかったとは言えない
- よって「効かない」ではなく、「低コントロールで主戦略にしづらい」が正しい

修正後の仮説:
- `他人の投稿にぶら下がる施策` は補助施策にはなる
- ただしメインにすべきではない

### 3. 「ストアインプレッションが根本的に足りない」
評価: `ほぼ正しい`

理由:
- `Gymty 42`, `GoGoBombs 29` は、1週間の母数としてかなり少ない
- 一方で `3/3` の Gymty インストールは、同日のSNS施策が見当たらないので、ストア内発見や外部からの遅延流入の可能性がある
- つまり「ストア内発見はゼロ」ではない

修正後の仮説:
- `今の最大ボトルネックは発見量`
- ただし `SNSだけ` で考えず、ストア流入計測と ASO の改善余地も同時に見るべき

### 4. 「GoGoBombsの方がSNSマーケとの相性が良い」
評価: `方向性は正しいが、まだ仮説止まり`

理由:
- ゲームは SNS で語れる切り口が多いので、Gymty よりコンテンツ化しやすい
- ただし、まだインストールは `2件` だけで、十分な証拠とは言えない
- Gymty は「全国バズ」より「地域・利用者文脈」で勝つタイプなので、単純比較がずれている

修正後の仮説:
- `GoGoBombs は全国向けSNSで伸ばしやすい`
- `Gymty はローカルSNS・コミュニティで伸ばすべき`

## アクションごとの評価

### 採用してよい

1. `GoGoBombs の短尺動画を複数本出す`
- 良い
- ただし「VALORANTあるある」だけだとアプリ固有価値が薄くなる
- `戦略判断クイズ`, `この場面どう動く？`, `エイム無しでも勝敗が決まる理由` のように、アプリの独自性に近い切り口に寄せた方がいい

2. `Xで戦略クイズ投稿`
- 良い
- ただし来週すぐのインストール獲得というより、`反応が取れる論点の探索` と `フォロワー基盤育成` の意味合いが強い

3. `Gymty を地域コミュニティで紹介`
- 良い
- ただし「アプリ宣伝」ではなく、「今週末どこが空いてるかを探すのが面倒な人向けの便利ツール」として価値先出しにするべき

### 条件付きで採用

4. `Reddit 投稿`
- 条件付き
- Reddit公式ヘルプでも、各コミュニティのルール順守が前提
- 大きいゲーム系サブレは自己宣伝への許容度が低いことが多い
- いきなり本丸サブレに投稿するより、まず通常参加か、`modmail` で確認してからが安全

5. `Discord で紹介`
- 条件付き
- 参加実績がない状態の投下は、ほぼスパム扱いになる
- やるなら「宣伝」ではなく「ゲームバランスや戦略理解のフィードバック募集」に寄せる

6. `YouTube Shorts に解説投稿`
- 良い
- ただし `TikTok より伸びやすい` は現時点で根拠不足
- 同じ題材を TikTok と Shorts に同時投稿し、`視聴維持` と `ストア流入` を比較すべき

### 非推奨

7. `Googleマップの体育館レビューにアプリ紹介コメント`
- 非推奨
- Google Maps の投稿ポリシーは「実体験に基づくこと」を求めており、関係ない宣伝は削除や制限の対象になりやすい
- Gymty は地域密着で相性が良さそうに見えるが、このやり方は長期で資産にならない

## 次の一週間でやるべきこと

結論として、次週は `施策数を増やす` より先に `計測できる実験に作り直す` のが最優先です。今のままだと、たまたま入った 1 件を誤学習して、間違った方向に最適化する可能性が高いです。

### 最優先: 計測を入れる

3/9 にやること:
- App Store Connect で投稿ごとの `campaign link` を作る
- Google Play 側は投稿ごとに `referrer` を分ける
- `TikTok-1`, `TikTok-2`, `Shorts-1`, `X-quiz-1` のように施策単位で名前を固定する
- 来週以降は `再生数` ではなく `ストア到達` と `インストール` で評価する

この工程がないと、次の週も「たぶんこれが効いた」で終わります。

### GoGoBombs: 次週の実験

優先順位は `高` です。

やることは 3 本で十分です。

1. `短尺動画を3本`
- テーマを変える
- `あるある` 1本
- `戦略クイズ` 1本
- `なぜこのラウンドは負けたか` 1本
- すべて冒頭 3-6 秒で問いを出し、途中で盤面や判断を見せ、最後に軽くアプリへ接続する

2. `同じ動画を TikTok と YouTube Shorts の両方に出す`
- 「どっちが伸びるか」を思い込みで決めず、同条件比較にする

3. `マイクロクリエイター or 小規模アカウント 10件に声かけ`
- VALORANT の解説、小ネタ、コーチング、クリップ編集をしている小規模アカウントに絞る
- 依頼内容は「宣伝してください」ではなく、「1本だけ、あなたの文脈で触れてほしい」にする
- 今のSNSは、本人発信より `その界隈の顔` を借りる方が初速が出やすい

### Gymty: 次週の実験

優先順位は `中` です。

やること:

1. `Sora動画ではなく、実画面の15-20秒デモを2本`
- 「空き状況を見るまで何タップか」
- 「Webよりどこが楽か」
- Gymty は面白動画より、即理解できる便利さの方が強い

2. `地域文脈のある投稿を3本`
- 例: 「体育館予約前に、空きをスマホで一気に確認したい人向け」
- 例: 「バドミントン/バスケ利用者向けに、確認の手間を減らすツールを作った」
- 全国向けの薄い訴求ではなく、利用シーンを具体化する

3. `地域コミュニティに5件だけ丁寧に投下`
- Facebook グループ、地域スポーツ系 X アカウント、サークル管理者など
- 数をばら撒くより、相手文脈に合わせて書き分ける

## やめるべきこと

- `コメント欄営業を主戦略にする`
- `規約グレーな場所に投下する`
- `AI動画が伸びた = アプリ訴求が刺さった` と解釈する
- `再生数` を成功指標にする

## 来週の判定基準

次の週は、以下で判断するのがいいです。

- どの投稿が `ストア到達` を生んだか
- どの投稿が `インストール` までつながったか
- `GoGoBombs` では `どの切り口` が一番保存・コメント・クリックに強いか
- `Gymty` では `地域文脈` と `実用デモ` のどちらが強いか

再生数だけ伸びて、ストア到達が増えないなら、その動画は `認知` で止まっていて獲得には効いていません。

## 参考にした最新の公式情報

- Apple App Store Connect: campaign links で施策別計測が可能  
  [https://developer.apple.com/help/app-store-connect/view-app-analytics/manage-campaigns](https://developer.apple.com/help/app-store-connect/view-app-analytics/manage-campaigns)
- Apple App Analytics: どの外部ソースが product page に送客したか確認できる  
  [https://developer.apple.com/app-store-connect/analytics/](https://developer.apple.com/app-store-connect/analytics/)
- Google Play Install Referrer: 流入元ごとの referrer 計測が可能  
  [https://developer.android.com/google/play/installreferrer](https://developer.android.com/google/play/installreferrer)
- TikTok Creative Tips Finder / Strategic Games: 冒頭フック、自然な文脈、ゲーム戦略訴求が重要  
  [https://ads.tiktok.com/help/article/about-the-creative-tips-finder?lang=en](https://ads.tiktok.com/help/article/about-the-creative-tips-finder?lang=en)  
  [https://ads.tiktok.com/business/creativecenter/quicktok/online/creative-tips-for-strategic-games/pc/en](https://ads.tiktok.com/business/creativecenter/quicktok/online/creative-tips-for-strategic-games/pc/en)
- TikTok Creator Marketplace / TikTok One: クリエイター連携と計測の重要性  
  [https://ads.tiktok.com/creative/creatormarketplace](https://ads.tiktok.com/creative/creatormarketplace)
- YouTube Help: 発見は関連性、エンゲージメント、満足度シグナルが重要  
  [https://support.google.com/youtube/answer/9962575](https://support.google.com/youtube/answer/9962575)
- Reddit Help / r/VALORANT: 自己宣伝はコミュニティルールに強く依存  
  [https://support.reddithelp.com/hc/en-us/articles/22755369815700-Running-promotions-on-Reddit](https://support.reddithelp.com/hc/en-us/articles/22755369815700-Running-promotions-on-Reddit)  
  [https://www.reddit.com/r/VALORANT/](https://www.reddit.com/r/VALORANT/)
- Google Maps 投稿ポリシー: 実体験に基づかない宣伝的投稿は不適切  
  [https://support.google.com/contributionpolicy/answer/7400114](https://support.google.com/contributionpolicy/answer/7400114)
