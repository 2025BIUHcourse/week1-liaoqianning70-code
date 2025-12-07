# Week 1 实验报告

## 1. 实验任务说明

### **任务 1：安装双系统 / 虚拟机（必做）**

-   Ubuntu 安装完成截图：\
    ![Ubuntu安装](images/ubuntu安装完成.png)
-   UTM + Ubuntu 截图：\
    ![UTM界面](images/UTM界面.png)
-   Ubuntu 桌面截图：\
    ![Ubuntu桌面](images/Ubuntu界面.png)

### **任务 2：VSCode 的安装与配置（必做）**

-   安装 C++ 插件\
-   在 VSCode 中运行 C++ 的 Hello World\
    ![run](images/运行.png)

### **任务 3：完成 Git 学习与作业上传（必做）**

-   创建 Github 账号（格式：姓名_学号）
-   加入对应小组仓库
-   学习 Git 基本命令
-   使用 SSH 克隆并提交作业

### **任务 4：编写 Markdown 实验报告（必做）**

实验报告要求：

  -----------------------------------------------------------------------
  内容项                              要求
  ----------------------------------- -----------------------------------
  实现全过程说明                      清晰描述步骤与方法

  实验截图 / 视频                     必须提供运行结果

  问题记录                            包含原因分析与尝试过程

  模块理解                            对知识点进行总结

  文件命名规范                        team_张三_week1_draft.md（周五） /
                                      team_张三_week1_final.md（周天）
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 2. 实现过程

### **2.1 安装 UTM 与 Ubuntu**

#### **安装 UTM**

-   前往官网：https://mac.getutm.app\
-   下载并安装 UTM\
-   创建新虚拟机\
-   配置示例：
    -   内存：4GB\
    -   CPU：4 核\
    -   磁盘：64GB\
    -   网络：NAT

#### **安装 Ubuntu**

-   从官网下载安装 ISO\
-   在 UTM 中选择 ISO 启动并安装\
-   完成安装后重启进入系统

------------------------------------------------------------------------

### **2.2 安装 VSCode 与 C++/Markdown 插件**

``` bash
wget -O vscode.deb "https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64"
sudo dpkg -i vscode.deb
```

-   在 VSCode 扩展中安装：
    -   **C/C++**\
    -   **Markdown All in One**

------------------------------------------------------------------------

### **2.3 C++ 程序运行**

``` bash
sudo apt install g++
g++ hello.cpp -o hello
./hello
```

------------------------------------------------------------------------

### **2.4 Git 学习及上传作业**

#### **安装 Homebrew**

``` bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### **安装 Git**

``` bash
brew install git
```

#### **配置 Git 信息**

``` bash
git config --global user.name "GitHub用户名"
git config --global user.email "GitHub邮箱"
```

#### **生成 SSH 密钥**

``` bash
ssh-keygen -t ed25519 -C "GitHub邮箱"
```

#### **克隆仓库（SSH）**

``` bash
git clone git@github.com:用户名/仓库名.git
```

------------------------------------------------------------------------

## 3. 遇到的问题及解决方法

### **问题 1：虚拟机每次开机都进入 Ubuntu 安装界面**

**原因：** UTM 挂载了 ISO，并且引导顺序优先光驱。

**解决方法：** 1. 完全关闭虚拟机\
2. UTM → 编辑 → **CD/DVD** → 选择"无"\
3. UTM → 编辑 → **启动（Boot）** → 将 **Hard Disk** 调整为第一位\
4. 保存后重启即可正常进入系统

------------------------------------------------------------------------

### **问题 2：Ubuntu 终端无法输入中文**

#### **解决方法 1：安装中文输入法**

``` bash
sudo apt update
sudo apt install fcitx fcitx-pinyin
sudo dpkg-reconfigure locales
```

#### **解决方法 2：使用 VSCode 输入中文**

-   在终端输入 `code` 打开 VSCode\
-   新建文件即可正常中文输入

------------------------------------------------------------------------

### **问题 3：UTM 卡顿、运行缓慢（新增）**

**原因：** UTM 采用 QEMU 仿真，图形界面性能较弱；同时 ARM 架构下模拟 x86
程序效率更低。

#### ✅ **解决方法（推荐）---使用 VMware + SSH，流畅度提升巨大**

1.  在 Mac 上下载并安装 **VMware Fusion**（比 UTM 快非常多）\

2.  在 Ubuntu 中启用 SSH 服务：

    ``` bash
    sudo apt install openssh-server
    ```

3.  获取虚拟机的局域网 IP\

4.  在 Mac 终端远程连接：

    ``` bash
    ssh 用户名@虚拟机IP
    ```

5.  使用 SSH 操控 Ubuntu 几乎无延迟，体验远好于 UTM 图形界面

------------------------------------------------------------------------

## 4. 总结与心得

-   文件命名需严格遵守格式规范\
-   Markdown 在实验报告编写中非常高效\
-   熟悉 Linux 基础命令可提升操作效率\
-   Git 的 SSH 提交流程是今后课程的核心技能

### 提交流程示例

``` bash
cd week1-liaoqianning70-code
git checkout -b my-homework
echo "我的作业内容" > 作业.txt
git add 作业.txt
git commit -m "提交Week1作业"
git push -u origin my-homework
```
