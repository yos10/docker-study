# Docker Desktop で Node.js の開発

参考にすると良さそうなページ

DockerCon で Docker Captain が講演している動画とそのリポジトリ

- 2019 年版

  - https://www.youtube.com/watch?v=Zgx0o8QjJk4

  - https://github.com/BretFisher/nodejs-rocks-in-docker/tree/7773bc49fa478181f5ee46201ab14f6039366ada

  - https://github.com/BretFisher/node-docker-good-defaults

- 2022 年版

  - https://www.youtube.com/watch?v=Z0lpNSC1KbM

  - https://github.com/BretFisher/nodejs-rocks-in-docker

## ファイルを共有するとパフォーマンスが低下するときの対処法

Mac の場合

- Docker Desktop の設定で Virtiofs(試験的な機能)を有効にすると良さそう(Mac 使ったことないからわからない)。

Windows の場合

1. Microsoft Store から Ubuntu をインストール

1. Docker Desktop の Dashboard から WSL INTEGRATION で Ubuntu にチェック

1. ファイルは //wsl$/Ubuntu/home/USERNAME/ 以下に置く

1. VS Code に [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) 拡張機能をインストール

### パフォーマンス低下の具体的な例

- JavaScript の実行速度が遅い

  - 簡単なテストコードでも遅い
  - サーバー起動が遅い

- イメージのビルドが遅い

### 試行錯誤したことのメモ

https://www.docker.com/blog/file-sharing-with-docker-desktop/

公式ブログにファイル共有のベストプラクティスが公開されていたのでメモ。

> - Large, static dependency trees or libraries could be moved into a named volume, or WSL, or even baked into the container image

- 名前つきボリューム

  - デメリット
    - インテリセンスの入力候補が表示されない

- イメージに含む

  - デメリット
    - インテリセンスの入力候補が表示されない

- VS Code の devcontainer
  - インテリセンスの入力候補が表示される
