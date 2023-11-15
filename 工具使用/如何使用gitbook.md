# 如何使用Gitbook

最开始时，在工作目录下运行`gitbook init`，会自动生成`README.md`和`SUMMARY.md`。按照一定格式编辑`SUMMARY.md`，再运行`gitbook init`，就会按照目录的格式，生成对应的文件。
具体可以参考[gitbook入门指南](https://demones.github.io/gitbook-guide/index.html)


其逻辑相当奇怪。首先，它会根据你的`SUMMARY.md`文件对应生成文件夹和文件，同时也会根据你的现有文件夹生成目录，所以没事别瞎建没用的目录，会让显示效果非常难看。目前来看，文件夹名对应章节名，文件名就是对应的文章名，非常严格，运行`gitbook serve`之后显示的目录就是这样命名的。

## 如何将gitbook推送到github page上

在你的github上建立一个仓库，然后再gitbook的工作目录（即和`SUMMARY.md`同目录下）运行如下命令：
```bash
rm -rf _book
rm -rf gh_pages
gitbook build
mkdir gh_pages
cp -r _book/* gh_pages/
cd gh_pages
git init
git remote add origin git@github.com:you_github_id/repo.git
git checkout -b gh-pages
git add .
git commit -m 'Publish book'
git push -f --set-upstream origin gh-pages
rm -rf gh_pages
```

然后在分支的设置中打开page页面，将分支设定为提交的`gh-pages`上即可。