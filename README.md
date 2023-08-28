叉自https://github.com/sunnyguhz/Padavan
以下附上keke和其他五位大神的源码地址供参考：
https://github.com/vb1980/Padavan-KVR  
https://github.com/keke1023/Padavan  
https://github.com/hanwckf/rt-n56u  
https://github.com/chongshengB/rt-n56u  
https://github.com/padavanonly/rt-n56u  
https://github.com/immortalwrt/padavan
固件默认wifi名称
2.4G：机器名_mac地址最后四位，如K2P_9981
5G：机器名_5G_mac地址最后四位，如K2P_5G_9981
wifi密码
1234567890
管理地址
192.168.123.1
管理账号密码
admin
admin
特点：
MTK全家桶破解支持KVR  
已测试机型：  
JDC-1 KR 暂时能用的状态,功能偏少,
京东云一代JDC-1需要修改Padavan/trunk/configs/templates文件夹下的JDC-1.config第11行>>CONFIG_TOOLCHAIN_DIR=/opt/rt-n56u/toolchain-mipsel改成你自己实际的路径!~
KVR组网需要把所有路由器都刷上支持KVR（至少要支持K）的固件，并把wifi名称和密码设成一样。信道建议岔开，一般会自动岔开不用管，也可以手动指定。除了作为主路由的路由器以外，其他路由器设置成AP模式。
最后，你的手机需要支持KVR漫游。目前我手上的手机漫游效果：苹果=红米Note8pro>RealmeGTneo，华为/荣耀可能不能漫游或者漫游效果较差（不确定，他们之前自己官方这么说的）
看信道用wifianalyzer，测试漫游效果用wifi测评大师，查看KVR支持情况用win10电脑上的winfi
# Ubuntu18.0.4.6LTS下编译教程
# 安装依赖
sudo apt update
sudo apt install unzip libtool-bin curl cmake gperf gawk flex bison nano xxd \
    fakeroot kmod cpio git python3-docutils gettext automake autopoint \
    texinfo build-essential help2man pkg-config zlib1g-dev libgmp3-dev \
    libmpc-dev libmpfr-dev libncurses5-dev libltdl-dev wget libc-dev-bin
# 拉取源码    
git clone --depth=1 https://github.com/wontonman/Padavan.git
# 准备工具链(下面的用户名adiawoo替换成你自己的)
cd /home/adiawoo/Padavan/toolchain-mipsel
# （推荐）使用脚本下载预编译的工具链：
sh dl_toolchain.sh
# 或者，也可以从源码编译工具链，这需要一些时间：我使用这种方式
# 清理工具链
./clean_toolchain
# 编译工具链
./build_toolchain
# 转到编译文件夹
cd /home/adiawoo/Padavan/trunk
# 开始编译
fakeroot ./build_firmware_modify JDC-1
# 脚本第一个参数为路由型号，在trunk/configs/templates/中
# 编译好的固件在trunk/images里
# 首次编译完成后，如果需要再次编译其它固件，需要执行清理脚本：
./clean_tree
# 教程参考
https://www.jianshu.com/p/6b8403cdea46
