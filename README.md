# REST-APIをAWSで実装する

## 作業記録

1. Poetryの導入

### Poetryの導入実験

- [参考ドキュメント:Poetry documentation 日本語](https://cocoatomo.github.io/poetry-ja/)

1. インストール
    - 公式ドキュメントのコマンドでは404エラーが発生してインストール出来ない

    ``` bash
    curl -sSL https://install.python-poetry.org | python -
    ```

2. プロジェクトのセットアップ
    - Poetryの管理に関わるファイル
        - `pyproject.toml` : 最も重要なファイル。プロジェクトの依存関係を統括する
        - `poetry.lock` : 依存関係のパッケージのバージョンを指定する
    - プロジェクトの作成コマンド

    ``` bash
    # 新規にプロジェクトを作る場合
    > poetry new poetry-demo

    # すでに存在するプロジェクトでPoetryを有効にする場合
    > poetry init
    ```

    - 依存関係の定義・インストールコマンド
        - インストールするパッケージのバージョンを固定したい場合は `poetry.lock` で定義する

    ``` bash
    # 依存するパッケージの追加・インストール
    > poetry add ${パッケージ名}

    # パッケージを削除する
    > poetry remove ${パッケージ名}

    # プロジェクトで定義された依存するパッケージのインストール
    > poetry install

    # プロジェクトで定義された依存するパッケージのバージョンアップ
    > poetry update

    # 利用可能なパッケージを列挙する
    > poetry show
    ```

    - スクリプトの実行コマンド

    ``` bash
    # 作成したPythonスクリプトの実行
    > poetry run python ${スクリプト名}
    ```

    - 仮想環境の起動コマンド

    ``` bash
    # 仮想環境を起動する
    > poetry shell

    # 仮想環境を終了する
    > exit

    # シェルを無くさずに仮想環境を終了する
    > deactivate
    ```
