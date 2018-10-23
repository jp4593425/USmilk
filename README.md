搭建酸酸乳上某国外搜索网站//自建吃鸡加速服务器教程


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eafc435f46cb?w=1200&h=750&f=png&s=831363)

2018年来了，去年zf加大力度重重打击了各大翻墙网站，各大代理公司全部宣布停止服务，前段时间还抓了一个私人售卖梯子的，说是非法盈利70多万，被判5年有期徒刑，罚没财产50万，想想都口怕。然而，作为一名程序员，科学上网是刚需，不是我黑度娘，有些东西它确实搜不到，好多答案都是复制粘贴的，没啥营养价值。而g00gle一搜一个准，答案的质量也很高，所以，科学上网就更有必要了。

关于vps，我这边用过好几个国内外知名大公司的（免费的没用过，便宜没好货，即使天上掉馅饼的好事，估计我也捡不到，所以还是不考虑了），最后还是觉得vultr的比较好，性价比高。搬瓦工的话，便宜是便宜，但是是半年一年的卖，现在封的严，运气不好今天买的明天就不能用了，所以不推荐...其他的不说了，性价比不高。

关于vultr还有几点好处。

1.支持支付宝付款

2.vultr实际上是折算成小时来计费的，比如服务器是5美元1个月，那么每小时收费为5/30/24=0.0069美元 会自动从账号中扣费，只要保证账号有钱即可。如果你部署的服务器实测后速度不理想，你可以把它删掉（destroy），重新换个地区的服务器来部署，方便且实用。因为新的服务器就是新的ip，所以当ip被墙时这个方法很有用。

所以本篇教程以vultr为例。

下面，我将教大家如何一步一步的搭建酸酸乳服务器科学上网。



为防止文章被锁定，以下全部使用别名：



![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb01250149e8?w=539&h=94&f=png&s=56676)

他们俩有啥区别：功能都一样，最早出来的是原版酸酸乳，后来有人在其基础上多加了一个协议，变成了酸酸乳，据说可以防止ip被封。

第一步 注册vultr并充值
打开www.vultr.com并注册账号 ，上文提到过，vultr是支持支付宝的，所以这里给出支付宝充值的示例图。

写个教程不容易，兄弟姐妹们支持一下我的注册推广链接：

https://www.vultr.com/?ref=7237445

界面虽然是英文的，但是肯定难不倒各位小伙伴，何况浏览器还有翻译功能，所以注册的图我就不放了。

接下来是充值，这是必须的，不多bb（这里最少充值10美元）



![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb05e674e572?w=1240&h=613&f=png&s=110234)


第二步 新建vps服务器
点击右上角加号，新建一个服务器


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb17a997b2f0?w=1240&h=613&f=png&s=118413)


这里可以选择各个大洲的服务器。推荐两个，一个是日本，一个洛杉矶。

日本的节点好处是延迟很低，大概在80-120左右，但是掉包率有点高。

洛杉矶的节点延迟大概在120-220左右，掉包率低，几乎不掉包。

其他的节点也可以试试，比如硅谷也不错，虽然延迟高了点，但是不容易被墙，很稳定。

如果需要打游戏加速，请选择延迟低的节点

2018-1-25更新

昨天早上很多ip被qiang，请大家不要选亚洲节点，即jp和新家坡的。可以尝试一下冷门的，比如悉尼、澳大利亚等



![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb1cc006c6f2?w=1240&h=613&f=png&s=223884)

接下来选择vps的操作系统和套餐，没啥说的，选择centos6 64位操作系统，然后选择5刀或其他的套餐，目前迈阿密和日本好像还有2.5刀一个月的。

套餐价格不仅仅跟流量多少和配置等明面上的信息有关，跟分配的vps的带宽也有关，比如$5比$2.5的带宽就高，速度也更快，如果是个人或3人以下使用，建议5刀（速度还行）的，多人（5-8）可以选择10刀的(速度贼快)。

总之就是，越贵的，分配的带宽越高，看自己需求来吧，我目前是用的10刀的。


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb220c4b91e5?w=1240&h=733&f=png&s=302109)


最后点击立即创建



![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb24bed9259a?w=1240&h=83&f=png&s=46937)

过一段时间后，服务器创建完成。

第三步 部署服务器
紧接上一步，服务器新建完成后，点击下图的菊花图标，查看详情（要等到右边的绿色文字变为Running之后点击）


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb271b3985d9?w=1240&h=613&f=png&s=130433)

下面是服务器详细信息，需要说明的是服务器IP、用户名和密码，下面会用到的


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb295986e93d?w=1240&h=601&f=png&s=183185)

接下来你需要下载一个叫Xshell的软件来进入服务器的控制台界面，这里提供一个下载地址，如果挂了，请自行度娘“Xshell”

Xshell百度软件中心

如果你是苹果电脑操作系统，更简单，无需下载xshell，系统可以直接连接VPS。打开终端（Terminal），输入ssh root@ip 其中“ip”替换成你VPS的ip, 按回车键，然后复制粘贴密码，按回车键即可登录。粘贴密码时有可能不显示密码，但不影响， 参考设置方法 如果不能用MAC自带的终端连接的话，直接网上搜“MAC连接SSH的软件”，有很多，然后通过软件来连接vps服务器就行，具体操作方式参考windows xshell。

