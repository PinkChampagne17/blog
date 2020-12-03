---
title: Go语言的环境配置与Hello world
date: 2020-07-19 13:57:00
categories: 
- Go
---

这只是一个简单的示例，个别细节没做太多解释，可去官网或其他网站自行了解。

## 示例系统
- Windows 10

## 安装Go语言开发工具
根据自己的喜好在以下两个链接中，选择其中一个来下载Go语言开发工具，选择下载以`.msi`作为后缀名的Windows版。
- [Go语言中文网](https://studygolang.com/dl)

- [Go语言官网](https://golang.org/dl/)（需要魔法上网）

## 检查Go语言开发工具是否可用
在命令行中直接输入`Go`命令，如果显示出如以下的提示，说明Go语言开发工具已经安装成功。
```text
> go

Go is a tool for managing Go source code.

Usage:

        go <command> [arguments]

The commands are:

        bug         start a bug report
        build       compile packages and dependencies
        clean       remove object files and cached files
        doc         show documentation for package or symbol
        env         print Go environment information
        fix         update packages to use new APIs
        fmt         gofmt (reformat) package sources
        generate    generate Go files by processing source
        get         add dependencies to current module and install them
        install     compile and install packages and dependencies
        list        list packages or modules
        mod         module maintenance
        run         compile and run Go program
        test        test packages
        tool        run specified go tool
        version     print Go version
        vet         report likely mistakes in packages
```

## 安装编辑器
在这个示例中我们使用VS Code作为Go语言的编辑器。

### 安装VS Code
- [VS Code官网](https://code.visualstudio.com/)

### 安装VS Code插件
打开VS Code，选择左侧的Extensions，查找并安装以下两个用于**中文化**和**Go语言**的插件。
- Chinese (Simplified) Language Pack for Visual Studio Code
- Go

## 安装/更新工具
### 配置代理
因为国内网络较为特殊的原因，需要配置代理才能通过网络安装/更新工具。

在命令行中输入以下命令配置代理。
```text
> go env -w GO111MODULE=on
> go env -w GPROXY=https://goproxy.cn,direct
```


在VS Code中使用按`Ctrl`+`Shift`+`P`，在打开的输入框中输入`Go`，这时就可以看到名为**Go: Install/Update Tools**的选项。点击后将列出的所有工具勾上，再点击确认(OK)进行安装。

当VS Code自带的命令行出现类似以下的提示，安装项以`SUCCEEDED`结尾，说明该安装项已经安装成功。
```text
Installing github.com/uudashr/gopkgs/v2/cmd/gopkgs SUCCEEDED
Installing github.com/ramya-rao-a/go-outline SUCCEEDED
Installing github.com/acroca/go-symbols SUCCEEDED
Installing golang.org/x/tools/cmd/guru SUCCEEDED
Installing golang.org/x/tools/cmd/gorename SUCCEEDED
Installing github.com/cweill/gotests/... SUCCEEDED
Installing github.com/fatih/gomodifytags SUCCEEDED
Installing github.com/josharian/impl SUCCEEDED
```
如果出现了类似以下提示，那就是有安装项安装失败了。
```text
1 tools failed to install.
```

## Hello, world!
新建一个名为hello-world的文件夹，并在此文件夹下运行go mod init {项目名}：
```shell
> mkdir hello-world             # 新建名为hello-world文件夹
> cd ./hello-world              # 切换目录到该文件夹下
> go mod init hello-world       # 使用go mod进行初始化
```
新建一个名为**main.go**的文件，放入以下代码。
```GO
package main

import "fmt"

func main() {
        fmt.Print("Hello, world!")
}
```

使用命令行**进入main.go所在的目录**，使用以下命令运行我们刚刚编写的Hello world程序。
```text
> go run main.go
```
最后命令行打印出以下内容，说明刚刚编写的Hello world程序已经成功运行。
```text
Hello, world!
```
