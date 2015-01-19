###在工作目录中初始化新仓库
对某个项目用GIT管理，在此项目所在目录，执行

	$ git init
初始化后，在目录中会出现一个 `.git` 目录，Git需要的数据和资源存放在这个目录中。

###从现有仓库克隆
克隆仓库的命令格式为 `git clone [url]`。

	$ git clone git@github.com:laborclx/Git.git

自己定义新建的项目目录名称

	$ git clone git@github.com:laborclx/Git.git myGit