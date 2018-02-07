#PYthon 学习笔记

### 一些基本的语法

 -*- coding: utf-8 -*-  输出为 print u 这样就可以输出中文   
 '\n'代表换行 '\t' 代表制表  
 多行字符可以用r'''dada'''来表示 这样就不用转义了  
 List[]可以理解成数组，并且不要求统一数据类型,append()函数是吧数据放到屁股后面 insert(int index , date x)是把下标为index的换成数据x  
 tuple() 是不能变的  
 if 后面要加:  
 dict 是相当于c++里面的map d = { a:100 } 其中a是key 100是value，len()函数表示里面的对数  
  set([])    
 def是函数定义前面的东西  
 `reduce(函数，list，初始值)` 这是一个函数  
 `filter(函数，list)`就是过滤掉list里面不满足这个函数的东西   
 `sorted(list,函数) return -1` 的排前面  
 `lambda x,y ：return x*y` [这个是代表一个小函数]  
 decorate 装饰器 样例 高级函数的一个简单用法
 ```py
 import time
 def performance(f):
    def fn(*args , **kw):
       t1 = time.time()
       r = f(*args,**kw)
       t2 = time.time()
       print 'call %s() in %fs' % (f.__name__, (t2 - t1))
       return r
    return fn

@performance
def factorial(n):
    return reduce(lambda x,y: x*y, range(1, n+1))

print factorial(10)
```
class 代表一个类 ‘__ ’有这个下标表示是私有成员  
   `__init__`(self,)这个是构造函数吧可以这样理解  
  同样他在继承的时候也和其他语言一样需要对父类也进行初始化
  super(子类，self).`__init__`(参数)
  特殊方法：  
  `__str__(self)` 用于print的用处 例如
  ```py
  class Person(object):
      def __init__(self, name, gender):
          self.name = name
          self.gender = gender

  class Student(Person):
      def __init__(self, name, gender, score):
          super(Student, self).__init__(name, gender)
          self.score = score
      def __str__(self):
          return name + gender
       __repr__ = __str__
  s = Student('Bob', 'male', 88)
  print s
  ```
  就可以直接输出s这个对象了
  `__repr__` 和 `__str__` 则是因为str给用户看 repr是给开发人员看
  对于用户他们需要去print p 而我们如果直接打出 p 则是会出错
  还有就是封装的时候看例子 我们可以写get什么什么的 也可以重载=预算符
  ```py
  class Student(object):

    def __init__(self, name, score):
        self.name = name
        self.__score = score

    @property
    def score(self):
        return self.__score

    @score.setter
    def score(self, score):
        if score < 0 or score > 100:
            raise ValueError('invalid score')
        self.__score = score

    @property
    def grade(self):
        if(self.score >= 80): return 'A'
        if(self.score < 60):    return 'C'
        return 'B'

s = Student('Bob', 59)
print s.grade
s.score = 60
print s.grade
s.score = 99
print s.grade
```
只能说基本语法知识吧
`__slots__` 这个的意思是在一个类中预先申明一下有些什么东西  

>#### 目前知道就这么多语法，舒服了其实也没有太大的不同主要区别在于他的那个高端函数 看起来挺高端的 其实好像也就一个封装的作用舒服了

##要开始实战了 舒服了
