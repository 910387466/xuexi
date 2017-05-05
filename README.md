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
      
      

