###初次运行 Git 前的配置
Git有一个工具：`git config`，用来配置或读取相应的工作环境变量。

- `/etc/gitconfig` 文件：对所有用户都普遍使用的配置，使用 `git config` 时用 `--system` 选项，读写的就是这个文件。
- `~/.gitconfig` 文件：用户目录下的配置，使用 `git config` 用 `--global` 选项，读写的就是这个文件。
- 项目中的GIT目录中的配置文件，只对当前项目有效。

###用户信息
配置个人的用户名和email。每次GIT提交都会一起写入历史记录。

	$ git config --global user.name "lixin"
	$ git config --global user.email lixincsr@163.com
`--global` 选项，更改的配置文件是位于你用户主目录下的。

###文本编辑器
设置的是默认使用的文本编辑器。

	$ git config --global core.editor XXXX

###差异分析工具
解决合并冲突时使用哪种差异分析工具.

	$ git config --global merge.tool XXXX

###查看配置信息

	$ git config --list