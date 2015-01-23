###储藏你的工作
现在你想切换分支，但是你还不想提交你正在进行中的工作；所以你储藏这些变更。为了往堆栈推送一个新的储藏，只要运行 `git stash`。

	$ git stash
这时你的工作目录就干净了。
要查看现有的储藏，你可以使用 `git stash list`：

	$ git stash list
你可以重新应用你刚刚实施的储藏，所采用的命令就是之前在原始的 `stash` 命令的帮助输出里提示的：`git stash apply`。如果你想应用更早的储藏，你可以通过名字指定它，像这样：`git stash apply stash@{2}`。如果你不指明，Git 默认使用最近的储藏并尝试应用它：

	$ git stash apply
执行上面的命令，你会发现被暂存的文件没有重新被暂存。想要发现，必须运行 `git stash apply` 命令时带上一个 `--index` 的选项来告诉命令重新应用被暂存的变更。

apply 选项只尝试应用储藏的工作——储藏的内容仍然在栈上。要移除它，你可以运行 `git stash drop`，加上你希望移除的储藏的名字：

	$ git stash drop stash@{0}

你也可以运行 `git stash pop` 来重新应用储藏，同时立刻将其从堆栈中移走。
###取消储藏(Un-applying a Stash)
在某些情况下，你可能想应用储藏的修改，在进行了一些其他的修改后，又要取消之前所应用储藏的修改。可以通过取消该储藏的补丁达到同样的效果：

	$ git stash show -p stash@{0} | git apply -R
如果你没有指定具体的储藏，会选择最近的储藏。

	$ git stash show -p | git apply -R
###从储藏中创建分支

	$ git stash branch testchanges
