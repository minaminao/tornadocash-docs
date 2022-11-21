# Minified UI Hosted Locally
トルネード・キャッシュ・プロトコルは、コア開発者チームによって利用可能にされた最小化されたユーザー・インターフェース・バージョンを通じて、あなたのコンピュータ上でローカルに起動することができます。

{% embed url="https://github.com/tornadocash/ui-minified" %}.

### Step #1: Clone the Github repository on your computer
コマンドラインインターフェイスを開いて、以下のコマンドを実行すると、まずリポジトリをクローンし、新しくコピーされたフォルダの中に入ることができます。

```
git clone https://github.com/tornadocash/ui-minified.git
cd ui-minified
```
### Step #2: Serve the Folder with Your Favorite HTTP Server
```
python -m SimpleHTTPServer 8080
```
[ npmjs.com/package/http-server](https://www.npmjs.com/package/http-server)など、他のhttpウェブサーバーも当然使用できます。

### Step #3: Run the UI on Localhost on your Favorite Web Browser
ウェブブラウザー上で[http://localhost:8080](http://localhost:8080)を起動し、魔法をかけるだけですᾤ。

## Running a TOR service
.onionドメインでトルネードキャッシュUIを提供したい場合、docker-composeを使用して簡単に実現する方法があります。

* `docker-compose.yml`に以下を貼り付ける必要があります。

```
version: '2'

services:
  tornado_ui:
    image: tornadocash/ui
    restart: always
    container_name: tornado_ui
  watchtower:
    image: v2tec/watchtower
    restart: always
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    command: --interval 60 tornado_ui
  tor:
    image: strm/tor
    restart: always
    depends_on: [ tornado_ui ]
    environment:
      LISTEN_PORT: 80
      REDIRECT: tornado_ui:80
      # Generate a new key with
      # docker run --rm --entrypoint shallot strm/tor-hiddenservice-nginx ^torn
      PRIVATE_KEY: |
        -----BEGIN RSA PRIVATE KEY-----
        ...
        -----END RSA PRIVATE KEY-----
```
* そして、次のコマンドを実行するだけです：`docker-compose up -d`

トルネードキャッシュUIをお楽しみください🌪。

*This tutorial is inspired from the*[ *README.md document*](https://github.com/tornadocash/ui-minified/blob/gh-pages/README.md) *present in the Github repository.*

__

*Written by* [*@ayefda*](https://torn.community/u/ayefda)

