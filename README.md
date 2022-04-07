# action-concatenate-files

（日本語が後に続きます）

This GitHub Action concatenates the specified files into one file.

このGitHub Actionは、指定したファイルをつなげて1つのファイルを作ります。

## Inputs

### `sources`

**Required** The paths to the concatenated files.  
Specify them from left to right, separated by spaces.

The content of the left file is followed by the content of the right file.  
If you specify `path/to/file1 path/to/file2`, the contents of file1 are followed by the contents of file2.

Specify these as relative paths from the root of the repository.  
**Space characters must be escaped** (see Example).

**必須** つなげるファイルのパス。  
空白で区切って左から右へ並べます。

左のファイルの内容の後に、右のファイルの内容をつなげます。  
`path/to/file1 path/to/file2`と指定した場合、file1の内容の後にfile2の内容が続きます。

リポジトリのルートからの相対パスで指定してください。  
**空白文字はエスケープ** してください（Exampleを参照ください）

### `destination`

**Required** The path to the created file.  
Specify this as relative paths from the root of the repository.  

**必須** 作成されるファイルのパス  
リポジトリのルートからの相対パスで指定してください。

## Example Usage

The use case is to concatenate the contents of files which are divided into multiple files to run [doctest](https://docs.python.org/3/library/doctest.html).  
Specifically, when you use Sphinx, you want to include several reST files to form a single chapter and run doctest on the contents of the chapter.

- See [example.yml](https://github.com/ftnext/action-concatenate-files/blob/main/.github/workflows/example.yml) for how to call this Action
- See [under the `example` directory](https://github.com/ftnext/action-concatenate-files/tree/main/example) for the details of the files

ユースケースは、複数のファイルに分かれた[doctest](https://docs.python.org/ja/3/library/doctest.html)を通して実行するために、ファイルの内容をつなげるというものです。  
具体的には、SphinxでいくつかのreSTファイルをincludeして1つの章を構成する場合です。

- このActionの呼び出し方については[example.yml](https://github.com/ftnext/action-concatenate-files/blob/main/.github/workflows/example.yml)を参照ください
- 各ファイルについては、[`example`ディレクトリ以下](https://github.com/ftnext/action-concatenate-files/tree/main/example)を参照ください。

## FAQ

### Q: Why does this Action not run doctest? / doctestの実行までをこのActionに含めていないのはなぜ？

I also considered an implementation of running doctest on the concatenated file.  
It may be necessary to install third-party libraries to execute doctest.  
i decided to leave the installation of the necessary libraries to each repository's Action and to have this Action only **concatenate the target files**.  
Concatenation is always needed regardless of whether or not third-party libraries are necessary.  
This decision made it easier to reuse this Action.

指定されたファイルをつなげた後、できたファイルについてdoctestを実行する実装も考えました。  
doctestの実行にサードパーティライブラリのインストールが必要な場合も考えられます。  
必要なライブラリのインストールは各リポジトリのActionにゆだね、このActionには、サードパーティライブラリの有無によらず**必要なファイルの連結だけを切り出す**ことにしました。  
このActionを再利用しやすくするための判断です。
