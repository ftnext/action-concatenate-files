# action-concatenate-files
concatenate files into one file

このGitHub Actionは、指定したファイルをつなげて1つのファイルを作ります。

## Inputs

### `sources`

**必須** つなげるファイルのパス  
左のファイルの内容の後に、右のファイルの内容をつなげます。  
`path/to/file1 path/to/file2`と指定した場合、file1の内容の後にfile2の内容が続きます。

リポジトリのルートからの相対パスで指定してください。  
**空白文字はエスケープ** してください（Exampleを参照ください）

### `destination`

**必須** 作成されるファイルのパス  
リポジトリのルートからの相対パスで指定してください。

## Example Usage

ユースケースは、複数のファイルに分かれた[doctest](https://docs.python.org/ja/3/library/doctest.html)を通して実行するために、ファイルの内容をつなげるというものです。  
具体的には、SphinxでいくつかのreSTファイルをincludeして1つの章を構成する場合です。

- このActionの呼び出し方については[example.yml](https://github.com/ftnext/action-concatenate-files/blob/main/.github/workflows/example.yml)を参照ください
- 各ファイルについては、[`example`ディレクトリ以下](https://github.com/ftnext/action-concatenate-files/tree/main/example)を参照ください。

## FAQ

### Q: doctestの実行までをこのActionに含めていないのはなぜ？

指定されたファイルをつなげた後、できたファイルについてdoctestを実行する実装も考えました。  
doctestの実行にサードパーティライブラリのインストールが必要な場合も考えられます。  
必要なライブラリのインストールは各リポジトリのActionにゆだね、このActionには、サードパーティライブラリの有無によらず**必要なファイルの連結だけを切り出す**ことにしました。  
このActionを再利用しやすくするための判断です。
