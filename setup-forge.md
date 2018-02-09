## Minecraft Forgeをセットアップする

Forgeは推奨されているバージョン（Download Recommended）のmdkを
[files.minecraftforge.net](https://files.minecraftforge.net/)
からダウンロードします。
本稿を執筆している現在、1.12.2が最新バージョンです。悪質な広告がAdobe Flash playerをアップデートしなさいと画面に表示しますが、
落ち着いてSkipボタンを押してください。そうするとforge-1.12.2-14.23.2.2611-mdk.zip(1.12.2以降のマイナーバージョンは違うかもしれません。)
がダウンロードされるのでダブルクリックするなどして解凍します。
Terminal(ターミナルアプリ)を開き、先ほど解凍したフォルダに移動します。

```shell
$ cd ~/Downloads/forge-1.12.2-14.23.2.2611-mdk
```

`cd`はchange directory、すなわち別のディレクトリへ移動するコマンドです。`~/`は実行中のアカウントのホームディレクトリ(`$HOME`)を指すショートハンドです。
Mac OSではブラウザ等でダウンロードしたファイルは基本的にホームディレクトリ直下の`Downloads`ディレクトリに入るので、
上記のコマンドで解凍したforgeのディレクトリに移動する事が出来ます。バージョンが違う場合はディレクトリ名を解凍したフォルダ名で移動します。
現在のディレクトリを知るには`pwd`コマンドを使います。

```shell
$ pwd
/Users/nksma/Downloads/forge-1.12.2-14.23.2.2611-mdk
```

Gradleスクリプトでワークスペースをセットアップします。
READMEによると下記のコマンドを実行するよう書いてあります。
> Windows: "gradlew setupDecompWorkspace"<br/>
> Linux/Mac OS: "./gradlew setupDecompWorkspace"

私の環境はMac OSなので、下記の通りにコマンドを打つと、gradleスクリプトが実行されて必要なファイルがダウンロードされたりパッチ（MCPへのパッチ）が当てられたりします。
パッチ(Patch)とは変更点とそれを適用する場所を含んだファイルで、patchを当てる事でオリジナルのファイルに意図した変更を加える事ができます。

```shell
$./gradlew setupDecompWorkspace
```

バージョンが変わるとセットアップ方法が変わる場合があります。
このドキュメントの通りにしても上手くいかない場合はフォルダ内のREADMEを読んでみてください。
ネットワークのエラーで失敗する事もあるので、再度上記のコマンドで`gradle`スクリプトを実行すると成功するかもしれません。
失敗して困ったらお知らせください。Terminalは閉じずにそのまま次のステップに進みます。

IDE（開発環境）はIntellijを使います。Eclipseを使っている方はこれを機に乗り換えましょう。Intellijは
[Jetbrainsのダウンロードページ](https://www.jetbrains.com/idea/download/)
からCommunity Editionをダウンロードします。間違ってもEclipseのKey bindは使わないように。

Intellijを開き、Import projectを選びます。先ほどダウンロードして解凍したForgeのディレクトリ内にある`build.gradle`を開きます。
[OracleのJavaページ](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
Gradle JVMの欄にjdkが表示されない場合、JDKがインストールされている場所を指定してください。JDKのインストールがお済みでない場合は、
下記のサイトからJDK 8をインストールしてください。Minecraft/ForgeはJDK 9での動作が確認されていません。

インポートすると、ビルドスクリプトが実行されます。しばらくかかるので、完了するまでお待ちください。
ビルドが完了したら、プロジェクトを閉じてTerminalに戻ります。

Intellij用のgradleスクリプトを実行します。

```shell
$ ./gradlew genIntellijRuns
```

Intellijを開き、forgeプロジクトを選んで開きます。
Intellijの画面中央上部に再生ボタンがあります。その左のプルダウンメニューからMinecraft Clientを選び、
再生ボタンをクリックするとプロジェクトが実行され、マインクラフトが開きます。
Intellij画面下部にあるRun(実行)ウィンドウに実行ログが表示されます。その中に下のようなexamplemodと書かれたメッセージが表示されます。

```
[22:49:56] [main/INFO] [examplemod]: DIRT BLOCK >> minecraft:dirt
```

これはForgeに同梱されている恐ろしく単純なサンプルModによって書き出されています。
