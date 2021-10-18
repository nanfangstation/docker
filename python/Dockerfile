# 向 Dockerfile 添加的第一行是 # syntax parser 指令。虽然这个指令是可选的，但它指示 Docker 构建器在解析 Dockerfile 时使用什么语法，并允许使用 BuildKit 的旧版本在开始构建之前升级解析器。解析器指令必须出现在 Dockerfile 中的任何其他注释、空格或 Dockerfile 指令之前，并且应该位于 Dockerfiles 的第一行。
# 我们建议使用 docker/dockerfile: 1，它总是指向版本1语法的最新版本。BuildKit 会在构建之前自动检查语法更新，确保您使用的是最新版本。
  #Next, we need to add a line in our Dockerfile that tells Docker what base image we would like to use for our application.
  #接下来，我们需要在 Dockerfile 中添加一行，告诉 Docker 我们希望为应用程序使用什么基本镜像
# syntax=docker/dockerfile:1
FROM python:3.8-slim-buster

# 为了在运行剩下的命令时让事情变得更简单，让我们创建一个工作目录。这指示 Docker 使用此路径作为所有后续命令的默认位置。通过这样做，我们不必输入完整的文件路径，但可以使用基于工作目录的相对路径。
WORKDIR /app

# 通常，一旦下载了用 Python 编写的项目，您要做的第一件事就是安装 pip 包。这可以确保您的应用程序安装了所有的依赖项。
# 在运行 pip3安装之前，我们需要将 requirements.txt 文件放到镜像中。我们将使用 COPY 命令来完成这项工作。COPY 命令有两个参数。第一个参数告诉 Docker 希望将哪些文件复制到镜像中。第二个参数告诉 Docker 您希望将该文件复制到何处。我们将把 requirements.txt 文件复制到我们的工作目录/应用程序中。
COPY requirements.txt requirements.txt

# 一旦我们在镜像中有了 requirements.txt 文件，我们就可以使用 RUN 命令来执行 pip3 install 命令。这与我们在机器上本地运行 pip3安装的工作方式完全相同，但是这一次模块被安装到了镜像中。
RUN pip3 install -r requirements.txt

# 现在，我们有了一个基于 Python 3.8版本的镜像，并且我们已经安装了依赖项。下一步是将源代码添加到镜像中。我们将使用 COPY 命令，就像上面处理 requirements.txt 文件一样。
COPY . .
# 这个 COPY 命令获取工作目录中的所有文件并将它们复制到图像中。现在，我们所要做的就是告诉 Docker 当我们的映像在容器中执行时，我们想要运行什么命令。我们使用 CMD 命令进行此操作。注意，我们需要通过指定 -- host = 0.0.0.0来使应用程序对外可见(即从容器外部)。
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]