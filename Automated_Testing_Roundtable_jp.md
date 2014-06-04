These are some notes from the Game Developers Conference 2011 roundtable session entitled "Automated Testing Roundtable: Proper Care and Feeding of Your Robot Armies".
#これは、GDC2011で行われたラウンドテーブル「Automated Testing Roundtable: Proper Care and Feeding of Your Robot Armies」の議事録です。
#（タイトルも無理やり訳すと・・・「テスト自動化ラウンドテーブル：あなたのロボット兵隊への適切なケアと餌」）
 
 
 
== Disclaimer / Corrections / Feedback ==
#免責事項、修正、フィードバックについて
 
 
 
These notes are my interpretations of my notes combined with my admittedly flawed and probably biased memory.  If you have corrections, clarifications, other feedback, please feel free to e-mail the account "leander" at the domain "1stplayble.com" (or reply to the mailing list posts).
#このノートには不明確な部分や著者のあいまいな記憶が混ざっている部分があります。もし正確な解釈やフィードバックがあるなら著者にメールをするか、メーリングリストにポストして下さい。
 
 
Generally I'm going to speak with an imperative voice for brevity -- these are, however, not necessarily my opinions or the opinions of my employer; they represent a simplified version of what was discussed at the time.  Any and all omissions and errors are solely my own.
#通常、簡潔な発言を義務付けています、が、～～～？？？。省略や失敗がある部分は私の～～です。
 
 
These are mostly in the same order that they were discussed, but there is some reorganization to clump related topics together.
#議論されたのと同じ順に書いていますが、一部関連するトピックをまとめて再編集しています。
 
 
Finally, all of these comments lack attribution; since I feel I cannot be 100% accurate in attribution, I'd prefer to avoid the issue entirely.  If you contributed something and would like a note to that effect, drop me a line.
#最後に、全てのコメントの発言者？（attribution）は書いていません。理由は100%正確に書くことができないため、全く無い方が良いと思ったからです。その後の文？？？、もし貢献してくれるならその点を心にとめて、ご一報下さい？
 
 
And a big _thank you_ to everyone who contributed to the sessions!
#そしてこのセッションに貢献してくれた全ての人にありがとう！
 
 
 
== Day 1 (Wednesday) ==
#1日目
 
 
 
The suggested topic of day 1 (Wednesday) was specific tests: what proved useful, and why.
#1日目のトピックはテストについて具体的に：何が有効でその理由は？
 
 
Attendees were mostly programmers, although we did have a handful of QA and production folks as well.
#出席者はほとんどプログラマー、しかし少数のQAと生産の人も居た。
 
 
 
=== Simple Tests, Scheduling, and Tools ===
#シンプルなテスト、スケジューリング、ツール
 
 
 
We opened with a discussion of what were the simplest tests that had the greatest returns/usefulness.
#まず、最も効果が高くて実用性のある最もシンプルなテストについての議論から始めようと思います。
 
 
* Prefer basic functional tests to unit tests when starting to test an existing project.
* Find specific "hotspots" -- areas of difficulty/interest for your particular project.
* Leverage already-extant systems that record and play back gameplay to produce additional metrics.
* Parse existing TTY output, or add some more output to an existing TTY logging system, to quickly bootstrap initial tests.
* Start with "does the game load?", and "does each level load?" smoke tests.
* A visual scripting system is a great place to have small tests.
#*既存のプロジェクトのテストを始める場合は、ユニットテストよりも基本的な機能テストを好む
#*明確な「ホットスポット」を見つける。プロジェクト特有の複雑な部分やありそうな部分に注目する
#*既存のシステムを活用する：ゲームプレイの記録と再生ができ、追加のメトリクス情報を生成する。
#*TTY（標準出力）出力をパース、もしくは既存のTTYログシステムにさらに出力を追加して、すぐに最初のテストをブートストラップ（今あるものだけで何とか）します。
#*「ゲームがロードされているか？」「それぞれのレベルがロードされているか？」というスモークテストから始める。
#*視覚的なスクリプトシステムは、小さなテストを行うための素晴らしい環境です。
#http://forum.unity3d.com/threads/54580-Visual-Scripting-System
#http://www.extremetech.com/article2/0,2845,1152028,00.asp
 
 
There was some concern about accumulated technical debt as it relates to maintaining the testing infrastructure.  Keep things simple to start to help defer this.
#テストインフラを整える事と関連して、累積された技術的な負債があると思います。物事をシンプルにして、これらの問題は先送りにして始めましょう。
 
 
Simple pass/fail reporting is sufficient for basic tests.  [More sophisticated reporting was covered in later discussions/days.]
#単純な通過/失敗レポートは基本テストとして充分です。（より精錬されたレポーティングについては後日の議論でカバーされています）
 
 
Some studios have the ability to run tests before committing changes.  "Local versions" of tests are beneficial even if they have to be stripped down somewhat relative to their more full-featured counterparts.
#変更をコミットする前にテストを実行する（能力のある）スタジオもあります。"ローカル版"テストは、よりフル機能に対応したものと比べて幾分取り除かれてるとしても有益です。
 
 
Tests are not all-or-nothing; it's wise to have a mixture of immediate (before commit and post-commit) and deferred testing (e.g. scheduled daily).  Defer anything that slows down build iteration time significantly.
#テストは、オールオアナッシングではない。すぐにやらなくてはならない（コミット前、かコミット後）ものと、猶予のあるテスト（デイリーでスケジュール化されたもののように）両方ある。ビルドイテレーション時間を大きく遅らせるようなものは後でやるべきだ。
 
 
It may be useful to allow "expected to fail" tests in some cases.
#「失敗を期待する」テストはいくつかのケースで有用だろう。
 
 
The choice of viable "next targets" for testing is at least partly the responsibility of project leads and producers.
#テストのための「次のターゲット」をどう選択していくかの計画実行には、少なくとも部分的にはプロジェクトリーダーやプロデューサーが責任を持つ。
 
 
The setup and layout of your version control system is important; it may dictate what's easy and hard to automate.
#バージョン管理システムのセットアップやレイアウトは重要だ。それは自動化が容易か難しくなるかに影響する。
 
 
How do people drive tests?  Many use a continuous integration build server or test suite management system.  At least the following were mentioned on the first day (these are CI / continuous build unless otherwise noted):
#どうやってテストを運用していますか？多くの人はCI（continuous integration）ビルドサーバーか、テストスイート管理システムを使用しているでしょう。少なくとも1日目には次の内容を話し合います。（CI/継続ビルドについて）
 
 
* TeamCity 
* Pulse Continuous Integration Server
#http://zutubi.com/products/pulse/ , http://zutubi.com/sales/
* Hudson [forked to "Jenkins"]
* CruiseControl.NET
* Buildbot
* Bitten (automated metrics collection for Trac)
#http://bitten.edgewall.org
* Cucumber (behavior-driven testing)
#http://cukes.info/
* BugSplat (drop-in crash tracking)
#http://www.bugsplatsoftware.com/
#BugSplatはあなた自身の製品のエンドユーザーがクラッシュを追跡するためのツールの包括的なセットを提供しています。 BugSplatを使用すると、簡単には、ユーザーがクラッシュを監視し、ライブラリを統合して取得します。クラッシュのイベントでは、ユーザーは、オンラインサービスへのクラッシュ情報をアップロードするオプションが与えられます。あなたのエンジニアリングチームはBugSplatのWebサイトにあるすべてのクラッシュ情報を閲覧することができます象徴呼び出し、実際の問題を特定するために使用できるスタックを含む貴重な情報へのアクセスを持っています。オンラインクラッシュ報告はあなたの傾向を分析し、最も一般的なユーザーがクラッシュを分離するツールの広いセットを提供します。(Featuresを機械翻訳)
 
 
It's valuable to have a "command line parser" built into the game; your CI build can execute e.g. "rungame.exe alltests" as a post-build step.
#ゲームに「コマンドラインパーサー」を組み込む事は役に立ちます：例えばCIビルドが「rungame.exe alltests」のようにビルド後のステップを実行する事ができます。
 
 
 
 
=== Input Driving ===
#入力の扱い
 
 
 
