# Writing your first Django app--part 3


> view : Django应用(作为一个特殊的功能或者有一个特定的模版)里的一种网页.

在DemoAppPoll里,我们下面的view:

* Question index  page  -->展示最新的问题

* Question detail page -->展示一个问题和一个投票表格

* Question result page --> 展示特定问题的投票结果

* Vote action --> 处理特定问题的投票.

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

>    在DemoAppPoll.urls里,我们绑定了views.index来处理请求.

![成功处理请求](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/Django/images/DemoAppPoll-first-app.png)

-----

1. url()参数:regex
python将url请求在工程里urls.py中的pattterns列表中一一匹配.
并且这种匹配不会匹配请求的参数.即http://www.example.com/myapp/?name=zx仅会匹配myapp/

2. url()参数:view
匹配到正则表达式之后,调用特定的view函数.

3. url()参数:kwargs
   任意的关键字参数,可以通过字典传递给特定的view.

4. url()参数:name 
    给url命名,这样就可以全局使用.

----

## 添加更多的view

**DemoAppPoll/urls.py**
```python
from django.conf.urls import patterns,url

from DemoAppPoll import views

urlpatterns = patterns('',
    url(r'^$', views.index, name='index'),
    url(r'^(?P<question_id>\d+)/$', views.detail, name='detail'),
    url(r'^(?P<question_id>\d+)/results/$', views.results, name='results'),
    url(r'^(?P<question_id>\d+)/vote/$', views.vote, name='vote'),
)

```

指定类/方法/函数来处理匹配到url:

> views.index -->处理/DemoAppPoll/

> views.detail-->处理/DemoAppPoll/[number]/

> view.results-->处理/DemoAppPoll/[number]/results/

> views.vote -->处理/DemoAppPoll/[number]/vote/


下面的是类/方法/函数具体如何响应请求的:

**DemoAppPoll/views.py:**

```python
from django.shortcuts import render
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello,urmyfatih.")

def detail(request, question_id):
    return HttpResponse("You're looking at question %s." % question_id)

def results(request, question_id):
    response = "You're looking at the results of question %s."
    return HttpResponse(response % question_id)

def vote(request, question_id):
    return HttpResponse("You're voting on question %s." % question_id)

```
![路径匹配](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/Django/images/DemoAppPoll-url-view.png)

---

当请求http://localhost:8080/DemoAppPoll/33/的时候,

第一步:Django加载项目下的urls.py模块,即(**demoSite.urls**),从demoSite/urls.py中找到代表匹配列表的变量:urlpatterns,从列表中匹配.
```python
 url(r'^DemoAppPoll/', include('DemoAppPoll.urls')),
```

此时,匹配到DemoAppPoll/,

当Django遇到include()的时候,截掉已经匹配到的(DemoAppPoll/),将剩余的(33/)传递到URLconf继续处理.


第二步:Django截掉前面的之后,剩下的(33/),使用**DemoAppPoll.urls**模块(DemoAppPoll/urls.py)来处理.

```python
url(r'^(?P<question_id>\d+)/$', views.detail, name='detail'),
```
此时,匹配到view.detail,

第三步:由view.detail(DemoAppPoll/views.py中detail函数)响应请求.

![include()](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/Django/images/request-url.png)

------