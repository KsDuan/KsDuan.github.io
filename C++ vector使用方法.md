# C++ vector使用方法

2021-02-26 10:50 更新

#### 在 c++ 中，vector 是一个十分有用的容器。它能够像容器一样存放各种类型的对象，简单地说，vector是一个能够存放任意类型的动态数组，能够增加和压缩数据。 C++ 中数组很坑，有没有类似 Python 中 list 的数据类型呢？类似的就是 vector！vector 是同一种类型的对象的集合，每个对象都有一个对应的整数索引值。和 string 对象一样，标准库将负责管理与存储元素相关的内存。我们把 vector 称为容器，是因为它可以包含其他对象。一个容器中的所有对象都必须是同一种类型的。

## 一、什么是vector？

向量（Vector）是一个封装了动态大小数组的顺序容器（Sequence Container）。跟任意其它类型容器一样，它能够存放各种类型的对象。可以简单的认为，向量是一个能够存放任意类型的动态数组。

## 二、容器特性

### 1.顺序序列

顺序容器中的元素按照严格的线性顺序排序。可以通过元素在序列中的位置访问对应的元素。

### 2.动态数组

支持对序列中的任意元素进行快速直接访问，甚至可以通过指针算述进行该操作。操供了在序列末尾相对快速地添加/删除元素的操作。

### 3.能够感知内存分配器的（Allocator-aware）

容器使用一个内存分配器对象来动态地处理它的存储需求。

## 三、基本函数实现

### 1.构造函数

- `vector()`:创建一个空vector
- `vector(int nSize)`:创建一个vector,元素个数为nSize
- `vector(int nSize,const t& t)`:创建一个vector，元素个数为nSize,且值均为t
- `vector(const vector&)`:复制构造函数
- `vector(begin,end)`:复制[begin,end)区间内另一个数组的元素到vector中

### 2.增加函数

- `void push_back(const T& x)`:向量尾部增加一个元素X
- `iterator insert(iterator it,const T& x)`:向量中迭代器指向元素前增加一个元素x
- `iterator insert(iterator it,int n,const T& x)`:向量中迭代器指向元素前增加n个相同的元素x
- `iterator insert(iterator it,const_iterator first,const_iterator last)`:向量中迭代器指向元素前插入另一个相同类型向量的[first,last)间的数据

### 3.删除函数

- `iterator erase(iterator it)`:删除向量中迭代器指向元素
- `iterator erase(iterator first,iterator last)`:删除向量中[first,last)中元素
- `void pop_back()`:删除向量中最后一个元素
- `void clear()`:清空向量中所有元素

### 4.遍历函数

- `reference at(int pos)`:返回pos位置元素的引用
- `reference front()`:返回首元素的引用
- `reference back()`:返回尾元素的引用
- `iterator begin()`:返回向量头指针，指向第一个元素
- `iterator end()`:返回向量尾指针，指向向量最后一个元素的下一个位置
- `reverse_iterator rbegin()`:反向迭代器，指向最后一个元素
- `reverse_iterator rend()`:反向迭代器，指向第一个元素之前的位置

### 5.判断函数

- `bool empty() const`:判断向量是否为空，若为空，则向量中无元素

### 6.大小函数

- `int size() const`:返回向量中元素的个数
- `int capacity() const`:返回当前向量所能容纳的最大元素值
- `int max_size() const`:返回最大可允许的 vector 元素数量值

### 7.其他函数

- `void swap(vector&)`:交换两个同类型向量的数据
- `void assign(int n,const T& x)`:设置向量中前n个元素的值为x
- `void assign(const_iterator first,const_iterator last)`:向量中[first,last)中元素设置成当前向量元素

### 8.看着清楚

