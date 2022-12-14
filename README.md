# Linux学習リポジトリ

## Linux環境を構築する

### 1. ローカルPCに当リポジトリをcloneする

ご自信のPCに当リポジトリをcloneしてください

### 2. Ubuntuコンテナを起動する

cloneしたディレクトリ内に移動し、下記コマンドを実行してください
```
$ make up
```
こちらを実行すると、Ubuntuで作成されたLinux環境のコンテナが作成/起動されます

### 3. Ubuntu内にログインする

コンテナが起動していることを確認し、以下コマンドを実装してください
```
make login
```
こちらを実行すると起動しているUbuntuコンテナにログインしできます。  
コマンドラインのプロンプト(戦闘の部分)が `student@152b43d7ec64:~$` のように表示されていれば、ログインは成功です。  
この状態になっている時は作成したLinux環境内にいることを示しています。

## 注意事項

### 環境について
当リポジトリで使用している Linux ディストリビューションは `Ubuntu:22.04` となります。  
そのため、CentOS や RHL をはじめとした、別の Linux ディルトリビューションで採用されている一部の技術やコマンドはご利用できません。  
また、当リポジトリで作成される Linux 環境は Docker を使用して構築されています。  
Dockerは仕組み上、動作軽量化のために最小限の機能のみがインストールされるようになっています。  
そのため、検索でヒットした Linux に関するコマンドや作業手順、Tipsなどを試す際に、うまく動作しない場合などがございます。 

### 作業をするディレクトリについて  
Linux環境にログインした際は、Linux環境内のホームディレクトリという場所からスタートします。  
Linux内で作業を行う際はなるべくこちらのディレクトリ内で行うようにしてください。

### Makeコマンドについて
Makeコマンドは複雑なDockerのコマンドを簡略化するために用意しているものになります。  
`Makefile` という特殊なファイルで定義しているため、こちらが配置されているディレクトリ内でしか使用できません。  
cloneしたディレクトリに移動してから実行をしてください。

#### 用意しているコマンド一覧
- `make up`  
  Linux環境のコンテナを起動するコマンドになります。  
  コンテナが未作成の場合は自動で作成をしてから起動します。
- `make login`  
  Linux環境のコンテナにログインし、Linux環境に切り替えます。
  コンテナが起動していない状態だとログインに失敗してエラーになります。
- `make stop`  
  コンテナを停止させるコマンドになります。削除はされません。
- `make rebuild`  
  Dockerの設定などを更新してコンテナを再起動します。  
  Dockerfileに何かしらの修正が発生した場合に使用します。
- `make down`  
  コンテナを削除するコマンドになります。  
  Linux環境内のホームディレクトリの状態は別で保存されているので、  
  再度コンテナを作成すると元の状態を復元できます (ホームディレクトリのみ)。
- `make destroy`  
  保存状態なども含めて完全にコンテナを削除します。
  こちらを実行した場合、再度コンテナを作成しても前の状態は復元されません。
- `make refresh`  
  destroyと同様に完全にコンテナを削除した後に、新たなコンテナを作成し直します。
  完全に初期化して最初の状態に戻したい場合に使用します。