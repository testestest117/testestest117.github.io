# Linuxコマンド

Linuxコマンドまとめ。  
アルファベット順。

---

## cat
ファイルの中身を標準出力に出力(画面に表示)します。

<br>

#### 基本形

cat [ファイル名]


<br>

#### 使用例  

```bash
# /home/work/AAA.txtファイルの中身を出力
$ cat /home/work/AAA.txt
AAA
BBB
CCC
```

```bash
#id_rsa.pubファイルの内容をauthorized_keyファイルの最終行に付け足し
$ cat /tmp/id_rsa.pub >> ~/.ssh/authorized_keys"
```

---

## cd
ディレクトリを移動します。

<br>

#### 基本形
cd [対象パス]

<br>

#### 使用例  

```bash
# /var/www/htmlディレクトリに移動
$ cd /var/www/html/
```

---

## cp
ファイルをコピーします。

<br>

#### 基本形
cp [コピー元パス] [コピー先パス]

<br>

#### 使用例  

```bash
# 今いるディレクトリのA.htmlファイルを一つ上の階層にコピー
$ cp ./A.html ..
```

---

## chmod
* ファイルやディレクトリの権限を変更します。
* 権限については[ここらへん](http://www.webzoit.net/hp/it/internet/homepage/env/cs/server/os/type/unix/linux/command/permissions/modes/)をご確認ください。
* ファイル権限によっては意図した場面でプログラムが動かなかったり、編集できない人が出たりします。

<br>

#### 基本形
chmod [パーミッション] [ファイル名]

<br>

#### 使用例  

```bash
# index.htmlのパーミッションを755に変更します
$ chmod 755 index.html
```

---

## chown
ファイルやディレクトリの所有者を変更します。

<br>

#### 基本形
chown [所有者] [ファイル名]

<br>

#### 使用例  

```bash
# /var/www/html配下の所有者を全てuser01に変更する
$ chown -R /var/www/html
```

---

## crontab
* cronとは定期的にコマンドやスクリプト等を自動実行してくれるプログラムです。
* **-l**オプションで、現在設定されているcrontabを表示します。
* **-e**オプションで、crontabを編集します。  
  (crotabの設定の書き方は[こちら](http://www.server-memo.net/tips/crontab.html))  
* **-r**オプションで、現在設定してあるcrontabが全て消えます。
* /var/crontabファイルを直接編集する場合もあります。

<br>

#### 基本形
crontab (オプション)

<br>

#### 使用例  

```bash
$ crontab -l
1 * * * * echo test
```

---

## du
* 特定のディレクトリ等の容量を調べます。
* -shオプションをつけて使うと、見やすいようです。

<br>

#### 基本形
du (オプション)

<br>

#### 使用例  

```bash
#現在のディレクトリ配下の容量を確認
$ du -sh *
4.0K	CONTRIBUTING.md
4.0K	Gruntfile.js
4.0K	LICENSE
240K	css
4.0K	index.html
128K	js
164K	lib
8.0K	md
4.0K	package.json
320K	plugin
184K	test
```
---

## df
* ディスクの使用状況等を確認します。
* -hオプションを使うと分かりやすく表示されるようです。

<br>

#### 基本形
df (オプション)

<br>

#### 使用例

```bash
#色々情報が表示される
$df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.3G  1.6G  5.4G  23% /
tmpfs                 295M     0  295M   0% /dev/shm
/vagrant              466G  208G  258G  45% /vagrant
/var/www/revealjs     466G  208G  258G  45% /var/www/revealjs
```

---

## diff
2つのファイルの差分を取ります

<br>

#### 基本形
diff (オプション) [ファイル名1] [ファイル名2]

<br>

#### 使用例
```bash
# ./backup/ディレクトリと./src/ディレクトリ内のファイルを比較して、差分をdiff.txtに書き出す
diff -crsb --strip-trailing-cr  ./backup/ ./src/ > ./diff/diff.txt
```

---

## find
* ファイルやディレクトリを検索します。
* 使い方によって色々出来そうですが詳しくは知りません。。

<br>

#### 基本形
find [検索対象パス] -name [ワイルドカード]  
※この使い方しか知らない

<br>

#### 使用例
```bash
# testディレクトリ内にある拡張子が付いたファイルを全て検索する
$ find ./test/ -name '*.*'
./test/.DS_Store
./test/examples/.DS_Store
./test/examples/assets/image1.png
./test/examples/assets/image2.png
./test/examples/barebones.html
./test/examples/embedded-media.html
./test/examples/math.html
./test/examples/slide-backgrounds.html
```

---

## grep
* 文字列を検索します。
* -i オプションで小文字/大文字の区別なく検索します。
* -r オプションでディレクトリ内を再帰的に検索します。

<br>

#### 基本形
grep (オプション) [検索文字列] [ファイル名/ディレクトリ名]

<br>

#### 使用例

```bash
$ grep -ir 'test' ./
```

---

## ls
* 現在いるディレクトリのファイルやディレクトリ情報を表示します。
* -a オプションでドットファイルも表示します。
* -l オプションでファイルの詳細情報も表示します。
* 多くの環境ではエイリアスでllコマンドが設定されていて、ls -lと同じ働きをします。

#### 使用例

```bash
$ ll
total 16
drwxr-xr-x  4 watanabejun  staff   136 11 17 10:45 .
drwxr-xr-x  5 watanabejun  staff   170  6 22 14:57 ..
drwxr-xr-x  3 watanabejun  staff   102  6 22 14:57 .vagrant
-rw-r--r--  1 watanabejun  staff  4880 11 17 10:45 Vagrantfile
```

---


## php
* phpファイルをコマンドラインから実行する場合に使います。
* ```-f```オプションをつけて使うことが多いです(つけなくても好いようです)。

<br>

#### 基本形
php (オプション) [ファイル名]

<br>

#### 使用例  

```bash
#今いるディレクトリのtext.phpファイルを実行
$ php -f ./test.php
```

---

## ps
* 実行中のプロセスを表示します。
* auxオプションをつけると、必要十分な情報がとれると思います。  

<br>

#### 基本形
ps (オプション)

<br>

#### 使用例

```bash
# grepと一緒につかうと欲しい情報だけ抽出できる
$ ps aux | grep 'php'
mainte   22559  0.0  0.0   9228  1048 ?        Ss   13:19   0:00 /bin/bash -c (cd /var/backend/au/cron; /usr/bin/php -f Postcard_Composite_Schedule.php >/dev/null 2>&1)
mainte   22561  0.0  0.0   9228  1048 ?        Ss   13:19   0:00 /bin/bash -c (cd /var/backend/au/cron; /usr/bin/php -f Order_Bill.php >/dev/null 2>&1)
mainte   22579  0.0  0.0   9228  1052 ?        Ss   13:19   0:00 /bin/bash -c (cd /var/backend/asbe-z/photo/cron; php Order_Bill.php >/dev/null)
mainte   22580  0.0  0.0   9228   508 ?        S    13:19   0:00 /bin/bash -c (cd /var/backend/au/cron; /usr/bin/php -f Postcard_Composite_Schedule.php >/dev/null 2>&1)
mainte   22581  0.0  0.0   9228  1044 ?        Ss   13:19   0:00 /bin/bash -c (cd /var/backend/asbe-z/photobook/cron; php Photobook_Print_Chk.php >/dev/null 2>&1)
```

---

## top
サーバの稼働状況を確認します。

<br>

####使用例  

```bash
#実行
$ top
```

<img src="../img/top.png" alt="Drawing" style="width: 800px;"/>

---

## tail
* ファイルの末尾を表示します。  
* -fオプションで、対象ファイルの内容を常に監視できます。  
* -fオプションを使って、ログを監視するときによく使います。

<br>

#### 基本形
tail (オプション) [ファイル名]

<br>

#### 使用例

<br>

```bash
tail -f ./application.log
```

```bash
# grepと一緒に使うことで、特定の文字が含まれる行のログだけ出せる
tail -f ./application.log | grep 'ERROR!'
```

---

## tar
* ファイルをまとめたり(アーカイブ)、展開したりします。
* アーカイブするときのオプションはzcvfとか
* 解凍するときのオプションはzxvfとか

<br>

#### 使用例

```bash
# アーカイブ使用例
$ tar zcvf /home/mainte/backup/0811_admin.tgz ./admin
```

```bash
# 上のアーカイブしたファイルを解凍する場合
$ tar zxvf /home/mainte/backup/0811_admin.tgz
```


---

## ssh
* サーバにSSHでログインします。
* ~.ssh/configでエイリアスを設定することで、接続がラクになります([参考](http://webkaru.net/linux/ssh-config-file/))

<br>

#### 基本形

ssh [ユーザ名]@[ホスト]

<br>

#### 使用例

```bash
ssh mainte@XXX.XXX.XXX.XXX
```

---

## history
* コマンドの実行履歴を表示します。
* historyコマンドの後に![番号]を入力すると、その番号のコマンドが実行されます。
* -d [番号]で対象番号のhistory履歴を消去できます。  
    (間違ってパスワード等を入力してしまった時など)
      
<br>

#### 基本形
history (オプション)

<br>

#### 使用例

```bash
$ history
   21  vagrant ssh
   22  exit
   23  cd Desktop/MAIN/
   24  ll
   25  cd share_test/
   26  ll
   27  cd myCentOSVM/
   28  vagrantup
   29  vagrant up
   30  vagrant ssh
```

---

## おまけ
reveal.jsとGithub Pagesで資料作成

---

## Github Pagesの用意
1. Githubアカウント作成  
  ・エイリアス(+XXXXX@gmail.com)を使えばメールアドレスを特別に用意しなくてもアカウント簡単に作れる。  
  ・アカウント作成後に、メールでアカウント認証しておかないとGithub Pages使えないようなので注意  

2. リポジトリ作成  
  ・ **[アカウント名].github.io**という名前でリポジトリを作成する。  
  ・カスタムドメインを使う方法もある?

3. Push
  ・適当にindex.htmlを用意し、作成したリポジトリに対してPush
  ・ブラウザで**[アカウント名].github.io**にアクセスするとPushしたindex.htmlが表示される。
  ・最初のPushの場合、ページが見えるようになるまで10分くらいかかるかも。  
  ・HTTPでPushがうまく行かない場合、リモートのアドレスにユーザ名を入れる  
    例： **url = https://account_namae@github.com/test/test.github.io.git**

---

## reveal.jsの準備
1. [Github](https://github.com/hakimel/reveal.js/)の"Download ZIP"をクリックしてソースを取得
2. 展開したフォルダでgit init。
2. ソースを展開してindex.htmlを開く。
3. 44行目付近の< div class="slides"\> の中のタグを全て消す。
4. 消した箇所に以下をコピペ。


```
            <section data-markdown="./md/revealjs.md"
                     data-separator="\n---\n$"
                     data-vertical="\n--\n">
                <script type="text/template">
                < /script>
            </section>
```

---

## 資料の準備(Markdown)
1. Markdownで記事を書く。(スライドとスライドの区切りには"---"を書く)  
2. index.htmlと同階層にmdディレクトリを用意し、中にrevealjs.mdというファイル名でMarkdownのファイルを入れる
3. git push origin master

---

## 使ってみて
* Markdownだけでスライドが作成できるのはよい
* ただし、reveal.jsの設定が面倒(CSSとか調整必要)
* 複雑なスライドは作れない
* サーバ必須?めんどくさい <div class="fragment roll-in">=>必須じゃなかった</p>

---

## ローカルだけでスライド作成するには

```
            <section data-markdown="./md/revealjs.md"
                     data-separator="\n---\n$"
                     data-vertical="\n--\n">
                <script type="text/template">
                < /script>
            </section>
```

※修正後  
Markdownファイルを外だししない  

```
            <section data-markdown=
                     data-separator="\n---\n$"
                     data-vertical="\n--\n">
                <script type="text/template">
                  # =>ここに直接Markdownを書く
                < /script>
            </section>
```


---

## 参考
* [Reveal.js、Markdown、Githubでスライドを作成する。](http://qiita.com/budougumi0617/items/19b19019bbe01f86e251)  
* [なんかかっこいいプレゼンテーションテンプレートを探しているならreveal.js使ってみろって](http://qiita.com/ryurock/items/9c6de36b9d6a716e7992)  
* [reveal.js+Markdown](http://qiita.com/siguremon/items/c717eca388070215712c)  
* [REVEAL.JSを使ってみた](http://tmlife-storage.googlecode.com/svn/trunk/reveal.js-guide/index.html#/)  
* [Reveal.jsとMarkdownでちょっとしたスライドを手軽に作る](http://n.blueblack.net/articles/2013-03-02_reveal_js_and_markdown_presentation/)
* [Git初心者でも大丈夫！完全無料でGithub PagesにWebページを公開する方法](http://liginc.co.jp/web/html-css/html/96453)


