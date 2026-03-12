question1：

Save your environment with printenv to a file, create a venv, activate it, printenv to another file and diff before.txt after.txt. What changed in the environment? Why does the shell prefer the venv? (Hint: look at $PATH before and after activation.) Run which deactivate and reason about what the deactivate bash function is doing.

Answer：
printenv > before.txt

python3 -m venv .venv #创建虚拟环境

source .venv/bin/activate #激活虚拟环境

printenv > after.txt

diff before.txt after.txt #没有diff请教ai老师怎么安装，arch可以 pacman -S diffutils

激活虚拟环境后，环境变量发生了变化。最明显的是新增了 VIRTUAL_ENV，它指向当前虚拟环境的目录。另外，PATH 也被修改了，.venv/bin 被放到了 PATH 的最前面。

shell 之所以会 prefer the venv，是因为 shell 查找命令时会按照 PATH 从左到右依次搜索。激活虚拟环境后，.venv/bin 在最前面，所以输入 python 或 pip 时，shell 会先找到虚拟环境里的可执行文件，而不是系统里的版本。

deactivate是一个 bash function。可以用 type deactivate 和 which deactivate查看。它的作用是撤销 activate 对当前 shell 环境做的修改，比如恢复原来的 PATH，删除 VIRTUAL_ENV，恢复原来的提示符，并清理临时变量，从而退出虚拟环境。

question2：

Create a Python package with a pyproject.toml and install it in a virtual environment. Create a lockfile and inspect it.

Answer：

mkdir mypkg-demo

cd mypkg-demo

python3 -m venv .venv

source .venv/bin/activate

mkdir -p src/mypkg 

printf 'def hello():\n    return "hello from mypkg"\n' > src/mypkg/__init__.py

cat > pyproject.toml #会看到这样的东西，它是包的构建和元信息配置

pip install -e .   #关键命令，安装这个包到虚拟环境

python -c "import mypkg; print(mypkg.hello())"

pip freeze > requirements.lock #锁定当前环境

cat requirements.lock

注意：为什么要有lockfile，因为pyproject.toml只是声明依赖(范围)，而pip会解析完整依赖树，lockfile则锁定所有版本


question3：
Install Docker and use it to build the Missing Semester class website locally using docker compose.

Answer：
<img width="2545" height="1438" alt="image" src="https://github.com/user-attachments/assets/b85fc29f-4570-4011-9f0e-4a4e40c41c67" />


question4：
Write a Dockerfile for a simple Python application. Then write a docker-compose.yml that runs your application alongside a Redis cache.



Answer：






question5：
Publish a Python package to TestPyPI (don’t publish to the real PyPI unless it’s worth sharing!). Then build a Docker image with said package and push it to ghcr.io.



Answer：




question6：
Make a website using GitHub Pages. Extra (non-)credit: configure it with a custom domain.


Answer：
