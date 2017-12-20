# **PullRequestでconflictが発生していたら**

## GithubのWebツールで解消する
1. 「conflictあるよ」ってメッセージがあるところに`Resolve conflict`なるボタンがあるので押す
2. エディタが出るので該当部分を煮るなり焼くなり好きにする
3. 右上に`Mark as resolve`というボタンがあるので押す
4. その上に`commit merge`とかいうボタンが出るので押す
5. PullRequestを確認したら解消されているはず

## 自分でどうにかする(1.が使えない場合など)
1. `$ git fetch origin`
1. `$ git checkout -b (branch名) origin/(branch名)`
	- A brach named ~ が出るけど問題ない
3. `$ git merge develop`
4. メッセージが出るので、ここの`CONFLICT`がついたファイルを弄る
5. commitしてpush
6. PullRequestを確認したら解消されているはず