下载安装Xshell后，打开软件

点击左上角文件--打开--新建

![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb2de9f002b2?w=450&h=163&f=png&s=66728)


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb2fa400442c?w=570&h=348&f=png&s=116209)


然后填入下面信息，只需要改图中两个箭头所指，其他的不用改


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb317053ea6e?w=576&h=499&f=png&s=166770)

接下来输入用户名（有的小伙伴反应不能弹出这个框，如果有这种情况，ping一下这个ip，ping不通的原因是因为这个ip被qiang了，只能destory当前ip，然后重开一个，这个没得办法，不会ping的搜索一下）

![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb34f4f8c769?w=345&h=195&f=png&s=67977)

![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb3779329dca?w=437&h=395&f=png&s=131433)

密码输入正确之后，如下图所示


![](https://user-gold-cdn.xitu.io/2018/10/23/1669eb3954ad46c9?w=964&h=754&f=png&s=346585)

接下来分享一段一键部署服务器的代码，是中文版的，功能很强大，感谢作者，推荐大家使用

斜体加粗部分为代码，大家直接全部复制，然后按回车键

【一键部署酸酸乳代码】

CentOS/Debian/Ubuntu 酸酸乳单/多端口一键管理脚本：

--------------------以下区域全部复制--------------------------------

yum -y install wget

wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh
复制代码
----------------------------------------------------------------------

备用下载地址：

--------------------以下区域全部复制--------------------------------

yum -y install wget
wget -N --no-check-certificate https://softs.wtf/Bash/ssr.sh && chmod +x ssr.sh && bash ssr.sh
复制代码
-----------------------------------------------------------------------

安装成功之后显示如下图，如果下次还想调出此界面，输入 bash ssr.sh



接下来我们一起来设置相关信息，照着图走就行











然后就会开始部署酸酸乳了，耐心等待一会，到这一步，输入y，然后再继续耐心等待2分钟左右





到这一步会卡一下





复制下图的连接信息到记事本





最后一步 安装g**gle BBR加速酸酸乳
下面加粗斜体部分，整个复制，粘贴进控制台，然后会自动运行

【g**gle BBR加速教程】
--------------------以下区域全部复制--------------------------------

yum -y install wget

wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh

chmod +x bbr.sh

./bbr.sh

------------------------------------------------------------------------

到下面这里需要按一下回车键





按任意键确定安装





接下来等待安装即可，哦对了，这里也会卡一会



安装完成如下图，最后输入y重启服务器即可





好了，到这里，酸酸乳安装大工搞成

最后一步 使用酸酸乳科学上网

客户端，我推荐原版的酸乳，个人感觉界面更简约

然后ios的客户端，需要是appStore里下载。因为我没用过苹果手机，所以麻烦自行百度。

这里是“酸酸乳”的下载地址

windows 酸酸乳客户端： 下载地址 备用地址

mac 酸酸乳客户端：下载地址 备用地址

android 客户端：下载地址 备用下载地址

这是“原版酸酸乳”下载地址

windows 客户端：下载地址

android 客户端：下载地址

mac的我不晓得，sorry，麻烦百度一下，搜不到就用酸酸乳吧。



游戏加速请下载ssTap

windows-ssTap客户端：下载地址

这个使用方法我就不放了，都差不多的~

下载了之后，以windows原版酸酸乳为例。

打开刚才保存在记事本中的连接信息

如果你使用的原版酸酸乳客户端，复制原版酸酸乳的连接信息

如果你使用的酸酸乳客户端，就复制酸酸乳的连接信息


然后打开软件，右键小飞机图标，选择服务器--从剪贴板导入URL..（这里不好截图，如果没有这个选项，就只能手动一个个填入信息了）







它会自动填入信息，然后点击确定即可





然后这里的启用系统代理，就可以科学上网了

系统代理模式有两种，pac和全局，pac是部分网页通过酸酸乳，全局是所有流量都通过酸酸乳





好了，教程到此结束，谢谢大家的兹辞

================================================================

========切记一定不要利用本教程作出有损中华人民共和国利益的事情==========

=========切记一定不要利用本教程作出有损中华人民共和国利益的事情=========

=========切记一定不要利用本教程作出有损中华人民共和国利益的事情=========

===================请大家做一个遵纪守法的合格公民====================

================================================================

有朋友反馈说连不上，具体原因我也搞不懂呢。。有问题的私信我留下微信吧，我看到了帮你们解决~

关于上不去网

如果有一天你本来用得好好的，突然发现连不上google了，那估计是ip被qiang了，这只能重新开一个ip了，之前的可以destory，新开服务器多收$0.02，大概也就1毛钱吧

请大家不要在评论里恢复一些关键字眼，文章会被删
===问题区===
有的说搭完了上不去网的，可以这么排查下问题

1.右键小飞机图标，看是否已"启用系统开启代理"，如果开启了还是不行，把“系统代理模式”改成“全局模式”（默认是pac模式），再试试能不能上g00gle

2.看ip是否ping的通，ping不通代表被qiang了，只能destory后重新部署一次

3.在服务器上输入bash ssr.sh查看是否安装好酸酸乳，如图




4.如果上述都没问题，在上图的时候，输入3，卸载酸酸乳，卸载完成后，再输入bash ssr.sh, 输入1 ，再安装一次，应该就可以了