Make good use input recording / driving / playback: a "monkey" that randomly presses buttons or travels in random directions is used by more than a few teams.
#入力の記録・運用・プレイバックをうまく使おう：ランダムにボタンを押したりランダムな方向に向かって動く「モンキー」は少なくともいくつかのチームで使われている。
 
 
If a random-walk bot gets "stuck", use heat map data from prior game runs to teleport it back to a frequently traveled location, possibly report the "sticky" place, and continue testing.
#もしランダムに歩かせるボットが動きがとれなくなったら、前のゲーム実行のヒートマップデータを使って頻繁に移動している場所にテレポートして戻す、その時「厄介な」場所としてレポートを残すかもしれない、そしてテストを継続する。
 
 
The use of automated UI/menu traversal varies widely per team and per product:
#UIとメニューの横断テストの自動化はチーム毎かプロダクト毎に異なる
 
 
* Some teams record input streams from tester play throughs, then play these back in automated tests, checking for successful completion or lack of errors/crashes.
#テスターのプレイの入力ストリームをそのまま記録するチームもある、そしてそれを自動テストで再生する、成功して完走するか失敗/クラッシュするかをチェックする。
** On some games, these input streams go "stale" frequently due to game or UI changes, and there's some overhead to re-recording.  (Some people were of the opinion that the overhead was too high to warrant continuing this type of test, some found it simple, depending on the product and tech.)
##ゲームやUIの頻繁な変更に伴いこれらの入力ストリームが「古く」なる場合があります、そして再レコーディングするオーバーヘッドもあります。（このタイプのテストでは整合性を保つためのオーバーヘッドが大きすぎるという人も居ます。簡単に言えば、プロダクトや技術者に依存します。）
** On other games, the UI attains a stability vs. recorded input streams and the need to re-record is infrequent.
##UIが安定に達するのと、入力ストリームの記録をとり再記録がめったに起きなくなるのを競わせたゲームもあります。
* Some teams drive UI traversal at a different level using an API (sometimes provided by a framework or language feature).
#UI横断テストには違ったレベルのAPI（フレームワークや言語機能として提供される）を使うチームも居ました
 
 
There is at least one team having success with both recorded input streams _and_ script-driven UI traversal.  QA create the tests, and can use either streams they record or scripts they write (or some combination of both) to test UI flow.
#少なくとも1チームは入力ストリームの記録とスクリプトによるUI横断テストの両方を使って成功している。QAはテストを作り、記録されたストリームか直接書かれたスクリプトのどちらか（あるいは両方）をUIフローのテストに利用する事ができる。
 
 
One individual suggested that fuzz testing is his primary tool, rather than recordings or scripts: he fuzzes inputs, network packets, files -- anything he can -- during parsing or loading, to simulate faulty hardware or software bugs.  The engine that his team is using has fallback resources for almost everything that cannot load, and it has been a really quick way to find bugs in both normal and error handling code paths.  Having an engine stable enough to deal with some hardware defects is helpful on a big title that might reach millions of users (and therefore potentially thousands of defective units).
#fuzz testingを主要ツールとして使っていて個人的に推薦するという人が居た。入力の記録やスクリプトよりも。ネットワークパケットやファイル（とかその他可能なもの）からファズデータをパース・ロードし、ハードウェアの欠陥やソフトウェアバグをシミュレートする。彼のチームのエンジンはほとんど全てのものに対してロードができなかった場合の代替リソースがある、そしてその方法は対象のコードパスに対する正常・異常を見つけるのが本当に早い。（PCゲームのこと？）いくつものハードウェア障害に対応できる安定したエンジンが何百万ものユーザを持つビッグタイトルを支えます（おそらく何千もの不良ユニットを持っている可能性がある）。
#http://www.ibm.com/developerworks/jp/java/library/j-fuzztest.html
#http://www.sophia-it.com/content/fuzz+testing
#セーブデータが壊れている場合とかチートとか、純粋に機器の故障、パケット遅延、改ざん対策ができるのかな。（感想）
 
 
 
