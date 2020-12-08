# golang-try
第一次尝试golang，记录一些初学者可能会遇到的坑

#### 使用proto buffer自动生成文件时，遇到的一些问题
    protoc默认情况下不会生成接口，如果需要生成接口需要使用plugins（插件）模式
    使用命令：protoc --go_out=plugins=grpc:. *.proto
    
    会出现如下提示信息：
    --go_out: protoc-gen-go: plugins are not supported; use 'protoc --go-grpc_out=...' to generate gRPC
    
    需要升级protoc，使用如下命令：go get github.com/golang/protobuf/protoc-gen-go
    再次执行上面的命令，完美！
