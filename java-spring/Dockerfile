# syntax=docker/dockerfile:1
# 基本镜像使用来自 Docker Hub with Java JDK 的官方 openjdk 映像，它已经拥有运行 Java 应用程序所需的所有工具和包。
FROM openjdk:16-alpine3.13
# 为了在运行剩下的命令时更简单，让我们设置镜像的工作目录。这指示 Docker 使用此路径作为所有后续命令的默认位置。通过这样做，我们不必输入完整的文件路径，但可以使用基于工作目录的相对路径。
WORKDIR /app

COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:go-offline
COPY src ./src
CMD ["./mvnw", "spring-boot:run"]