=== Reporting and History ===
#レポートと履歴
 
 
 
Record a history of actions in the content tools; package this with bug or crash reports.
#内蔵のツールでの行動履歴を記録します：バグやクラッシュレポートと一緒に梱包します。
 
 
Graphs help tremendously with understanding reported information.  Correlate graph entries with individual revisions and focus on trends / differences over time.
#グラフは、報告された情報を理解するのに大いに役立ちます。相関グラフにより個々のリビジョンと時間経過によるトレンド/差異にフォーカスしたエントリーを見る事ができます。
 
 
Long soak tests (one individual mentioned 1 day to 2 weeks) can use graphs to show leaks or other issues.
#Long soak tests：浸せき試験（1日から2週間って言っていた）を行えばリークや他の問題をグラフ化する事ができるよ。
#http://www.c-able.ne.jp/~tips-com/00topics/01dictionary/0111sa/　（信頼性テスト）
 
 
For smoke and soak tests, record memory usage, FPS, GPU stats (e.g. poly counts), and gameplay events or balance-related statistics.
#スモークテストやソークテストのために、メモリー使用、FPS、GPUステート（ポリゴン数など）、ゲームプレイに関するイベントやバランス調整に関する統計情報等を記録する。
 
 
Attach stack traces to crash/hang reports; possibly parse these and bucket or assign them automatically based on e.g. P4 blame.  "Hash" the stack trace to help with bucketing.  [See also "Debugging in the (Very) Large" paper.]
#クラッシュ/ハングレポートにスタックとレースを添付する：それらレポートかまるまる全部を、例えばP4 blameで（Perforceの機能？）、自動的にパースするかアサインするという手もある。スタックトレースに「ハッシュ」を付けるのもデータを汲むのに役立つ。["Debugging in the (Very) Large"という論文参照]
#"Debugging in the (Very) Large"→http://research.microsoft.com/apps/pubs/default.aspx?id=81176
 
 
A few people tried Windows Error Reporting but expressed that the turnaround time for receiving info was too high for their liking; they preferred custom solutions.
#Windowsのエラーレポートを試したが情報を得るまでのターンアラウンドタイムが期待より長すぎた；カスタムソリューションを推奨した。
 
 
The commercial product BugSplat was mentioned as a drop-in crash reporting solution.
#商用製品の「BugSplat」はドロップインのクラッシュレポーティングソリューションとして言及された。
#http://www.bugsplatsoftware.com/
 
 
Expose what you already have!  Leverage existing systems to add more info to reports.
#すでに持っているものをさらしてみよう！既存のシステムにテコ入れして、レポートのためにもっと情報を追加しよう！
 
 
 
=== Test Environments ===
#テスト環境
 
 
 
Environment snapshots are sometimes useful to maintain one or more consistent OS and software stacks for testing.  Some people use VMWare for this.
#環境のスナップショットはテストのための一貫性のあるOSやソフトウェアスタックを構築したり維持するのに有用です。VMWareを使ってこれを実現している人も居ます。
 
 
Special environments such as Valgrind, Bounds Checker, Insure++, or the like may be useful places to run a supplemental scheduled test.
#Valgrind,  Bounds Checker, Insure++ といったツール専用の環境はスケジューリングされたテストに追加して走らせるのに良い場所です。
#Valgrind http://ja.wikipedia.org/wiki/Valgrind
#Bounds Checker http://www.microfocus.co.jp/products/devpartner/devpartner_fm/devpartnervisualc/
#Insure++ http://www.techmatrix.co.jp/quality/insure/index.html
 
 
Be wary of differences between debug and release, or "special" builds: some people find special builds cause more bugs, or crazy bugs only show up in non-special builds.  One person asserted "debug is just release with logging".
#debugビルドやreleaseビルド、「特別な」ビルドの違いには慎重になるべきだ：特別なビルドはバグをより一層生成するし、クレイジーなバグは特別な事をしていないビルドでしか浮き上がってこない。「debugビルドはreleaseにログ機能を付けるだけであるべき」と断言する人も居た。
 
 
 
=== Anti-patterns, Things to Avoid ===
#アンチパターン、避けるべき事
 
 
 
Some people try to get full unit test coverage, but the general consensus seemed to be that this was a duplication of effort: some things are better tested with functional tests.
#ユニットテストのカバレッジを100%にしようとする人が居るが、大体の人の意見はそれは努力の無駄遣いだという傾向にある：いくつかは機能テストにより充分にテストされているし。
 
 
Still, if a unit test fits, it's usually fast to create and faster to run than a "corresponding" functional test: prefer unit tests when all else is equal.
#ユニットテストがフィットしているとしても、「よく似た」機能テストを作成して走らせた方が往々にして早い：他の全てが同じようにユニットテストが好ましいとしても
 
 
Using data reported from an evolving build for tuning can cause serious problems as things change.  [There were some excellent presentations on this at the GDC 2011 AI Summit, including "AI Pr0n: Maximum Exposure of Your Debug Info!" by Michael Dawe (Big Huge Games/38 Studios), Rez Graham (Electronic Arts - Sims Division), and Brian Schwab (Blizzard Entertainment).]
#チューニングのために進化（改造）されたビルドからデータを使用する場合、何かが変わった時に深刻な問題が発生する。[このGDC2011のAI Summit内"AI Pr0n: Maximum Exposure of Your Debug Info!" by Michael Dawe(Big Huge Games/38 Studios), Rez Graham (Electronic Arts - Sims Division), and Brian Schwab (Blizzard Entertainment) でこの事に関するすばらしい発表があった]
 
 
Avoid beta, experimental, or immature tools and components [in build and test automation, perhaps also in general] if possible.
#可能であれば、ベータ、実験、未熟なツールとコンポーネントは[ビルドや自動テスト内で使うのを、おそらく一般使用も]避けるべきだ。
 
 
Mock objects are often more trouble to maintain than they're worth.  (Some people had success here, others find it a consistent problem.)
#モックはそれらの価値から得られるものよりも大体の場合維持のトラブルがある。（ここで数人は成功したと言ったが、それ以外は一貫性の問題を挙げた）
 
 
"Process and people make all the difference."
#ことわざ「people make all the difference」にProcessもつけた物と思われる。ひとそれぞれ、プロセスもそれぞれ
 
 
Make sure people are actually running the build themselves!  All too often there is a "it's too broken right now" attitude, and you must overcome that.
#ビルドは実際には彼らの手によって実行される事に注意しないといけない！よくある「これは今壊れた」という態度に、あなたはそれを打開しないといけない。
#（おそらく、よくある「今ビルドしてみたら通らないんですけど」と言うがそれ以前におかしくなっていたという場合にがんばれという話）
 
 
 
