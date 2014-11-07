# Linuxでよく使うコマンド

history見て使っているコマンドを洗い出してみました。

## php

コマンドラインでPHPファイルを実行するときに使う。  
(```-f```を使って使うことが多いが、```-f```をつけなくても実行できるっぽい。)

**使用例**  

```bash
$ php -f ./test.php
```

---

## pwd
今いるディレクトリを確認する。

```bash
$ pwd
/home/watanabe/test
```

---

## cp
ファイルをコピーする。

**使用例**

今いるフォルダにあるhtmlファイルを1つ上の階層のcontentsディレクトリにコピー

```bash
cp ./test.html ../contents/
```


