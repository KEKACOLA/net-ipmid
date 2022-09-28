## phosphor-ipmi-net 统一编码风格
+ 代码格式按照`clang-format`配置要求，使用命令`clang-format -style=file -i include/zdtech/AES.hpp`格式化代码文件
+ 提交代码之前先使用`git diff -U0 HEAD^ | clang-format-diff -i -p1 -style=file`命令检查是否满足统一编码风格
+ 格式化C++项目的代码`find . -regex '.*\.\(cpp\|hpp\|cu\|c\|h\)' -exec clang-format -style=file -i {} \;`

## 特性说明
+ 默认开启防暴力破解功能，默认连续失败3次，锁定ipmi操作180秒,不影响bmcweb、ssh等用户操作,相反如果用户在web、ssh被锁定lanplus则也被锁定
+ v211默认只有eth0，如需增加NIC则在bbappend文件中增加
```
ALT_RMCPP_IFACE = "eth1"
SYSTEMD_SERVICE:${PN} += " \
        ${PN}@${ALT_RMCPP_IFACE}.service \
        ${PN}@${ALT_RMCPP_IFACE}.socket \
        "
```
## To Build
```
To build this package, do the following steps:

    1. ./bootstrap.sh
    2. ./configure ${CONFIGURE_FLAGS}
    3. make

To clean the repository run `./bootstrap.sh clean`.