=== Bots ===
#ボット
 
 
 
[Random walk was mentioned above, in Input Driving]
#[ランダムウォークについては上の Input Driving で述べられました。]
 
 
Simulate a competent player or players to test in-game economy to help reveal balance-breaking changes.
#優秀なプレイヤーをシミュレートして、ゲーム内経済においてバランス崩壊する変更が露呈するのをテストします。
 
 
 
=== Static Code Analysis ===
#静的コード解析
 
 
 
Mixed results here.  Most people could not recommend it due to signal-to-noise ratio issues.
#意見が分かれました。検出：ノイズの比率の問題でほとんどの人はそれ（静的解析）をお勧めしませんでした。
 
 
"Definitely" use some sort of pre-runtime checking for non-compiled languages (such as Python scripts).
#「当然」、（Pythonスクリプトなどの）非コンパイル言語に対するランタイムチェック前のある程度のソートは使っている。
 
 
Do track local conventions and have an existing static code analysis tool or a custom tool detect violations.  Use "smart comments" to bypass these checks if you know what you're doing.
#昔ながらのやりかたでの追跡か既存の静的解析ツールかカスタムツールどれでも良いので違反を検知しましょう。あなたがどんな事をしているか（コードを書いているか）を知るために、「スマートコメント」を使ってこれらのチェックをバイパスします。
 
 
Static code analysis has proved very useful for some people to fix "porting to 64-bit" issues.
#静的解析は「64bit移植」問題を修正する時にかなり役立ったという人も居た。
 
 
It's easier to do static code analysis if you start with it.
#それから始める場合は、静的解析を使うと簡単です。（64bit移植のこと？）
 
 
Reporting only differences between runs helps with the signal-to-noise ratio if you're working with a legacy code base.
#レガシー（新しいものが出現したが、長年使われ、いろいろな事情で完全に捨てることができない古い技術や仕様など。）なコードをベースに作業する場合、検出とノイズの割合（閾値）を調整して走らせる事で、差異に対してのみレポーティングする事ができる。
 
 
Turn compiler warnings up as far as possible, and "Treat Warnings As Errors", if at all possible.
#コンパイラの警告はできる限り大きくしておくべきです、そして「警告をエラーとして扱う」、できる限り。
 
 
 
== Day 2 (Thursday) ==
#2日目
 
 
 
The suggested topic of day 2 (Thursday) was infrastructure: who deploys and maintains automation, and which tools and practices have helped.
#2日目のトピックはインフラです：誰がデプロイや自動化を保持しますか、そしてどんなツールやプラクティスを使っていますか。
 
 
[For Thursday, we switched to a "gather general questions, then attempt to answer them" model.]
#この日は「一般的な質問を集めて、それらについて答えていく」モデルにしました。
 
 
 
=== Questions / Topics ===
#質問/トピック
 
 
 
* In house vs. 3rd party solutions
* Telemetry
* Integration [where and how, and maintenance]
* Branches and continuous integration strategy; topic branches
* Turnaround times
* Presentation (of gathered information, test results, etc)
* Distributed builds
#*内製かサードパーティーのソリューションか
#*テレメトリー？
#*インテグレーション[どこでどうやって、そしてメンテナンス]
#*ブランチとCI（継続的インテグレーション）の戦略；特にブランチの扱いについて
#*応答（所要）時間
#*提供方法（集めた情報、テスト結果、など）
#*分散ビルド
 
 
 
=== In-house vs. 3rd Party ===
#内製vsサードパーティー
 
 
 
Attendees primarily (~75% or more) were using in-house custom build and test solutions.
#出席者の75%以上は内製のカスタムビルド＆テストソリューションを使用している。
 
 
Time to integrate and maintain automation is key: often the automation itself lacks testing.  Some teams have an assigned automation tester.  Some cannot afford this.
#統合と自動化のメンテナンス時間がキーです：その自動化システム自体がテストされていない、という事はよくあります。自動化テスターが割り当てられたチームもある。買う余裕のないところもある。
 
 
The following 3rd party tools were mentioned:
#サードパーティーのツールは以下のものが挙げられました：
 
 
* Hudson (builds)
#Hudson→forked to Jenkins http://jenkins-ci.org/
* TeamCity (builds)
* JIRA (issue/project tracking) [someone mentioned integration with Hudson here]
* FishEye (VCS notification, visualization, and search)
#http://www.atlassian.com/software/fisheye/  10 users $10
 
 
 
=== Telemetry ===
#テレメトリー
 
 
 
