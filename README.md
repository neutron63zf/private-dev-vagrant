# private-dev-vagrant

# 概要

PCが壊れても必要なソフトウェアが存在していれば即座にバックアップメディアからデータを吸い出し、コードを実行できるようにすることを目的としたリポジトリです。

これは2022/03/15に個人用のPCが浸水により使用不能になり、退避した先であるPCで「コードは存在するものの、認証情報と実行環境が存在しない」という状態に陥ったことを教訓として作成されました。

# 想定

以下の状況を想定します

- インターネットにアクセスできる
- 2段階認証にアクセスできる
- 代替となるコンピュータが存在している
- 代替となるコンピュータは仮想マシンを走らせることができる程度のスペックを持つ
- 代替となるコンピュータには以下のものがインストールされている
  - Virtual Box
  - Vagrant
  - Ansible
  - Microsoft Remote Desktop Client
- バックアップが存在している

# 手順

## 仮想マシンのセットアップ

vagrant upにより立ち上げます。自動でansibleによるセットアップも走るはずです。

## アカウントの回復

まず必要なことは、アカウントのログインです。以下のものはこの順番にログインすることをおすすめします。

- Google Chrome
- Discord
- Notion
- Slack
- Zoom
- Wireguard

## バックアップの吸い出し

仮想マシン内に含まれるduplicityを用いてデータを吸い出しましょう。これにより認証情報の大部分が取得され、sshやgithubアクセス、aws cliの操作などの操作が行えるようになるはずです。

2022-03-31現在、linuxから読めるバックアップはMEGAと外付けHDDの両方に保管されています。MEGAから読み出しを行う場合、インターネット接続と.megarcが必要です。

## リポジトリの統合

先程の操作でgithubなどの操作ができるようになっていると考えられるため、githubからクローンしたものにバックアップからのリストアを上書きコピーし、状態を復活させます。必要に応じてリモートに情報をpushします。

# 仮想マシンに含まれるツール

## コマンドライン類

### aptで入るもの

- git
- zsh
- megatools
- duplicity
- openjdk-16-jdk
- xrdp
- jq

### gitリポジトリクローン+αで入るもの

- zsh-completions
- zsh-autosuggestions
- nodenv
- pyenv

### シェルスクリプトが必要なもの

- starship
- yarn
- rustup
- pipenv
- aws cli
- eb cli
- docker
- jc

### 未確認

現在なし

## GUI類

- Google Chrome
  - Todoist
  - Toggl Track
  - Pomofocus
- Discord
- Zoom
- Slack
- Notion
- VSCode
- Minecraft
- Virtualbox
- Wireguard
- Gitkraken
- 1password
- Tweetdeck
- Steam
- Postman

# 仮想マシンのセッティング

- デフォルトシェルのzshへの変更

# 仮想マシンに含まれていないが、検討が必要なもの

- 日本語入力ユーティリティー
- 画面分割ユーティリティー
- データベース操作GUIクライアント