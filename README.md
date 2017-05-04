# xuexi
开始时困难，但不知道何时才会度过这个令人不安的时间段！


DJANGO笔记一  学习网站TWD1.7：http://hackerxu.com/Twd/#2  第三章开始
该笔记的环境为Ubuntu下的实现。
1： windows安装python的步骤：去pypi下载 与计算机电脑匹配的64位或者32位的python版本；进行安装，一般会成功，但有时PATH环境
变量会添加失败，需要手动添加-------步骤如下：
          1.点击开始按钮,右键点击我的电脑选择属性.
          2.点击高级选项卡.
          3.电机环境变量按钮.
          4.在系统变量列表里,查找名字叫Path的变量,点击并选择编辑按钮
          5.在行末添加;C:\python27;C:\python27\scripts.不要忽略分号 - 还有不要添加空格.
          6.点击确定保存配置.
          7.关闭所有的命令行,重新打开,试试看键入python.
这时，打开命令行（win+R）,输入python ，显示为python的详细信息和版本，时间等  为成功！

2： 安装 setuptools 和pip
      下载 setuptools的文件去pypi上，下载.tar.gz的文件，进行解压 到setuptools-版本，这时一个好习惯。
      进入该目录后 输入：sudo python ez_setup.py
      
    在上面的包管理工具安装好后， 直接安装pip： sudo easy_install pip
     pip install -u  django==版本  下载指定的版本， 如没有要求用:pip install django (默认下载最新的django)
假如你想把已安装的包列表分享给其他的开发者使用：  pip freeze  > requirements.txt
      当在其它的电脑上配置环境的时候就简单了  ：    pip install -r requirements.txt
      
虚拟环境    实现多个django开发环境的存在  virtual environment
      pip install virtualenv
      pip install virtualenvwrapper
      第一个包提供了创建虚拟环境的基础，安装第二个包就是使这个过程简化。
      类似Unix系统的话，需要在命令行中启动脚本： source virtualenvwrapper.sh
      如果为win下的环境，需要下载 virtualenvwrapper-win 包 ： pip install virtualenvwrapper-win
       
      使用教程：
      
      mkvirtualenv rango 创建虚拟环境
      lsvirtualenv   列出创建的虚拟环境
      
      workon rango   激活其创建的虚拟环境
      当命令行提示符显示为当前的虚拟环境，就像是上面的rango，，现在就可以在环境里安装任何包了，并且它们不会干预
      其他的虚拟环境，输入 pip list  检查是否安装django和pillow，没有时，可以使用pip来安装它们，但是只存在于虚拟环境
      
      
      ### Xiaomispider
* [爬取小米市场的网址](http://app.mi.com/topList)

* python

* 实现了多页爬取

* 写入文件json

* 爬取apk保存到本地

缺点 ：下载时会阻断，就会导致下载的效率不是很高。
       下载部分代码为用的python的urllib来下载的，自己研究scrapy的下载没有成功，里面的results没有任何东西。懂得大神可以教教我哟。
       
这个为最近工作需要，时间紧迫所临写的，目的为下载小米市场的应用，使用后发现scrapy这个爬虫框架真心的高大上。
代码中也要部分的注释，使用时看看就会懂。
 
### 在scrapy中多页爬取有三中策略。
1
```
start_urls = ['http://app.mi.com/topList?page=%s' %n for n in xrange(1,4)] //通过在初始爬取中循环来实现多页爬取
```
2
```
if newxia:#下一页
    newxiayiye = self.start_urls[0]+newxia.encode('utf-8')
    yield scrapy.Request(newxiayiye,callback=self.parse_S)
else:
    pass   //通过判断网页上下一页来实现多页爬取
```
3
```
rules = (
        Rule(LinkExtractor(allow=(r'http://app\.mi\.com/topList\?page=\d+.*')),callback='parse_S'),
        )   //通过调用scrapy的内置方法LinkExtractor,来实现多页爬取，具体的使用请自行查找【注意这个方法是从网页上静态的获取，无法获取像1 2 3 4 ... 20 。
```
 
### 使用
 修改后setting中的FILES_STORE ，实现自己的下载路径
 
```
 scrapy crawl xiaomi  //或者 scrapy  crawl xiaomi -L WARNING  为不输出log内容，只输出自定义的输出。
 
 scrapy crawl xiaomi -s LOG_FILE=scrapy.log   //将log内容保存到文件。

```
 
### JSON中保存的内容

* 应用的名称

* 软件大小

* 版本

* 分类

* 包名

* 更新时间

* 公司

* appid

* 下载地址

* 评价

* 权限详情

该为临时的爬虫，会进行改进，__本人新手，大神勿喷__。

