# 新公司
以后的酸甜苦辣会更新到这个下面，感觉记录生活还是很有必要的，哈哈

# 入职 第一周(2018.12.03)

1. 入职材料的递交与手续办理

2. 项目在Ubuntu系统上操作，为hp elitebook安装双系统(第一次安装双系统，之后会写一下步骤，加上安装项目之见沟通的工具和自己日常习惯使用的工具共耗费2日)
3. 漫长的等待代码权限的审批，以及在github上看mazilla/gaia的代码，感觉挺老旧的代码格式，但是风格和代码工整度都很强

# 停电 第二周(2018.12.10)

1. 公司处于一栋稍微老旧的办公楼，结果周末发生电井火灾事件，故通知在家办公

2. 公司还是要处于运行状态的，故和总公司和物业交涉一方面在家办公了几天一方面又催着抢修电力，这周总体时闲的屁疼，基本还是熟悉代码，不过比较明确的是自己将要做哪方面的code，不至于像无头苍蝇

3. 针对Firefox的webide通过USB接口连接手机设备出现的问题

   1. 手机设备debug开启
   2. 通过USB装置连接，打开终端 

   ```shell
   adb root //
   adb devices //查看设备是否连接上
   sudo adb kill-server
   sudo adb start-server
   lsusb //可以查看到当前进程与设备id
   ```

4. 对于下周的展望，尽快融入工作环境

# 推送 第三周(2018.12.17)

1. git fork的仓库与源库保持代码同步(使用命令行)

   ``` shell
   git remote -v // 查看远程库信息
   git remote add upstream git@github.com:xxx/xxx.git // 添加源库
   git fetch upstream // fetch后在本地生成了新的本地分支：upstream/master
   git merge upstream/master // 合并源库代码到本地
   git push // 推送到自己远程库
   ```

2. 外界显示器到手,连接上外接显示器分辨率总是1280*768让人不爽,搜索答案无非两个
   1. 显示器驱动更新,识别外接显示器的分辨率
   2. VGA接口太老旧,请进行更换(我的用这个搞定的)

3. 记一个比较悲剧的事情,上午花了一些时间总结了一部分现在的业务逻辑,搞双屏关机重启的时候忘记保存了,nngt,只能重新再搞了

4. .deb包的安装卸载命令 

   ```shell
   sudo dpkg -i xxx.deb #安装iptux.deb软件包（其中-i等价于--install）
   sudo dpkg -L xxx #查看iptux软件包安装的所有文件（软件名称可通过dpkg -I命令查看，其中-L等价于--listfiles）
   sudo dpkg -r xxx #卸载iptux软件包（软件名称可通过dpkg -I命令查看，其中-r等价于--remove）
   ```

   注：dpkg命令无法自动解决依赖关系。如果安装的deb包存在依赖包，则应避免使用此命令，或者按照依赖关系顺序安装依赖包。

5. Ubuntu下修改磁盘分区名称,因为自己装系统的时候貌似没注意,导致装了两个名称表现一样的的磁盘分区名称,每次找文件在此两盘中做抉择都会搞错,故决定给其改名字做一区分

   ``` shell
   sudo fdisk -l // 获取磁盘分区信息
   设备           Start     末尾    扇区   Size 类型
   /dev/sda1       2048     739327    737280   360M EFI System
   /dev/sda2     739328    1001471    262144   128M Microsoft reserved
   /dev/sda3    1001472  299835891 298834420 142.5G Microsoft basic data
   /dev/sda4  484427776  752965631 268537856 128.1G Microsoft basic data
   /dev/sda5  752965632  958599167 205633536  98.1G Microsoft basic data
   /dev/sda6  958601216  960608255   2007040   980M Windows recovery environment
   /dev/sda7  960608256 1000204287  39596032  18.9G Microsoft basic data
   /dev/sda8  299837440  482426879 182589440  87.1G Linux filesystem
   /dev/sda9  482426880  484427775   2000896   977M Linux swap
   
   //sudo umount /dev/sda5 // 先卸载要修改的分区
   sudo ntfslabel -f /dev/sda5 Twitter // 修改名称
   ```

6. 作为`ubuntu`小白一枚,开始安装`nodejs`的时候,不明就里直接使用`sudo apt-get install nodejs`,其实应该使用[https://github.com/nodesource/distributions/blob/master/README.md](https://github.com/nodesource/distributions/blob/master/README.md)文档进行安装的,可以安装指定版本的`nodesource`,现在安装的是高版本的`v11.x`,尴尬的问题来了,现在开发环境上需要是`8.x`版本的node,各种降版本都行不通,只能变通的想其他办法来使用.<font color='red'>`nvm`到你了,node版本管理工具,使我们合理的切换node环境版本</font>

   To install or update nvm, you can use the [install script](https://github.com/creationix/nvm/blob/v0.33.11/install.sh) using cURL:

   ```shell
   curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
   ```

   or wget

   ```shell
   wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
   ```

   test

   ```shell
   nvm --version
   command -v nvm
   ```

   接下来查看系统已安装的node版本

   ```shell
   nvm ls
   ->       v8.8.0
          v10.14.2
            system
   default -> 8.8.0 (-> v8.8.0)
   node -> stable (-> v10.14.2) (default)
   stable -> 10.14 (-> v10.14.2) (default)
   iojs -> N/A (default)
   lts/* -> lts/dubnium (-> v10.14.2)
   lts/argon -> v4.9.1 (-> N/A)
   lts/boron -> v6.15.1 (-> N/A)
   lts/carbon -> v8.14.1 (-> N/A)
   lts/dubnium -> v10.14.2
   ```

   查看远程node版本

   ```shell
   nvm ls-remote
   ```

   选择安装,我这边选择安装了笔记时间最新版本`(20181221)`的最新稳定版本`v10.14.2LTS`版本,以及目前项目所需的`v8.x`版本的`v8.8.0`版本,图个吉利数字哈哈

   切换:

   ```she
   nvm use 8.8.0
   Now using node v8.8.0 (npm v5.4.2)
   ```

   good!

   `yarn`的安装[https://yarn.bootcss.com/docs/install/#debian-stable](https://yarn.bootcss.com/docs/install/#debian-stable)

   使用homebrew安装版本过低,修改链接[https://www.jianshu.com/p/754823b00275](https://www.jianshu.com/p/754823b00275)

   熟悉一下`yarn`的使用,和`npm`类似

   > 极其快速

   > Yarn 会缓存它下载的每个包，所以无需重复下载。它还能并行化操作以最大化资源利用率，安装速度之快前所未有



## **比较重要的事情是**

终于理清了这边的`git`使用思路,

也比较明确以后若是修改`bug`或者是添加需求`code`时的协作,

虽然觉得这不是最重要的,

但是也是第一次在项目上使用`gitbash`还是蛮期待的,

觉得`git`真的是非常强大的版本管理系统,

其实也不算晚,弄清楚了就好