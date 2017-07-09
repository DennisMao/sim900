# SIM900 Go's package
本模块用于通过计算机串口实现与GSM电话模块之间的通讯，原作者[argandas](https://github.com/argandas),本版本在原作者基础上修复了短信经常发送失败问题，增加中文CS2短信发送支持和独立日志打印功能。

## 如何安装

需要支持:
-  Golang 1.4以上版本
- SIM900模块是基于 [serial](https://github.com/DennisMao/serial) 模块上开发而来，因此需要先获取serial串口模块

安装过程:
```bash
go get github.com/DennisMao/serial  # installs the serial package
go get github.com/DennisMao/sim900  # installs the SIM900 package
```

## 如何使用

硬件准备:
- USB转TTL 5V串口模块
- USB转TTL 串口模块驱动
- 在使用本程序前可通过串口调试助手测试连通情况

软件准备:
通过SIM900模块

## 程序样例

```go
package main
import "github.com/argandas/sim900"

func main() {
	gsm := sim900.New()
	err := gsm.Setup("COM1", 9600)
	if err != nil {
		panic(err)
	}
	defer gsm.Teardown()
	phoneNumber := "13711112222" // The number to send the SMS
	gsm.SendSMS(phoneNumber, "Hello World!")
}
```

## 引用

- SIM900支持的AT指令列表 [here](http://wm.sim.com/upfile/2013424141114f.pdf).
- 更多的使用方法，可在godoc上查询本模块获取。

Go explore!

## License

SIM900 package is MIT-Licensed