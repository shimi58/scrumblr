# Scrumblr構築

    Docker上にScrumblr環境を構築する

## 構築手順

1. リポジトリをcloneする
1. dockerenvディレクトリに移動し､以下を実行する

    ```cmd
    docker-compose build
    ```

    再度､クリーンビルドしたい場合は｢--no-cache｣オプションをつける

1. コンテナを起動する

    ```cmd
    docker-compose up -d
    ```

1. 以下のURLにアクセスする

    ```url
    http://localhost:2080
    ```

    ※構築完了まで10秒程度待つ必要あり

