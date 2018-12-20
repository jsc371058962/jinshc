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

# 暂定 第三周(2018.12.17)

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

4. privileged  有特权的,有优惠的  certified 合法的,有保证的

5. .deb包的安装卸载命令 

   ```shell
   sudo dpkg -i xxx.deb #安装iptux.deb软件包（其中-i等价于--install）
   sudo dpkg -L xxx #查看iptux软件包安装的所有文件（软件名称可通过dpkg -I命令查看，其中-L等价于--listfiles）
   sudo dpkg -r xxx #卸载iptux软件包（软件名称可通过dpkg -I命令查看，其中-r等价于--remove）
   ```

   注：dpkg命令无法自动解决依赖关系。如果安装的deb包存在依赖包，则应避免使用此命令，或者按照依赖关系顺序安装依赖包。

6. Ubuntu下修改磁盘分区名称,因为自己装系统的时候貌似没注意,导致装了两个名称表现一样的的磁盘分区名称,每次找文件在此两盘中做抉择都会搞错,故决定给其改名字做一区分

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




