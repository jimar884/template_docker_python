# template_docker_python
Docker で Python 環境を作るためのテンプレートです．

### 前提条件
Docker (https://docs.docker.com/) のインストールが完了していること．

### 使用の流れ
1. **.env** ファイルを作成．  中身は，`SRC_PATH=./src`
1. `docker compose up -d --build` を実行により，コンテナ・イメージを生成，コンテナを起動．
1. `docker container ls` と `docker image ls` の実行により，起動中のコンテナとイメージをそれぞれ確認．
1. `docker exec -it python3_sample bash` の実行によりコンテナに接続．  `python3_smaple` は， `docker container ls` 実行時に確認できるコンテナの名前．  **docker-compose.yml** 内で指定した名前のコンテナが `build` 時に生成される．
1. `python sample.py` で動作確認
1. `exit` の実行によりコンテナから抜ける．
1. 'docker container stop containerID' の実行により，コンテナを停止．  containerIDは `docker container ls`で確認可能．

### おまけ
- **作成済みのコンテナの利用** : 'docker container start containerID' の実行により，作成済みのコンテナを再起動．  起動していないコンテナは確認には， `docker container ls -a` を実行する．  その後の使い方は，先に説明した使用の流れ (`docker exec ...`) と同じ．
- **コンテナの削除** : 'docker container rm containerID' によりコンテナ削除．  削除前にコンテナは停止させる．
- **イメージの削除** : 'docker image rm imageID' によりイメージ削除
