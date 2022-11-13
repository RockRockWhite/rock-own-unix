# 编译bochs

不知道为什么，apt上下载下来的bochs在调试的时候会报内存错误， 因此我决定从源码install。

环境：

```bash
  /mnt/c/Users/rock-pc ················································································  13:13:48 ─╮
❯ cat /etc/os-release                                                                                                ─╯
PRETTY_NAME="Ubuntu 22.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.1 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```

这次编译安装大体上顺风顺水。

首先需要提前安装一些依赖

```bash
sudo apt install build-essential xorg-dev libgtk2.0-dev
```

然后下载软件包 [Bochs x86 PC emulator - Browse /bochs at SourceForge.net](https://sourceforge.net/projects/bochs/files/bochs)

```bash
tar -xzvf bochs-2.7.tar.gz
cd bochs-2.7
```

生成配置文件

```bash
./configure --with-x11 --with-wx --enable-debugger --enable-disasm --enable-all-optimizations --enable-readline --enable-long-phy-address --enable-ltdl-install --enable-idle-hack --enable-plugins --enable-a20-pin --enable-x86-64 --enable-smp --enable-cpu-level=6 --enable-large-ramfile --enable-repeat-speedups --enable-fast-function-calls  --enable-handlers-chaining  --enable-trace-linking --enable-configurable-msrs --enable-show-ips  --enable-debugger-gui --enable-iodebug --enable-logging --enable-assert-checks --enable-fpu --enable-vmx=2 --enable-svm --enable-3dnow --enable-alignment-check  --enable-monitor-mwait --enable-avx  --enable-evex --enable-x86-debugger --enable-pci --enable-usb --enable-voodoo
```

make & make install

```bash
make
sudo make install
```