> 1.push_back 在数组的最后添加一个数据
>
> 2.pop_back 去掉数组的最后一个数据
>
> 3.at 得到编号位置的数据
>
> 4.begin 得到数组头的指针
>
> 5.end 得到数组的最后一个单元+1的指针
>
> 6．front 得到数组头的引用
>
> 7.back 得到数组的最后一个单元的引用
>
> 8.max_size 得到vector最大可以是多大
>
> 9.capacity 当前vector分配的大小
>
> 10.size 当前使用数据的大小
>
> 11.resize 改变当前使用数据的大小，如果它比当前使用的大，者填充默认值1
>
> 2.reserve 改变当前vecotr所分配空间的大小
>
> 13.erase 删除指针指向的数据项
>
> 14.clear 清空当前的vector
>
> 15.rbegin 将vector反转后的开始指针返回(其实就是原来的end-1)
>
> 16.rend 将vector反转构的结束指针返回(其实就是原来的begin-1)
>
> 17.empty 判断vector是否为空
>
> 18.swap 与另一个vector交换数据

## 四、基本用法

```
#include < vector> 
using namespace std;
```

## 五、简单介绍

1. Vector<类型>标识符
2. Vector<类型>标识符(最大容量)
3. Vector<类型>标识符(最大容量,初始所有值)
4. Int i[5]={1,2,3,4,5}Vector<类型>vi(I,i+2);//得到i索引值为3以后的值
5. Vector< vector< int> >v; 二维向量//这里最外的<>要有空格。否则在比较旧的编译器下无法通过



## 六、vector使用实例

**使用vector注意事项：**

1、如果你要表示的向量长度较长（需要为向量内部保存很多数），容易导致内存泄漏，而且效率会很低；

2、Vector 作为函数的参数或者返回值时，需要注意它的写法：

```
double Distance(vector<int>&a, vector<int>&b)
```

 其中的“&”绝对不能少！！！

# vector对象的定义和初始化

同样的，使用前，导入头文件 #include 可以使用using声明：using std::vector;vector 是一个类模板（class template）。使用模板可以编写一个类定义或函数定义，而用于多个不同的数据类型。因此，我们可以定义保存 string 对象的 vector，或保存 int 值的 vector，又或是保存自定义的类类型对象（如 Sales_items 对象）的 vector。
声明从类模板产生的某种类型的对象，需要提供附加信息，信息的种类取决于模板。以 vector 为例，必须说明 vector 保存何种对象的类型，通过将类型放在类型放在类模板名称后面的尖括号中来指定类型：

| vector<T> v1;       | 保存类型为 T 对象。默认构造函数 v1 为空。 |
| ------------------- | ----------------------------------------- |
| vector<T> v2(v1);   | v2 是 v1 的一个副本。                     |
| vector<T> v3(n, i); | v3 包含 n 个值为 i 的元素。               |
| vector<T> v4(n);    | v4 含有值初始化的元素的 n 个副本。        |

【注意：1、若要创建非空的 vector 对象，必须给出初始化元素的值；2、当把一个 vector 对象复制到另一个 vector 对象时，新复制的 vector 中每一个元素都初始化为原 vectors 中相应元素的副本。但这两个 vector 对象必须保存同一种元素类型；3、可以用元素个数和元素值对 vector 对象进行初始化。构造函数用元素个数来决定 vector 对象保存元素的
个数，元素值指定每个元素的初始值】

## vector对象动态增长：

vector 对象（以及其他标准库容器对象）的重要属性就在于可以在运行时高效地添加元素。

> 注意：因为 vector 增长的效率高，在元素值已知的情况下，最好是动态地添加元素。

**实例：**

vector<int>test;//建立一个vector，int为数组元素的数据类型，test为动态数组名

简单的使用方法如下：

```
vector<int>test;//建立一个vector
test.push_back(1);
test.push_back(2);//把1和2压入vector，这样test[0]就是1,test[1]就是2
```

实例：

```
vector<vector<Point2f> > points; //定义一个二维数组
points[0].size();  //指第一行的列数
```



**1 、基本操作**

(1)头文件`#include<vector>`.

(2)创建vector对象，`vector<int> vec`;

(3)尾部插入数字：`vec.push_back(a)`;

(4)使用下标访问元素，`cout<<vec[0]<<endl`;记住下标是从0开始的。