E-mails are a common and easy way to report data.
#E-mailは万国共通
 
 
Log asserts and warnings, report those.
#アサートや警告ログをレポートする
 
 
Graph memory stats.
#メモリ状況をグラフ化する
 
 
When graphing anything, try to show a "current snapshot" and contrast with historical data.  Especially useful with memory.
#なにかをグラフ化するときは、履歴のデータに対応した「現在のスナップショット」を見せるようにする。特にメモリ。
 
 
The following 3rd party tools were mentioned:
#サードパーティーのツールは以下のものが挙げられました：
 
 
* Confluence (info share)
#http://www.atlassian.com/software/confluence/  $10
* SQL Server Reporting Services (analytics)
#http://msdn.microsoft.com/ja-jp/library/ms159106.aspx
* Callgrind [part of Valgrind] (call graph)
#http://valgrind.org/docs/manual/cl-manual.html
* Tableau (analytics) [this was specifically called "expensive", but worth it if you could afford it]
#http://www.tableausoftware.com/   日本サポート会社あり   http://www.tableausoftware.jp/  [高いと言われるけど、買う余裕があればそれだけの効果がある]
 
 
Harvest some telemetry from each and every build (even individuals' builds) and also from a build run periodically (e.g. every 12 hours).  Separate the visualization for each.
#ビルド毎にテレメトリーを収穫する、定期的（12時間毎など）にも実行する、そしてそれぞれについて見れるようにする。
 
 
One team gathers data from a 5-minute game run under Callgrind.
#Callgrindを使って5分毎のゲームのデータを集めているチームもあった。
 
 
Try "all possible combinations of weapons vs. zombie", report number of hits, damage, who won, etc.
#「全ての可能な武器vsゾンビの組み合わせに対して」ヒット数、ダメージ、誰が勝つかを試すとか。
 
 
Record all "achievements" acquired during testing.
#テスト中に獲得した全ての「達成（achievements）」を記録する。
 
 
Record playtime (can "check on QA" this way, if so inclined).
#プレイ時間を記録する（「QA側のチェック」はこの方法でできる、もし傾向があれば）
 
 
Tool telemetry is important:
#テレメトリーツールは重要：
 
 
* record actions and the time they took to complete
#アクションと完了までにかかった時間を記録
* keep track of data build times
#ビルド時の追跡データを残す
* use a single simple global (e.g. SQL) database and (e.g. ASP) web service for collecting data
#データを集めるために1つの簡単なグローバルデータベース（例：SQL）と（例ASPのような）webサービスを使う。
* take screen shots
#スクリーンショットを撮る
* upload logs and screen shots when a crash occurs, or a bug report is issued; can place these in a test case management system
#クラッシュした時やバグレポートが提出された際にログとスクリーンショットをアップロードする；これらはテストケース管理システムに置く事ができる。
 
 
"Collection is easy.  Presentation is hard."  [paraphrased]
#「収集は簡単、提示が難しい」[言い換え？]
 
 
Reporting can be via unreliable networking: UDP or HTTP.  Statistically you still get what you need.
#レポートは信頼できないネットワーク（UDP、HTTP）でもレポーティングできる。統計的に必要なものが得られる。
 
 
 
=== Integration / Maintenance ===
#統合/メンテナンス
 
 
 
About 15% of attendees used unit tests.  Also about 15% of attendees used functional tests.  (There was some overlap.)
#出席者の約15%はユニットテストを使っている。同じく15%の出席者は機能テストも行っている。（それなりにかぶっている）
 
 
Some teams have difficulty getting info about new features to the people responsible for maintaining automation.
#自動化の維持を任せる事ができる人々という新しい特徴の情報を得る事が難しいというチームも居る
 
 
Automatically created test cases (e.g. input dumps) tend to "thrash" and produce false failures a lot.
#（入力ダンプのように）自動でテストケースを作ると「打ちのめされる」、失敗をたくさん作ってしまう傾向がある。
 
 
Take screen shots.  These can be verified by a human quickly, or you can use pixel-by-pixel compare (breaks often, depending on product) or PerceptualDiff.  Bots should take screen shots as they traverse the game.
#スクリーンショットを撮る。これは人によって素早く検証できるし、ピクセル毎の比較にも使える（よく失敗するし、プロダクトに依存するが）、もしくはPerceptualDiff。ボットはゲームを旋回する中でスクリーンショットを撮るべきだ。
#PerceptualDiff  http://pdiff.sourceforge.net/
 
 
For rendering tests, render simple boxes or skeletons and do image comparison on these.  It may not be worth going further.
#レンダリングのテストには、シンプルなボックスかスケルトンにレンダーしそれらの画像比較を行う。推進するほどの価値はないかもしれないが。
 
 
When do you add a test?  When the build breaks, or with each bug, or with new features.
#いつテストを追加しますか？ビルドが壊れた時、バグの起こった時毎、機能追加する時。
 
 
 
=== Turnaround Time ===
#応答（所要）時間
 
 
 
Some durations from a few folks' tests:
#いくつかのテストの系統によって期間が分かれた？
 
 
* Wii: 1 hour
* PC: 5-6 minutes
 
 
Smoke test should be quick.  Ideas:
#スモークテストは早くできるべき。アイデア：
 
 
* start editor
* start each level
* save and then load
 
 
Some people prefer to avoid tests that require sequential steps (so that early failures don't prevent the test from completing).  Others suggested this didn't matter as long as the test turnaround time is fast and the fixes are fast.
#シーケンシャルなステップ（初期の失敗がテストの完了を阻止しない？）を必要とするテストはやりたくないと言う人も居た。
#ターンアラウンドタイムは早く修正も早いので気にするほど長くはないと言う人も居た。
 
 
Many teams do incremental data builds (caching results) and full code builds on their build server.  Once a day (or less often), they'd do a clean data and code build.
#多くのチームはインクリメンタルデータビルド（結果をキャッシュ）とビルドサーバーでのフルコードビルドを行う。1日に1回（かもっと多く？少なく？）データとコアのビルドをクリーンにする。
 
 
Code build times were generally quick, with most people reporting full code build times in minutes, but some reporting above 40 minutes or an hour, even distributed.
#コードのビルド時間は一般的には早い、ほとんどの人はフルコードビルドは数分で終わると答えた、しかし40分や1時間と答えた人も居た、分散（ビルド）しているのに。
 
 
Identify idle consoles (e.g. Xbox) and run a test suite opportunistically.
#空いているコンソール（Xboxなど）を確認してテストスイートを日和見的に走らせる。
 
 
Dedicated automated test hardware is common.
#自動テスト専用のハードウェアがあるは一般的です。
 
 
 
=== Presentation ===
#プレゼンテーション（見せ方、表現方法）
 
 
 
Present results once or twice a day.
#結果を1日に1回か2回は出力する。
 
 
Prefer pushing data to users to having them seek it out.  But don't push too often.
#結果は探させるよりユーザに提示しよう。けれどやりすぎは良くない。
 
 
Allow users to voluntarily subscribe to other more frequent push sources (build successes, current stats, etc).
#ユーザには自発的に他の人にもっと頻繁にソース（ビルドの成功、現在の状態など）をプッシュする事を賛成するのを許可しましょう
 
 
Test or build failures are an exception: push these immediately to responsible parties.
#テストやビルドの失敗は例外（exception）です：これらはすぐに関係者に通知するようにしましょう。
 
 
Prefer to present data visually (vs. textually).
#データはビジュアルに見えるようにしたほうが好まれる（vs. テキスト表示）
 
 
Use simple visualizations, e.g. red and green dots, in an easily-findable overview.
#シンプルなビジュアル化を使おう、例：赤と緑のドット、概要が簡単につかめるように。
 
 
"Trial builds" via TeamCity or Perforce "shelving" functionality with full testing are well loved by those who have this ability.
#TeamCityの「Trial builds」やPerforceの「shelving」機能とフルテストを合わせる事はこれらを使いこなせる人達に愛されている。
 
 
Report errors "per build phase".  [Separate various types of data build errors from each other and from code build errors or script compilation errors.]  Mail to appropriate groups based on this.
#「ビルドフェイズ毎」のエラーレポート。[それぞれのビルドエラーをタイプ毎に分ける事ができ、コードのエラーかスクリプトのコンパイルエラーか等切り分けることができる]。結果に適した相手にメールを送る。
 
 
Don't be afraid to write scripts (e.g. python) to parse build logs for specific errors of interest and "promote" them.
#Pythonといったスクリプト言語を書くことを恐れてはいけない。ビルドログや特定のエラーに興味を持たせ、「宣伝」するために。
#☆使って興味持ってもらって活用してもらうためにがんがん手を加えていけという事ですね。
 
 
Keep final reports human-readable.  If possible, include a basic description of how to fix or a link to more details.
#最後の（最新の）レポートはだれでも読めるようにしておこう。可能なら、基本的な修正方法の概要と詳細へのリンクを含める。
 
 
Methods for notification:
#通知方法について
 
 
* e-mail
* yammer
#https://www.yammer.com/
* tumblr
#http://www.tumblr.com/
* growl
#http://growl.info/ , http://ascii.jp/elem/000/000/562/562062/
* the famous GitHub traffic light =)
#http://blog.littlebirdelectronics.com/git-hub-traffic-light-via-urbanhonkingcom
* a siren =)
#本物のサイレンの事だと思われる
* centrally located TV or monitor
#真ん中に置かれたTVとかモニター
 
 
Keep To/Cc lists small: fewer people = more effective.  If a pushed failure isn't addressed within a certain time, "promote" it to senior folks, producers, or managers.
#To/Ccのリストは最小限に：人数を少なくすればするほど = 効果的。通知されたfaiureに一定期間対処されない場合、それを上司やプロデューサー、マネージャーに「宣伝する」。
 
 
Simple but brutally effective: prevent commits if the build is failing.
#シンプルだが容赦なく効果的：ビルドが失敗したらコミットを拒否する。
 
 
 
