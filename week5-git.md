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




























sensitive-data-from-a-repository/)。
