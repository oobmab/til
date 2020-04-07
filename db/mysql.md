# mysqlメモ

---
#### 本番環境などで、必要なデータを取得したいけど件数が多いときに実行するクエリ

```
# mysqldump -h [DBホスト名] -u [DBユーザー名] -p -t [DB名] [テーブル名] --where="true limit [出力したい件数]" > [出力ファイル名]
mysqldump -h host -u user --where="true limit 3000" --single-transaction | gzip > db.date +%Y%m%d.dmp.gz
```
---

#### 暗号化できているかの確認
`show status like'Ssl_cipher';`
非暗号化だと何も表示されない。

```
mysql > show status like'Ssl_cipher';
+---------------+--------------------+
| Variable_name | Value              |
+---------------+--------------------+
| Ssl_cipher    | DHE-RSA-AES256-SHA |
+---------------+--------------------+
1 row in set (0.01 sec)
```

---

#### .my.cnf
mysql 出力はteeオプション。出力を停止するときは、noteeオプション。
```
[client]
host=hostname
user=username
password=password
default-character-set=utf8

[mysqld]
character-set-server=utf8

[mysqldump]
default-character-set = utf8

[mysql]
default-character-set = utf8
prompt='\\U [\\d] \\R:\\m >\\_'
tee=~/mysql/user_console.log
```
---
#### xmlで検索結果を取得
```
mysql db -e 'select * from db.table;' --xml
```
---

#### shell コマンド実行
```
mysql > \! ls -la
```
---

#### ファイルからクエリ実行
```
mysql > source work/test.txt
```
---

#### 実行中のSQL確認
sqlが長いときは途中で途切れるので、fullをつける。
```
show full processlist;
```
---

#### create文出力
dumpとるまでもないとき
```
show create database db\G
show create table table_name\G
```
---

#### より詳細にテーブル定義確認
```
show full columns from table_name;
```
---

#### ポートフォワーディングして別サーバのmysql接続
```
ssh -f -N -L 60500:db_hostname:3306 -i ~/.ssh/id_rsa username@remote_hostname
mysql -h 127.0.0.1 -P 60500
```
使い終わったらプロセスはkillしておく。
```
ps auxf | grep ssh
kill XXX
```
---

#### blob型からデータを取り出して中身確認するときのコマンド
- N: カラム名を出力しない  
- s: セパレータをタブに置換して出力
```
mysql -Ns -e 'select hex(column_name) from table_name;' | fold -w60 | xxd -r -ps -c 30 > file_name.zip
zcat file_name.zip | head -n 10
```
---
