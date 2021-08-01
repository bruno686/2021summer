#### linux和windows下统一路径

使用os构建相对路径在windows和linux都可以使用

```python
import os
path = os.path.abspath('项目下面包名/文件名')
```

[<img src="https://z3.ax1x.com/2021/07/25/W2RuK1.png" alt="W2RuK1.png" style="zoom:50%;" />](https://imgtu.com/i/W2RuK1 )  

------

#### 读取文件

```python
f = open(file)
fr = f.read()  #readlines() 读取返回一个列表，每一行是列表的一个元素
f.close()  #不关闭存一份打开的状态在内存中

#有时候会忘掉关闭文件，自动关闭文件
with open(file) as f:
    fr = f.readlines()
    print(fr)
```

#### 列表

------

1.列表的定义

- `list`是**最频繁**的数据类型，在其他语言中叫做**数组**
- 专门用于存储**一串信息**
- 列表用`[]`定义，**数据**之间用`,`分割
- 列表的**索引**从`0`开始

[<img src="https://z3.ax1x.com/2021/07/30/WOOw4J.png" alt="WOOw4J.png" style="zoom: 67%;" />](https://imgtu.com/i/WOOw4J)

#### Numpy

------

> 快速处理任意维度的数组，支持常见的数组和矩阵操作

1.numpy介绍 -数值计算库

- num-numerical 数值化的；py-python
- ndarray；n-任意个，d-dimension，array-数组
- numpy提供了一个**N维数组类型ndarray**，它描述了**相同类型**的“items“集合
- 存储风格：ndarray，存储相同类型，通用性差；list，可以存储不同类型，通用性很强
- ndarray支持并行化运算（向量化运算），c语言编写

1.ndarray属性

```python
import numpy as np
score = np.array([[2,2,2,2,2],[3,3,3,3,3]])

score.shape  #(2, 5)二维数组
score.ndim  #2
score.size  #10
score.dtype  #dtype('int64')

vec = np.array([1,2,3,4,5,6])
vec.shape   #(6,)一维数组
```

默认整数类型是 `int64`

默认小数类型是`float64`

2.ndarray方法

> ndarray.方法()；np.函数名() -> np.array()

2.1生成数组的方法

1. 0和1

```python
np.zeros(shape) -> 既可以用(3, 4)，也可以[3, 4]
np.ones(shape)
```

2. 从现有数组中生成

```
np.array()  np.copy()  深拷贝，当原数组发生改变时，复制后的数组不发生变化
np.asarray()  浅拷贝，当原数组发生改变时，复制后的数组也跟随发生变化
```

3. 生成固定范围的数组

```python
np.linspace(0,10,2)    #array([ 0., 10.]) 2，代表在这个区间等间距两个数
np.arange(0,10,2)  #array([0, 2, 4, 6, 8]) 2，代表在这个区间的数step2
```



#### 面向对象

1.面向过程

1. 面向过程是把每一个需求的所有步骤从头到尾的逐步实现
2. 根据开发需求，将某些**功能独立**的代码**封装**成一个又一个**函数**
3. 最后完成的代码，就是顺序调用**不同函数**

2.面向对象

> 相比较函数，面向对象是更大的封装，根据职责在一个对象中封装多个方法

1. 在对象内部封装不同的方法

3.对象

> 类是抽象的，不能直接使用，**类**相当于制造飞机时的图纸，是一个**模板**，是**负责创建对象**的。对象（飞机）是由类创建出来的一个具体存在，可以直接使用

4.类的设计

大驼峰命名法：每一个单词的**首字母大写**，单词与单词之间没有下划线

5.类的调用

> 由**哪一个对象**调用的方法，方法内的`self`就是**哪一个对象的引用**

- 在类封装的内部，`self`就表示**当前调用方法的对象自己**
- 在调用方法时，程序员不需要传递`self`参数
- 在方法内部
  - 可以通过`self.`**访问对象的属性**
  - 也可以通过`self.`**调用其他的对象方法**

```python
class Cat:
    def eat(self):
        # 哪一个对象调用的方法，self就是哪一个对象的引用！
        print("eat water")
    def drink(self):
        print("drink water")
#创建猫对象
Tom = Cat()#Tom对Cat的对象引用,Cat创建一个对象被Tom引用
Tom.name = "Tom"#增加属性
Tom.eat()
Tom.drink()
```

6.初始化方法

- 当使用了`类名()`创建对象时，会**自动**执行以下操作：
  1. 为对象在内存中**分配空间** --创建对象
  2. 为对象的属性**设置初始值** --初始化方法（init）
- 这个**初始化方法**就是`__init__`方法，`__init__`是对象的**内置方法**

> `__init__`方法是**专门**用来定义一个类**具有哪些属性的方法**！

```python
class Cat:
    def __init__(self):
        print("this is created automatilly")
        self.name = "Tom"  为Cat类定义name属性
```

- 初始化同时设置初始值

```python
class Cat:
    def __init__(self,new_name):
        print("this is created automatilly")
        self.name = new_name  为Cat类定义name属性
        
lazy_cat = Cat("Tom")
```

7.面向对象三大特性

1. **封装** 根据**职责**将**属性**和**方法**封装到一个抽象的**类**中
2. **继承** 实现**代码的重用**，相同的代码不需要重复的编写
3. **多态** 不同的对象调用相同的方法，产生不同的执行结果，**增加代码的灵活度**

#### 继承

1.特点

- **子类**继承自**父类**，可以直接**享受**父类中已经封装好的方法，不需要再次开发
-  **子类**中根据职责，封装**子类特有的属性和方法**

子类=派生类，父类=基类，类继承=类派生

#### 模块

> **模块是python程序架构的一个核心概念**

- 每个以扩展名`py`结尾的`python`源代码文件都是一个**模块**
- 模块名同样也是一个**标识符**，需要符合标识符的命名规则
- 在模块中定义的**全局变量、函数，类**都是提供给外界直接使用的**工具**
- 模块就好比是**工具包**，要想使用这个工具包中的公开，需要先导入这个模块

1.import(as)

[<img src="https://z3.ax1x.com/2021/07/30/WOrAQx.png" alt="WOrAQx.png" style="zoom: 67%;" />](https://imgtu.com/i/WOrAQx)

[<img src="https://z3.ax1x.com/2021/07/30/WOrmwD.png" alt="WOrmwD.png" style="zoom: 67%;" />](https://imgtu.com/i/WOrmwD)

2.from...import 导入

- 如果希望**从某一个模块**中，导入**部分**工具，就可以使用from...import的方式
- import 模块名是**一次性**把模块中**所有工具全部导入**，并且通过**模块名/别名**访问

```python
#从模块导入某一个工具
from 模块名1 import 工具名（全局变量，函数，类之一）
```

- 导入之后**不需要**通过`模块名`，可以直接通过**模块提供的工具--全局变量、函数、类**

```python
from ... import *  可以一次性导入所有工具，并且可以直接使用工具
```

[<img src="https://z3.ax1x.com/2021/07/30/WOcT8H.png" alt="WOcT8H.png" style="zoom:80%;" />](https://imgtu.com/i/WOcT8H)