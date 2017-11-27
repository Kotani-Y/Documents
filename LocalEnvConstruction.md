# Docker導入からLaravelプロジェクト作成まで

## **前提**
+ Windows7使用

---
## **Intel(R) VirtualizationTechnology有効化**
### デフォルトでDisabledになっているIntel(R) VirtualizationTechnologyの有効化
1. 起動時にBIOSを立ち上げる(電源押したらF2連打)
2. Advancedのタブへ移動
3. CPU Configurationを選択(一番上)
4. Intel(R) VirtualizationTechnologyをEnabledへ変更(テンキーの+)
5. F10でセーブし、Windows起動
---

## **<font color="Red">※VirtualBoxとDocker Toolboxは別にインストールした方がよい※</font>**

## **Oracle VM VirtualBox・Docker Toolboxのインストール**
### Oracle VM VirtualBoxインストール
1. Oracle VM VirtualBox を以下リンクからダウンロード
[**Oracle VM VirtualBox**](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html?ssSourceSiteId=otnjp) <-リンク
2. インストール

### Docker Toolboxインストール
1. Docker Toolboxを以下リンクからダウンロード
[**Docker Toolbox**](https://www.docker.com/products/docker-toolbox) <-リンク
2. KitematicとDocker Quickstart Terminalをインストール
**※VirtualBoxのチェックは外す**

### 仮想マシン作成
1. Kitematicを開く
2. `USE VIRTUALBOX`を選択
3. Defaultという仮想マシンが作成される
4. 仮想マシン作成完了を待つ
5. Docker Hubへのログインを聞かれるが必要なければ`SKIP FOR NOW`
---
## **環境作成**
1. Docker Quickstart Terminalを起動

2. 自身のホームディレクトリへ移動
``$ cd ~``

3. {project_name}ディレクトリ作成
``$ mkdir {project_name}``

4. {project_name}ディレクトリに{laravel_project}をclone
``$ cd {project_name}``
``$ git clone https://github.com/{foobar}/{laravel_project}.git``

5. {laravel_project}ディレクトリへ移動
``$ cd {laravel_project}``

6. コンテナを立てる
``$ docker-compose up -d``

7. コンテナのログで"done!"が出るまで待つ
``$ docker logs -f --tail=10 {project_name}_workspace_1``

8. 192.168.99.100へアクセス
