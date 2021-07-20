# Algo

## OOP  
前：提纲，包括其需求；
开始时，关注每项任务的输入输出，需要做什么而不是如何去做；


## Sorting  
按特定顺序（递增、非递减、递减、非递减、lexicographical, etc）对数组（或列表）的项（可以进行比较，例如整数、浮点数、字符串等）进行重新排序。
比较算法优劣的指标：比较次数和数据移动次数；包括三种情况：最好情况（数据已排序），最坏情况（反序），平均情况（数据顺序随机）；  
1. 基本排序算法
   1. 插入排序

   2. 选择排序
   3. 冒泡排序
   4. 梳排序  
2. 决策树  
每个排序算法都可以表示成为一个弧上标有是或否的二叉树，树的非终端节电包含标记的条件或查询，叶子节点的顺序可以是应用该算法的数组的任何顺序，这种类型的树称为决策树。 
不同长度数组需要不同决策树。  



## DS  
ADT：定义了一个数据对象，各数据元素之间的关系，对数据元素的操作；
   体现了程序设计中，问题分解、抽象和信息隐藏的特性；
ADT标准格式：
```C
ADT 抽象数据类型名
Data
   数据元素之间逻辑关系的定义
Operation
   操作1
      初始条件
      操作结果描述
   操作2
      ...
   操作n
      ...
endADT
```  

## Algo
五个基本特性：输入、输出、有穷性、确定性和可行性  
   其他特性：正确、可读、健壮、高效和低存储量  

效率度量方法：  
- 事后统计  
- 事前分析  

渐进增长：n>N,f(n)>g(n),f渐进增长快于g  

关注主项（最高阶项）的阶数  

时间复杂度

一般在没有特殊说明的情况下，都是指最坏时间复杂度。  

### 线性表List
有序且有限  
```C
ADT 线性表(List)
   Data
   数据对象集合 {a1,a2,...,an};.每个元素类型均为 DataType；  
   其中，除第一个元素外，每个元素有且只有一个直接前驱元素；除最后一个元素外，每个元素有且只有一个直接后继元素；数据元素之间的关系是一对一关系；  

   Operation
   InitList (*L) : 初始化操作,建立一个空的线性表L；  
   ListEmpty (L) : 若线性表为空,返回true；否则返回false；  
   ClearList (*L) : 将线性表清空；  
   GetElem (L, i, *e) : 将线性表L中的第i个元素位置值返回给e；  
   LocateElem (L ,e) : 在线性表L中查找与给定e相等的元素,如果查找成功,返回该元素在表中序号表示成功;否则，返回0表示失败；  
   ListInsert (*L， i，e) : 在线性表L中的第i个位置插入新元素e；  
   ListDelete (*L, i, *e) : 删除线性表L中第i个位置元素,并用e返回其值；  
   ListLength (L) : 返回线性表L的元素个数；  
end ADT

```

```C
/*
* 实现两个线性表集合A和B的并集操作；把存在于B中但不存在于A中的数据元素插入到A中；  
*/
void union(List *La, List *Lb)
{
   // TODO
}
```

顺序存储结构  
一维数组实现顺序存储  
```C
//包含三个属性：存储空间起始位置；最大存储容量；当前长度；  
#define MAXSIZE 20
typedef int ElemType;
typedef  struct
{
   ElemType data[MAXSIZE];
   int length;
}SqList;
```
按地址读数据：LOC(ai)=LOC(a1)+(i-1)*c;  
c表示每个元素占用存储空间；  

随机存取结构：存取时间性能为O(1);利用地址存取数据，对每个线性表位置的存入或取出数据，对于计算机都是相同时间；  

顺序存储结构的插入与删除：
```C
Status GetElem(SqList L,int i,ElemType *e)
{
   // TODO
}

Status ListInsert(SqList *L,int i,ElemType e)
{
   // TODO
}

Status ListDelete(SqList *L,int i,ElemType *e)
{
   // TODO
}

插入和删除的时间复杂度  

优缺点  


```

线性表的链式存储结构  
结点（Node）：数据域，指针域；
头结点数据域不存信息；
c.f. 头结点和头指针；  
```C
/*
* 线性表的单链表存储结构
*/
typedef struct Node
{
   ElemType data;
   struct Node* next;
} Node;  
typedef struct Node *LinkList;
```
单链表的读取：  
```C
/*
*初始条件：顺序线性表L已存在，1<=i<=ListLength(L)
*操作结果： 用e返回L中第i个数据元素的值
*/
Status GetElem(SqList L,int i,ElemType *e)
{
   // TODO
}

/*
*初始条件：顺序线性表L已存在，1<=i<=ListLength(L)
*操作结果： 在L中第i个位置之前插入新的数据元素e，L的长度加1
*/
Status ListInsert(SqList *L,int i,ElemType e)
{
   // TODO
}

/*
*初始条件：顺序线性表L已存在，1<=i<=ListLength(L)
*操作结果： 删除L的第i个数据元素，并用e返回其值，L的长度减1
*/
Status ListDelete(SqList *L,int i,ElemType *e)
{
   // TODO
}

/*
*整表创建
*随机产生n个元素的值，建立带表头结点的单链线性表L（头插法）
*/
void CreateListHead(LinkList *L, int n)
{
   // TODO
}
（尾插法）
void CreateListTail(LinkList *L, int n)
{
   // TODO
}

/*
*整表删除
*初始条件：顺序线性表L已存在，操作结果：将L重置为空表
*/
Status ClearList(LinkList *L)
{
   // TODO
}
```

单链表结构与顺序存储结构优缺点  

静态链表  






