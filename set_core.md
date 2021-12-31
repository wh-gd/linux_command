设置core文件的格式

echo “1” > /proc/sys/kernel/core_uses_pid

echo “core.%e.%p” > /proc/sys/kernel/core_pattern

权限不够可以切换到root，%e表示相关的命令名，%p表示进程pid，还有其他的一些参数可选：

%p - insert pid into filename 添加pid

%u - insert current uid into filename 添加当前uid

%g - insert current gid into filename 添加当前gid

%s - insert signal that caused the coredump into the filename 添加导致产生core的信号

%t - insert UNIX time that the coredump occurred into filename 添加core文件生成时的unix时间

%h - insert hostname where the coredump happened into filename 添加主机名

%e - insert coredumping executable name into filename 添加命令名

产生的core文件默认在当前目录，也可指定到core文件到某个目录(需事先创建好):

echo “/tmp/core/core.%e.%p” > /proc/sys/kernel/core_pattern
