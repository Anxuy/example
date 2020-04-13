# GoAdmin Example

A example show how to run go-admin. Just for reference, [here](http://www.go-admin.cn/en) to know more.

Following three ways to run the code.

If you are Windows user, [go-sqlite-dirver](https://github.com/mattn/go-sqlite3) require to download the gcc to make it work.

---

一个运行go-admin的例子。仅供参考，在[这里](http://www.go-admin.cn)了解更多。

以下三种方法。建议go版本大于1.11使用模块加载，同时设置环境变量```GOPROXY=http://goproxy.cn```，版本低于1.11的盆友使用第二种方法。如果本机没有golang环境，可以使用docker。

**如果你没有golang基础，是golang新手的话，建议花几分钟了解一下[golang的依赖包管理机制](https://ms.logger.im/search?q=golang%20%E4%BE%9D%E8%B5%96%E7%AE%A1%E7%90%86)**

如果你是windows用户，那么你需要下载gcc，因为本例子使用的是sqlite数据库，如果你不想使用sqlite数据库，你可以换成mysql，则不需要下载gcc。

劝退：没有计算机基础或基础比较差的请谨慎使用或不要使用orz。

## use go module 使用模块加载依赖

To use go module, you should set GO111MODULE=on first.

使用 go module的话，需要先设置环境变量```GO111MODULE```为```on```

### step 1

```shell
git clone https://github.com/GoAdminGroup/example.git
```

### step 2

```shell
cd example
GO111MODULE=on go run .
```

visit: [http://localhost:9033/admin](http://localhost:9033/admin)

## use gopath 使用GOPATH加载依赖

To use go path, you should set GO111MODULE=off first.

使用 go path的话，需要先设置环境变量```GO111MODULE```为```off```

### step 1

```shell
git clone https://github.com/GoAdminGroup/example.git
```

### step 2

```shell
go get github.com/kardianos/govendor
cd example
govendor sync
```

如果你在中国，因为各种原因导致用以上步骤进行下载安装依赖有问题，那么你可以直接从这里下载：[vendor.zip](http://file.go-admin.cn/go_admin/vendor/v1_2_8/vendor.zip)

下载完解压到项目文件夹即可。

### step 3

```shell
go run .
```

visit: [http://localhost:9033/admin](http://localhost:9033/admin)

## use docker 使用docker

### step 1

```shell
git clone https://github.com/GoAdminGroup/example.git
```

### step 2

```shell
cd example
docker build -t go-admin-example .
```

### step 3

```shell
docker attach $(docker run -p 9033:9033 -it -d go-admin-example /bin/bash -c "cd /go/src/app && GOPROXY=http://goproxy.cn GO111MODULE=on go run .")
```

visit: [http://localhost:9033/admin](http://localhost:9033/admin)