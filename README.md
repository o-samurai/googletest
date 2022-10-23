<!--# GoogleTest-->
# GoogleTest

## GoogleTestドキュメント日本語訳について
このリポジトリは[GoogleTest](https://github.com/google/googletest)のドキュメントを日本語訳したものです。この日本語訳は公式なものではありません。また、本日本語訳を利用したことにより発生するいかなる損害に対しても訳者は一切その責任を負いません。

<!--### Announcements-->
### お知らせ

<!--#### Live at Head-->
#### いつも最新

<!--GoogleTest now follows the-->
<!--[Abseil Live at Head philosophy](https://abseil.io/about/philosophy#upgrade-support).-->
GoogleTestは[AbseilのLive at Head理念](https://abseil.io/about/philosophy#upgrade-support)に従っています。

<!--We recommend-->
<!--[updating to the latest commit in the `main` branch as often as possible](https://github.com/abseil/abseil-cpp/blob/master/FAQ.md#what-is-live-at-head-and-how-do-i-do-it).-->
そのため[最新の`main`ブランチに可能な限り頻繁に追従](https://github.com/abseil/abseil-cpp/blob/master/FAQ.md#what-is-live-at-head-and-how-do-i-do-it)することを推奨します。


<!--#### Documentation Updates-->
#### 最新のドキュメント

<!--Our documentation is now live on GitHub Pages at-->
<!--https://google.github.io/googletest/. We recommend browsing the documentation on-->
<!--GitHub Pages rather than directly in the repository.-->
ドキュメントはGitHub Pagesにある https://o-samurai.github.io/googletest/ を更新しています。
直接リポジトリ中のドキュメントを参照するのではなくこのGitHub Pagesを参照することをお勧めします。

<!--#### Release 1.12.1-->
#### Release 1.12.1

<!--[Release 1.12.1](https://github.com/google/googletest/releases/tag/release-1.12.1)-->
<!--is now available.-->
[Release 1.12.1](https://github.com/google/googletest/releases/tag/release-1.12.1)
が利用可能です。

<!--The 1.12.x branch will be the last to support C++11. Future releases will-->
<!--require at least C++14.-->
1.12.xブランチはC++11をサポートしています。将来のリリースでは少なくともC++14が必要となります。

<!--#### Coming Soon-->
#### Coming Soon

<!--*   We are planning to take a dependency on-->
<!--    [Abseil](https://github.com/abseil/abseil-cpp).-->
<!--*   More documentation improvements are planned.-->
[Abseil](https://github.com/abseil/abseil-cpp)
に依存する計画があります。より詳しい説明をする予定です。

<!--## Welcome to **GoogleTest**, Google's C++ test framework!-->
## ようこそ、GoogleのC++フレームワークの **GoogleTest** へ！

<!--This repository is a merger of the formerly separate GoogleTest and GoogleMock-->
<!--projects. These were so closely related that it makes sense to maintain and-->
<!--release them together.-->
このリポジトリは以前は分かれていたGoogleTestとGoogleMockを統合したものです。
これらは似たもの同士であり一緒にメンテナンス・リリースすることは道理に適います。

<!--### Getting Started-->
### はじめに

<!--See the [GoogleTest User's Guide](https://google.github.io/googletest/) for-->
<!--documentation. We recommend starting with the-->
<!--[GoogleTest Primer](https://google.github.io/googletest/primer.html).-->
[GoogleTestユーザーガイド](https://o-samurai.github.io/googletest/)を見てください。
最初に[GoogleTest入門](https://o-samurai.github.io/googletest/primer.html)から始めるとよいでしょう。

<!--More information about building GoogleTest can be found at-->
<!--[googletest/README.md](googletest/README.md).-->
GoogleTestのビルドについての情報は[googletest/README.md](googletest/README.md)にあります。

<!--## Features-->
## 機能

<!--*   An [xUnit](https://en.wikipedia.org/wiki/XUnit) test framework.-->
*   [xUnit](https://en.wikipedia.org/wiki/XUnit)テストフレームワーク
<!--*   Test discovery.-->
*   テストの検出
<!--*   A rich set of assertions.-->
*   豊富なアサーション
<!--*   User-defined assertions.-->
*   ユーザ定義のアサーション
<!--*   Death tests.-->
*   デステスト
<!--*   Fatal and non-fatal failures.-->
*   致命的な失敗と非致命的な失敗の区別
<!--*   Value-parameterized tests.-->
*   値注入テスト
<!--*   Type-parameterized tests.-->
*   型注入テスト
<!--*   Various options for running the tests.-->
*   多彩なテスト実行オプション
<!--*   XML test report generation.-->
*   XMLによるテストレポート

<!--## Supported Platforms-->
## サポートするプラットフォーム

<!--GoogleTest follows Google's-->
<!--[Foundational C++ Support Policy](https://opensource.google/documentation/policies/cplusplus-support).-->
GoogleTestはGoogleの基本的なC++サポートポリシーに従います。
<!--See-->
<!--[this table](https://github.com/google/oss-policies-info/blob/main/foundational-cxx-support-matrix.md)-->
<!--for a list of currently supported versions compilers, platforms, and build-->
<!--tools.-->
サポートするコンパイラ、プラットフォーム、ビルドツールとそのバージョンは[この表](https://github.com/google/oss-policies-info/blob/main/foundational-cxx-support-matrix.md)を参照してください。

<!--## Who Is Using GoogleTest?-->
## GoogleTestを使っているのは誰？

<!--In addition to many internal projects at Google, GoogleTest is also used by the-->
<!--following notable projects:-->
GoogleTestは次のような有名なプロジェクトで使用されています。また、Google内部における多くのプロジェクトでも使用されています。

<!--*   The [Chromium projects](http://www.chromium.org/) (behind the Chrome browser-->
<!--    and Chrome OS).-->
*   [Chromium projects](http://www.chromium.org/) (Chromeブラウザ、Chrome OSの裏側にあるプロジェクト)
<!--*   The [LLVM](http://llvm.org/) compiler.-->
*   [LLVM](http://llvm.org/) コンパイラ
<!--*   [Protocol Buffers](https://github.com/google/protobuf), Google's data-->
<!--    interchange format.-->
*   [Protocol Buffers](https://github.com/google/protobuf) Googleのデータ変換フォーマット
<!--*   The [OpenCV](http://opencv.org/) computer vision library.-->
*   [OpenCV](http://opencv.org/) コンピュータビジョンライブラリ

<!--## Related Open Source Projects-->
## 関連するオープンソースプロジェクト

<!--[GTest Runner](https://github.com/nholthaus/gtest-runner) is a Qt5 based-->
<!--automated test-runner and Graphical User Interface with powerful features for-->
<!--Windows and Linux platforms.-->
[GTest Runner](https://github.com/nholthaus/gtest-runner) はQt5に基づくWindowsとLinux向けの強力な機能を備えたグラフィカルユーザーインターフェースと自動化されたテストランナーです。

<!--[GoogleTest UI](https://github.com/ospector/gtest-gbar) is a test runner that-->
<!--runs your test binary, allows you to track its progress via a progress bar, and-->
<!--displays a list of test failures. Clicking on one shows failure text. GoogleTest-->
<!--UI is written in C#.-->
[GoogleTest UI](https://github.com/ospector/gtest-gbar) はテストの進捗をプログレスバーで表示し、失敗したテストの一覧を見せるテストランナーです。失敗したテストをクリックすると失敗の詳細を表示します。GoogleTest UIはC#で実装しています。

<!--[GTest TAP Listener](https://github.com/kinow/gtest-tap-listener) is an event-->
<!--listener for GoogleTest that implements the-->
<!--[TAP protocol](https://en.wikipedia.org/wiki/Test_Anything_Protocol) for test-->
<!--result output. If your test runner understands TAP, you may find it useful.-->
[GTest TAP Listener](https://github.com/kinow/gtest-tap-listener) は テスト結果を [TAP protocol](https://en.wikipedia.org/wiki/Test_Anything_Protocol) で知らせるイベントリスナーです。もし使用するテストランナーがTAPを使える場合に有用です。

<!--[gtest-parallel](https://github.com/google/gtest-parallel) is a test runner that-->
<!--runs tests from your binary in parallel to provide significant speed-up.-->
[gtest-parallel](https://github.com/google/gtest-parallel) はテストの並列化によって高速化をもたらすテストランナーです。

<!--[GoogleTest Adapter](https://marketplace.visualstudio.com/items?itemName=DavidSchuldenfrei.gtest-adapter)-->
<!--is a VS Code extension allowing to view GoogleTest in a tree view and run/debug-->
<!--your tests.-->
[GoogleTest Adapter](https://marketplace.visualstudio.com/items?itemName=DavidSchuldenfrei.gtest-adapter) はGoogleテストのツリー表示とテスト実行・デバッグをサポートするVisual Studio Codeの拡張です。

<!--[C++ TestMate](https://github.com/matepek/vscode-catch2-test-adapter) is a VS-->
<!--Code extension allowing to view GoogleTest in a tree view and run/debug your-->
<!--tests.-->
[C++ TestMate](https://github.com/matepek/vscode-catch2-test-adapter) はGoogleテストのツリー表示とテスト実行・デバッグをサポートするVisual Studio Codeの拡張です。

<!--[Cornichon](https://pypi.org/project/cornichon/) is a small Gherkin DSL parser-->
<!--that generates stub code for GoogleTest.-->
[Cornichon](https://pypi.org/project/cornichon/) はGoogleTestのスタブコードを生成する小さなGherkin DSLパーサーです。

<!--## Contributing Changes-->
## 貢献について

<!--Please read-->
<!--[`CONTRIBUTING.md`](https://github.com/google/googletest/blob/main/CONTRIBUTING.md)-->
<!--for details on how to contribute to this project.-->
このプロジェクトに貢献したい場合は [`CONTRIBUTING.md`](https://github.com/google/googletest/blob/main/CONTRIBUTING.md) をお読みください。

<!--Happy testing!-->
よいテストを！
