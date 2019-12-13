# learning-docker: Dockerの練習

## ミニレポート

### Q1-1: 同じ `docker container run` コマンドを2回実行すると、1回目と2回目で違いはありますか？どう違いますか？

【回答欄】
1回目
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
7ddbc47eeb70: Pull complete
c1bbdc448b72: Pull complete
8c3b70e39044: Pull complete
45d437916d57: Pull complete
Digest: sha256:6e9f67fa63b0323e9a1e587fd71c561ba48a034504fb804fd26fd8800039835d
Status: Downloaded newer image for ubuntu:latest
Hello world
2回目
Hello world

### Q1-2: なぜ違いますか？

【回答欄】
最初にはイメージファイルがなかったからダウンロードしたから

### Q1-3: `docker container ls` と `docker container ls -a` はどう違いますか？

【回答欄】
docker container ls
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

docker container ls -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                     PORTS               NAMES
1c90c5d4449c        ubuntu:latest       "/bin/echo 'Hello wo…"   3 minutes ago       Exited (0) 3 minutes ago                       naughty_swirles
a6221d5efc42        ubuntu:latest       "/bin/echo 'Hello wo…"   5 minutes ago       Exited (0) 5 minutes ago                       stupefied_volhard
e578401fdb16        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                          lucid_moser
702dca02c4af        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                          bold_hamilton
2d2c42caa9ca        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                          modest_meninsky

-a オプションを使ったら全てのcontainerを見せます

### Q1-4: `docker image ls` と `docker container ls -a` はどう違いますか？（間違ってもいいので、自分の考えを述べてください）

【回答欄】
docekr image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              latest              775349758637        6 weeks ago         64.2MB
hello-world         latest              fce289e99eb9        11 months ago       1.84kB

docker container ls -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                     PORTS               NAMES
1c90c5d4449c        ubuntu:latest       "/bin/echo 'Hello wo…"   7 minutes ago       Exited (0) 7 minutes ago                       naughty_swirles
a6221d5efc42        ubuntu:latest       "/bin/echo 'Hello wo…"   9 minutes ago       Exited (0) 9 minutes ago                       stupefied_volhard
e578401fdb16        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                          lucid_moser
702dca02c4af        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                          bold_hamilton
2d2c42caa9ca        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                          modest_meninsky

imageはimageの詳しい情報を、containerは何のイメージを使うのかを含めたcontainerの情報を見せる

### Q1-5: `ubuntu` イメージでの `cat /etc/issue` の結果をペーストしてください

【回答欄】
Ubuntu 18.04.3 LTS \n \l

### Q1-6: `docker image ls` と `docker container ls -a` はどう変化しましたか？

【回答欄】
docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              latest              775349758637        6 weeks ago         64.2MB
hello-world         latest              fce289e99eb9        11 months ago       1.84kB

docker container ls -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                        PORTS               NAMES
735e22178349        ubuntu:latest       "/bin/bash"              2 minutes ago       Exited (130) 35 seconds ago                       distracted_bardeen
1c90c5d4449c        ubuntu:latest       "/bin/echo 'Hello wo…"   13 minutes ago      Exited (0) 13 minutes ago                         naughty_swirles
a6221d5efc42        ubuntu:latest       "/bin/echo 'Hello wo…"   15 minutes ago      Exited (0) 15 minutes ago                         stupefied_volhard
e578401fdb16        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                             lucid_moser
702dca02c4af        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                             bold_hamilton
2d2c42caa9ca        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                             modest_meninsky

docker image lsは変わってなかったんですがdocker container ls -aでは/bin/bashが追加されました。

### Q2-1: `-d` (デタッチド・モード) でコンテナを起動すると、どのような状態になりましたか？

【回答欄】
バックグラウンドで実行します。

### Q2-2: http://localhost/ をブラウザで開くと、何が表示されましたか？

【回答欄】
It works!

### Q2-3: コンテナの起動時と終了時で、docker container ls -a はどのように変化しましたか？

【回答欄】
docker container ls -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                        PORTS               NAMES
e5feae28ee16        nginx               "nginx -g 'daemon of…"   4 minutes ago       Created                                           webserver
735e22178349        ubuntu:latest       "/bin/bash"              12 minutes ago      Exited (130) 10 minutes ago                       distracted_bardeen
1c90c5d4449c        ubuntu:latest       "/bin/echo 'Hello wo…"   23 minutes ago      Exited (0) 23 minutes ago                         naughty_swirles
a6221d5efc42        ubuntu:latest       "/bin/echo 'Hello wo…"   25 minutes ago      Exited (0) 25 minutes ago                         stupefied_volhard
e578401fdb16        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                             lucid_moser
702dca02c4af        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                             bold_hamilton
2d2c42caa9ca        hello-world         "/hello"                 7 days ago          Exited (0) 7 days ago                             modest_meninsky

nginx -g 'demon of...が追加されました。

### Q3-1: `docker build -t sample-image .` 実行時に表示されている `building...` は、Dockerfileのどの行から実行されましたか？

【回答欄】
12行の RUN echo "building..."

### Q3-2: `docker run sample-image` を実行すると、どうなりましたか？

【回答欄】
Switch to inspect mode.が出力されます。