=== Distributed Builds ===
#分散ビルド
 
 
 
3rd party products mentioned:
#以下のサードパーティーの商品が挙がった
 
 
* SN-DBS (Sony platforms)
#http://www.snsys.jp/products/SN-DBS.asp
#SN-DBS は PlayStationR2、PSP? (PlayStationRPortable) 及び PlayStationR3 の開発者の皆様にこれより無償で、 Product Licensing System 無 しにご利用いただけます。 
* IncrediBuild
#http://www.xoreax.co.jp/
 
 
Some people have in-progress efforts to use IncrediGrid to distribute asset building.
#分散アセットビルドのために IncrediGrid を使おうとしている人もいた。
 
 
Generally, people seem to prefer multicore-scalable tools to distributed tools.  [Easier to construct and maintain, more predictable, less likely to break in strange ways.]
#一般的に、分散ツールよりもマルチコアスケーラブルツールの方が好まれるようだ。[構築とメンテナンスの容易性、もっとわかり易いのは、変なやり方をしても壊れにくい点]
 
 
Build system: get it more cores, and one or more solid state drives.  These seem to matter more than most other things these days.
#ビルドシステム：より多くのコアでより信頼できる1つ以上のドライブを使用するべき。これらは最近、他のほとんどのものよりも重要であるように思われる。
 
 
Distribute your unit test.  (One example: reduction from 6 minutes to 40 seconds.)
#ユニットテストを分散しよう。（1例として：6分かかるものが40秒になった）
 
 
What VCSes are people using?  Mostly Perforce (perhaps 60%) with a tail of Subversion (perhaps <10%) and a few teams using Git.
#VCS（バージョン管理システム）は何を使っていますか？ほとんどの人はPreforce（60%くらい）、次にSubversion（10%未満くらい）、いくつかのチームはGit。
#（粉川が現地で取った記録では、Perforceが50%以上、Subversion20%、gitが1人、2人くらいに感じましたが。ちなみにこの日のラウンドテーブル参加者は30人くらい？）
 
 
 
== Day 3 (Friday) ==
#3日目
 
 
 
The suggested topic of day 3 (Friday) was data gathering, mining, and visualization.
#3日目のトピックはデータ収集、マイニング、可視化について。
 
 
[Since it worked well Thursday, we kept the  "gather general questions, then attempt to answer them" model for Friday.]
#[前日に結構うまくいったので、「一般的な質問を集めて、それらについて答えていく」モデルを続けます。
 
 
 
=== Questions / Topics ===
#質問/トピック
 
 
 
* Generally, how do you automate?
* Testing high-level game systems
* Return on investment
* Testing on mobile devices
* What is "enough" testing vs. "too much"?
* Framework choices
* Visualization tools
* Investment in unit tests vs. integration testing?
* Testing on the web
#普段どのように自動化していますか？
#ゲームシステムの上位層のテストについて
#投資収益率
#モバイル機器でのテストについて
#「充分」vs「やりすぎ」なテスト
#フレームワークの選択
#可視化ツール
#ユニットテストvs結合テスト、どちらに投資する？
#webでのテスト
 
 
 
=== How do you automate? ===
#どのように自動化していますか？
 
 
 
