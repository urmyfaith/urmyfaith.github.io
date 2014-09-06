# Writing your first Django app--part 3


> view : Django应用(作为一个特殊的功能或者有一个特定的模版)里的一种网页.

在DemoAppPoll里,我们下面的view:

* Question index  page  -->展示最新的问题

* Question detail page -->展示一个问题和一个投票表格

* Question result page --> 展示特定问题的投票结果

* Vote action --> 处理特b定问题的投票.

    在Django里,每一个view都代表一个python 函数/方法.

    请求一个url的时候,Django就会使用一个view来处理这个page.

    从URL传递到view,Django使用URLconfs

## 第一个view

1.修改DemoAppPoll/views.py:
```python
from django.shortcuts import render
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello,urmyfatih.")

```

2.创建DemoAppPoll/urls.py

```python
from django.conf.urls import patterns,url
from DemoAppPoll imoprt views

urlpatterns =patterns(
    '',
    url(r'^$',views.index,name='index')
    )

```
3.在工程demoSite/urls.py中添加应用DemoAppPoll的urls.py
```python
from django.conf.urls import patterns, include, url
from django.contrib import admin

urlpatterns = patterns('',
    # Examples:
    # url(r'^$', 'demoSite.views.home', name='home'),
    # url(r'^blog/', include('blog.urls')),
    url(r'^DemoAppPoll/', include('DemoAppPoll.urls')),
    url(r'^admin/', include(admin.site.urls)),
    
)
```
>   url(r'^DemoAppPoll/', include('DemoAppPoll.urls')),就是我们新增的.

>    表示,我们使用DemoAppPoll.urls来处理http://localhost:8080/DemoAppPoll/的请求.

>    在DemoAppPoll.urls里,我们使用了绑定了views.index来处理请求.


