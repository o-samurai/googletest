<!--# Quickstart: Building with CMake-->
# クイックスタート：CMakeによるビルド

<!--This tutorial aims to get you up and running with GoogleTest using CMake. If-->
<!--you're using GoogleTest for the first time or need a refresher, we recommend-->
<!--this tutorial as a starting point. If your project uses Bazel, see the-->
<!--[Quickstart for Bazel](quickstart-bazel.md) instead.-->
このチュートリアルはCMakeを使ってGoogleTestを始めることを目標としています。
もしあなたがGoogleTestを初めてか久しぶりに使うのであれば、このチュートリアルから始めることをお勧めします。
もしあなたのプロジェクトがBazelを使っている場合は代わりに[Bazelによるクイックスタート]を参照ください。

<!--## Prerequisites-->
## 前提

<!--To complete this tutorial, you'll need:-->
このチュートリアルを進めるためには次のものが必要です。

<!--*   A compatible operating system (e.g. Linux, macOS, Windows).-->
*   互換オペレーティングシステム（例：Linux、macOS、Windows）
<!--*   A compatible C++ compiler that supports at least C++14.-->
*   少なくともC++14以上をサポートする互換C++コンパイラ
<!--*   [CMake](https://cmake.org/) and a compatible build tool for building the-->
<!--    project.-->
*   [CMake](https://cmake.org/) とプロジェクトをビルドする互換ビルドツール
<!--    *   Compatible build tools include-->
<!--        [Make](https://www.gnu.org/software/make/),-->
<!--        [Ninja](https://ninja-build.org/), and others - see-->
<!--        [CMake Generators](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)-->
<!--        for more information.-->
    *   互換ビルドツールには次のものを含みます。
        [Make](https://www.gnu.org/software/make/)、
        [Ninja](https://ninja-build.org/)、等…より詳しい説明は
        [CMake Generators](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)
        を参照してください。

<!--See [Supported Platforms](platforms.md) for more information about platforms-->
<!--compatible with GoogleTest.-->
GoogleTest互換のプラットフォームについての詳細は[サポートするプラットフォーム](platforms.md)をご覧ください。

<!--If you don't already have CMake installed, see the-->
<!--[CMake installation guide](https://cmake.org/install).-->
もしまだCMakeをインストールしていないのであれば [CMake インストールガイド](https://cmake.org/install)をご覧ください。

<!--{: .callout .note}-->
<!--Note: The terminal commands in this tutorial show a Unix shell prompt, but the-->
<!--commands work on the Windows command line as well.-->
{: .callout .note}
Note: このチュートリアルで示すターミナルとコマンドはUNIXのシェルプロンプトのものですがWindowsのコマンドラインでも同様に動作します。

<!--## Set up a project-->
## プロジェクトのセットアップ

<!--CMake uses a file named `CMakeLists.txt` to configure the build system for a-->
<!--project. You'll use this file to set up your project and declare a dependency on-->
<!--GoogleTest.-->
CMakeは `CMakeLists.txt` というファイルをプロジェクトをビルドするシステムを設定するために使います。
このファイルを設定することでプロジェクトでGoogleTestを使用することを宣言できます。

<!--First, create a directory for your project:-->
まず、プロジェクト用のディレクトリを作ります。

<!--```-->
<!--$ mkdir my_project && cd my_project-->
<!--```-->
```
$ mkdir my_project && cd my_project
```

<!--Next, you'll create the `CMakeLists.txt` file and declare a dependency on-->
<!--GoogleTest. There are many ways to express dependencies in the CMake ecosystem;-->
<!--in this quickstart, you'll use the-->
<!--[`FetchContent` CMake module](https://cmake.org/cmake/help/latest/module/FetchContent.html).-->
<!--To do this, in your project directory (`my_project`), create a file named-->
<!--`CMakeLists.txt` with the following contents:-->
次に、 GoogleTestを使うことを宣言する `CMakeLists.txt` を作ります。
CMakeエコシステムでは依存関係を説明する方法はたくさんあります。
このクイックスタートでは
[`FetchContent` CMakeモジュール](https://cmake.org/cmake/help/latest/module/FetchContent.html)
を使います。
以上から、プロジェクトのディレクトリ (`my_project`) に作る `CMakeLists.txt` は次の内容となります。

<!--```cmake-->
<!--cmake_minimum_required(VERSION 3.14)-->
<!--project(my_project)-->

<!--# GoogleTest requires at least C++14-->
<!--set(CMAKE_CXX_STANDARD 14)-->

<!--include(FetchContent)-->
<!--FetchContent_Declare(-->
<!--  googletest-->
<!--  URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip-->
<!--)-->
<!--# For Windows: Prevent overriding the parent project's compiler/linker settings-->
<!--set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)-->
<!--FetchContent_MakeAvailable(googletest)-->
<!--```-->
```cmake
cmake_minimum_required(VERSION 3.14)
project(my_project)

# GoogleTest requires at least C++14
set(CMAKE_CXX_STANDARD 14)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)
```

<!--The above configuration declares a dependency on GoogleTest which is downloaded-->
<!--from GitHub. In the above example, `03597a01ee50ed33e9dfd640b249b4be3799d395` is-->
<!--the Git commit hash of the GoogleTest version to use; we recommend updating the-->
<!--hash often to point to the latest version.-->
上記の設定ではGitHubからダウンロードするGoogleTestを使うことを宣言しています。
この例ではGitにおけるコミット `03597a01ee50ed33e9dfd640b249b4be3799d395` が使用するGoogleTestのバージョンとなります。
使用するハッシュは頻繁に最新バージョンのものにすることをお勧めします。

<!--For more information about how to create `CMakeLists.txt` files, see the-->
<!--[CMake Tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/index.html).-->
`CMakeLists.txt` をどのように作るかについてのより詳しい情報は[CMakeチュートリアル]を参照してください。

<!--## Create and run a binary-->
## 作成と実行

<!--With GoogleTest declared as a dependency, you can use GoogleTest code within-->
<!--your own project.-->
GoogleTestへの依存を宣言できたら今度はあなたのプロジェクトでgoogleTestを使ってみましょう。

<!--As an example, create a file named `hello_test.cc` in your `my_project`-->
<!--directory with the following contents:-->
`my_project` ディレクトリに以下の内容の `hello_test.cc` を作る場合の例を示します。

<!--```cpp-->
<!--#include <gtest/gtest.h>-->

<!--// Demonstrate some basic assertions.-->
<!--TEST(HelloTest, BasicAssertions) {-->
<!--  // Expect two strings not to be equal.-->
<!--  EXPECT_STRNE("hello", "world");-->
<!--  // Expect equality.-->
<!--  EXPECT_EQ(7 * 6, 42);-->
<!--}-->
<!--```-->
```cpp
#include <gtest/gtest.h>-->

// Demonstrate some basic assertions.
TEST(HelloTest, BasicAssertions) {
  // Expect two strings not to be equal.
  EXPECT_STRNE("hello", "world");
  // Expect equality.
  EXPECT_EQ(7 * 6, 42);
}
```

<!--GoogleTest provides [assertions](primer.md#assertions) that you use to test the-->
<!--behavior of your code. The above sample includes the main GoogleTest header file-->
<!--and demonstrates some basic assertions.-->
GoogleTestが提供する[アサーション](primer.md#assertions)を使ってあなたのコードの振る舞いをテストします。
上のサンプルはGoogleTestの主となるヘッダをincludeしており、基本的なアサーションを実際に試すことができます。

<!--To build the code, add the following to the end of your `CMakeLists.txt` file:-->
コードをビルドするために、 `CMakeLists.txt` の末尾に以下の内容を追加します。

<!--```cmake-->
<!--enable_testing()-->

<!--add_executable(-->
<!--  hello_test-->
<!--  hello_test.cc-->
<!--)-->
<!--target_link_libraries(-->
<!--  hello_test-->
<!--  GTest::gtest_main-->
<!--)-->

<!--include(GoogleTest)-->
<!--gtest_discover_tests(hello_test)-->
<!--```-->
```cmake
enable_testing()

add_executable(
  hello_test
  hello_test.cc
)
target_link_libraries(
  hello_test
  GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(hello_test)
```

<!--The above configuration enables testing in CMake, declares the C++ test binary-->
<!--you want to build (`hello_test`), and links it to GoogleTest (`gtest_main`). The-->
<!--last two lines enable CMake's test runner to discover the tests included in the-->
<!--binary, using the-->
<!--[`GoogleTest` CMake module](https://cmake.org/cmake/help/git-stage/module/GoogleTest.html).-->
上記の設定はCMakeによるテストを有効にし、C++のテストバイナリ (`hello_test`) をビルドし、GoogleTest (`gtest_main`)にリンクすることを宣言します。 
最後の二行はバイナリ中のテストを見つける
[`GoogleTest` CMakeモジュール](https://cmake.org/cmake/help/git-stage/module/GoogleTest.html)
を使ったCMakeのテストランナーを有効にします。

<!--Now you can build and run your test:-->
これでテストをビルドして実行することができます。

<!--<pre>-->
<!--<strong>my_project$ cmake -S . -B build</strong>-->
<!---- The C compiler identification is GNU 10.2.1-->
<!---- The CXX compiler identification is GNU 10.2.1-->
<!--...-->
<!---- Build files have been written to: .../my_project/build-->

<!--<strong>my_project$ cmake --build build</strong>-->
<!--Scanning dependencies of target gtest-->
<!--...-->
<!--[100%] Built target gmock_main-->

<!--<strong>my_project$ cd build && ctest</strong>-->
<!--Test project .../my_project/build-->
<!--    Start 1: HelloTest.BasicAssertions-->
<!--1/1 Test #1: HelloTest.BasicAssertions ........   Passed    0.00 sec-->

<!--100% tests passed, 0 tests failed out of 1-->

<!--Total Test time (real) =   0.01 sec-->
<!--</pre>-->
<pre>
<strong>my_project$ cmake -S . -B build</strong>
-- The C compiler identification is GNU 10.2.1
-- The CXX compiler identification is GNU 10.2.1
...
-- Build files have been written to: .../my_project/build

<strong>my_project$ cmake --build build</strong>
Scanning dependencies of target gtest
...
[100%] Built target gmock_main

<strong>my_project$ cd build && ctest</strong>
Test project .../my_project/build
    Start 1: HelloTest.BasicAssertions
1/1 Test #1: HelloTest.BasicAssertions ........   Passed    0.00 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.01 sec
</pre>

<!--Congratulations! You've successfully built and run a test binary using-->
<!--GoogleTest.-->
おめでとうございます！GoogleTestを使ってテストをビルド・実行することができました。

<!--## Next steps-->
## 次に

<!--*   [Check out the Primer](primer.md) to start learning how to write simple-->
<!--    tests.-->
*   [入門を見て](primer.md) 簡単なテストをどのように書くか学びましょう。 
<!--*   [See the code samples](samples.md) for more examples showing how to use a-->
<!--    variety of GoogleTest features.-->
*   [コードサンプル](samples.md) GoogleTestの機能をどのように使うかの例を見てみましょう。
