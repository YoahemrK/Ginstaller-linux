# GInstaller 使用文档

Linux game installer/manager

Linux游戏服务器一键下载/管理工具



## 介绍

- 最新版本***v2.2.3***
- **目前仅完美支持Debian11系统**
- 下载功能支持的游戏：
  1. 饥荒联机版
  2. Terraria泰拉瑞亚
  3. TShock泰拉瑞亚插件服
  4. tModLoader泰拉瑞亚模组服
  5. Minecraft-基岩版
  6. Minecraft-Java版
- 管理功能支持的游戏：
  1. 饥荒联机版
  2. tModLoader泰拉瑞亚模组服


------



## 开始之前

本项目开始于7月中旬，最初是准备自己用的，所以一切设计都围绕着我的习惯展开，包括支持的Linux发行版、使用方式、文件分布等等。**如果你不喜欢，请谨慎使用本工具**。

本篇手册会尽可能详细的说明所有参数、命令的用法和注意事项，并附上所参考的资料。希望能对你有所帮助。

**最后，基于种种因素的考虑，现阶段的GInstaller不打算开源，如果你介意请不要使用。**

------



## 目录

[TOC]

------



## Installer下载

GInstaller最初设计的功能，也是目前的主要功能，用于下载Linux端游戏服务器

**用法: `./ginstaller [Options]`**

- 安装的游戏均在`~/MyGames/`目录下；

- 存档路径若未说明，则默认在`~/GameSaves/`目录。

- 如果未特别标注，则默认支持连续输入，即一次可以输入多个参数；

- 除有特别说明的参数外，其他参数不建议使用root账户运行。

- 有些参数以***" - "***开头，有些以***" -- "***开头，不要弄混了

- **`[Options]`可选参数：**

  ```
  -h,-help  <!--参数说明-->
  -basic  <!--安装基础软件-->
  -dst  <!--饥荒联机版专用服务器工具-->
  -tr  <!--泰拉瑞亚-->
  -ts  <!--泰拉瑞亚插件服务器-->
  -mc-bds  <!--我的世界基岩版-->
  -mc-java  <!--我的世界Java版-->
  -tmod  <!--泰拉瑞亚模组服务器-->
  --steam  <!--单独安装SteamCMD-->
  --sudo <USER>  <!--简单设置sudo-->
  --set-color  <!--简单设置界面颜色-->
  --swap <SIZE>  <!--开启交换分区-->
  ```

  

### 1.  -h,-help

1. 显示简单的用法说明


*(不支持连续输入)*



### 2. -basic

<u>**需要root权限**</u>

1. 安装基础软件比如zip、curl；
2. 安装常用的软件比如vim；
3. 做一些软件设置的调整。

上述安装均通过系统自带的包管理器。

如果你不想使用此参数来一键安装软件，只需要保证 **zip|unzip|curl|screen|sudo** 这五个软件已安装，否则运行其他参数时会出错；

*(不支持连续输入)*



### 3. -dst

