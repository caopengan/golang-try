# golang-try
第一次尝试golang，记录一些初学者可能会遇到的坑

#### 使用proto buffer自动生成文件时，遇到的一些问题
    protoc默认情况下不会生成接口，如果需要生成接口需要使用plugins（插件）模式
    使用命令：protoc --go_out=plugins=grpc:. *.proto
    
    会出现如下提示信息：
    --go_out: protoc-gen-go: plugins are not supported; use 'protoc --go-grpc_out=...' to generate gRPC
    
    需要升级protoc，使用如下命令：go get github.com/golang/protobuf/protoc-gen-go
    再次执行上面的命令，完美！
### 使用goRPC生成客户端和服务端的接口
    通过protocol buffer的编译器protoc以及一个特殊的gRPC插件来完成，
    首先下载这两个插件,将这两个文件放到gopath的bin目录下
   [protoc.exe](https://github.com/caopengan/golang-try/blob/main/plugins/protoc.exe)、[protoc-gen-go.exe](https://github.com/caopengan/golang-try/blob/main/plugins/protoc-gen-go.exe)
   ```
   protoc --go_out=plugins=grpc:. route_guide.proto
   ```
    输入上面的命令，如果不识别protoc命令，说明你没有把gopath加入到环境变量，采用插件的模式是因为，默认情况下，protocol buffer不会生成接口的代码，插件模式下可以生成接口
