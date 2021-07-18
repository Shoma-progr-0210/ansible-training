# Ansible on Centos7

## コンテナ構築

### ビルド

```
$ docker-compose build --no-cache
```

### 削除

```
$ reset.bat
```

## コンテナ起動・停止

### 起動

```
$ restart.bat
```

### 停止

```
$ stop.bat
```

## centos コンテナの環境構築

コンテナに入る

```
$ docker-compose exec ansible bash
```

ansible の動作確認

```
$ ansible -m ping localhost
```

確認結果

```
localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

インベントリファイルを設定します。
最初は、テンプレートを使用します。

```
$ cp inventory.ini hosts
```

node01~03 に対して、ssh で接続確認を行います。
この作業で、予めターゲットノードを ssh の known に登録します。
※node0x の x は 1~3 に置き換えてください
※接続を続けるかを聞かれた場合は yes と入力して下さい

```
$ ssh node0x
$ exit
```

ターゲットノードに対して疎通確認を行います。

```
$ ansible -m ping node
```

playbook.yml を実行して、ターゲットノードに httpd をセットアップします。

```
$ ansible-playbook playbook.yml
```

ターゲットノードで httpd が正常に動作しているかをブラウザで確認してください。

node0x: http://localhost:808x
