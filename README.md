# Quantumult X 
## iPhone （免拔卡）解锁 TikTok + 换区 + 发布视频 + 直播 + 点赞评论
视频教学：

## 一、准备工作

- 在App Store下载 TikTok | Quantumult X
- 自备代理，ss/ssr/vmess等

注册美国苹果ID方法：https://youtu.be/H6GtrR1OFfU

小火箭Shadowrocket下载和使用方法：https://youtu.be/1e7D_SGUAqY


## 二、操作步骤
- 1、打开Quantumult X
- 2、开启MitM并信任Quantumult X证书，iOS 14、iOS 13和iOS 12操作略有不同： * 设置--)MitM--)开启MitM--)生成密钥及证书--)右上角点保存--)允许安装描述文件--)关闭--)前往手机的设置，不在Quantumult X了--)看到已下载描述文件--)安装--)输入手机的解锁密码--)安装--)安装--)前往手机的设置--)通用--)关于本机--)证书信任设置--)找到Quantumult X Custom Root Certificate…点绿它以信任该根证书--)继续
- 3、添加配置文件（下面二种方法）
### 方法一：
### 日本
    
    https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Quantumult%20X/TikTok-JP.conf, tag=TikTok, update-interval=86400, opt-parser=false, enabled=true

### 台湾

    https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Quantumult%20X/TikTok-TW.conf, tag=TikTok, update-interval=86400, opt-parser=false, enabled=true


### 韩国

    https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Quantumult%20X/TikTok-KR.conf, tag=TikTok, update-interval=86400, opt-parser=false, enabled=true


### 美国

    https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Quantumult%20X/TikTok-US.conf, tag=TikTok, update-interval=86400, opt-parser=false, enabled=true


### 方法二：
- 1.在[rewrite_local]中添加以下重写

        (?<=_region=)CN(?=&) url 307 JP
        (?<=&mcc_mnc=)4 url 307 2
        ^(https?:\/\/(tnc|dm)[\w-]+\.\w+\.com\/.+)(\?)(.+) url 302  $1$3
        (?<=\d\/\?\w{7}_\w{4}=)1[6-9]..(?=.?.?&) url 307 17

- 2、在[mitm]中添加

        hostname = *.tiktokv.com, *.byteoversea.com, *.tik-tokapi.com

## 开启Quantumult X：前往Quantumult X的主页--）找到TikTok策略--）长按添加节点--)TikTok愉快


## 三、添加分流
- 找到[filter_remote]添加下句分流(无论使用方法一或是方法二，此分流都需要添加！)

       https://raw.githubusercontent.com/Semporia/Quantumult-X/master/Filter/TikTok.list, tag=TikTok, force-policy=TikTok, update-interval=86400, opt-parser=false, enabled=true

## 四、换区操作
在[rewrite_local]中添加下句重写，并将CN改为想看的国家/地区的2位大写英文简写 JP（日本）｜KR（韩国）｜UK（英国）｜US（美国）｜TW（台湾）

        (?<=_region=)CN(?=&) url 307 CN

## 特别说明
- 1、为什么要先卸载TikTok，TikTok会在第一次使用时触发限制，并导致之后无法通过MiMt解密
- 2、所以先配置好规则之后，然后在下载TikTok，减少重定向的请求次数，降低风险，延长规则的寿命
- 3、为什么配置好之后还是无法使用，请检查软件的证书有没有安装，信任，
- 4、或者是Https解密（MiMt）与重写（Rewrite）有没有开启
- 5、或者是软件是不是盗版，比如用共享ID下载的Quantumult X，有设备限制，是无法使用重写脚本功能的

