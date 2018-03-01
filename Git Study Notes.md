## Git 简介
- 下载安装git，<code>git --version</code>检查是否成功安装
- 配置Git
  <pre><code>$ git config --global user.name "Your Name"
  $ git config --global user.email "email@example.com"</code></pre>
- 初始化一个Git仓库，使用<code>git init</code>命令。
- 添加文件到Git仓库，分两步：
  1. 使用命令<code>git add &lt;file&gt;</code>，注意，可反复多次使用，添加多个文件；
  2. 使用命令<code>git commit -m "description"</code>，完成。
- 修改更新提交
  - <code>git status</code>查看工作区的状态。
  - <code>git diff</code>查看修改内容。
  - 提交修改和提交新文件是一样的两步，先使用命令<code>git add  &lt;file&gt;</code>，再使用命令<code>git commit -m "description"</code>。
## 版本穿梭
- <code>git log</code>命令显示从最近到最远的提交日志，可以加上<code>--pretty=oneline</code>参数简单显示。
- 在Git中，用HEAD表示当前版本，上一个版本是HEAD^，往上n个版本写成HEAD~n。
- HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令<code>git reset --hard commit_id</code>。
  - 穿梭前，用<code>git log</code>可以查看提交历史，以便确定要回退到哪个版本。
  - 要重返未来，用<code>git reflog</code>查看命令历史，以便确定要回到未来的哪个版本。
- <code>git checkout -- &lt;file&gt;</code>可以用版本库里的版本替换工作区的版本
- 用命令<code>git reset HEAD &lt;file&gt;</code>可以把暂存区的修改撤销掉（unstage），重新放回工作区。
<br><code>git reset</code>命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用HEAD时，表示最新的版本。</br>
## 远程仓库
- 要关联一个远程库，使用命令<code>git remote add origin git@server-name:path/repo-name.git</code>；
- 关联后，使用命令<code>git push -u origin master</code>第一次推送master分支的所有内容；
- 此后，每次本地提交后，只要有必要，就可以使用命令<code>git push origin master</code>推送最新修改；
