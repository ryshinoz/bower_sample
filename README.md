# Bower

基本的なことについて

## About

- Twitterが開発したWeb用のパッケージマネージャー
- nodeでできてるよ
- バウアーとよぶらしい

## Install Bower

bower自身はnpmでインストールします

```bash
$ npm install -g bower
```

## Install

### バージョンを指定しないでインストール

最新版がインストールされます

```bash
$ bower install jquery
bower jquery#*              not-cached git://github.com/components/jquery.git#*
bower jquery#*                 resolve git://github.com/components/jquery.git#*
bower jquery#*                download http://github.com/components/jquery/archive/2.0.3.tar.gz
bower jquery#*                 extract archive.tar.gz
bower jquery#*                resolved git://github.com/components/jquery.git#2.0.3
bower jquery#~2.0.3            install jquery#2.0.3

jquery#2.0.3 bower_components/jquery
```

`bower_components`ディレクトリ配下にインストールされる ※設定で変更できる

```bash
$ tree bower_components/
bower_components/
└── jquery
    ├── README.md
    ├── bower.json
    ├── component.json
    ├── composer.json
    ├── jquery-migrate.js
    ├── jquery-migrate.min.js
    ├── jquery.js
    ├── jquery.min.js
    └── package.json
```

### バージョンを指定してインストール

```bash
$ bower install jquery#2.0.2
bower jquery#2.0.2          not-cached git://github.com/components/jquery.git#2.0.2
bower jquery#2.0.2             resolve git://github.com/components/jquery.git#2.0.2
bower jquery#2.0.2            download http://github.com/components/jquery/archive/2.0.2.tar.gz
bower jquery#2.0.2             extract archive.tar.gz
bower jquery#2.0.2            resolved git://github.com/components/jquery.git#2.0.2
bower jquery#2.0.2             install jquery#2.0.2

jquery#2.0.2 bower_components/jquery
```

### 既にインストール済みのパッケージのバージョンと違うバージョンをインストール

バージョンを選択 ※複数バージョンのインストールはできない

```bash
nable to find a suitable version for jquery, please choose one:
    1) jquery#2.0.2 which resolved to 2.0.2 and has bower_sample as dependants
    2) jquery#2.0.3 which resolved to 2.0.3

Prefix the choice with ! to persist it to bower.json

Choice: 2
bower jquery#2.0.3             install jquery#2.0.3

jquery#2.0.3 bower_components/jquery
```

## Uninstall

複数バージョンはインストールできないのでバージョン指定はいらない

```bash
$ bower uninstal jquery
bower uninstall     jquery
```

## Info

パッケージのバージョンリストを表示する

```bash
$ bower info jquery-mobile
jquery-mobile

  Versions:
    - 1.4.0-alpha.1
    - 1.3.2
    - 1.3.1
    - 1.3.0
    - 1.3.0-rc.1
    - 1.3.0-beta.1
    - 1.2.1
    - 1.2.0
    - 1.2.0-rc.2
    - 1.2.0-rc.1
    - 1.2.0-pre
    - 1.2.0-beta.1
    - 1.2.0-alpha.1
    - 1.1.2
    - 1.1.1
    - 1.1.1-rc.1
    - 1.1.0
    - 1.1.0-rc.2
    - 1.1.0-rc.1
    - 1.0.1
```

## Search

パッケージを検索する

```bash
$ bower search jquery-mobile
Search results:

    jquery-mobile git://github.com/jquery/jquery-mobile.git
    jquery-mobile-angular-adapter git://github.com/tigbro/jquery-mobile-angular-adapter.git
    jquery-mobile-events git://github.com/caseywebdev/jquery-mobile-events
    jquery-mobile-bower git://github.com/jobrapido/jquery-mobile-bower.git
    jquery-mobile-reset git://github.com/bhurlow/jqmobile-reset.git
    jquery-mobile-min git://github.com/dimsk/jquery-mobile
```

## Cache

1回インストール（ダウンロード）したパッケージはキャッシュされ次回以降のインストールにはキャッシュが利用される

キャッシュは`$#HOME/.cache/bower`配下に設置される

### キャッシュされたパッケージを確認する

```bash
$ bower cache list
jquery=git://github.com/components/jquery.git#2.0.2
jquery=git://github.com/components/jquery.git#2.0.3
```

### キャッシュを削除する

```bash
$ bower cache clean
bower deleted       Cached package jquery: /Users/ryshinoz/.cache/bower/packages/29cb4373d29144ca260ac7c3997f4381/2.0.3
bower deleted       Cached package jquery: /Users/ryshinoz/.cache/bower/packages/29cb4373d29144ca260ac7c3997f4381/2.0.2
```

## Configuration

`$HOME/.bowerrc`を作成する事でbowerに関する設定ができる

JSONフォーマットで記述

### directory

デフォルトでインストーされるディレクトリ

```json
{
    "directory": "javascripts"
}
```

インストールするとデフォルトの`bower_components`ではなく`javascripts`にインストールされる

```bash
$ tree javascripts/
javascripts/
└── jquery
    ├── README.md
    ├── bower.json
    ├── component.json
    ├── composer.json
    ├── jquery-migrate.js
    ├── jquery-migrate.min.js
    ├── jquery.js
    ├── jquery.min.js
    ├── jquery.min.map
    └── package.json
```

## bower.json

```bash
$ bower init
[?] name: Sample
[?] version: 0.0.1
[?] main file: index.js
[?] set currently installed components as dependencies? Yes
[?] add commonly ignored files to ignore list? Yes
```

- `name` - パッケージ名
- `version` - パッケージバージョン
- `main file` - エンドポイント
- `set currently installed components as dependencies?` - 既にインストール済みのパッケージを依存関係に含めるか？
- `add commonly ignored files to ignore list?` - 共通のignore設定を加えるか？

### インストール

bower.jsonが存在するとそれに従ってパッケージをインストールします

```bash
$ bower install
bower jquery#~2.0.3             cached git://github.com/components/jquery.git#2.0.3
bower jquery#~2.0.3           validate 2.0.3 against git://github.com/components/jquery.git#~2.0.3
bower jquery-mobile#~1.4.0-alpha.1           cached git://github.com/jquery/jquery-mobile.git#1.4.0-alpha.1
bower jquery-mobile#~1.4.0-alpha.1         validate 1.4.0-alpha.1 against git://github.com/jquery/jquery-mobile.git#~1.4.0-alpha.1
bower jquery#~2.0.3                         install jquery#2.0.3
bower jquery-mobile#~1.4.0-alpha.1          install jquery-mobile#1.4.0-alpha.1

jquery#2.0.3 javascripts/jquery

jquery-mobile#1.4.0-alpha.1 javascripts/jquery-mobile
```

### インストール時に設定を追記する

--saveオプションをつける

```bash
$ bower install jquery-mobile --save
```

アンインストールも一緒

```bash
$ bower uninstall jquery-mobile --save
```

## Links

- [bower](http://bower.io/)
