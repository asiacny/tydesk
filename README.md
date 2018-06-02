# TyDesk - 统医桌面
医院终端桌面管理之神器

## 医院需要有效的桌面管理程序！！
历来ERP、CRM、桌面云都无法像征服其他企业一样在医院中取得真正的推广，原因首先在于医院信息系统相对复杂。 围绕着对医院各种业务的切割，诞生了HIS、PACS、RIS、LIS、OA、病理、心电、麻醉、防统方、财务、科研等等子系统。 其次，医院中的电脑终端种类繁多，按业务分：医生站、护士站、技师站、行政站等，按设备分：有人业务终端、无人业务终端、笔记本、服务器等。 第三，各种系统部署运行方式不一，有的是纯桌面应用，有的是Web应用，但是需要不同的浏览器才能正确使用。第四，接口复杂：其中一个系统为外界提供了Web接口，但是需要深度嵌入集成，医生想直接使用很困难。第五，医院轮班很正常，业务流转较多基于工作站，而不是基于员工账号。第六，由于电脑公用，传统电脑桌面快捷方式、浏览器收藏夹等管理混乱，不懂技术的医护人员每天浪费在寻找、定位、报修上的时间很多。

统医桌面旨在解决以上问题。不仅有效地集成各个子系统，还能管理好各种业务终端；不仅提高临床医护的工作效率，还能实现IT管理的自动化。

## 主要功能
- 实现了多系统的桌面集成
- 对Web应用的集中分发
- 对医院内、外网环境的适应
- 对多种浏览器的支持
- 对离线的支持
- 为医院IT自动化管理提供接口与支持

## IT 管理上的功能与特色
- 自动收集各种终端的物理参数
- 终端USB存储的集中管理
- 多角度、自动化对IT终端的盘点
- 为防统方等应用提供位置API服务
- 为核心业务系统提供安全的IP/主机绑定
- 为信息系统安全和审计提供技术基础与保障

## 使用指南

### 下载服务器
[https://github.com/tydesk/tyserver/releases](https://github.com/tydesk/tyserver/releases "服务器下载页面")， 下载TyServer.zip

### 配置服务器
下载完毕后，解压缩TyServer.zip。直接启动里面的Exe即可启动服务器。 要发布新应用，需要配置config.json


```json
{
  "admins": [
    { "ip": "192.168.30.101", "name": "Panzhang Wang"},
    { "ip": "192.168.40.34", "name": "Panzhang Wang"}
  ]
}
```

系统管理员不需要用户名密码登录，通过绑定管理员的IP，允许授权终端的访问。管理员通过WEB界面分发和部署应用。

### 下载客户端
[https://github.com/tydesk/tydesk/releases](https://github.com/tydesk/tydesk/releases)，下载tydesk.zip

### 配置客户端
下载完毕后，解压缩tydesk.zip。 同样，无需安装点击里面的Exe文件即可。事先需修改config.ini，指向正确的内网、外网服务器IP
```ini
inner.host=172.20.10.100
outer.host=192.168.30.101
```
> inner.host为服务器的内网IP；outer.host为服务器的外网IP

### 可以使用了
新分发的WEB应用在30分钟后会自动更新到所有的客户端上。 根据所在内外网，管理员可以往访问管理界面了：
```html
http://<inner.host>:5678/admin/index
http://<outer.host>:5678/admin/index
```

## 环境与配置

### 客户端
支持Win xp, Win 7, win 8, Win 10

### 服务器
64位的任何版本的Windows Server或者64位的Win 7/10, 内存4G以上

### 浏览器
支持各种浏览器，并能自适应

### 构建Exe
需要懂一点Python知识。

1. 下载安装Python 2, 安装requests等依赖
2. pip install pyinstaller
3. pyinstaller --onefile --noconsole tydesk.py




