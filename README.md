# REST-APIをAWSで実装する

- [講座情報](https://www.udemy.com/course/awsrest-api/learn/lecture/33857942#overview)

## 作業記録

1. Poetryの導入
2. 講座を開始

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

### 受講メモ

#### 使用環境

|ツール|Version|メモ|
|---|---|---|
|OS: Mac|3.3.1 (a)（22E772610a）||
|curl|8.1.2||

#### ゴール

- REST APIの特徴（メリット、デメリット）を説明できる
    - メリット
    - デメリット
- サーバレスアーキテクチャの特徴（メリット、デメリット）を説明できる
- AWSの以下のサービスを使った講座の環境を説明できる
    - Amazon API Gateway
    - AWS Lambda
    - Amazon DynamoDB

#### APIの種類

- API
    - API: 単一のAPIリクエストを1回のAPI呼び出しで行うAPI
    - Composite API: 複数のAPIリクエストを1回のAPI呼び出しで可能にするAPI
- APIの公開範囲
    - Open API: 全ての企業などに公開しているAPI
        - 例: Google Maps API
    - Partner API: 特定の企業、個人に限定公開しているAPI
        - 例: Amazon Product Advertising API
    - Closed API: 非公開のAPI -> 外部の人は使えない
        - 例: A銀行預金残高API
- APIの作り方
    - REST API: リソース単位(各リソースで実行できる処理を作る)で作成する。 XML、JSON形式で提供される
    - SOAP: メソッド単位(登録などの操作単位で各リソースにアクセスする)で作成する。 XML形式で提供される
