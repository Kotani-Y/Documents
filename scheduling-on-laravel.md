# Laravelフレームワークにおけるバッチ処理の作成

## バッチって何よ
コマンドを実行したときに一連の処理を実行してくれるという処理

## 作る
1. `$ php artisan make:command (filename)`のartisanコマンドを叩く

2. app\Console\Commansに(filename)のクラスファイルが作成される

3. クラスの`$signature`と`$description`を書き換える
	- `$signature`は実行するときのコマンド
		- 引数がある場合は`protected $signature = 'example:example {argument1} {argument2}';`
			- `{argumentX?}`のように末尾に`?`を付けることで任意引数に設定可能
			- `{argumentX=example}`で任意指定の場合のデフォルトを設定可能
		- `{--option-example}`で実行時のオプションを設定可能
			- `{--options-argument-example=}`のように記述すればオプションの引数を設定可能
	- `$description`は`$ php artisan list`で表示されるときの説明文
		- マルチバイト文字だとなんか表示がおかしくなる？
		- `protected $description = 'Just descriptioon {argument1 : an argument1.} {argument2 : an argument2.}'`のように引数説明を設定可能
	- 引数取得
		- `$this->argument('argiment1');`

4. 2.のクラスをapp\Console\Kernel.phpの`$commands`配列に追加する

   ```
   protected $commands = [
	   Commands\ExampleCommand::class
   ];
   ```

5. コマンドラインで確認する
	- `$ php artisan list`
	- commandの下に3.で記述した$signature,$descriptionが表示されていればOK

6. 実行する内容はクラスのhandle()に記述。

7. App/Console/Kernel.phpのschedule()へジョブ追加
   + appendOutputTo($path);追加してもいいかもしらん

8. `crontab -e` でcronエントリ追加
9. `* * * * * php /prohjet_path/artisan schedule:run >> /dev/null 2>&1` を記述
