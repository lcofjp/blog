* mbed CLI的安装和配置参考：https://os.mbed.com/docs/v5.6/tools/setup.html
* 英文连接参考：https://os.mbed.com/docs/v5.6/tools/create.html
-----
1. 创建工程：`mbed new your-app-name`，这一步要执行一段时间，需要从github上下载最新mbed-os系统和库文件
1. 新建源文件main.cpp，注意是**cpp**文件，否则编译会报错，并编辑: `cd your-app-name`, `vim main.cpp`
1. 编译：`$ mbed compile -t ARM -m K64F`，其中-t是指定工具链，可选的有`ARM`,`GCC_ARM`,`IAR`， -m是你所使用的电路板，查询mbed支持的电路板使用命令：`mbed compile -S`。
1. 将生成的bin文件拖拽到mbed磁盘，即可运行。
------
mbed driver API参考：https://os.mbed.com/docs/v5.6/reference/drivers-overview.html