Assertions:
#アサーションについて
 
 
* Approximately 5 teams disallowed assertions entirely.
* Some use assertions extensively for validating data that is assumed to be in a correct format.
* Get call stacks with your asserts, if you can!
* Some use "skippable asserts", letting execution flow continue:
** a bot (e.g. monkey test) can record all assertions it triggers;
** skipped assertions from user playthroughs can be reported to the server (along with a user name!).
* Some use assertions to "test all parameters going into functional units";
* similarly, assertions to "test all pre- and post-conditions".
* Keep your assertions "artist friendly".  Include a human-readable description and possibly fix instructions, or a link.
* Tag asserts with a group (e.g. via macro), and reported automatically to a likely-able-to-fix set of people.
* Keep statistics on assertions -- this helps identify buggy systems.
* Possibly separate out a FATAL assert from normal skippable asserts.
* About 10% of teams that use asserts don't disable them when they go live.
* Some reserve asserts for a "error in the algorithm" and handle all data error cases with other code.
#およそ5チームではアサーションが完全に禁止されています。
#データが正しいフォーマットであるかどうかを検証するためにアサーションを広範囲に使用している人もいる。
#できるなら、アサート時にコールスタックを取れるように！
#実行フローを継続させる事ができる「スキップできるアサート」を使っている人もいる。
##（例：モンキーテストのような）ボットにトリガーされた全てのアサーションを記録するようにしている。
##ユーザのプレイを通してスキップされたアサーションはサーバにレポートされる（ユーザ名と一緒に！）。
#「関数単位で全てのパラメータをテストする」ためにアサーションを使う人もいる。
#似たような感じで、「全ての事前、事後状態をテストする」ためにアサーションを使う。
#アサーションは「アーティスト（デザイナ）フレンドリー」であるべき。人間に読める記述と、修正のための指示やリンクを含めよう。
#アサートにグループによるタグ付けをする（マクロを使ったりして）、自動的に修正ができる人にレポートする。
#アサーションの統計をとる　--　これによりバグの多いシステムを識別する事ができる。
#できるだけ、通常のスキップ可能なアサートと致命的なアサートを切り分ける。
#アサートを使用するチームの約10%は、稼働させる時にに無効にしない
#アサートは「アルゴリズムのエラー用」に限定し、全てのデータエラーのケースは別のコードで扱う人もいる。
 
 
Only 5-6 teams used code coverage / branch coverage analysis tools.
#5,6チームだけがコードカバレッジ/ブランチカバレッジ解析ツールを使用
 
 
 
=== Testing High-Level Game Systems ===
#ゲームシステムの上位層のテスト
 
 
 