(5)使用迭代器访问元素.

```
vector<int>::iterator it;
for(it=vec.begin();it!=vec.end();it++)
    cout<<*it<<endl;
```

(6)插入元素：`vec.insert(vec.begin()+i,a)`; 在第i+1个元素前面插入a;

(7)删除元素：`vec.erase(vec.begin()+2)` ; 删除第3个元素

`vec.erase(vec.begin()+i,vec.end()+j)`; 删除区间[ i,j-1] 区间从0开始

(8)向量大小: `vec.size()`;

(9)清空: `vec.clear()`;

特别提示：这里有 begin() 与 end() 函数、front() 与 back() 的差别



**2、重要说明**

vector 的元素不仅仅可以是 int,double,string 还可以是结构体，但是要注意：结构体要定义为全局的，否则会出错。

```
#include<stdio.h>  
#include<algorithm>  
#include<vector>  
#include<iostream>  
using namespace std;  
typedef struct rect  
{  
    int id;  
    int length;  
    int width;  
　　//对于向量元素是结构体的，可在结构体内部定义比较函数，下面按照id,length,width升序排序。  
　　bool operator< (const rect &a)  const  
    {  
        if(id!=a.id)  
            return id<a.id;  
        else  
        {  
            if(length!=a.length)  
                return length<a.length;  
            else  
                return width<a.width;  
        }  
    }  
}Rect;  
int main()  
{  
    vector<Rect> vec;  
    Rect rect;  
    rect.id=1;  
    rect.length=2;  
    rect.width=3;  
    vec.push_back(rect);  
    vector<Rect>::iterator it=vec.begin();  
    cout<<(*it).id<<' '<<(*it).length<<' '<<(*it).width<<endl;      
return 0;  
}  
```



**3、算法**

(1) 使用reverse将元素翻转：需要头文件 #include<algorithm>

reverse(vec.begin(),vec.end());将元素翻转，即逆序排列！

(在vecto r中，如果一个函数中需要两个迭代器，一般后一个都不包含)

(2)使用 sort 排序：需要头文件 #include<algorithm>，

sort(vec.begin(),vec.end());(默认是按升序排列,即从小到大).

可以通过重写排序比较函数按照降序比较，如下：

定义排序比较函数：

```
bool Comp(const int &a,const int &b)
{
    return a>b;
}
```

调用时: sort(vec.begin(),vec.end(),Comp)，这样就降序排序。 



**输出Vector的中的元素**  

vector<float> vecClass; 

int nSize = vecClass.size();  

 //打印 vecClass,方法一：  

```
for(int i=0;i<nSize;i++)    
{    
   cout<<vecClass[i]<<"     ";    
}    
   cout<<endl;   
```

需要注意的是：以方法一进行输出时，数组的下表必须保证是整数。

 //打印 vecClass,方法二：   

```
for(int i=0;i<nSize;i++)    
{    
   cout<<vecClass.at(i)<<"     ";    
}    
   cout<<endl;    
```

//打印 vecClass,方法三：输出某一指定的数值时不方便

```
for(vector<float>::iterator it = vecClass.begin();it!=vecClass.end();it++)    
{    
    cout<<*it<<"   ";    
}    
    cout<<endl;    
```



**二维数组的使用：**

```c++
#include "stdafx.h"  
#include <cv.h>  
#include <vector>   
#include <iostream>   
using namespace std;  
int main()  
{  
    using namespace std;  
    int out[3][2] = { 1, 2,   
             3, 4,  
            5, 6 };  
    vector <int*> v1;  
    v1.push_back(out[0]);  
    v1.push_back(out[1]);  
    v1.push_back(out[2]);  
    cout << v1[0][0] << endl;//1  
    cout << v1[0][1] << endl;//2  
    cout << v1[1][0] << endl;//3  
    cout << v1[1][1] << endl;//4  
    cout << v1[2][0] << endl;//5  
    cout << v1[2][1] << endl;//6  
    return 0;  
}  
```