## Anaconda とは

チュートリアルの参加者の中には、Pythonをインストール済みの方もいるかもしれませんね。
[Pythonのインストール](../python_installation/README.md)の方法とは異なり、*Anaconda*という道具を使ってPythonをインストールされた方もいるかもしれません。

Anacondaは、Pythonのインストールに使われる道具の1つです。
**Anacondaをインストールすることで、Pythonが使えるようになります**。
Anacondaでは、科学分野での計算に使うPythonのパッケージも合わせてインストールされます。
Pythonでデータサイエンスや機械学習をする場合に、Anacondaが選択されることがあります。

AnacondaでのDjangoのインストール方法は、このチュートリアルで説明している「仮想環境」とは異なります。
Anacondaを使っている方向けにこのチャプターを用意しました。

## Conda環境

Django をインストールする前に、あなたのコーディング環境を、きれいにしておく便利な道具の使い方を学びましょう。
このステップをとばすこともできますが、しかし、このステップをとばすことは全くお勧めしません。
可能な限りベストなセットアップで始めることは将来のたくさんのトラブルからあなたを救うはずですから！

さあ、**Conda環境（Conda environment）**を作成してみましょう。
Conda環境（Conda environment）ではプロジェクト単位であなたのPython/Djangoのセットアップを他から隔離します。
これは、あなたがひとつのウェブサイトにおこなったどんな変更も、あなたが開発している他のサイトに影響を及ぼさないということです。便利でしょ？

Conda環境を作成する前にやることが一つあります。
それは、Djangoのアプリケーションを作成したいディレクトリを見つけることです（たとえばホームディレクトリなどです）。
Windowsでは、ホームディレクトリは、`C:\Users\Name`と書かれているかもしれません (`Name`はあなたのログインネームです)。

> **補足：**　Windowsの方は、ディレクトリ名に特殊文字やアクセント記号を含まないよう気をつけてください。もし、ユーザー名が特殊文字を含む場合は、`C:\djangogirls` のようなディレクトリを作成してください。

このチュートリアルのために、ホームディレクトリに新しいディレクトリ`djangogirls`を作成します。

{% filename %}command-line{% endfilename %}

    $ mkdir djangogirls
    $ cd djangogirls
    

いよいよConda環境（Conda environment）を作成します。
Anacondaの特徴の1つは、複数のバージョンのPythonを切り替えられることです。
このチュートリアルで作成するConda環境には、Pythonの*パージョン3.6*を使いましょう。

<!--sec data-title="Conda environment: Windows" data-id="condaenv_installation_windows"
data-collapse=true ces-->

新しいConda環境を作成するために、コマンドプロンプトを開き（コマンドプロンプトについては何章か前にお話ししましたね。覚えてますか？）、`conda create -n myvenv python=3.6`を実行して下さい。
たとえばこのように入力します：

{% filename %}command-line{% endfilename %}

    C:\Users\Name\djangogirls> conda create -n myvenv python=3.6
    

`myvenv` というところが、あなたのConda環境の名前です。
どんな名前でも使うことができますが、必ず小文字で表記し、スペース・アクセント記号・特殊文字は入れないでください。
短い名前にしておくのもいいアイデアですーあなたはこの名前を何度も参照しますから！

実行中に処理を継続するか聞かれます。

{% filename %}command-line{% endfilename %}

    Proceed ([y]/n)?


yを入力してEnterキーを押し、処理が終了するのを待ちましょう。

<!--endsec-->

<!--sec data-title="Conda environment: OS X" data-id="condaenv_installation_linuxosx"
data-collapse=true ces-->

OS XでConda環境を作るときは、`conda create -n myvenv python=3.6`と実行するだけです。
たとえばこんな感じです：

{% filename %}command-line{% endfilename %}

    $ conda create -n myvenv python=3.6
    

`myvenv` は、あなたのConda環境の名前です。
どんな名前でも使うことができますが、必ず小文字で表記し、スペースは入れないでください。
短い名前にしておくのもいいアイデアですーあなたはこの名前を何度も参照しますから！

実行中に処理を継続するか聞かれます。

{% filename %}command-line{% endfilename %}

    Proceed ([y]/n)?


yを入力してEnterキーを押し、処理が終了するのを待ちましょう。

<!--endsec-->

## 仮想環境の操作

上に示したコマンドは`myvenv` という名前（あるいはあなたが選んだ名前）のConda環境を生成します。
次に我々がしたいのは、これを実行し、開始することです。

<!--sec data-title="Working with Conda environment: Windows" data-id="condaenv_windows"
data-collapse=true ces-->

実行して、仮想環境を起動します。

{% filename %}command-line{% endfilename %}

    C:\Users\Name\djangogirls > conda activate myvenv
    

`myvenv`のところをあなたが選んだConda環境名に置き換えることを忘れないで下さいね！

> **補足：**Anacondaのバージョンが古い場合は、`conda activate myvenv`でエラーが出てしまいます。代わりに`activate myvenv`というコマンドを使ってください。

<!--endsec-->

<!--sec data-title="Working with Conda environment: OS X" data-id="condaenv_osx"
data-collapse=true ces-->

実行して、仮想環境を起動します。

{% filename %}command-line{% endfilename %}

    $ conda activate myvenv
    

`myvenv`のところをあなたが選んだConda環境名に置き換えることを忘れないで下さいね！

> **補足：**Anacondaのバージョンが古い場合は、`conda activate myvenv`でエラーが出てしまいます。代わりに`source activate myvenv`というコマンドを使ってください。

<!--endsec-->

Conda環境が起動すると、プロンプトの行頭に`(myvenv)`が現れます。

Conda環境の中で作業しているとき、`python`は自動的に正しいバージョンの`Python`を参照しますので、`python3`の代わりに`python`を使うことができます。

OK,これでDjangoのインストール前に入れておきたい依存関係の準備がすべて整いました。
いよいよDjangoのインストールです！

## Djangoのインストール

あなたのConda環境を起動したので、Djangoをインストールすることができます。

Conda環境では`conda`コマンドでDjangoをインストールします。

{% filename %}command-line{% endfilename %}

    (myvenv) ~$ conda install django=2.0


### Requirementsファイルを用意する

ここまででDjangoのインストールができました。
最後にデプロイに備えた設定をしましょう。（デプロイはこの後の[デプロイ！](../deploy/README.md)で詳しく説明します）

デプロイで使うRequirementsファイルを作成します。
このチュートリアルのデプロイ先では、`conda`コマンドではなく、`pip`コマンドでDjangoをインストールします。
Requirementsファイルは`pip`コマンドでインストールするためのパッケージリストが記載されているファイルです。

前にインストールしたコードエディタを使用して、`requirements.txt` ファイルを `djangogirls/` フォルダーの中に作ります:

    djangogirls
    └───requirements.txt
    

`djangogirls/requirements.txt` ファイル中に以下のテキストを追加します:

{% filename %}djangogirls/requirements.txt{% endfilename %}

    Django~={{ book.django_version }}
    

以上です！あなたは（ついに）Djangoアプリケーションを作成する準備が整いました！