Save gameplay instructions (e.g. a message stream) easily or automatically; QA can pick up these saved streams and use them in scripts for testing.  Make the sequence to start/stop recording very simple.
#ゲームプレイ中の指示（メッセージストリーム等）を簡単にもしくは自動的に記録するようにする；QAは記録されたストリームを取り出しスクリプトから使う事ができる。シーケンスを記録のスタート/ストップが簡単にできるように作っておくべきだ。
 
 
Saving input or gameplay messages helps keep the game deterministic, which can have other benefits.
#入力とゲームプレイメッセージを記録する事はゲームを一意に決定するのを助ける事ができる、他の恩恵もある。
 
 
Assert on any unrealistic parameters coming into the system.  This also helps with anti-cheat mechanisms.
#非現実なパラメータがシステムに入ってきた場合アサートする。チート対策にも使える。
 
 
When a functional test fails, possibly try it again to see if it repros.  (Only a few teams do this currently.)
#機能テストが失敗した時、もう一度同じ事が起こるか試してみるのもあり。（数チームだけがこの方法をやっていた）
 
 
Make sure your AI has a well-defined API and is "drivable" at the start of development.  Harness this API to create automated tests.
#あなたのAIはきちんと定義されたAPIがあるかを確認してください、そして開発のスタート時に「動かせる（drivable）」事を確認してください。このAPIを装備する事により自動テストが作れます。
 
 
Have your server run at unlimited frame rate (possibly with rendering disabled); this accelerates tests.
#サーバをフレームレートを固定せずに実行できるようにした方がいい（できればレンダリングのOffも）；これによりテストを速くできる。
 
 
Record test results as e.g. SQL strings.  Don't get too fancy with reporting protocols or database setup; it's not worth it.
#テスト結果をSQL等に記録する。レポートのプロトコルやデータベースのセットアップに過剰装飾をしてはいけない；そんなに価値はない。
 
 
Mock some objects [selectively -- there's a lot of unhappiness with the mock object pattern, as there was on Wednesday] to help with higher level testing.
#いくつかのモック[抜粋--モックオブジェクトパターンにはたくさんの不幸があるが、これについては1日目に話した]は上位層のテストを行う助けになる。
 
 
 
=== Return on Investment ===
#投資収益率
 
 
 
Track your time: track normal development time, track automation development and maintenance time, and track bug fix time.  Reduced bug counts and bug fix time should be obvious once automation is in place.
#時間を記録する：通常の開発時間、自動化方法の開発・メンテナンス時間・バグの修正時間を記録する。一度自動化が導入されれば減らすことができたバグの数やバグの修正時間が明らかになるべき。
 
 
On a "one and done" project such as a one-time port or DLC, focus on simple high level functional testing like smoke tests.  Don't try to retrofit unit tests.
#一度だけの移植やDLCなどの「一度作って終わり」のプロジェクトは、スモークテストのようなシンプルな上位レベルの機能テストに注目される。ユニットテストに取り組むのはやめるべき。
 
 
Gather and report on all the failures the automated testing catches.
#自動テストのキャッシュから全ての失敗を集めてレポートするべき。
 
 
 
=== Testing on Mobile Devices ===
#モバイル機器でのテストについて
 
 
 
3rd party products mentioned:
#以下のサードパーティーの製品が挙がりました
 
 
* Selenium (web specific)
#http://seleniumhq.org/
* Sikuli (GUI testing with screen shots)
#http://sikuli.org/
#http://www.moongift.jp/r/2010/01/project-sikuli/
* .NET UI Automation framework
#http://msdn.microsoft.com/ja-jp/library/ms747327.aspx
 
 
Get something "like Selenium" up and running: at least a "touch monkey" that simulates tapping randomly.
#「Seleniumのような」なにかは使って走らせよう：少なくともランダムにタップを行う「タッチモンキー」くらいは。
#http://en.wikipedia.org/wiki/Monkey_test
 
 
[As in prior sessions] much disagreement about whether input recording and playback for UI testing is "evil" (too prone to false failures, too high maintenance).
#[前のセッションで出たように]入力の記録と、UIテストのプレイバックのどちらが「邪悪」か意見が分かれた。「邪悪」：（あまりにも間違った失敗をし･･･おそらくテストのfalse報告が間違っているの意味･･･、メンテナンスコストが高い）
 
 
Accessibility features can be a boon to automated UI traversal.
#アクセスしやすいという特徴はUIの自動横断テストに恩恵を与える。
 
 
Grab a "map" of the UI from the pipeline, before the build, then use that to create tests.
#パイプラインからUIの「マップ」を引っこ抜く、ビルドの前に、そしてそれをテストの生成に使う。
 
 
If your UI is data driven by XML, you can parse that XML for testing.
#もしUIがXMLのデータドリブンであれば、そのXMLをテストにパースする事ができる。
 
 
For most games, 80% of the needed tests are on game components.  The RoI is much higher there than on UI testing.
#ほとんどのゲームで、80%の必要とされるテストはゲームコンポーネントについてだ。それはUIテストのRoI (return on investment：投資利益率)よりももっと高くなる。
 
 
 
=== What is "Enough" Testing Vs. "Too Much"? ===
#「充分」vs「やりすぎ」なテスト
 
 
 
Prefer to test reusable components first.
#最初に再利用可能なコンポーネントをテストするのが良い。
 
 
Prefer to test gameplay before other systems.
#他のシステムよりもまずゲームプレイのテストをした方が良い。
 
 
We need more "QA as a profession".  We have QA -> Production and even QA -> Programming; we need more QA -> QA.  We want a "Software Design Engineer" or "QA Engineer" position in more companies (some have this already!).  And pay them well, if possible.  =)
#より「専門的職業としてのQA」を必要とする。QA→生産とQA→プログラミングの両方がある;もっとQA→QAが必要；「ソフトウェアデザインエンジニア」か「QAエンジニア」のポジションをより多くの会社に与えて欲しい（すでにいくつかの会社にはある！）。そして彼らにたくさん給料をあげよう、できればね^^
 
 
QA turnover is a huge problem that needs to be addressed.
#QAによる--〔一定の期間の〕粗利益、益金？〔会社などの〕離職者数［率］、補充者数？--は取り組まれるべき巨大な問題だ。
 
 
Encourage "across the wall" communication.  (Only about 50% of those in attendance do this.)  Bring a single QA person to the daily "scrum" or meeting.
#「壁を越えた」コミュニケーションを促進しよう。（出席者のうちたった50%しかこれに取り組んでいなかった。）デイリー「スクラム」かミーティングにQAの人を1人は連れてこよう。
 
 
Encourage diverse backgrounds for QA and test engineers.  For example: a hardware background can contribute valuable and uncommon insight.
#QAやテストエンジニアにさまざまなバックグラウンドを持たせよう。例えば：ハードウェアの知識は有益で卓越した洞察力に貢献する。
 
 
Some companies solve the QA turnover problem by growing a static core QA department and expanding seasonally with temporaries.
#QA turnover（上述）の問題に対して、独立したQA部門を成長させるのと期ごとのアルバイトを拡大する事で解決している会社もあった
 
 
 
=== Visualization Tools ===
#可視化ツール
 
 
 
[Most of these have been mentioned on prior days; some are not strictly visualization tools.  But here's the list from Friday!]
#[以下のほとんどは初日に挙げられた；いくつかは厳密には可視化ツールではないが、この日挙がったリストとして]
 
 
* Hudson (builds)
* CruiseControl (builds)
* TeamCity (builds)
* NUnit (unit testing)
* VMWare (virtual machines)
* Sonar (code coverage)
#http://www.sonarsource.org/
* Tableau (analytics)
 
 
...and an assortment of home-brew tools.
#･･･と内製のツール詰め合わせ
 
 
 
=== Investment in unit tests vs. integration testing? ===
#ユニットテストvs結合テスト、どちらに投資する？
 
 
 
[I'm missing notes from this section -- it was brief, as we were nearing the end.  Apologies!]
#[このセクションのノートを無くしてしまった・・・簡潔だったのと終わりが近かったので・・・ごめんなさい！]
 
 
 
=== Testing on the Web ===
#webでのテスト
 
 
 
Leverage users: instrument your web app/game and report back.
#ユーザを活用する：webアプリやゲームを使って、レポートを返すようにする
 
 
Automate browsers using bots.
#ボットを使ってブラウザの自動化。
 
 
Keep a separate lab with dedicated hardware and environments (e.g. different OSes, browsers, etc) for testing.  Possibly use VMs.
#テストのために、専用のハードウェアと環境毎（例えばOS毎、ブラウザ毎、など）に分けて用意する。VMを使ったり。
 
 
 
== Other References ==
#その他のリファレンス
 
 
 
* IGDA Tools SIG: http://www.igda.org/toolssig
** tools_discuss mailing list: http://two.pairlist.net/mailman/listinfo/tools_discuss
** wiki: http://wiki.igda.org/Tools_SIG
 
 
* IGDA QA SIG: http://www.igda.org/qa/
** wiki: http://wiki.igda.org/Quality_Assurance_SIG
 
 
* My prior roundtable, "Six Million Dollar Tester: Making QA Better/Stronger/Faster Through Automation", was based on a presentation given at an Albany IGDA meeting approximately 20 billion years ago (in 2006): http://archives.igda.org/qa/docs/SixMillionDollarTester.
#リンク切れしているが、タイトルから論文を見つけた
 
 
* The GDC Vault can be a great source of information, too (some free content, some paid): http://www.gdcvault.com/
