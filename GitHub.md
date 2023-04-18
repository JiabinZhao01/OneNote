### 远程仓库（remote）

    目前我对于 git 所有操作都是在本地进行的。在开发中显然不能这样的，这时我们就需要一个远程的 git 仓库。远程的 git 仓库和本地的本质没有什么区别，不同点在于远程的仓库可以被多人同时访问使用，方便我们协同开发。在实际工作中，git 的服务器通常由公司搭建内部使用或是购买一些公共的私有 git 服务器。我们学习阶段，直接使用一些开放的公共 git 仓库。目前我们常用的库有两个：GitHub 和 Gitee（码云）

    将本地库上传 git：

    ```bash
    git remote add origin https://github.com/lilichao/git-demo.git
    # git remote add <remote name> <url>

    git branch -M main
    # 修改分支的名字的为main

    git push -u origin main
    # git push 将代码上传服务器上
    ```

    将本地库上传 gitee：

    ```bash
    git remote add gitee https://gitee.com/ymhold/vue-course.git
    git push -u gitee main
    ```

    ### 远程库的操作的命令

    ```bash
    git remote # 列出当前的关联的远程库
    git remote add <远程库名> <url> # 关联远程仓库
    git remote remove <远程库名>  # 删除远程库
    git push -u <远程库名> <分支名> # 向远程库推送代码，并和当前分支关联
    git push <远程库> <本地分支>:<远程分支>
    git clone <url> # 从远程库下载代码

    git push # 如果本地的版本低于远程库，push默认是推不上去
    git fetch # 要想推送成功，必须先确保本地库和远程库的版本一致，fetch它会从远程仓库下载所有代码，但是它不会将代码和当前分支自动合并
    		 # 使用fetch拉取代码后，必须要手动对代码进行合并
    git pull  # 从服务器上拉取代码并自动合并

    ```

    注意：推送代码之前，一定要先从远程库中拉取最新的代码

    ### tag 标签

-   当头指针没有执行某个分支的头部时，这种状态我们称为分离头指针（HEAD detached），分离头指针的状态下也可以操作操作代码，但是这些操作不会出现在任何的分支上，所以注意不要再分离头指针的状态下来操作仓库。

-   如果非得要回到后边的节点对代码进行操作，则可以选择创建分支后再操作

    ```bash
    git switch -c <分支名> <提交id>
    ```

-   可以为提交记录设置标签，设置标签以后，可以通过标签快速的识别出不同的开发节点：

    ```bash
    git tag
    git tag 版本
    git tag 版本 提交id
    git push 远程仓库 标签名
    git push 远程仓库 --tags
    git tag -d 标签名 # 删除标签
    git push 远程仓库 --delete 标签名 # 删除远程标签
    ```

    ### gitignore

-   默认情况下，git 会监视项目中所有内容，但是有些内容比如 node_modules 目录中的内容，我们不希望它被 git 所管理。我们可以在项目目录中添加一个`.gitignore`文件，来设置那些需要 git 忽略的文件。

### github 的静态页面

-   在 github 中，可以将自己的静态页面直接部署到 github 中，它会给我们提供一个地址使得我们的页面变成一个真正的网站，可以供用户访问。
-   要求：
    -   静态页面的分支必须叫做：gh-pages
    -   如果希望页面可以通过 xxx.github.io 访问，则需要将库的名字配置为 xxx.github.io

### docusaurus

-   facebook 推出的开源的静态的内容管理系统，通过它可以快速的部署一个静态网站

-   使用：

    -   网址：

        -   https://docusaurus.io/

    -   安装

        -   `npx create-docusaurus@latest my-website classic`

    -   启动项目

        -   `npm start`或`yarn start`

    -   构建项目

        -   `npm run build`或`yarn build`
        -

    -   配置项目：

        -   docusaurus.config.js 项目的配置文件

    -   添加页面：

        -   在 docusaurus 框架中，页面分成三种：1.page，2.blog，3.doc

    -   案例地址：

        -   https://github.com/lilichao/lilichao.github.io