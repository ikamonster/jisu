# ブラウザー拡張機能『字数』

<img src="https://user-images.githubusercontent.com/3040830/168125056-411ffe26-0ef3-4d24-9e81-55e1ecb01bc5.png" alt="screen shot" width="640px"/>

### ダウンロード・インストール
- [Chrome Web Store](https://chrome.google.com/webstore/detail/dgnmohofbgnaacababkedheeannmdohi)
- [Edge Add-ons](https://microsoftedge.microsoft.com/addons/detail/bbclbgdgnkggbgnknlppkkgghfemliap)

<br>

## 概要

選択テキストの文字数を数えるChrome・Edge対応ブラウザー拡張機能です。

対象のテキストを範囲選択して右クリックし、コンテキストメニューから〈字数〉を選ぶとその文字数が表示されます。

### 特長

- 空白・改行の数も報告します
- 含まれる仮名・漢字・英字などの数と比率を表示できます
- 含まれる文の数と文の最大長・平均長を表示できます
- 含まれる表外漢字を表示できます
- 文字数を原稿用紙の枚数に換算できます
- サロゲートペアや結合文字列に対応し、カラー絵文字も正しく数えます
- ウェブページ内で一度実行するかアイコンをクリックすると、以降はテキストを選択するだけで自動的に文字数が表示されます（自動計数モード）
- フォームへの入力文字数も表示できます（自動計数モード時・要設定）
- ショートカットキーに対応しています（要設定）

#### やや専門的な特長

- 通信しません。安全で、オフラインでも動きます
- 自動計数モード時は、テキスト選択中の結果表示をあえて遅延させ、目にとまらない無駄な表示と計算を省いています。このため、CPU性能が限られる環境下でも支障が少なく、電力消費も抑えられます
- 最新のブラウザー拡張機能仕様Manifest V3（MV3）に対応しています

### ご注意

- ウェブページによっては、構造やセキュリティーの制約などにより期待通り作動しないことがあります
- 結果の正確さ・不具合なきこと・提供の継続などについて、開発者は何ら保証しません。また、ご利用に関して生じた損害等について、開発者は一切の責任を負いません

<br>

## 詳細

#### ショートカットキーに対応していますか？

対応しています。ただし、初期状態ではキーを割り当てていません。ブラウザーの ``拡張機能 → キーボードショートカット`` 画面（``chrome://extensions/shortcuts`` または ``edge://extensions/shortcuts``）を開き、お好みのキーを設定してください。

なお、ウェブページによってはキー操作が効かない場合があります。

#### 表外漢字とは何ですか？

常用漢字表（平成22年内閣告示第２号 2,136字種）に含まれない漢字です。常用漢字とは、社会生活一般で多用が認められる日本語の漢字です。義務教育で習い、公文書や報道における漢字使用の基準とされますが、目安であって制限ではありません。表外漢字の報告は、難しい漢字が不必要に使われ過ぎていないかの判断にお役立てください。

#### サロゲートペアとは何ですか？

ブラウザー上のユーザープログラム環境であるJavaScriptは、文字をUTF-16として扱います。UTF-16においては、文字は基本的に16ビットで表されますが、一部の文字は32ビットつまり16ビットの組で表されます。これをサロゲートペアと呼び、適切な扱いが求められます。

下に示す漢字・絵文字はサロゲートペアの例です。当拡張機能はそれぞれ正しく１字と数えますが、一部の拡張機能やウェブアプリケーションでは誤って２字と数えられてしまいます。

``𡈽𦨞𩸽😂🙏🌎``

#### 結合文字列とは何ですか？

UTF-16を含むUnicodeにおいて一部の文字、日本語なら濁点・半濁点を伴う字は、たとえば「ガ」と１字で表せるほか、「カ」と「゛」の合成としても表すことができます。前者を合成済み文字、後者を結合文字列と呼びます。見た目には区別がつかず、現れることが（macOS以外では）まれなため、サロゲートペアと同じく見過ごされやすい要素です。

濁点付きのカナを２字などと数えるのは人間にとって不自然なため、当拡張機能は数える前に結合文字列を合成済み文字にまとめます（NFC正規化）。ただし、合成済み文字の存在しない組み合わせなど、まとめられない結合文字列もあります。

ちなみに、こうした結合は異字体や絵文字の表現にも使われることがあり、合わせて「書記素クラスター」と呼ばれます。

#### 空白とは何を指しますか？

半角スペース、全角スペース、タブのほか、ノーブレークスペース（``&nbsp;``）、N幅スペース（``&ensp;``）、M幅スペース（``&emsp;``）、狭幅スペース（``&thinsp;``）といったHTMLによく使われる空白文字、自動改行や合字の制御に用いられる特殊なゼロ幅文字など、合わせて数十種類の空白を認識します。

#### 制御コードは数えますか？

数えません。改行や空白の一種と見なせるものを除く、特殊な制御コードは人間にとって無意味なため、あらかじめ除外します。いずれにしても、ウェブページにそうした制御コードが含まれることは一般的ではありません。

#### 文の数え方は？

句点・句点に準ずる約物の並び・改行コード・テキスト末尾のいずれかに続く、一連の可読文字列を１文と数えます。

句点には全角終止符“``．``”も含まれます（実数表記の小数点などに全角終止符を使っていると、そこで文が区切られてしまうので注意）。一方、半角終止符“``.``”は句点と見なさないため、英語などの文を数えることはできません。

たとえば“``？　``”のように、疑問符や感嘆符の後に空白がつく場合も句点と見なします（句点に準ずる約物の並び）。

文中に挿入される台詞や注釈のような、カギ括弧や括弧を用いた文の入れ子構造は無視されることにご注意ください。たとえば、“``彼は「ノー（いいえ）」と答えた``”という文は、まとめて15文字の１文と解釈されます。括弧類は特別扱いされず、他の記号や文字と同様に処理されます。

この規則は、入れ子構造における子に句点がある場合に、直感的な文の数と齟齬を生じやすくなります。たとえば、“``彼は「いいえ。違います」と答えた``”という文は、“``彼は「いいえ。``”と“``違います」と答えた``”の２文と解釈されます。

括弧類を特別扱いする例外もあります。行がまるごとカギ括弧や括弧で囲まれている場合（典型的には会話文）は、その中身だけを取り出して文を数えます。

#### 原稿用紙の枚数の計算方法は？

デフォルトは、数えた文字数を400で割る「概算」です。端数は切り上げます。

計算方法はオプション画面で変更できます。用紙の字数×行数を任意に設定できるほか、「マス埋め」計算法を選ぶことができます。ｎ字×ｍ行のマス埋め計算の手順は次のとおり。

1. ｎ個のマスを用意。そのマスに、選択テキストの文字を１字ずつ、空白も含めて書き込んでいく。
2. マスがすべて埋まったら、もしくは改行が出現したら、１行分の処理が完了。次の行に移る。
3. 以上を繰り返し、処理した総行数をｍで割る。端数を切り上げ、原稿用紙の枚数とする。

空白や改行の役割が処理に反映されるため、「概算」よりも実際的な枚数になります。ただし、半角文字やゼロ幅空白にも１マスを使い、禁則処理も省くなど、完全ではありません。

ちなみに、日本人が日本語の文章を読む平均速度は、１分間に500字前後といわれています。計算方法を「概算：可読文字数」にし、用紙の字数を500などに設定すれば、１枚＝１分として文章を読み終える時間の目安ともなるでしょう。

#### 自動計数モードとは何ですか？

テキストの範囲選択操作中、またはフォームへのテキスト入力中（要設定）に、文字数を自動的に数えて即時表示する機能です。

コンテキストメニューから〈字数〉を一度実行するか、メニューバー上の〈字数〉アイコンをクリックすると有効になります。アイコンを再度クリックすると無効に戻ります。ショートカットキーを割り当てることもできます。

ただし、ウェブページによっては機能しない場合があります。

#### 情報収集などに悪用される恐れは？

ありません。悪用の意図のないことはもちろん、デリケートな情報を取得したり外部と通信したりする特別な権限が当拡張機能には与えられていません。また、グーグル・アナリティクスのような使用状況追跡機能も組み込まれていません。

当拡張機能はマニフェスト（拡張機能が利用する機能や権限の宣言）適合・作動審査を経て、各ブラウザー公式ウェブストアでのみ提供しています。インストールした拡張機能の権限は、ブラウザーの ``拡張機能 → 詳細`` 画面で確認できます。

#### 和文の文字数ではなく、欧文の単語数を数えるには？

ブラウザー拡張機能『[語数](https://ikamonster.github.io/gosu/)』をご利用ください。

<br>

## 既知の問題

#### 結果が表示されません・結果の表示が崩れます

次の理由により、当拡張機能が正常に作動しないことがあります。

- 対象ページのHTML構造やJavaScript制御が入り組んでおり、選択テキスト・入力テキストが得られないか不完全となる
- 対象ページのCSS指定やJavaScript制御の干渉を受け、結果表示ウィンドウが崩れる・隠される
- 対象ページにアクセスする権限がない
- 対象ページが通常のウェブページでない（空のタブやブラウザー設定画面など）

なお、ネットワーク上のウェブページではなく、お使いのPC上のHTMLファイル（「file[]()://」で示されるローカルファイル）を対象に作動させるには、ブラウザーの ``拡張機能 → 〈字数〉詳細`` 画面 で「ファイルのURLへのアクセスを許可する」を有効にしてください。

#### フォームの入力文字数が表示されません

フォームの入力文字数表示機能はHTMLのtextarea要素、またはtype属性がtextのinput要素にのみ対応しています。これらはテキスト入力ボックスを構成する最も一般的なHTML要素ですが、ウェブページによっては別の要素が使われていることがあり、その場合は作動しません。また、ウェブページが読み込まれたあと動的に生成されたフォームに対しても作動しません。

#### 報告された文字数が不正確です

ウェブページの原理に由来する、やむを得ない仕様です。報告はあくまでも目安と捉え、著しく誤った結果の出る場所でのご利用は諦めてください。

当拡張機能はブラウザーのAPIから返された選択文字列を素直に数えます。一方、ブラウザー上での文字の表示のされ方はHTML・CSS・フォント等に左右され、たとえ存在していてもユーザーにすべて見えているとは限りません。そのほか絵文字が画像として表示されていたりなど、さまざまな理由により、見かけの文字数と数えた文字数とが異なる場合があります。

また、選択範囲が「親と子のフレームをまたぐ」あるいは「フレーム内の本文と入力フォームとをまたぐ」場合には、APIが完全な文字列を返してくれず、これもやむを得ず不正確な結果となることがあります。しかし、こうしたまれな場合に対応するための追加処理で全体のリソース消費を増やしてしまうのはバランスを欠くと判断し、割り切り仕様としています。今日ではフレームは動画・地図・SNSボタン・広告などの第三者リソースの埋め込みに使われることが専らで、問題となることは少ないはずですが、あらかじめご了承ください。


#### 文字種の含有比率が不正確です

文字種の含有比率はそれぞれ四捨五入して表示しています。そのため、合計が100パーセントちょうどにならない場合があります。

#### 文の数や長さが不正確です

テキスト中のどこからどこまでを一文と見なすかの判定が困難なためです。また、同じ文字列でも、選択範囲によって文の区切りの解釈が変わることがあります。

日本語の書き方は多様であり、約物の使用規則も統一されておらず、さらに外国語を交ぜて書くことすら可能です。また、文学的・詩的表現においては文とそうでないものとの境界が曖昧です。文の判定は左様に難しい問題で、高い解析能力を持つ専門のソフトウェアでさえ完全ではありません。こうしたことから、当拡張機能ではいっそ処理効率のほうを優先し、一般的な約物だけを区切りとして単純なアルゴリズムで文を判定しています。よって、報告は目安程度とご理解ください。

#### CPUに負荷がかかります

小説がまるごと掲載されているウェブページで使用するなど、対象のテキスト量によってはCPUに負荷がかかることがあります。今日の標準的なPCにおいては微々たる程度ですが、性能が著しく限られた環境下や、電力消費をわずかでも減らしたい場合は、オプション画面で次の設定をお試しください。

- 「報告する文字の種類」の「かな・カナ・漢字・数字・英字・他」のチェックをすべて外す  
　→ 文字種別のカウント処理が省かれる
- 「文の数と長さを報告」を「しない」にする  
　→ 文の判定処理が省かれる
- 「表外漢字の報告」を「しない」にする  
　→ 表外漢字の検索処理が省かれる
- 「原稿用紙の計算方法」を「なし」か「概算」のいずれかにする  
　→ 複雑なマス埋め計算処理を避ける
- 「自動計数モードへの自動移行」を「しない」にする  
　→ 自動計数処理の不要な実行を避ける
- 「自動計数の滑らかさ」を「遅延」にする  
　→ 自動計数モード時の処理の実行頻度が下がる
- 「自動計数から詳細結果への切替時間」を大きくする  
　→ 自動計数モード時の詳細報告処理の実行頻度が下がる

これでもまだ負荷が重い、不可視コード判定や正規化すら不要、精度や機能性を犠牲にしてとことん軽い処理を求める、という向きには残念ながら当拡張機能は適していません。よりシンプルな他の文字数カウント拡張機能をご利用ください。

<br>

## 主な改版履歴

- バージョン 2.5（※公開申請中）
  - ページをリロード・遷移しても同一タブ内では自動計数モードを維持する
  - 自動計数モードを示すバッジをアイコンに表示
  - 詳細結果のスタイルを改善
  - テーマカラーの種類を追加
- バージョン 2.4
  - フォームへの入力文字数を表示する機能を追加
  - 子フレーム内の文字を数えられない問題をおおむね解消
- バージョン 2.3
  - 詳細結果に文の数、文の最大長、文の平均長の報告を追加
  - UI言語に中国語（簡体字・繁体字）を追加
- バージョン 2.2
  - UIを国際化（i18n）。ブラウザーのUI言語設定が日本語以外なら英語で表示
  - 日本語話者以外には不要であろう機能を標準で無効にする
  - 加える情報がなければ自動計数から詳細結果への自動切り替えをしない
  - Edge Add-onsに公開
- バージョン 2.1
  - ひらがな・カタカナ・数字・その他のカウントを追加
  - 結果表示のレイアウトを変更
  - 表外漢字のカウントを出現数から文字種数に変更
  - 報告する文字の種類、自動計数の滑らかさ、自動計数から詳細結果への切替時間、テーマカラー、表示位置、フォントサイズの設定をオプション画面に追加
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

<hr>
© ika.monster
