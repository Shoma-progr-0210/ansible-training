# Ansible on CentOS7

## コンテナ構築

### ビルド

```
$ docker-compose build --no-cache
```

### 削除

```
$ docker-compose down -v
```

## コンテナ起動・停止

### 起動

```
$ docker-compose up -d
```

### 停止

```
$ docker compose stop
```

## centos コンテナの環境構築

コンテナに入る

```
$ docker-compose exec ansible bash
```

ansible の動作確認

```
$ ansible localhost -m ping
```

確認結果

```
localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

node0x に対して、SSH で接続確認を行います。  
この作業で、予めターゲットノードを SSH の known_hosts に登録します。  
※node0x の x はターゲットノードの番号に置き換えてください  
※接続を続けるかを聞かれた場合は yes と入力して下さい

```
$ ssh node0x
$ exit
```

ターゲットノードに対して疎通確認を行います。

```
$ ansible node -m ping
```

playbook.yml を実行して、ターゲットノードに httpd をセットアップします。

```
$ ansible-playbook playbook.yml
```

ターゲットノードで httpd が正常に動作しているかをブラウザで確認してください。

node0x: http://localhost:808x
