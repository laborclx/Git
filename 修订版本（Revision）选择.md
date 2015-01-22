###简短的SHA
	$ git log
可以通过 `git show` 查看每次提交的内容

	$ git show 1c002dd4b536e7479fe34593e72e6c6c1819e53b
	$ git show 1c002dd4b536e7479f
	$ git show 1c002d
Git 可以为你的 SHA-1 值生成出简短且唯一的缩写。如果你传递 `--abbrev-commit` 给 `git log` 命令，输出结果里就会使用简短且唯一的值；

	$ git log --abbrev-commit --pretty=oneline
###分支引用
如果你想知道某个分支指向哪个特定的 SHA。你可以使用一个叫做 `rev-parse` 的 Git 探测工具。

	$ git rev-parse topic1
	ca82a6dff817ec66f44342007202690a93763949
###引用日志里的简称
一份记录最近几个月你的 HEAD 和分支引用的日志。你可以使用 `git reflog` 来查看引用日志：

	$ git reflog
	39f5d3a HEAD@{0}: commit: 创建和克隆仓库、产看历史记录
	939d0ed HEAD@{1}: commit: GIT 运行前的配置
	4c5b7ba HEAD@{2}: checkout: moving from Git第一天 to master
	8ad4fbc HEAD@{3}: checkout: moving from master to Git第一天
	4c5b7ba HEAD@{4}: rebase finished: returning to refs/heads/master
	4c5b7ba HEAD@{5}: pull --progress --rebase --prune origin master: checkout 4c5b7
如果你想查看仓库中 HEAD 在五次前的值，你可以使用引用日志的输出中的 `@{n}` 引用：

	$ git show HEAD@{3}
也可以使用这个语法来查看某个分支在一定时间前的位置。

	$ git show master@{yesterday}
想要看类似于 `git log` 输出格式的引用日志信息，你可以运行 `git log -g`：

	$ git log -g master
###祖先引用
另一种指明某次提交的常用方法是通过它的祖先。如果你在引用最后加上一个 ^，Git 将其理解为此次提交的父提交。

	$ git log --pretty=format:'%h %s' --graph
想看上一次提交

	$ git show HEAD^
你也可以在 ^ 后添加一个数字——例如，d921970^2 意思是“d921970 的第二父提交”。这种语法只在合并提交时有用，因为合并提交可能有多个父提交。第一父提交是你合并时所在分支，而第二父提交是你所合并的分支：

	$ git show d921970^
	$ git show d921970^2
另外一个指明祖先提交的方法是 ~。这也是指向第一父提交，所以 `HEAD~` 和 `HEAD^` 是等价的。

	$ git show HEAD~3
###提交范围
你想要知道你的那个分支没有提交到主分支，你可以用 `master..experiment` 来让GIT显示这些提交的日志。“所有可从experiment分支中获得而不能从master分支中获得的提交”。

	$ git log master..experiment
与上面相反

	$ git log experiment..master
下面这条命令显示任何在你当前分支上而不在远程origin 上的提交。

	$ git log origin/master..HEAD
Git允许你在引用前使用^字符或者--not指明你不希望提交被包含其中的分支。因此下面三个命令是等同的：

	$ git log refA..refB
	$ git log ^refA refB
	$ git log refB --not refA
这个可以指定被两个引用中的一个包含但又不被两者同时包含的分支

	$ git log master...experiment

这种情形下，log命令的一个常用参数是--left-right，它会显示每个提交到底处于哪一侧的分支。这使得数据更加有用。

	$ git log --left-right master...experiment
