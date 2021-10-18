# docker demo

## python

命令
```
cd python
docker build --tag python-docker .
docker run --publish 5000:5000 python-docker // 注意端口映射否则无法访问
```
验证
```
http://localhost:5000/

`Hello, Docker!`
```

## java-spring
命令
```
cd java-spring
docker build --tag java-docker .
docker run --publish 8080:8080 java-docker
```
验证
```
http://localhost:8080/

`Greetings from Spring Boot!`
```

## go

命令
```
cd go
docker build -f ./Dockerfile . 
docker run docker-gs-ping
```
验证
```
http://localhost:8080/

`Hello, Docker! <3`
```

