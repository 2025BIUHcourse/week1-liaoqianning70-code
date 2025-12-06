# Week1 实验报告
## 1.实验任务任务 
### 1：安装双系统（必做）
>Ubuntu 安装完成截图
![Ubantu安装](images/ubuntu安装完成.png)
>UTM + Ubuntu 截图
![UTM虚拟机界面](images/UTM界面.png)
>Ubuntu 桌面截图
![Ubuntu桌面](images/Ubuntu界面.png)
###任务 2：VSCode 的安装与配置（必做）
>C++ 插件安装
>在 VSCode 中运行 C++ 的 Hello 
![c++run](images/运行.png)

### 任务 3：完成 Git 学习与作业上传（必做）
>加入自己的 Github 小组（例如 Group 1 的 Github 仓库网址为： https://classroom.github.com/classrooms/246406408-2025biuhcourse-classroom-group1 ，其他小组只需修改网址最后的数字即可）
>创建自己的 Github 账号（用户名格式：姓名_学号）
>完成 Git 命令的学习
>将作业使用命令提交到 Github 对应的仓库中。
###任务 4：编写 Markdown 实验报告（必做）
>实验报告要求：

>|内容项	    |    要求
 |:------------|:----------------
>|实现全过程说明  |	需清晰描述步骤与方法
>|实验截图 / 视频 |	必须提供运行结果
>|问题记录	     |包含原因分析与尝试过程
>|模块理解	     |对知识点进行总结
>|文件命名规范	  |team_张三_week1_draft.md(周五)
team_张三_week1_final.md(周天)
***
## 2. 实现过程
### 1. 安装虚拟机utm并安装ubuntu
#### 安装utm
>进入官网https://mac.getutm.app下载utm
>安装utm# 如果从官网下载的是 .dmg 文件
>启动 UTM 并新建虚拟机
>选择操作系统
>配置虚拟机
>>1. 系统设置：
   - 名称：Win11-ARM
   - 系统架构：ARM64 (aarch64)
   - 内存：4096 MB 或更高
   - CPU 核心：4 核心（根据主机配置调整）

>>2. 存储设置：
   - 点击 "Browse" 选择 Windows ISO 文件
   - 创建虚拟磁盘：64.0 GB（最小建议）
   - 接口类型：NVMe（性能更好）

>>3. 共享目录（可选但实用）：
   - 启用目录共享
   - 选择 Mac 上的文件夹
   - 在虚拟机中访问：\\tsclient\共享名

>>4. 显示设置：
   - 分辨率：1920x1080
   - 启用 Retina 显示支持
   - 3D 加速：关闭（Windows ARM 暂不支持）

>>5. 网络设置：
   - 默认使用共享网络（NAT）
   - 或桥接模式（让虚拟机获得独立 IP）
#### 安装ubuntu
>下载 Ubuntu ISO:
>>访问 https://ubuntu.com/download/desktop 下载最新版 Ubuntu
>在 UTM 中创建新虚拟机
>安装 Ubuntu
>完成安装后重启
### 4. 安装vscode 及c++，markdown
#### 安装vscode
>第1步：在Ubuntu终端中下载.deb包
`wget -O vscode.deb 'https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64'`
>第2步：在Ubuntu终端中安装
`sudo dpkg -i vscode.deb`
#### c++,markdown的下载
>在vscode中的拓展部分下载即可
### c++的运行
>安装g++编译器
`sudo apt install g++`
>编译和运行
`g++ hello.cpp -o hello`

### 3. git学习及上传
>先安装 Homebrew（访问 brew.sh 或运行命令）:
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
![安装 Homebrew](images/安装 Homebrew.png)
>安装 Git：
`brew install git`
![安装 git](images/安装git（部分截图）.png)
>配置 Git 用户信息:
`git config --global user.name "你的GitHub用户名"`
`git config --global user.email "你的GitHub注册邮箱"`
![配置 Git 用户信息](images/配置git用户信息.png)
>生成 SSH 密钥:
`ssh-keygen -t ed25519 -C "你的GitHub注册邮箱"`
>将 SSH 密钥添加到 GitHub
![密钥添加](images/密钥添加.png)
>克隆仓库（使用 SSH）：
`git clone git@github.com:用户名/仓库名.git`
![克隆仓库](images/克隆仓库.png)
***
### 遇到的问题及解决方法
#### 虚拟机的安装：虚拟机仍挂载着 Ubuntu ISO 且引导顺序以光驱优先，导致每次开机都进入安装程序而非已安装的系统
>解决方法：
>>1.关闭虚拟机确保 Ubuntu 虚拟机完全关机（不是挂起），回到 UTM 主界面。
>>2.移除 ISO 镜像挂载:
>>>选中你的 Ubuntu 虚拟机 → 点击右上角「编辑」（齿轮图标）。
>>>左侧菜单选择「CD/DVD」→ 右侧「镜像文件」下拉框，选择「无」。
>>>点击左上角「保存」（Cmd+S/ Ctrl+S）。
>>3.调整引导顺序（关键）
>>>再次进入虚拟机「编辑」→ 左侧菜单选择「启动」。
>>>找到「引导顺序」列表，将「Hard Disk（硬盘）」拖拽到第一个位置。
>>>取消「启动时连接 CD/DVD」（若勾选），保存设置。
>>>重启验证启动虚拟机，此时应直接进入已安装的 Ubuntu 系统，不再进入安装界面。
#### Ubuntu终端默认不支持中文输入
>解决办法1：启用终端中文输入，安装中文输入法
>>安装fcitx和拼音输入法
`sudo apt update`
>>配置输入法:配置区域和语言
`sudo dpkg-reconfigure locales`
>解决办法2:使用VS Code创建和编辑文件（
>>在终端输入 code 打开VS Code
>>在VS Code中创建新文件，按 Ctrl+N
>>VS Code支持中文输入！
>>保存文件时，可以直接用中文命名
>>回到终端编译运行
***
## 4.总结与心得
>1. 文件名一定要写对
![错误文件名](images/错误文件名（克隆仓库）.png)
>2. markdown
>>用 # 表示标题层级，# 数量越多，标题级别越低（1-6 级），# 后需加空格
>>加粗、斜体、删除线
>>用 数字+小数点 开头，后加空格（数字无需手动排序，Markdown 会自动修正）
>> 图片（插入本地 / 网络图片）
>>>语法：![图片加载失败时的提示文本](图片地址 "可选备注")（比链接多一个 !）
>>链接（跳转至网页 / 文档）
>>>语法：[链接显示文本](链接地址 "可选备注，hover 时显示")
>>展示代码：`code`
>>表格（整理结构化数据）
>>>用 | 分隔列，- 分隔表头和内容，冒号（:）可控制对齐方式（默认左对齐）
>3. linux的指令(部分)
>>cd Documents  切换到当前目录下的 Documents 子目录
>>cd ..   返回上级目录（核心常用）
>>cd ~    返回用户主目录（等价于 cd）
>>cd -    切换到上一次所在目录（类似“返回”）
>4. 提及流程
>>1. 进入项目
`cd week1-liaoqianning70-code`
>> 2. 创建开发分支
`git checkout -b my-homework`
>>3. 完成作业（添加文件、修改代码等）
`echo "我的作业内容" > 作业.txt`
>>4. 提交
`git add 作业.txt`
`git commit -m "提交Week1作业"`
>>5. 推送
`git push -u origin my-homework`