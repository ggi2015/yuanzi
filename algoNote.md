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

静态链表：用数组描述的链表  
```C
/*
*通常把数组建立得大一些，以便有空闲空间便于插入不至于溢出
*线性表的静态链表存储结构
*第一个元素和最后一个元素不存数据，第一个游标存备用链表的第一个节点下标，最后一个游标存第一个有数值的元素的下标，相当于单链表中头结点作用;(pic/DS3-12-2.png)
*/
#define MAXSIZE 1000 //假设链表最大长度1000
typedef struct
{
   ElemType data;
   int cur; //游标，为0时表示无指向
} Component,StaticLinkList[MAXSIZE];
```  

```C
/*
*将一维数组space中各分量链成一备用链表
*spac[0].cur为头指针，“0”表示空指针
*/
Status InitList(StaticLinkList space)
{
//TODO
}
```  

```C
/*
*若备用空间链表非空，则返回分配的结点下标，否则返回0
*/
Status Malloc_SLL(StaticLinkList space)
{
//TODO
}
```   

```C
/*
*在L中第i个元素之前插入新的元素e
*/
Status ListInsert(StaticLinkList L, int i, ElemType e)
{
//TODO
}
``` 

```C
/*
*删除在L中的第i个数据元素e
*/
Status ListDelete(StaticLinkList space, int i)
{
//TODO
}
```   

```C
/*
*将下标为k的空闲结点回收到备用链表
*/
Status Free_SSL(StaticLinkList space, int k)
{
//TODO
}
```   

```C
/*
*初始条件：静态链表已存在。操作结果：返回L中数据元素个数
*/
Status ListLength(StaticLinkList L)
{
//TODO
}
```   
静态链表优缺点  

### 循环链表
将单链表中终端结点的指针端由空指针改为指向头结点，就使整个单链表形成一个环，这种头尾相接的单链表称为单循环链表，简称循环链表。  

### 双向链表  
单链表的每个结点中，在设置一个指向其前驱结点的指针域。每个结点两个指针域，一个指向直接后继，另一个指向直接前驱；  
```C
/*
*线性表的双向链表存储结构
*/
typedef struct DulNode
{
   ElemType data;
   struct DulNode *prior;  //直接前驱指针
   struct DulNode *next;   //直接后继指针
} DulNode, *DuLinkList;
```  

### 总结  
|线性表     |          |       |      |       |  
|----      |----      |----   |----  |----   |
|顺序存储结构|链式存储结构|       |      |       | 
|          |单链表     |静态链表|循环链表|双向链表|  


## 栈与队列  
栈：限定仅在表尾进行插入和删除操作的 - 线性表 -  
队列：只允许在一端进行插入操作、而在另一端进行删除操作的线性表  

### 栈
栈顶（top）：允许插入删除的一端，另一端：栈底；  
LIFO  
3个元素，5种可能的出栈次序；  

```C
ADT Stack
Data
    元素具有相同的类型，相邻元素具有前驱和后继关系
Operation
   InitStack(*S):初始化操作，建立一个空栈S。
   DestroyStack(*S):若栈存在，则销毁它。
   ClearStack(*S):将栈清空。
   StackEmpty(S):若栈为空，返回true， 否则返回false。
   GetTop(S, *e):若栈存在且非空，用e返回S的栈顶元素。
   Push(*S, e):若栈S存在，插入新元素e到栈S中并成为栈顶元素。
   Pop(*S, *e):删除栈S中栈顶元素，并用e返回其值。
   StackLength(S):返回栈S的元素个数。
endADT  
```    
#### 栈的顺序存储结构及其实现
栈空top=-1，栈满top=MAXSIZE-1 
```C
/*
*栈的结构定义
*/
typedef int SElemType; //SElemType类型根据实际情况而定，这里假设为int
typedef struct
{
   SElemType data[MAXSIZE];
   int top; //用于栈顶指针
}SqStack
```  

```C
/*
* 进栈操作，插入元素e为新的栈顶元素
*/
Status Push(SqStack *S, SElemType e)
{
   //TODO
}
```

```C
/*
* 出栈操作；若栈不为空，则删除S的栈顶元素，用e返回其值，并返回OK；否则返回ERROR
*/
Status Pop(SqStack *S, SElemType *e)
{
   //TODO
}
```
#### 两栈共享空间  
```C
/*
* 两栈共享空间结构
*/
typedef struct
{
   SElemType data[MAXSIZE];
   int top1;   //栈1栈顶指针
   int top2;   //栈2栈顶指针
}SqDoubleStack;

//插入元素e为新的栈顶元素
Status Push(SqDoubleStack *S, SElemType e, int stackNumber)
{
   //TODO
}

//若栈不空，则删除S的栈顶元素，用e返回其值，并返回OK；否则返回ERROR
Status Pop(SqDoubleStack *S, SElemType *e, int stackNumber)
{
   //TODO
}
```  

