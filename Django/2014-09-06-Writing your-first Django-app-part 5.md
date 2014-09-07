# Writing your-first Django-app-part 5 -test


## 确认bug
如果传入一个未来的时间,那么was_published_recently()会返回什么?

```python
D:\desktop\todoList\Django\mDjango\demoSite>python manage.py shell
Python 2.7.6 (default, Nov 10 2013, 19:24:18) [MSC v.1500 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> import datetime
>>> from django.utils import timezone
>>> from DemoAppPoll.models import Question
>>> future_question = Question(pub_date=timezone.now()+datetime.timedelta(days=30))
>>> future_question.was_published_recently()
True

```
##写test测试暴露bug
将上述的过程,写成test如下:

***DemoAppPoll/tests.py***

```python
import datetime

from django.test import TestCase
from django.utils import timezone

from DemoAppPoll.models import Question

class QuestionMethodTests(TestCase):
    def test_was_published_recently_with_future_question(self):
        time = timezone.now()+datetime.timedelta(days=30)
        furture_question = Question(pub_date=time)
        self.assertEqual(furture_question.was_published_recently(),False)
```

运行测试:

```python
python manage.py test DemoAppPoll
```

> 1> "python manage.py test DemoAppPoll "从DemoAppPoll(APP)下找tests.

> 2>"**django.test.TestCase**",测试示例,DemoAppPoll作为TestCase参数传入:
```python
class QuestionMethodTests(TestCase):
```

> 3>创建了一个为了测试的特殊的数据库

> 4>assertEqual() 最后来判断.



## 修复bug

***DemoAppPoll/models.py***

```python
def was_published_recently(self):
        now = timezone.now()
        return now-datetime.timedelta(days=1) <=self.pub_date<=now
        #return self.pub_date >= timezone.now() - datetime.timedelta(days=1)
```

> 由原来的单边不等式,改为现在的双边不等式即可.

测试结果:
```python
D:\desktop\todoList\Django\mDjango\demoSite>python manage.py test DemoAppPoll
Creating test database for alias 'default'...
.
----------------------------------------------------------------------
Ran 1 test in 0.318s
OK
Destroying test database for alias 'default'...
```

## 更多测试例子

如果是以前的问题?如果是最近的问题?

***DemoAppPoll/tests.py***
```python
    def test_was_published_rencently_with_old_question(self):
        time = timezone.now()-datetime.timedelta(days=30)
        old_question = Question(pub_date=time)
        self.assertEqual(old_question.was_published_recently(),False)
    def test_was_published_rencently_with_recent_question(self):
        time = timezone.now()-datetime.timedelta(hours=1)
        recent_question=Question(pub_date=time)
        self.assertEqual(recent_question.was_published_recently(),True)
       
```
----



