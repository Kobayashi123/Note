# OS

## 起動するまで

**ブートストラップ**：電源投入によって開始されるOS起動までの一連の動作

電源ON → システムBIOS → ブートローダー → OSの起動 の手順で起動する。

1. **システムBIOS**：パソコン本体が備えている機能で、ブートローダーを検出して起動する
2. ブートローダー：OS を検出・起動する
3. OS: GUI が表示される

## ソケット通信

サーバーとクライアント間でネットワークを介してデータの送信・受信を行う仕組みのことである。

IPアドレスとポート番号を指定して、データのやり取りを行う。

1. *socket()*: `socket.socket(address family, socket type)`

    ソケットを生成する。デフォルト設定でいい場合は、引数は不要。

    ＜引数＞
    - address family: アドレスファミリー（デフォルト AF_INET）
    - socket type: ソケットタイプ（デフォルト *SOCK_STREAM*）

    ＜返り値＞
    - ソケットオブジェクト

2. *bind()*: `socket.bind(address)`

    socket()を実行してもソケットが作られただけであり、IPアドレスとポート番号は未確定。

    そこで、bind()により、IPアドレスとポート番号をソケットに割り当てる。

    ＜引数＞
    - IPアドレスとポート番号のタプル

3. *listen()*: `socket.listen([backlog])`

    ソケットを接続待ちの状態にする。

    ＜引数＞
    - 同時接続可能なクライアント数

4. *accept()*: `socket.accept()`

    クライアントからの接続要求に対して、通信の確立を行う。

    ＜返り値＞
    - ソケットオブジェクトと相手のIPアドレス

5. *recv()*: `socket.recv(bufsize)`

    ソケットから送られたデータを受け取る。

    bufsizeは一度で受け取れる最大データ量を指定する。

    bufsizeには4096や2048のような、２の累乗を指定することが勧められている。

    ＜返り値＞
    - 受け取ったデータのバイトオブジェクト

6. *close()*: `socket.close()`

    ソケットを閉じる。

## カーネルビルド

ソースコードの取得
`git clone --depth=1 https://github.com/torvalds/linux.git`

カーネルコンフィグの準備
`make oldconfig`

カーネルモジュールのインストール
`sudo make modules_install`

カーネルのビルド
`make -j8`

カーネルのインストール
`sudo make install`
