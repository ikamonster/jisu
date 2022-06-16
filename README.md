<img src="https://user-images.githubusercontent.com/3040830/172667011-52732b4b-8bfd-4679-939c-41b5d46f9e04.png" alt="screen shot" width="640px"/>

### ダウンロード・インストール
- [Chrome Web Store](https://chrome.google.com/webstore/detail/dgnmohofbgnaacababkedheeannmdohi)
- [Edge Add-ons](https://microsoftedge.microsoft.com/addons/detail/bbclbgdgnkggbgnknlppkkgghfemliap)

<br>

# 概要

選択テキストの単語数・文字数を数えるChrome・Edge対応ウェブ拡張機能です。

対象のテキストを範囲選択して右クリックし、コンテキストメニューから〈単語を数える〉〈文字を数える〉を選ぶと、テキストに含まれる単語数・文字数が表示されます。

## 特長１：単語数に関する多くの情報を表示

- 単語数
  - 単語の最長文字数
  - 単語の平均文字数
- 文の数
  - 文中の最大単語数
  - 文中の平均単語数
- 文字数
  - 可読文字数
  - 空白数
  - 改行数
- 可読性
- 読了時間

## 特長２：文字数に関する多くの情報を表示

- 全文字数
  - 可読文字数
    - 漢字・かな・カナ・外語・数字・記号の数と比率
  - 空白数
  - 改行数
  - 文の数
    - 文の最大長
    - 文の平均長
  - 原稿用紙の枚数
  - 含まれる表外漢字

※〈文字を数える〉機能を使うにはオプション画面で有効にするか、ショートカットキーを割り当てる必要があります。

## 特長３：豊富かつ柔軟な機能

- ショートカットキーに対応
- クリックしなくても自動で単語数／文字数を表示する「自動計数モード」搭載
- フォームに入力した単語数／文字数も自動表示可能
- 単語数・文字数の音声読み上げ機能搭載
- 多くの言語の単語を認識
- 単語を分ける文字を設定可能
- 文を区切る文字を設定可能
- 可読性の測定方法を設定可能（英語向け）
- 表示色を設定可能

## やや専門的な特長

- サロゲートペアや結合文字列も正しく認識します
- 通信しません。安全で、オフラインでも動きます
- 自動計数モード時は、テキスト選択中の結果表示をあえて遅延させ、目にとまらない無駄な表示と計算を省いています。このため、CPU性能が限られる環境下でも支障が少なく、電力消費も抑えられます
- 最新のブラウザー拡張機能仕様「Manifest V3」に準拠しています

## ご注意

- ウェブページによっては、構造やセキュリティーの制約などにより期待通り作動しないことがあります
- 結果の正確さ・不具合なきこと・提供の継続などについて、開発者は何ら保証しません。また、ご利用に関して生じた損害等について、開発者は一切の責任を負いません

<br>

# 詳細

## 共通

### ショートカットキーに対応していますか？

対応しています。ただし、初期状態ではキーを割り当てていません。ブラウザーの「拡張機能 → キーボードショートカット」画面（``chrome://extensions/shortcuts`` または ``edge://extensions/shortcuts``）を開き、お好みのキーを設定してください。

なお、ウェブページによってはキー操作が効かない場合があります。

### 自動計数モードとは何ですか？

テキストの範囲選択操作中、またはフォームへのテキスト入力中（要設定）に、単語数／文字数を自動的に数えて即時表示する機能です。

コンテキストメニューからカウント処理を一度実行するか、メニューバー上の〈字数〉アイコンをクリックすると有効になります。アイコンを再度クリックすると無効に戻ります。ショートカットキーを割り当てることもできます。

ただし、ウェブページによっては機能しない場合があります。

### 音声読み上げ（スピーチ）とは何ですか？

単語数／文字数を音声で知らせる機能です。音量にご注意ください。

|#|選択肢|読み上げるタイミング|
|---|---|---|
|1|ショートカットキー|「選択テキストの単語数／文字数を読み上げる」に割り当てたショートカットキーが押されたとき|
|2|結果表示が妨げられたとき|#1に加え、当拡張機能が正常に作動しないPDFビューワーなどの非HTMLページにおいて、コンテキストメニューから「単語／文字を数える」が実行されたとき（ただし可能とは限らない）|
|3|フォーム入力を除き常に|#1,#2に加え、詳細結果を表示するとき。ただし、フォーム入力の自動計数を除く|
|4|常に|#1,#2に加え、詳細結果を表示するとき|

### 空白とは何を指しますか？

半角スペース、全角スペース、タブのほか、ノーブレークスペース（``&nbsp;``）、N幅スペース（``&ensp;``）、M幅スペース（``&emsp;``）、狭幅スペース（``&thinsp;``）といったHTMLによく使われる空白文字、自動改行や合字の制御に用いられる特殊なゼロ幅文字など、合わせて数十種類の空白を認識します。

### 制御コードは数えますか？

数えません。改行や空白の一種と見なせるものを除く、特殊な制御コードは人間にとって無意味なため、あらかじめ除外します。いずれにしても、ウェブページにそうした制御コードが含まれることは一般的ではありません。

### サロゲートペアとは何ですか？

ブラウザー上のユーザープログラム環境であるJavaScriptは、文字をUTF-16として扱います。UTF-16においては、文字は基本的に16ビットで表されますが、一部の文字は32ビット、つまり16ビットの組で表されます。これをサロゲートペアと呼び、適切な扱いが求められます。

下に示す漢字・絵文字はサロゲートペアの例です。当拡張機能はそれぞれ正しく１字と数えますが、一部の拡張機能やウェブアプリケーションでは誤って２字と数えられてしまいます。

``𡈽𦨞𩸽😂🙏🌎``

### 結合文字列とは何ですか？

UTF-16を含むUnicodeにおいて一部の文字、日本語なら濁点・半濁点を伴う字は、たとえば「`ガ`」と１字で表せるほか、「`カ`」と「`゛`」の合成としても表すことができます。前者を合成済み文字、後者を結合文字列と呼びます。見た目には区別がつかず、現れることが（macOS以外では）まれなため、サロゲートペアと同じく見過ごされやすい要素です。

濁点付きのカナを２字などと数えるのは人間にとって不自然なため、当拡張機能は数える前に結合文字列を合成済み文字にまとめます（NFC正規化）。ただし、合成済み文字の存在しない組み合わせなど、まとめられない結合文字列もあります。

ちなみに、こうした結合は異字体や絵文字の表現にも使われることがあり、合わせて「書記素クラスター」と呼ばれます。

### 情報収集などに悪用される恐れは？

ありません。悪用の意図のないことはもちろん、当拡張機能には外部と通信するための特別な権限がありません。

当拡張機能はマニフェスト（拡張機能が利用する機能や権限の宣言）適合・作動審査を経て、各ブラウザー公式ウェブストアでのみ提供しています。インストールした拡張機能の権限は、ブラウザーの「拡張機能 →〈字数〉詳細」画面で確認できます。

## 単語数に関する詳細

### 文の数え方は？

終止符（半角ピリオド）および終止符に準ずる約物（半角クエスチョンマーク等）＋空白、改行コード、テキスト末尾のいずれかに続く、一連の可読文字列を１文と数えます。これらの約物や改行の扱いは、オプション画面で変更することができます。

### 読了時間の計算方法は？

数えた単語数を「読む速さ」（１分間に読める単語数）で割ります。表示は原則１分単位、１時間以上なら0.1時間単位で四捨五入して表示します（ただし１分未満は常に１分とする）。「読む速さ」は200がデフォルトですが、オプション画面で変更することができます。

### 可読性とは何ですか？

可読性（リーダビリティー）は、テキストの読みやすさを表す定量的な値です。主に英語を対象とし、単語・文・文字・音節などの数から求めます。可読性の値は通算就学年数（学年）に対応づけられ、読者層への適合性の指標として古くから用いられています。

### 可読性の測定方法は？

代表的な下記の測定方法を備えており、オプション画面で選ぶことができます。

|名称|主用途|作成|値|計算式|音節|
|---|---|---|---|---|---|
|[Flesch Reading Ease](https://en.wikipedia.org/wiki/Flesch%E2%80%93Kincaid_readability_tests#Flesch_reading_ease)|全般|1948|得点|206.835 - 1.015 * (単語数 / 文数) - 84.6 * (音節数 ÷ 単語数)|要|
|[Flesch–Kincaid Grade level](https://en.wikipedia.org/wiki/Flesch%E2%80%93Kincaid_readability_tests#Flesch–Kincaid_grade_level)|全般|1975|学年|0.39 * (単語数 / 文数) + 11.8 * (音節数 ÷ 単語数) - 15.59|要|
|[Gunning Fog Index](https://en.wikipedia.org/wiki/Gunning_fog_index)|業務|1952|学年|0.4 * (単語数 / 文数) + 100 * (難読語数 / 単語数)|要|
|[Automated Readability Index](https://en.wikipedia.org/wiki/Automated_readability_index)|技術|1967|学年|4.71 * (文字数 / 単語数) + 0.5 * (単語数 / 文数) - 21.43||
|[Coleman–Liau Index](https://en.wikipedia.org/wiki/Coleman%E2%80%93Liau_index)|教育|1975|学年|0.0588 * (文字数 / 単語数 * 100) - 0.296 * (文数 / 単語数 * 100) - 15.8||
|[SMOG](https://en.wikipedia.org/wiki/SMOG)|健康|1969|学年|1.043 * √(難読語数 * 30 / 文数) + 3.1291|要|
|[Lensear Write](https://en.wikipedia.org/wiki/Linsear_Write)|行政|1966|学年|(難読語数 * 3 + 非難読語数) / 文数 / 2 ※答えが10以下なら1を引く|要|
|[FORCAST](https://en.wikipedia.org/wiki/Readability#The_FORCAST_formula)|実用|1973|学年|20 - (単音節単語数 * 150 / 単語数 / 10)|要|

- FREの得点は値が高いほど読みやすいことを示します。100は小学５年生、０は大学を卒業した専門家の水準です。
- 学年の値は通算就学年数であり、値が低いほど読みやすいことを示します。６は小学６年生、13は大学１年生の水準です。
- 難読語とは、ここでは音節が3つ以上ある単語を指します。
- 音節を要する測定方法は、英語以外の言語では意味をなしません。また、単語の音節を数えるためのCPU負荷が加わります。


## 文字数に関する詳細

### 文の数え方は？

句点・句点に準ずる約物の並び・改行コード・テキスト末尾のいずれかに続く、一連の可読文字列を１文と数えます。たとえば“``？　``”のように、疑問符や感嘆符の後に空白がつく場合も句点と見なします（句点に準ずる約物の並び）。これらの約物や改行の扱いは、オプション画面で変更することができます。

文中に挿入される台詞や注釈のような、カギ括弧や括弧を用いた文の入れ子構造は無視されることにご注意ください。たとえば、“``彼は「ノー（いいえ）」と答えた``”という文は、まとめて15文字の１文と解釈されます。括弧類は特別扱いされず、他の記号や文字と同様に処理されます。

この規則は、入れ子構造における子に句点がある場合に、直感的な文の数と齟齬を生じやすくなります。たとえば、“``彼は「いいえ。違います」と答えた``”という文は、“``彼は「いいえ。``”と“``違います」と答えた``”の２文と解釈されます。

括弧類を特別扱いする例外もあります。行がまるごとカギ括弧や括弧で囲まれている場合（典型的には会話文）は、その中身だけを取り出して文を数えます。

### 表外漢字とは何ですか？

常用漢字表（平成22年内閣告示第２号 2,136字種）に含まれない漢字です。常用漢字とは、社会生活一般で多用が認められる日本語の漢字です。義務教育で習い、公文書や報道における漢字使用の基準とされますが、目安であって制限ではありません。表外漢字の報告は、難しい漢字が不必要に使われ過ぎていないかの判断にお役立てください。

### 原稿用紙の枚数の計算方法は？

デフォルトは、数えた文字数を400で割る「概算」です。端数は切り上げます。

計算方法はオプション画面で変更できます。用紙の字数×行数を任意に設定できるほか、「マス埋め」計算法を選ぶことができます。ｎ字×ｍ行のマス埋め計算の手順は次のとおり。

1. ｎ個のマスを用意。そのマスに、選択テキストの文字を１字ずつ、空白も含めて書き込んでいく。
2. マスがすべて埋まったら、もしくは改行が出現したら、１行分の処理が完了。次の行に移る。
3. 以上を繰り返し、処理した総行数をｍで割る。端数を切り上げ、原稿用紙の枚数とする。

空白や改行の役割が処理に反映されるため、「概算」よりも実際的な枚数になります。ただし、半角文字やゼロ幅空白にも１マスを使い、禁則処理も省くなど、完全ではありません。

ちなみに、日本人が日本語の文章を読む平均速度は、１分間に500字前後といわれています。計算方法を「概算：可読文字数」にし、用紙の字数を500などに設定すれば、１枚＝１分として文章を読み終える時間の目安ともなるでしょう。

<br>

# 既知の問題

## 結果が表示されません・結果の表示が崩れます

次の理由により、当拡張機能が正常に作動しないことがあります。

- 対象ページのHTML構造やJavaScript制御が入り組んでおり、選択テキスト・入力テキストが得られないか不完全となる
- 対象ページのCSS指定やJavaScript制御の干渉を受け、結果表示ウィンドウが崩れる・隠される
- 対象ページにアクセスする権限がない
- 対象ページが通常のウェブページでない（空のタブやブラウザー設定画面など）

なお、ネットワーク上のウェブページではなく、お使いのPC上のHTMLファイル（「file[]()://」で示されるローカルファイル）を対象に作動させるには、ブラウザーの「拡張機能 → 〈字数〉詳細」画面 で「ファイルのURLへのアクセスを許可する」を有効にしてください。

## フォームの入力単語数／文字数が表示されません

フォームの入力文字数表示機能はHTMLのtextarea要素、またはtype属性がtextのinput要素にのみ対応しています。これらはテキスト入力ボックスを構成する最も一般的なHTML要素ですが、ウェブページによっては別の要素が使われていることがあり、その場合は作動しません。また、ウェブページが読み込まれたあと動的に生成されたフォームに対しても作動しません。

## 報告された単語数／文字数が不正確です

ウェブページの原理に由来する、やむを得ない仕様です。報告はあくまでも目安と捉え、著しく誤った結果の出る場所でのご利用は諦めてください。

当拡張機能はブラウザーのAPIから返された選択文字列を素直に数えます。一方、ブラウザー上での文字の表示のされ方はHTML・CSS・フォント等に左右され、たとえ存在していてもユーザーにすべて見えているとは限りません。そのほか絵文字が画像として表示されていたりなど、さまざまな理由により、見かけの文字数と数えた文字数とが異なる場合があります。

また単語は、単語の境界を示す伝統的な正規表現「`\b`」を用いて切り分けています。単語の数え方はこの正規表現の仕様・実装次第であり、一般的な欧文規則や人間の感覚とは必ずしも一致しない場合があります。なおURLとメールアドレスは、分割文字の指定によらず常に１語とみなされます。

さらに、選択範囲が「親と子のフレームをまたぐ」あるいは「フレーム内の本文と入力フォームとをまたぐ」場合には、APIが完全な文字列を返してくれず、これもやむを得ず不正確な結果となることがあります。しかし、こうしたまれな場合に対応するための追加処理で全体のリソース消費を増やしてしまうのはバランスを欠くと判断し、割り切り仕様としています。今日ではフレームは動画・地図・SNSボタン・広告などの第三者リソースの埋め込みに使われることが専らで、問題となることは少ないはずですが、あらかじめご了承ください。

## 文の数や長さが不正確です

テキスト中のどこからどこまでを一文と見なすかの判定が困難なためです。また、同じテキストでも選択範囲によって文の区切りの解釈が変わることがあります。

単語カウントにおいては、先述のとおり極めて単純なアルゴリズムで文を判定しています。見出しや段落といったHTMLの論理構造を知らず（APIから渡される選択文字列はプレーンテキスト）、高度な構文解析をしているわけでもないため、書き手の意図や誤りをくみ取ることができません。たとえば文の途中に整形のための改行が入っていたり、終止符の後に空白を入れ忘れられていたりすることは、人間にとっては理解の妨げにならなくても、単純なアルゴリズムにとってはそうではありません。

文字カウントにおいては、対象のひとつである日本語の書き方はとりわけ多様であり、約物の使用規則も厳密には統一されておらず、さらに外国語を交ぜて書くことすら可能です。また、文学的・詩的表現においては文とそうでないものとの境界が曖昧です。

文の判定は左様に難しい問題で、高い解析能力を持つ専門のソフトウェアでさえ完全ではないことから、当拡張機能ではいっそ処理効率のほうを優先し、“概算”を示すことにしています。よって、報告される文の数は目安程度とご理解ください。

## 可読性の値がおかしい・よそでの測定結果と異なります

下記の理由により、当拡張機能の可読性測定の精度には限りがあります。

- 測定対象となる単語や文の認識が不正確な場合がある
	- 前節・前々節のとおり。
- 音節の判定精度の限界
	- 当拡張機能の音節判定には、英単語の綴りから音節数を割り出す、広く知られる単純なアルゴリズムを採用しています。しかし、実際にはその規則から外れる綴りも多々あります。だからといって、この付加機能のためだけに全英単語の音節を網羅する膨大な辞書を参照してリソースを消費するのはバランスを欠くため、現状の精度で妥協しています。
	- 英語以外の単語には、この音節判定処理は適用できません。
	- これらの欠点は、音節を使わない測定方法を選ぶことで回避できます。
- 古典的測定方法そのものの限界
	- 各測定方法は、いずれも単純な計算式であることからわかるように、ある程度以上の量のテキストを対象とし、統計的な結果を機械的に求めるよう設計されています。そのため、少ないテキストでは内容によって結果が大きくぶれてしまいます。たとえ理想的な条件下でも、得られるのは目安にすぎません。
	- そもそもいくつもの測定方法が考案されていること自体、どの方法も完全でないことを示しています。テキストの読みやすさが、単語や音節の数といった量的要因だけで決まるわけでないことは経験則からも明らかでしょう。結局、読みやすさの最終的な判断は人間が下すしかありません。とはいえ少なくとも、測定値はその補助として役立つ可能性があります。

## 文字種の比率が不正確です

文字種の比率はそれぞれ四捨五入して表示しています。そのため、合計が100パーセントちょうどにならない場合があります。

## 音声読み上げされません

- OSに音声読み上げ機能が備わっており、１つ以上の音声がインストールされている必要があります。PCの音量設定やスピーカー／ヘッドホンの接続もご確認ください。
- 音声データの読み込みなど音声エンジン側の処理の都合により、発声が遅れたりキャンセルされたりすることがあります（特に最初の実行時）。
- クラウドの音声を選んでいる場合、オフラインでは発声できません。
- ウェブページや他の拡張機能が音声読み上げをしている最中には、発声処理が重なってうまく鳴らなかったり聴こえにくくなったりすることがあります。

## 「テキストを数える」において、和文のページなのに単語を数えたり、欧文のページなのに文字を数えたりすることがあります

「テキストを数える」において文字を数えるのは、単語単位での分かち書きを原則しない言語、すなわちチベット語・日本語・クメール語・ラーオ語・ビルマ語・パーリ語・サンスクリット・タイ語・中国語が対象です（バージョン3.2）。これら以外の言語では単語を数えます。

この規則から挙動が外れるとすれば、原因は言語の誤認識です。

言語はブラウザーが認識します。ブラウザーは独自の言語認識アルゴリズムを備えていますが、ウェブページに使用言語が明記されている場合、それを最も重視します。その記述が不適切だと（ウェブサイトを制作・配信している主体の母国語が一律設定されていることが多い）、誤認識の原因となります。また、複数の言語が混在するページでは、必然的に誤認識が起こりやすくなります。

## オプション設定が反映されません

- 当拡張機能を再度実行する・ページをリロードする・ブラウザーを再起動する、のいずれかをお試しください。
- それでも反映されない場合は、設定情報が壊れている可能性があります。お手数ですが、当拡張機能をいったん削除して再度インストールしてください。
- 音声読み上げの音量と音声（言語）はデバイス間で同期されません。適切な値や可能な選択肢が環境によって異なるためです。

## CPUに負荷がかかります

小説がまるごと掲載されているウェブページで使用するなど、対象のテキスト量によってはCPUに負荷がかかることがあります。今日の標準的なPCにおいては微々たる程度ですが、性能が著しく限られた環境下や、電力消費をわずかでも減らしたい場合は、オプション画面で次の設定をお試しください。

- 「自動計数モードへの自動移行」を「しない」にする  
　→ 自動計数処理の不要な実行を避ける
- 「自動計数の滑らかさ」を「遅延」にする  
　→ 自動計数モード時の処理の実行頻度が下がる
- 「自動計数から詳細結果への切替時間」を大きくする  
　→ 自動計数モード時の詳細報告処理の実行頻度が下がる
- 「追加報告」のチェックをすべて外す  
　→ 文や表外漢字の判定処理・検索処理が省かれる
- 「可読性の測定方法」のチェックをすべて外す  
　→ 可読性の計算処理が省かれる
- 「報告する文字の種類」のチェックをすべて外す  
　→ 文字種別のカウント処理が省かれる
- 「原稿用紙の計算方法」を「なし」か「概算」のいずれかにする  
　→ 複雑なマス埋め計算処理を避ける

これでもまだ負荷が重い、不可視コード判定や正規化すら不要、精度や機能性を犠牲にしてとことん軽い処理を求める、という向きには残念ながら当拡張機能は適していません。よりシンプルな他の文字数カウント拡張機能をご利用ください。

## Google Docs で作動しません

技術的な理由です。

Google Docs は、テキスト編集領域をCanvas要素とし、文字列やUI操作を独自に処理・描画している高度なウェブアプリケーションです。当拡張機能が利用しているDOM上のテキストノードおよびその選択処理とは、テキストの扱いがまるで異なります（2022年現在）。これが Google Docs で当拡張機能が作動しない理由です。

他の同様のウェブアプリケーションや、より小規模であってもJavaScriptで制御された独自のテキスト領域（SNSの投稿画面や、Wikiなどのリッチテキスト編集画面に多い）に対しても、当拡張機能は正常に作動しないことがあります。

## 愛用のブラウザーに対応していません

開発に割くことができる時間や資源が限られていることから、当拡張機能は原則として次の条件を満たすウェブ拡張機能プラットフォームのみを対象としています。

1. 普及率の高いPC用モダンブラウザー最新版
2. Manifest V3と最新のAPIに対応しており、コード互換性が高い
3. 特殊な開発環境を要さず、ほぼ無料で配布できる

Firefox 版は、Firefox が Manifest V3 に正式対応し次第リリースする予定です。ただし、利用できるAPIの違いから、一部の機能を省くかもしれません（2022年6月現在）。  
Safari は３に当てはまらないため、今のところ対応する予定はありません。

<br>

# 改版履歴
- バージョン 3.3
  - 可読性の測定方法に「Lensear Write」を追加
  - ショートカットキーに「結果をクリップボードにコピー」を追加。TSV形式の詳細結果と選択テキストがクリップボードにコピーされる
- バージョン 3.2
  - コンテキストメニューに「テキストを数える」（単語か文字か、ブラウザーが検出したページの言語に適したほうを数える）を追加
  - コンテキストメニューに「なし」を追加
  - 認識文字種に点字を追加
- バージョン 3.1
  - 文字を数える
    - 句点とみなす文字の設定を追加
    - 文字種の認識精度を改善
    - 文字種の表示を「値・比率・両方」から選べるようにする
- バージョン 3.0
  - 単語を数える機能を追加
  - 音声読み上げ機能を追加
  - 設定項目を増やしオプション画面を刷新
- バージョン 2.5
  - 同一タブ・同一オリジン内ではページをリロード／遷移しても自動計数モードを維持する（特別な権限を要求しないよう修正）
  - 自動計数モードを示すバッジをアイコンに表示
  - 英字カウントを英字以外の言語も認識するよう拡張
  - 詳細結果のスタイルを改善
  - 表示色の種類を増加
- バージョン 2.4
  - フォームへの入力文字数を表示する機能を追加
  - 子フレーム内の文字を数えられない問題をおおむね解消
- バージョン 2.3
  - 詳細結果に文の数、文の最大長、文の平均長の報告を追加
- バージョン 2.2
  - UIを国際化（i18n）。ブラウザーのUI言語設定が日本語以外なら英語で表示
  - 日本語話者以外には不要であろう機能を標準で無効にする
  - 加える情報がなければ自動計数から詳細結果への自動切り替えをしない
  - Edge Add-onsに公開
- バージョン 2.1
  - ひらがな・カタカナ・数字・その他のカウントを追加
  - 結果表示のレイアウトを変更
  - 表外漢字のカウントを出現数から文字種数に変更
  - 報告する文字の種類、自動計数の滑らかさ、自動計数から詳細結果への切替時間、表示色、表示位置、フォントサイズの設定をオプション画面に追加
- バージョン 2.0
  - ブラウザー拡張機能Manifest V3対応
  - 自動計数の一定時間後に詳細結果を表示するよう変更
- バージョン 1.4
  - 結果表示をアラートダイアログからウェブページ内のオーバーレイ（自動計数モードと同じ）に変更
  - API名前空間を一般化し、Chromium版Edgeでの作動を確認
- バージョン 1.3
  - 自動計数モードを追加
- バージョン 1.2
  - 原稿用紙数換算機能を追加
  - オプション画面を追加
- バージョン 1.1
  - 表外漢字の出現数カウントを追加
- バージョン 1.0
  - 2019年7月 Chrome Web Storeに公開

不具合修正・UI改善などの軽微な改版では、バージョンの３つめの位が上がります（例：「1.0.0」→「1.0.1」）。

