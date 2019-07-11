# software test research

---

## 1.ソフトウェアテストについて

 ソフトウェアテスト (Software testing) は、コンピュータのプログラムから仕様にない振舞または欠陥（バグ）を見つけ出す作業のことである。

 テストの種類は以下の二種類がある。

 - ブラックボックステスト
  プログラムの入力と出力に注目したテスト

 - ホワイトボックステスト
  プログラムの内部構造に注目したテスト

 ### 1.1単体テスト(unit test)

 関数、メソッドなどの小さな単位で行うテストのことである。
 単体テストは、関数の場合には基本はブラックボックステストである。
 ブラックボックステストが済んだものの品質を確保するためにホワイトボックステストを行う。
 単体試験の道具としてJavaではテスティングフレームワークJUnitが有名である。
 これはJava専用である。他の言語にも同様のものがあり、それらを総称してxUnitと呼んでいる。

 ### 1.2結合テスト(integration testing)

 統合試験  は、単体試験が完了したプログラムを組み合わせて行う試験である。
 プログラムのどの部分から組み合わせていくかで、トップダウンテスト (top down test) とボトムアップテスト (bottom up test) に分けることができる。

 ### 1.3システムテスト(system testing)

 プログラムを単独ではなく、他のプログラムやハードウェア、通信ネットワーク、データベースなどと組み合わせて実施するテスト。
 
 ### 1.4リグレッションテスト(regression testing)

 プログラムを修正・変更した場合に、過去に実施したテストを再度実施することを回帰試験 (regression test) 又は退行テストという。
 修正前の試験に再度合格するかどうか、他の機能に影響与えていないかどうか、他の機能が動作するかどうかを確認する。
 過去のテスト資産を使い、実施する回数も多いことから、実施を省略することがないようにテスト自動化することにより効率化を図る。

 ### 1.5スタブとモック

 - スタブ（stub）
 プログラムのモジュールをテストする際、そのモジュールが呼び出す下位モジュールの代わりに用いる代用品のこと。
 下位モジュールが未完成でも代わりにスタブを用いることでテストが可能になる。
 逆に上位モジュールの代わりに用いる代用品をドライバと呼ぶ。

 - モック（mock）
 ソフトウェアテスト時、特にテスト駆動開発、ビヘイビア駆動開発における代用の下位モジュールスタブの一種。
 スタブと比較して、検査対象のモジュールがその下位モジュールを正しく利用しているかどうかを検証するのに使われる。
 
 - スタブとモックの違い
 モック:「オブジェクトのメソッドがどう呼ばれて何を返すか」というインタフェースも含めたテストのために使う

 - スタブ: テストをスムーズに行うために「あるオブジェクトのメソッドが呼ばれたら、ある戻り値を返す」ために使う

 ### 1.6カバレッジ

 所定の網羅条件がテストによってどれだけ実行されたかを割合で表したもの。
 網羅条件が命令であれば、命令網羅と呼ばれ(またはステートメントカバレッジ、C0とも呼ばれる)、すべての実行可能な命令のうち、テストで実行された命令の割合を意味する。
 そのほかに、すべての判定条件（if文による分岐など）のうち、テストで実行された判定条件を意味する判定条件網羅(ブランチカバレッジ、C1とも呼ばれる)などがあります。

## 2.testtthatについて

 Rのパッケージ開発のための自動化テストライブラリ。
 
 テストの粒度によって、expect、test、contextの３つが考慮されている。
 粒度の大きさとしてはcontext＞test＞expectとなっている。
 関数のテストはexpect単位で書いて、それをtestでまとめるというのが基本形。
 規模が大きくなるとtestをさらにcontextでまとめる。

 `expect_that`:入力する値と期待する結果のセット
 `test_that`:テストする項目名(関数単位)
 `expect_that`:テストをまとめたブロック
 
 `sample_code.R`

 ```R
 add <- function(x,y)x+y                #テストしたい関数
 ```

`test_code.R`

 ```R
 context("work numeric")                #テスト実行時に出すメッセージ
 test_that("numeric add", {             #unit test 項目名
  expect_that(add(1,2), equals(3))　　　 #入力する値と期待する結果のセット 1
  expect_that(add(-1,-1), equals(-2))　 #入力する値と期待する結果のセット 2
 })
 ```
モックらしき関数？
https://www.rdocumentation.org/packages/testthat/versions/2.1.1


## <参考URL>

 ### 1.ソフトウェアテストについて

 - [知識ゼロから学ぶソフトウェアテスト](https://qiita.com/kiyodori/items/94731da4cc3bcb5f6f2a)

 - [wacate](https://wacate.jp/)

 - [ソフトウェアテストことはじめ](https://www.slideshare.net/mhlyc/ss-53443695?ref=http://mhlyc.hatenablog.com/entry/2017/05/26/074749)

 - [はじめてのはじめてのソフトウェアテスト](https://www.slideshare.net/rinakume9/ss-63272759?ref=http://mhlyc.hatenablog.com/entry/2017/05/26/074749)

 - [wikipedia ソフトウェアテスト](https://ja.wikipedia.org/wiki/%E3%82%BD%E3%83%95%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A2%E3%83%86%E3%82%B9%E3%83%88)

 - [スタブ【テスト】 (stub)](https://wa3.i-3-i.info/word14933.html)

 - [スタブとモックの違い](https://qiita.com/k5trismegistus/items/10ce381d29ab62ca0ea6)

 - [TDD > モック / スタブ](https://qiita.com/7of9/items/8e2cb2070f2b2ea4e5ec)

 - [What are mock and stub used in unit testing?](https://blog.morizyun.com/blog/mock-stub-outline-rspec-ruby/)

 - [カバレッジ(網羅率)分析とは](https://www.techmatrix.co.jp/t/quality/coverage.html)

 ### 2.testthatについて

 - [testthatメモ](https://dichika.hateblo.jp/entry/20140308/p1)

 - [RDocumentation](https://www.rdocumentation.org/packages/testthat/versions/2.1.1)

 - [testthatを使って自動テスト用のデータをどこに置くか](https://codeday.me/jp/qa/20190224/280068.html)

 - [R packages by Hadley Wickham](http://r-pkgs.had.co.nz/tests.html) 