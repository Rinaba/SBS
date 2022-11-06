# 日誌
## 2022/11/06

* 以下の環境にRustの環境構築した時に詰まったこと

~~~
% sw_vers
ProductName:		macOS
ProductVersion:		13.0
BuildVersion:		22A380
~~~

cargo runが失敗する。

~~~
% cargo run
   Compiling first-project v0.1.0 (/xxxxx/xxxxxxxxxxxx/first-project)
error: linking with `cc` failed: exit status: 1
:
(略)
:
  = note: xcrun: error: active developer path ("/Applications/Xcode.app/Contents/Developer") does not exist
          Use `sudo xcode-select --switch path/to/Xcode.app` to specify the Xcode that you wish to use for command line developer tools, or use `xcode-select --install` to install the standalone command line developer tools.
          See `man xcode-select` for more details.

error: could not compile `first-project` due to previous error
~~~

'Use~'以下の通りに、`xcode-select --install`したが、再度同じエラーに。

もう一方のコマンド`sudo xcode-select --switch path/to/Xcode.app`はそのまま入力しても'path~が存在しない'と注意される。よく見ると、'path/to/Xcode.app'は明らかにパスの例だった。Xcode.appをインストールしていれば、Xcode.appのパスを指定すればいいが、あいにくXcode.appはインストールしていない。

`xcode-select --install`でインストールされたと思われるCoomandLineToolsのパスを指定すれば良さそうなので、どこにありそうかググる。

調べた結果、CommandLineToolsが以下に存在することがわかった。
/Library/Developer/CommandLineTools

参考：https://dezanari.com/homebrew-without-xcode/

以下のコマンドを実行し、
sudo xcode-select --switch /Library/Developer/CommandLineTools

cargo runでRustのプログラムが実行できた。
~~~
% cargo run
   Compiling first-project v0.1.0 (/xxxxx/xxxxxxxxxxxx/first-project)
    Finished dev [unoptimized + debuginfo] target(s) in 1.38s
     Running `target/debug/first-project`
Hello, world!
~~~

## 2022/03/27

* Reactのチュートリアルの機能拡張をテストコードを書いて実装してみたい。  

## 2022/03/13

* Reactのチュートリアルを実施  
  チュートリアル：Reactの導入  
  <https://ja.reactjs.org/tutorial/tutorial.html>
  * チュートリアル着手前に以下を確認  
    JavaScript「再」入門  
  <https://developer.mozilla.org/ja/docs/Web/JavaScript/A_re-introduction_to_JavaScript#numbers>

* 作成したチュートリアルのアプリをfirebaseにデプロイした。  
  <https://selftaughtreact.web.app/>  
  firebaseの登録とデプロイで参考にした記事は以下のとおり
  * （初心者向け）Firebase HostingへReactプロジェクトを公開する手順  
  <https://qiita.com/junara/items/74801923ca108b328b26>
  * Firebaseでデプロイしよう！  
  <https://qiita.com/hiroki-harada/items/ca22ac177db68e3c3796>
  * ホスティング動作を構成する  
  <https://firebase.google.com/docs/hosting/full-config?hl=ja>

## 2022/03/06

* 以下の動画を視聴
  * TDD Boot Camp 2020 Online #1基調講演/ライブコーディング  
 <https://www.youtube.com/watch?v=Q-FJ3XmFlT8&list=WL&index=21>
* Software Design 2022年3月号
  * そろそろはじめるテスト駆動開発の第3章の続きから最後まで実施

## 2022/02/27

* 以下の動画を視聴
  * VS Code Meetup #11 - 入門編2021  
 <https://www.youtube.com/watch?v=kEnnjzYcTC8&list=WL&index=18>
* VScodeをインストール
* Software Design 2022年3月号
  * そろそろはじめるテスト駆動開発の第3章の途中まで実施
  * 目的：テストコードの書き方とTDDのさわりを体験したい。
