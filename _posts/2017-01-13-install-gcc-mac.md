---
layout: default
title: Macにgccをインストールする
date: 2017/01/13 16:00
---

Xcode付属のgccはclangベースなので、ちゃんとしたgccを入れる。

### 環境等
+ macOS Sierra 10.12.2
+ 元から入ってるgcc：6.1.0
+ 新しいgcc：6.3.0

### SIPオフ

セキュリティ上使えないコマンドがあるので、システムのSIPを切る。
`Command + R`を押しながら再起動
そして、ターミナル画面を出し、
```
csrutil disable
```
を入力し、再起動
これでSIPは切れた。

### インストール
Homebrewが入ってることが前提
とりあえず、gccの最新版を入れる。

```
brew install gcc
```

gmp, libmpc, islとかのインストール時に何かエラー出るかも。

既存のgccをリネームしてバックアップ

```
sudo mv /usr/bin/gcc /usr/bin/gcc_default
```

localの方もやっておく

```
sudo mv /usr/local/bin/gcc /usr/local/bin/gcc_default
```

Homebrew版gccのリンクを張る。

```
sudo ln -s /usr/local/Cellar/gcc/6.3.0_1/bin/gcc-6 /usr/bin/gcc
```

```
sudo ln -s /usr/local/Cellar/gcc/6.3.0_1/bin/gcc-6 /usr/local/bin/gcc
```

g++も同様にやる。
バックアップ

```
sudo mv /usr/bin/g++ /usr/bin/g++_default
```

```
sudo mv /usr/local/bin/g++ /usr/local/bin/g++_default
```

リンク貼り
```
sudo ln -s /usr/local/Cellar/gcc/6.3.0_1/bin/g++-6 /usr/bin/g++
```

```
sudo ln -s /usr/local/Cellar/gcc/6.3.0_1/bin/g++-6 /usr/local/bin/g++
```