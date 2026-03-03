Question1-Major：

克隆[课程网站仓库](https://github.com/missing-semester/missing-semester)。

Answer：
git clone https://github.com/missing-semester/missing-semester

Question1-1：

通过将其可视化为图表来探索版本历史记录

Answer：

git log --graph


Question1-2：

最后修改 `README.md` 的人是谁？（提示：给 `git log` 传入一个参数）

Answer：
git log -1 README.md

输出结果：

commit 77b301d916ea01c08378d5716667e20b3d390bc5 (HEAD -> master, origin/master, origin/HEAD)

Author: Anish Athalye <me@anishathalye.com>

Date:   Sun Mar 1 13:45:19 2026 -0800


Question1-3：

与上次修改相关的提交消息是什么`_config.yml` 的 `collections:` 行？ （提示：使用 `git blame` 和 `git显示`）。

Answer：

git blame _config.yml | Select-String "collections:"

a88b4eac (Anish Athalye 2020-01-17 15:26:30 -0500 19) collections:


Question2：

学习 Git 时常见的一个错误是提交大文件不由 Git 管理或添加敏感信息。尝试添加一个文件到一个存储库，进行一些提交，然后从 _history_ 中删除该文件
（不仅仅是最新的提交）。您可能想看看[此](https://help.github.com/articles/removing-

Answer：

现在最好是使用git filter-repo了，基本上是最现代的重写git历史的工具，具体应用问AI吧

Question3:

从 GitHub 克隆一些仓库，并修改其中一个已有文件。
   执行 `git stash` 会发生什么？运行 `git log --all --oneline` 会看到什么？
   再执行 `git stash pop` 撤销之前的 stash 操作。
   这在什么情况下有用？

Answer:

<img width="1020" height="278" alt="image" src="https://github.com/user-attachments/assets/009d12bc-3e3f-4446-8fb5-4dc2bc63ae83" />

stash可以将增改的代码先存在其他地方，不影响工作区

Question4:

与许多命令行工具一样，Git 提供了配置文件（或点文件）
   称为 `~/.gitconfig`。在 `~/.gitconfig` 中创建一个别名，以便当您
   运行 `git graph` ，你会得到 `git log --all --graph --decorate 的输出
   --oneline`。您可以直接执行此操作
   [编辑](https://git-scm.com/docs/git-config#Documentation/git-config.txt-alias)
   `~/.gitconfig` 文件，或者您可以使用 `git config` 命令添加
   别名。可以找到关于git别名的信息

Answer:

 git config --global alias.graph "log --all --graph --decorate --oneline"


Question5:

通过模拟协作场景练习解决合并冲突：
    1. 使用 `git init` 创建一个新存储库并创建一个名为
       `recipe.txt` 有几行（例如，一个简单的食谱）。
    2.提交，然后创建两个分支：`git branch salty`和`git分支
       甜甜`。
    3. 在 `salty` 分支中，修改一行（例如，将“1 cup Sugar”更改为“1
       杯盐”）并提交。
    4. 在 `sweet` 分支中，对同一行进行不同的修改（例如，更改“1
       一杯糖”改为“2 杯糖”）并提交。
    5. 现在切换到 `master` 并尝试 `git merge salty`，然后 `git merge
       sweet`. What happens? Look at the contents of `recipe.txt` - 做什么
       `<<<<<<<`、`=======` 和 `>>>>>>>` 标记的含义是什么？
    6.通过编辑文件来保留你想要的内容来解决冲突，
       删除冲突标记，并使用 `git add` 完成合并
       和 `git commit` （或 `git merge --continue`）。或者，尝试使用
       `git mergetool` 解决与图形或
       基于终端的合并工具。
    7. 使用 `git log --graph --oneline` 可视化刚刚的合并历史记录
       创建的。

Answer:

mkdir danremy

cd danremy

echo recipe.txt > "woshidan"

git add . && git commit -m "1st"

git branch anna && git branch doremy

git switch anna

echo "I love anna" >> recipe.txt; git add .\recipe.txt; if ($?) { git commit -m "anna chan" }

git switch doremy

echo "Doremy is my wife" >> recipe.txt; git add .\recipe.txt; if ($?) { git commit -m "doremy" }

git switch main

git merge anna

git merge doremy  #发现不对

















