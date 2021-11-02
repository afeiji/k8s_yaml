FROM golang:1.11-alpine AS build

# 安装项目需要的工具
# 运行 `docker build --no-cache .` 来更新依赖
RUN apk add --no-cache git
RUN go get github.com/golang/dep/cmd/dep

# 通过 Gopkg.toml 和 Gopkg.lock 获取项目的依赖
# 仅在更新 Gopkg 文件时才重新构建这些层
COPY Gopkg.lock Gopkg.toml /go/src/project/
WORKDIR /go/src/project/
# 安装依赖库
RUN dep ensure -vendor-only

# 拷贝整个项目进行构建
# 当项目下面有文件变化的时候该层才会重新构建
COPY . /go/src/project/
RUN go build -o /bin/project

# 将打包后的二进制文件拷贝到 scratch 镜像下面，将镜像大小降到最低
FROM scratch
COPY --from=build /bin/project /bin/project
ENTRYPOINT ["/bin/project"]
CMD ["--help"]
