# laravelメモ
---

#### homestead
```
vagrant box add laravel/homestead
git clone https://github.com/laravel/homestead.git ~/Homestead
cd ~/Homestead
git checkout release
bash init.sh
provider: virtualbox
vagrant up
cd prj/
composer install --no-plugins
```
---

#### redis
```
sudo apt update
sudo apt install redis
redis-cli --version
sudo systemctl status redis
sudo systemctl enable redis-server
```
#### 登録済みデータを削除したいとき
```
redis-cli keys "*"
redis-cli flushdb
redis-cli keys "*"
```
---

#### dbuser作成
```
CREATE USER 'developer'@'localhost' IDENTIFIED BY 'developer';
SELECT user, host FROM mysql.user;
GRANT ALL ON test.* TO 'developer'@'localhost';
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'developer'@'localhost';
```
---

#### バッチ作成
```
php artisan make:command {バッチ名}
```
---

#### モデル作成
```
php artisan make:model Model/{モデル名}
```
---

#### mail 送信テスト
`.env` の設定を変更 `MAIL_DRIVER=log`
ログに出力されているので、そこから確認

#### sendmailの設定
`.env` の設定を変更 `MAIL_DRIVER=sendmail`, `MAIL_HOST=localhost`
```
# =======================
# メール送信(ローカル)
# =======================
MAIL_DRIVER=sendmail
MAIL_HOST=localhost
MAIL_PORT=
MAIL_USERNAME=
MAIL_PASSWORD=
MAIL_ENCRYPTION=
```

`/var/log/maillog`でメールの送信状況を確認  
`Mailhog`がインストールされていれば、 http://localhost:8025/ からでも確認可能  

#### Mailableクラス
```
php artisan make:mail SendErrorMail
```

#### メール送信テスト
結果がnull ならOK
```
php artisan tinker
Mail::raw('[test]', function($message) { $message->to('xxx@xxx')->subject('test'); });
```
---

#### 発行クエリを確認したいとき
#### laravel sql確認方法１
```
Log::debug($query->toSql(), $query->getBindings());
```
#### laravel sql確認方法２
こっちのが楽
```
DB::enableQueryLog();
Log::debug(DB::getQueryLog());
```
---

#### キャッシュクリアコマンド
`.env`編集後、設定を反映させるためにキャッシュは消す
```
composer dump-autoload
php artisan clear-compiled
php artisan optimize
php artisan config:cache
```
---

#### トランザクション処理
ロールバック、コミットの扱いに注意！
```
vagrant@homestead:~/prj/test/ $ grep -r createSavepoint vendor/
vendor/laravel/framework/src/Illuminate/Database/Concerns/ManagesTransactions.php:            $this->createSavepoint();
vendor/laravel/framework/src/Illuminate/Database/Concerns/ManagesTransactions.php:    protected function createSavepoint()
```
---

#### カスタムバリデーション
```
php artisan make:rule uniqueDate
```
---

#### コマンド実行時の注意点
--envオプションで実行環境を指定
```
php artisan command:{バッチ名} --env=production
```
---