1. 检查运行库；
2. 检查并安装SteamCMD；
3. 通过SteamCMD安装饥荒联机版专用服务器工具(Don't Starve Together Dedicated Server)；

> 参考资料
>
> - Value developer: [SteamCMD文档](https://developer.valvesoftware.com/wiki/SteamCMD:zh-cn)
> - Fandom Wiki: [多人版饥荒独立服务器](https://dontstarve.fandom.com/zh/wiki/%E5%A4%9A%E4%BA%BA%E7%89%88%E9%A5%A5%E8%8D%92%E7%8B%AC%E7%AB%8B%E6%9C%8D%E5%8A%A1%E5%99%A8)
> - Klei Forums: [Dedicated Server Quick Setup Guide - Linux](https://forums.kleientertainment.com/forums/topic/64441-dedicated-server-quick-setup-guide-linux/)



### 4. -tr

1. 下载安装原版泰拉瑞亚服务器工具(Terraria Server)


<u>*提示*</u>：泰拉瑞亚服务器支持同版本下的跨平台联机，即移动端与PC端可以一起联机。其中移动端需要官方原版（俗称为国际服）

> 参考资料
>
> - 泰拉瑞亚官方中文Wiki: [泰拉瑞亚服务器](https://terraria.wiki.gg/zh/wiki/%E6%9C%8D%E5%8A%A1%E5%99%A8)
> - 泰拉瑞亚官方中文Wiki: [指南:建立泰拉瑞亚服务器](https://terraria.wiki.gg/zh/wiki/Guide:%E5%BB%BA%E7%AB%8B%E6%B3%B0%E6%8B%89%E7%91%9E%E4%BA%9A%E6%9C%8D%E5%8A%A1%E5%99%A8)



### 5. -ts

1. 检查运行库；
2. 下载并安装TShock，泰拉瑞亚第三方插件工具；

***<u>注意</u>！！！***

GInstaller默认会从官方发布地址下载TShock，也就是Github。但因为众所周知的原因，直接从Github下载大概率会失败。<u>如果你也遇到了这种情况，GInstaller支持手动上传的软件包并安装</u>，你需要做的是从各种途径下载最新的TShock软件包到自己的电脑上，**不要解压！！**直接将软件包上传到Linux的`~/`目录然后运行`-ts`参数即可。

这里提供两个下载途径：

- Github上的[官方发布](https://github.com/Pryaxis/TShock/releases)，找带有绿色*"Latest"*的版本，下载带有*`linux-x64-Release`*字样的zip文件；
- 在GInstaller发布的地方找一找，应该会附带有软件包；

<u>*提示*</u>：TShock服务器对应的客户端为原版泰拉瑞亚，不需要再另外下载游戏；和原版泰拉瑞亚服务器同理，支持同版本下的跨平台联机，其中移动端需要国际服

> 参考资料
>
> - TShock for Terraria: [TShock文档](https://ikebukuro.tshock.co/#/)
> - TShock项目地址: [TShock on Github](https://github.com/pryaxis/tshock)



### 6. -mc-bds

<u>**(不推荐)**</u>

下载安装我的世界基岩版服务器(Minecraft Bedrock Server)

**默认存档路径为`~/MyGames/Minecraft-BDS/worlds/`**

不推荐用本工具安装，因为开MC服务器有更好的选择：[MCSManager](https://mcsmanager.com/)([项目地址](https://github.com/MCSManager/MCSManager))，目前这个项目很活跃，更新维护也积极。加上我不玩MC，对`-mc-bds`参数只做过简单的测试，这个参数并不算已完成。<u>如果你真的想用此参数来安装基岩版服务器，出现问题请及时联系</u>

> 参考资料
>
> - Fandom Minecraft Wiki: [Minecraft服务器](https://minecraft.fandom.com/zh/wiki/%E6%9C%8D%E5%8A%A1%E5%99%A8)
> - Fandom Minecraft Wiki: [基岩版专用服务器](https://minecraft.fandom.com/zh/wiki/%E5%9F%BA%E5%B2%A9%E7%89%88%E4%B8%93%E7%94%A8%E6%9C%8D%E5%8A%A1%E5%99%A8)
> - Fandom Minecraft Wiki: [教程/架设基岩版服务器](https://minecraft.fandom.com/zh/wiki/%E6%95%99%E7%A8%8B/%E6%9E%B6%E8%AE%BE%E5%9F%BA%E5%B2%A9%E7%89%88%E6%9C%8D%E5%8A%A1%E5%99%A8)
> - Fandom Minecraft Wiki: [服务器配置文件server.properties](https://minecraft.fandom.com/zh/wiki/Server.properties)



### 7. -mc-java

**(不推荐)**

下载安装我的世界Java版服务器(Minecraft Java Server)

**默认存档路径为`~/MyGames/Minecraft-Java/`**

同样因为更活跃稳定的项目[MCSManager](https://mcsmanager.com/)([项目地址](https://github.com/MCSManager/MCSManager))，不推荐使用本工具进行安装。不过与`-mc-bds`不同的是，此参数已通过测试，可以放心使用。

`-mc-java`安装的是原版服务器，如果你在寻找mod服与插件服，可以看看[教程/架设Mod服务器](https://minecraft.fandom.com/zh/wiki/%E6%95%99%E7%A8%8B/%E6%9E%B6%E8%AE%BEMod%E6%9C%8D%E5%8A%A1%E5%99%A8)

> 参考资料
>
> - Minecraft官网: [MINECRAFT：JAVA 版服务器](https://www.minecraft.net/zh-hans/download/server)
> - Fandom Minecraft Wiki: [Minecraft服务器](https://minecraft.fandom.com/zh/wiki/%E6%9C%8D%E5%8A%A1%E5%99%A8)
> - Fandom Minecraft Wiki: [教程/架设Java服务器](https://minecraft.fandom.com/zh/wiki/%E6%95%99%E7%A8%8B/%E6%9E%B6%E8%AE%BE%E6%9C%8D%E5%8A%A1%E5%99%A8)
> - Fandom Minecraft Wiki: [服务器配置文件server.properties](https://minecraft.fandom.com/zh/wiki/Server.properties)



### 8. -tmod

1. 检查安装运行库；
2. 下载安装tModLoader，泰拉瑞亚模组服；

***<u>注意</u>！！！***

GInstaller默认会从Github上下载tModLoader，因为众所周知的原因大概率会失败。<u>如果你也遇到了这种情况，与`-ts`同理</u>，从各种途径下载最新的tModLoader软件包到自己的电脑上，**不要解压！！**直接将软件包上传到Linux的`~/`目录然后运行`-tmod`参数即可。

这里提供两个下载途径：

- Github上的[官方发布](https://github.com/tModLoader/tModLoader/releases)，找到带有绿色*"Latest"*的版本，下载`tModLoader.zip`；
- 在GInstaller发布的地方找一找，应该附带有软件包；

<u>*提示*</u>：tmod需要另外下载客户端才能游玩；官方目前未提供移动版，所以tmod只支持PC联机

> 参考资料
>
> - tModLoader官方Wiki: [Starting a modded server](https://github.com/tModLoader/tModLoader/wiki/Starting-a-modded-server)
> - tModLoader官方Wiki: [tModLoader wiki](https://github.com/tModLoader/tModLoader/wiki)



### 9. --steam

单独下载SteamCMD，不安装任何游戏。

**SteamCMD的安装路径为`~/steamcmd/`**

> 参考资料
>
> - Value developer: [SteamCMD文档](https://developer.valvesoftware.com/wiki/SteamCMD:zh-cn)



### 10. --sudo \<USER\>

<u>**需要root权限**</u>

为名为\<USER\>的用户简单配置sudo权限

- 权限具体为：任何命令均可提权至root运行，且无需密码
- 你可以自定义sudo权限，请保证\<USER\>能使用`apt`



### 11. --set-color

简单设置用户界面的颜色

- 如果对设置的颜色不满意，请输入`mv ~/.bashrc.bak2 ~/.bashrc`，通过还原备份文件来重置设置。



### 12. --swap \<SIZE\>

<u>**需要root权限**</u>

开启交换分区，大小为\<SIZE\>，**只能从`[2/4/8]`三个值中选择一个**，单位GB。

------



## Manager管理

GInstaller管理游戏服务器。设计初期为单独的工具Manager，后来整合进了GInstaller

**`用法: ./ginstaller Commands [Options]`**

**<u>注意事项：</u>**

- 所有命令需要[Installer下载](#二、Installer下载)作为前置，否则会出现找不到游戏的情况
- 不支持连续输入
- 同样的，不建议使用root用户运行
- 这部分参考的资料和安装参数里的相同，不再单独列出
- 命令前**没有*" - "***



------

### 1. dst命令

**`用法: ./ginstaller dst [Options]`**

- 游戏路径`~/MyGames/DST/`

- 存档路径`~/GameSaves/dst_gamesaves/`

  *上传存档时请参考以下示例：*

  ```
   -- dst_gamesaves
      |-- Cluster_1/
      |   |-- Master/  <!--地面文件夹-->
      |   |-- Caves/  <!--洞穴文件夹-->
      |   |-- cluster.ini  <!--服务器配置文件-->
      |   |-- cluster_token.txt  <!--服务器令牌-->
      |
      |-- Cluster_2/
      |   |-- Master/
      |   |-- cluster.ini
      |   |-- cluster_token.txt
      |
  ```

- 上传存档时请保持默认的文件夹名`Cluster_X/`，*X*为数字。

- **`[Options]`可选参数：**

  ```
  --h,--help  <!--显示简单的使用说明-->
  --u,--update  <!--更新饥荒联机版专服工具-->
  --r,--start  <!--启动饥荒联机版服务器-->
  --q,--stop  <!--关闭饥荒联机版服务器-->
  --l,--list  <!--显示已启动的饥荒联机版服务器-->
  ```

  

#### --h, --help

显示`dst命令`的简单用法说明



#### --u, --update

手动更新饥荒联机版专服工具，并验证游戏完整性。



#### --r, --start

启动一个饥荒服务器。

输入此参数会依次询问三个问题：需要启动的存档序号？启动地面还是洞穴？64位or32位？

1. **存档序号？输入`数字`**。存档文件夹`Cluster_X/`中*"X"*的值；
2. **地面还是洞穴？输入`m/c/b`**。根据你存档里的文件，***m***为地面，对应`Master/`文件夹、***c***为洞穴；对应`Caves/`文件夹。可以单独启动，***b***为地面洞穴一起启动；
3. **64位or32位？输入`y/n`**。输入***y***会以64位运行，***n***或者不输入则为默认的32位。



#### --q, --stop

保存并关闭一个饥荒服务器。

会显示出所有已启动的饥荒服务器，格式示例`"饥荒-1-地面"`。中间的数字既是饥荒服务器的序号，也是存档对应的序号。

**输入你想关闭的服务器序号**，该序号下的地面与洞穴(如果有)会一起关闭。

*<u>注意</u>！*不支持不保存关闭，如有需要请手动关闭服务器



#### --l, --list

显示所有正在运行的饥荒服务器。

- 显示服务器名，格式示例`"饥荒-1-地面"`，中间的数字既是饥荒服务器的序号，也是存档对应的序号；
- 显示服务器启动的时间，格式`(月/日/年 时间)`



------

### 2. tmod命令

**`用法: ./ginstaller tmod [Options]`**

- 游戏路径：`~/MyGames/tModLoader/`

- 存档路径：`~/GameSaves/tmodloader_gamesaves/`

  *上传文件时请参考以下示例：*

  ```
   -- tmodloader_gamesaves/
      |-- Worlds/  <!--世界存档文件夹-->
      |   |-- world1.wld
      |   |-- world1.wld.bak  <!--存档的备份-->
      |   |-- world1.twld
      |   |-- world1.twld.bak
      |
      |-- Mods/  <!--模组文件夹-->
      |   |-- enabled.json  <!--模组是否启用的配置文件-->
      |   |-- yourmodname.tmod  <!--模组本体-->
      |
      |-- ModPacks/  <!--模组包-->
      |   |-- yourmodpackname/
      |
      |-- Config/  <!--配置文件夹，多开时会用到-->
      |   |-- serverconfig.txt
      |   |-- serverconfig-2.txt
      |
  ```

- **`[Options]`可选参数：**

  ```
  --h,--help  <!--显示简单的使用说明-->
  --r,--start  <!--启动tModLoader服务器-->
  --q,--stop  <!--关闭tModLoader服务器-->
  --l,--list  <!--显示已启动的tModLoader服务器-->
  ```

  

#### --h, --help

显示`tmod命令`的简单用法说明



#### --r, --start

启动一个tModLoader服务器

GInstaller会询问你想启动的TMOD服务器序号？

**通常情况下请直接回车**，以保持默认序号1，此时会使用配置文件`serverconfig.txt`启动服务器。

**需要多开服务器的玩家不要保持默认**：

- 创建一个新配置文件`serverconfig-X.txt`，推荐将***"X"***设置为大于等于2的整数；
- 修改好配置文件内容；
- 运行此参数；
- 输入你在第一条中设定的数字；

***<u>提示</u>：***TMOD服务器的设置均来自于对应的配置文件，请注意其内容的准确



#### --q, --stop

保存并关闭一个tModLoader服务器

首先会显示所有已启动的tModLoader服务器，格式示例`"TMOD-1"`，最后数字即为服务器的序号。

**输入你想关闭的服务器序号**，以关闭tModLoader服务器。

*<u>注意</u>！*不支持不保存关闭，如有需要请手动关闭服务器



#### --l, --list

显示所有正在运行的tModLoader服务器

- 显示服务器名，格式示例`"TMOD-1"`，最后的数字是tModLoader服务器的序号，也是对应配置文件序号；
- 显示服务器启动的时间，格式`(月/日/年 时间)`

------



## 计划推出的功能

***可能是即将推出，也可能是很久以后了，谁知道呢***

1. Installer：僵尸毁灭工程
2. Manager：泰拉瑞亚原版、TShock、我的世界Java版
3. Manager：饥荒联机版的自动备份、自动更新
4. Manager：饥荒联机版管理存档，调整服务器设置
5. Manager：tModLoader一键更新模组
6. 对于Debian 10的的支持
7. 对于Ubuntu 22.04及Ubuntu 20.04的支持
8. 对于CentOS 8或其他版本的支持

------



## 注意事项

1. **再次重复，除了几个标注的参数外，其他不建议使用root用户运行**

2. 对于Debian系的Linux发行版（Debian 10和Ubuntu），对它们的支持推出之前，以下参数不能使用，其余参数可以直接运行

   - `-basic`不能使用。你需要参照`-basic`的说明，自己做好必要软件的安装
   - `-ts`、`-tmod`谨慎使用。你需要自己安装运行库。

   RH系（CentOS）支持推出之前不要使用本工具。

3. “连续输入”指的是一次性输入多个参数。

4. TShock和tModLoader如果你实在找不到软件包，可以来我的QQ群里找。

5. 本项目现阶段不开源，但是你有任何代码方面的问题可以来找我，我乐意提供解答。

6. **有问题如何联系我？**推荐QQ群，其他途径诸如B站评论、私信等等不一定能及时回复。

7. 感谢你看到这里，其他事项等我想起来了再补充……



------

[^2023年8月19日]:第一版文档，GInstaller版本v2.2.3



------

> **下面是些无关紧要的废话，可以直接跳过**
>
> 作为传统派加上应用较浅，我对于Linux始终倾向于手动敲命令。今年因为各种原因，接触了不少新机器，每次都手动装软件、调设置等等。步骤不多，但总会忘掉那么几步，在之后的某一天冷不丁给我打断一下。虽说靠烂笔头(记事本)解决了这个问题，但人总是会接触新事物的，6、7月又发生了一些事情，促使我下决心，利用空余时间把烂笔头转换成一个一劳永逸的小工具。
>
> 由于是准备自己用的项目，还是shell脚本零基础，所以最初只写了3个参数；写完后想着发出来让有类似需求的人也能用，于是改进了部分功能，顺便多加了2个参数；之后又想到对小白友好一点，做了大量界面优化；还加入了更多的参数。下载工具写完又计划着写了管理工具Manager……终于在二十五天后做出了现在你看到的GInstaller。
>
> 如果你只想简单的使用，推荐你把这篇文档作为辅助，因为你更需要简单实用的教程；
>
> 如果你想了解全部功能，建议你浏览一遍本文档；
>
> 如果你和我一样偏传统，喜欢自己敲这些不复杂的命令，我也推荐你浏览一遍这篇文档，说不定能在我附上的资料里，找到你想要的东西；