#### 栈的链式存储结构及其实现  
空栈top=NULL，基本不存在栈满  
```C
/*
*结构代码
*/
typedef struct StackNode
{
   SElemType data;
   struct StackNode *next;
}StackNode, *LinkStackPtr;

typedef struct LinkStack
{
   LinkStackPtr top;
   int count ;
}LinkStack;
```  

```C
/*
* 进栈操作，插入元素e为新的栈顶元素
*/
Status Push(LinkStack *S, SElemType e)
{
   //TODO
}
```

```C
/*
* 出栈操作；若栈不为空，则删除S的栈顶元素，用e返回其值，并返回OK；否则返回ERROR
*/
Status Pop(LinkStack *S, SElemType *e)
{
   //TODO
}
```
顺序栈/链栈的Push/Pop操作，时间复杂度均为O(1)；  
栈的使用过程中，元素变化不可预料，时大时小，最好用链栈；反之，变化在可控范围，建议顺序栈；  

#### 栈的应用
1. 递归  
斐波那契数列实现：
定义：把一个直接调用自己或者通过一系列的调用语句间接调用自己的函数，称为递归函数  
递归函数必须要有终止条件，否则陷入无尽循环

2. 四则运算表达式求值  
逆波兰表达法：所有运算符都是要在运算数字的后面出现；  
从左到右遍历表达式，遇到数字进栈，遇到符号，将处于栈顶的两个数字出栈，进行运算，结果入栈，直到最后；  

### 队列
定义：一端插入，另一端删除的线性表。FIFO  
```C
ADT Queue
Data
   元素具有相同的类型，相邻元素具有前驱和后继关系。
Operation
   InitQueue(*Q);初始化操作，建立一个空队列Q
   DestroyQueue(*Q):若队列存在，则销毁它
   ClearQueue(*Q):将对列清空
   QueueEmpty(Q):若队列Q为空，返回true，否则返回false
   GetHead(Q, *e):若队列存在且非空，用e返回队列Q的对头元素
   EnHead(*Q, e):若队列存在，插入新元素e到队列Q中并成为Q的对头元素
   DeQueue(*Q, *e):删除队列Q中对头元素，并用e返回其值
   QueueLength(Q):返回队列Q的元素个数
endADT
```
#### 循环队列  
队列顺序存储不足：对头离开，后面的人都得往前挪一步；引入front和rear指针，假溢出  
定义：头尾相接的顺序存储结构称为循环队列  
判满：设置标志位；或者当front与rear相隔一个时，我们就认为满  
通用的计算队列长度公式：**(rear-front+QueueSize)%QueueSize**  
```C
/*
*循环队列的顺序存储结构
*/
typedef int QElemType; //QElemType 类型根据实际情况而定
typedef struct
{
   QElemType data[MAXSIZE];
   int front;  //头指针
   int rear;   //尾指针，若对列不为空，指向队列尾元素的下一个位置
}SqQueue;
```
```C
/*
*初始化一个空队列Q
*/
Status InitQueue(SqQueue *Q)
{
   //TODO
}
```
```C
/*
*循环队列求队列长度，返回Q的元素个数，也就是队列的当前长度
*/
int QueueLength(SqQueue Q)
{
   //TODO
}
```
```C
/*
*循环队列入队操作，若队列未满，则插入元素e为Q新的队尾元素
*/
Status EnQueue(SqQueue *Q， QElemType e)
{
   //TODO
}
```
```C
/*
*循环队列出队操作，若对列不为空，则删除Q中对头元素，用e返回其值
*/
Status DeQueue(SqQueue *Q, QElemType *e)
{
   //TODO
}
```

#### 队列的链式存储结构及其实现  
队列的链式存储结构，其实就是线性表的单链表，只不过只能尾进头出，简称链队列  
```C
/*
*链队列结构
*/
typedef int QElemType;  //QElemType类型根据实际情况而定，这里假设为int
typedef struct QNode //结点结构
{
   QElemType data;
   struct QNode  *next;
}QNode, *QueuePtr;
typedef struct //队列的链表结构
{
   QueuePtr front, rear;   //对头、队尾指针
}LinkQueue;
```
```C
/*
*队列链式存储的入队操作，插入元素e为Q新的队尾元素
*/
Status EnQueue(LinkQueue *Q， QElemType e)
{
   //TODO
}
```
```C
/*
*队列链式存储的出队操作，若对列不为空，则删除Q中对头元素，用e返回其值，并返回OK，否则返回ERROR
*/
Status DeQueue(SqQueue *Q, QElemType *e)
{
   //TODO
}
```
循环队列与链队列基本操作都是时间常数，都为O(1);循环队列是事先申请好空间，使用期间不释放，链队列，每次申请 和释放结点存在时间开销；故若出入队频繁，两者还是有区别；但链队列无空间浪费一说；  
在队列长度最大值确定的情况下，建议循环队列；无法预估队列长度，链队列  

### 总结回顾
|栈  |队列  |
|--- |---  |
|顺序栈|顺序队列|
|- 两栈共享空间|- 循环队列|
|链栈 |链队列|



