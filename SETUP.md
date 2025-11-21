# 環境構築ガイド

## インストール済みの環境

以下の環境がセットアップ済みです：

- **PHP**: 8.4.15 (Homebrew経由でインストール)
- **Composer**: 2.9.2 (Homebrew経由でインストール)
- **Node.js**: v20.19.4
- **npm**: 10.8.2
- **OPcache拡張**: 有効

## 使用方法

### 基本的な使用方法

1. **Webサーバーで実行**
   - `index.php` をWebサーバーのドキュメントルートに配置
   - ブラウザで `http://localhost/opcache-gui/index.php` にアクセス

2. **PHPのビルトインサーバーで実行**
   ```bash
   php -S localhost:8000
   ```
   ブラウザで `http://localhost:8000/index.php` にアクセス

### 開発時のビルド

フロントエンドのコードを変更した場合は、ビルドプロセスを実行してください：

```bash
# 通常のビルド
php ./build/build.php

# またはComposerスクリプトを使用
composer build

# 特定の言語でビルド
composer build-french   # フランス語
composer build-german   # ドイツ語
composer build-spanish  # スペイン語
```

## 確認コマンド

環境が正しくセットアップされているか確認：

```bash
# PHPのバージョン確認
php --version

# OPcache拡張の確認
php -m | grep -i opcache

# Composerのバージョン確認
composer --version

# Node.jsとnpmのバージョン確認
node --version
npm --version
```

## 注意事項

- PHP 7.1以上が必要です（現在はPHP 8.4.15がインストールされています）
- OPcache拡張が有効になっている必要があります（現在有効です）
- Webサーバーで実行する場合は、OPcacheが有効になっている必要があります

## トラブルシューティング

### OPcacheが有効になっていない場合

`php.ini` ファイルを編集してOPcacheを有効にしてください：

```ini
[opcache]
opcache.enable=1
opcache.enable_cli=1
```

設定ファイルの場所：
- `/usr/local/etc/php/8.4/php.ini` (Homebrewでインストールした場合)

