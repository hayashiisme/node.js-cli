# node.jsによるコマンドラインツール 導入

node.jsのスクリプトをコマンドラインツールとして動作させる手順。

linux(OS Xも？)だと[envコマンド](https://linuxjm.osdn.jp/html/gnumaniak/man1/env.1.html)というのがあって、shellを介してこれと連携すれば簡単にできる。

スクリプトの先頭に、

```
#!/usr/bin/env node
```

と書いてスクリプトに実行権限を付与するだけ。

(スクリプト hello_cls.js)
```
#!/usr/bin/env node
/*
node.jsのスクリプトをコマンドラインツールとして動作させる
 */
'use strinct';
console.log("Hello, CLI.");
```

ならば、スクリプトがあるディレクトリで、

(実行)
```
 $ ./hello_cli.js
 Hello, CLI.
 $
```

しかしこれだとPathが通っていなければそのディレクトリでしか実行できない。
スクリプトは実行単位(といえばいいのか)ごとにディレクトリ切ることが多いはずだからPathを通すのは現実的でない。

で、どうするかというと、npmでglobalインストールする。

インストールの設定のためにpackage.jsonファイルを作成する。

(package.json)
```
{
		"name": "hello_cli",
		"version": "0.0.1",
		"description": "First node.js script for CLI.",
		"author": "Lin Quan Studio.",
		"engines": {"node": ">=0.10"},
		"dependencies": {},
		"bin": {"hello_cli": "hello_cli.js"}
}
```

`"bin"`にインストールするコマンド名とスクリプトのペアを指定する。

書いたらそのディレクトリで、

```
 $ sudo npm install -g

```

でインストールすればコマンドとして実行できるようになる。

DOS(Windows)のコマンドプロンプトでは、envコマンドがなければスクリプトを直接実行はできないが、グローバルインストールすれば実行できるようになるので便利。








