###Git分支创建
	$ git branch <branchname> //<branchname>分支名
Git保存这一个名为HEAD的特别指针，它是一个指向你正在工作中的本地分支的指针。

创建的一个新的分支，但是不会切换到这个新分支中。
###切换到其他分支
	$ git checkout <branchname>
这时，HEAD就指向了 `<branchname>` 分支。

再次修改提交后，当前新建的分支会向前移动，但 master 分支仍然指向原来的 commit 对象。

现在切换到 master 分支，查看刚修改的文件，你会发现在这个分支里面的文件没有修改。

在 master 分支中在做修改，提交。这时就产生了两条线，这些修改是在不同的分支里，在不同的分支里进行切换，在合适的时候可以进行合并。
