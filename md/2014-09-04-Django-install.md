## Django 的安装:

* 安装包: 

百度盘里搜索"Django-1.7.tar.gz"


* 安装环境 WIN7


1. 解压文件

2. 移动到python安装目录下

3. python setup.py install

4. 遇到错误,重复第三步

5. 如果不是出现错误,耐心等待安装完成.


* 测试安装是否完成:

```python
import django
print  django.get_version()

```
上面的代码可以查看django版本.


* 升级安装要点

将下面的目录删除后,再安装新版本.

```python
import django
print  django.__path__

```