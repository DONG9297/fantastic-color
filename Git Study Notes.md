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
- 命令<code>git reset --hard commit_id</code>将HEAD指向其他版本。
  - <code>git log</code>查看提交历史。
  - <code>git reflog</code>查看命令历史。
- <code>git checkout -- &lt;file&gt;</code>可以用版本库里的版本替换工作区的版本
- 用命令<code>git reset HEAD &lt;file&gt;</code>可以把暂存区的修改撤销掉（unstage），重新放回工作区。
<br><code>git reset</code>命令既可以回退版本，也可以把暂存区的修改回退到工作区。</br>
## 远程仓库
- 要关联一个远程库，使用命令<code>git remote add origin git@server-name:path/repo-name.git</code>；
- 关联后，使用命令<code>git push -u origin master</code>第一次推送master分支的所有内容；
- 使用命令<code>git push origin master</code>推送最新修改；
- 要克隆一个仓库使用<code>git clone</code>命令。Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。
## 分支管理
#### 创建与合并分支
- Git鼓励大量使用分支：<br>
  - 查看分支：<code>git branch</code><br>
  - 创建分支：<code>git branch &lt;name&gt;</code><br>
  - 切换分支：<code>git checkout &lt;name&gt;</code><br>
  - 创建+切换分支：<code>git checkout -b &lt;name&gt;</code><br>
  - 合并某分支到当前分支：<code>git merge &lt;name&gt;</code><br>
  - 删除分支：<code>git branch -d &lt;name&gt;</code><br>
- 用<code>git log --graph</code>命令可以看到分支合并log。
#### 修复bug及feature分支
- 修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；
- 当手头工作没有完成时，先把工作现场<code>git stash</code>一下，然后去修复bug，修复后，再<code>git stash pop</code>，回到工作现场。
- 开发一个新feature，最好新建一个分支；
- 如果要丢弃一个没有被合并过的分支，可以通过<code>git branch -D &lt;name&gt;</code>强行删除。
#### 远程协作
- 查看远程库信息，使用<code>git remote -v</code>；
- 本地新建的分支如果不推送到远程，对其他人就是不可见的；
- 从本地推送分支，使用<code>git push origin branch-name</code>，如果推送失败，先用<code>git pull</code>抓取远程的新提交；
- 在本地创建和远程分支对应的分支，使用<code>git checkout -b branch-name origin/branch-name</code>，本地和远程分支的名称最好一致；
- 建立本地分支和远程分支的关联，使用<code>git branch --set-upstream branch-name origin/branch-name</code>；
- 从远程抓取分支，使用<code>git pull</code>，如果有冲突，要先处理冲突。
## 标签
- 命令<code>git tag &lt;name&gt;</code>用于新建一个标签，默认为HEAD，也可以指定一个commit id；
- <code>git tag -a &lt;tagname&gt; -m "blablabla..."</code>可以指定标签信息；
- <code>git tag -s &lt;tagname&gt; -m "blablabla..."</code>可以用PGP签名标签；
- 命令<code>git tag</code>可以查看所有标签。
- 命令<code>git push origin &lt;tagname&gt;</code>可以推送一个本地标签；
- 命令<code>git push origin --tags</code>可以推送全部未推送过的本地标签；
- 命令<code>git tag -d &lt;tagname&gt;</code>可以删除一个本地标签；
- 命令<code>git push origin :refs/tags/&lt;tagname&gt;</code>可以删除一个远程标签。
