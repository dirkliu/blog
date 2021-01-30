## Contributions未被Github计入的几个常见原因

* 进行Commits的用户没有被关联到你的Github帐号中。
* 不是在这个版本库的默认分支进行的Commit。
* 这个仓库是一个Fork仓库，而不是独立仓库。

## 如何排查
你可以在你的本地repo里用`git log`命令查看commit记录上的个人邮箱是否正确，像我就是因为之前切换到Mac平台开发之后用户名没有配置，
所以我之后的commit记录上的邮箱一直是Leo@Leo-MacBook-Pro.local，所以Github就会认为这些commits都不是你提交的！

## 补救措施
然而这也并不是没有补救办法的，Github官网上就有给出详细的补救过程，英语好的同学请自行移步[Changing author info](https://help.github.com/articles/changing-author-info/) ，
下面是我翻译自Github Help的简要步骤：
 * 1.进入你的github repo项目目录;
 * 2.复制粘贴如下脚本，并根据你的信息修改以下变量：旧的Email地址，正确的用户名，正确的邮件地址;
 ``` 
git filter-branch --env-filter '
OLD_EMAIL="旧的Email地址"
CORRECT_NAME="正确的用户名"
CORRECT_EMAIL="正确的邮件地址"
if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
 ```
  * 3.在命令行中运行
  * 4.用`git log `命令看看新 Git 历史有没有错误
  * 5.把正确历史 push 到 Github
  ``` 
  git push --force --tags origin 'refs/heads/*'
  ```
  
  ## 如何正确设置你的 git 个人信息
  * 全局设置：所有git repo公用的个人信息
  ``` 
  git config --global user.email "你的邮件地址"
  git config --global user.name "你的Github用户名"
  ```
  * 本地设置：当前git repo使用的个人信息
  ``` 
  git config --local user.email "你的邮件地址"
  git config --local user.name "你的Github用户名"
  ```
  有时候，需要使用多个git源，比如，使用github和自己搭建的gitlab，这个时候，如果使用全局配置的是gitlab的个人信息，且与github上的个人信息不一样，
  这时，如果你push github的commits，github是不会计入的。所以你必须在你的github中配置local个人信息。
 
