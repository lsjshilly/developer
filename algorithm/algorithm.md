

## 数据结构

### 栈

﻿线性表，右为头左为尾，上为顶下为底。

栈（stack）是限定仅在表尾进行插入或删除的线性表。其中添加/移除新项总发生在同一端。

这一端通常称为“栈顶”(top，表尾端)。与栈顶对应的端称为“栈底”（bottom，表头端）。 

栈的底部很重要，因为在栈中靠近底部的项是存储时间最长的。最近添加的项是最先移除的。 

这种排序原则有时被称为** LIFO( Last In First Out，即后进先出)**。 

可以把栈理解为在桌子上，把书一本本叠起来。拿起一本书放在书堆的最上面，当然也只有先拿走上面的书才能拿走下面的书。

**栈的基本操作**

- Stack() 创建一个空的新栈。 它不需要参数，并返回一个空栈。
- push(item)：在栈的最上方插入元素
- pop()：返回栈最上方的元素，并将其删除
- isEmpty()：查询栈是否为空
- top()，或者称为 peek()：返回栈最上方的元素，并不删除
- size()，返回 item 数量。

### 队列

队列（queue）是一种先进先出的（FIFO，First In First Out）线性表。只允许在表的一端插入而在另一端删除。
其中允许插入的一端称为队尾(rear)，允许删除的一端称为队头（front）。
当一个元素从队尾进入队列时，一直向队头移动，直到它成为下一个需要移除的元素为止。

**队列的基本操作**

- Queue() 创建一个空的新队列。 它不需要参数，并返回一个空队列。
- enqueue(item) 将新项添加到队尾。 它需要 item 作为参数，并不返回任何内容。
- dequeue() 从队头移除项。它不需要参数并返回 item。 队列被修改。
- isEmpty() 查看队列是否为空。它不需要参数，并返回布尔值。
- size() 返回队列中的项数。它不需要参数，并返回一个整数。

**双端队列**

双端队列（deque）是限定插入和删除操作在表的两端的线性表。它的两个端点（首部和尾部）都可以进行添加和删除操作。  
在某种意义上，这种混合线性结构提供了单个数据结构中的栈和队列的所有能力。但在实际应用中远不及栈和队列有用。

**双端队列的基本操作**

- Deque() 创建一个空的新 deque。它不需要参数，并返回空的 deque。
- addFront(item) 将一个新项添加到 deque 的首部。它需要 item 参数 并不返回任何内容。
- addRear(item) 将一个新项添加到 deque 的尾部。它需要 item 参数并不返回任何内容。
- removeFront() 从 deque 中删除首项。它不需要参数并返回 item。deque 被修改。
- removeRear() 从 deque 中删除尾项。它不需要参数并返回 item。deque 被修改。
- isEmpty() 测试 deque 是否为空。它不需要参数，并返回布尔值。
- size() 返回 deque 中的项数。它不需要参数，并返回一个整数。

**[循环队列](https://www.cnblogs.com/curo0119/p/8608606.html)**

在用数组实现队列的时候，当有元素出列，头指针front就向后移动，此时队列前面的空间就空了出来。
每当添加元素，尾指针rear+1，当尾指针rear移动到LENGTH时（数组的最大下标处的地址），再入队会发生假溢出。
也就是说实际上我们开辟的数组还有剩余空间，却因为rear越界表现为溢出。  
为了更合理的利用空间，将队列的首尾相连接。这样当rear移动到LENGTH时，会再从0开始循环。
那当什么时候队列满呢？当rear等于front的时候，无法判断队列为空还是满。有两个方法：  
办法一是设置一个标志变量flag，当front == rear,且flag = 0时为队列空，当front == rear,且flag= 1时为队列满。  
办法二牺牲一个存储空间，front前面不存数据，当rear在front前面的时候就是满了。

**循环队列的基本操作**

- LoopQueue(size) 创建一个空的新队列，size用于指定循环队列的大小，不输入参数size使用默认值。
- enqueue(item) 将新项添加到队尾。 它需要 item 作为参数，并不返回任何内容。
- dequeue() 从队头移除项。它不需要参数并返回 item。 队列被修改。
- isEmpty() 查看队列是否为空。它不需要参数，并返回布尔值。
- size() 或者 \_\_len\_\_() 返回队列中的项数。它不需要参数，并返回一个整数。

**队空与队满**

队空条件为：front==rear
队满条件为：(rear+1)%QueueSize==front

### 链表

**单链表**

- ist() 创建一个新的空单链表，无返回值。
- add(item) 在链表头部插入元素，需要item作为参数，无返回值。
- append(item) 在链表尾部添加元素，需要item作为参数，无返回值。
- insert(pos, item) 在指定位置 pos 插入元素 item。无返回值。
- remove(item) 删除节点值等于 item 的节点。一般无返回值。若没有该值，返回 -1，表示出错。
- search(item) 查找节点是否存在，返回布尔值。空列表返回False。
- isEmpty() 链表是否为空，返回布尔值
- size() 或者 \_\_len\_\_()，返回链表元素个数。
- traverse() 遍历整个链表，无返回值。

**循环链表**

循环链表(circular linked list)是另一种形式的链式存储结构，
它与单链表不同在于表中最后一个指针域指向头节点。整个链表形成一个环。

**双向链表**

单向链表只能顺指针往后寻找其他节点。若要寻查节点的直接前趋，则需要从表头指针出发。
为克服单链表的这种单向性的缺点，可利用双向链表（double linked list）。  
双向链表的节点中有两个指针域，其一指向直接后继，另一指向直接前趋。

### [树](https://blog.csdn.net/g360z247j123/article/details/51858563)

树的递归定义如下:
一棵树是一些节点的集合。这个集合可以为空集或非空集；
若树非空，则它由称为根(root)的节点r以及0个或多个非空的(子)树T1，T2，…Tk组成，
这些子树中每一棵树都被来自根r的一条有向的边(edge)所连接。 

####二叉树
二叉树（Binary Tree）是另一种树形结构，它的特点是每个结点至多只有两颗子树（即二叉树中不存在度大于二的节点）。
并且，二叉树的子树有左右之分，其次序不能任意颠倒。

[二叉树的分类](https://www.cnblogs.com/sunshineliulu/p/7775063.html)

- 二叉搜索树
- 平衡二叉树（AVL）

[轻松搞定面试中的二叉树题目](https://blog.csdn.net/luckyxiaoqiang/article/details/7518888)

### 红黑树

红黑树是每个节点都带有颜色属性的二叉查找树，颜色或红色或黑色。在二叉查找树强制一般要求以外，对于任何有效的红黑树我们增加了如下的额外要求:

性质1. 节点是红色或黑色。

性质2. 根节点是黑色。

性质3 每个红色节点的两个子节点都是黑色。(从每个叶子到根的所有路径上不能有两个连续的红色节点)

性质4. 从任一节点到其每个叶子的所有路径都包含相同数目的黑色节点。

这些约束强制了红黑树的关键性质:  从根到叶子的最长的可能路径不多于最短的可能路径的两倍长。结果是这个树大致上是平衡的。因为操作比如插入、删除和查找某个值的最坏情况时间都要求与树的高度成比例，这个在高度上的理论上限允许红黑树在最坏情况下都是高效的，而不同于普通的二叉查找树。

要知道为什么这些特性确保了这个结果，注意到性质3导致了路径不能有两个毗连的红色节点就足够了。最短的可能路径都是黑色节点，最长的可能路径有交替的红色和黑色节点。因为根据性质4所有最长的路径都有相同数目的黑色节点，这就表明了没有路径能多于任何其他路径的两倍长。

## 排序

### 插入排序

```C++
void insert(int *arr, int len)
{
	int i, j, t;
	for (i = 1; i < len; ++i)
	{
		t = arr[i];
		for (j = i - 1; j >= 0 && t < arr[j]; --j)
			arr[j + 1] = arr[j];
		arr[j + 1] = t;
	}
}
```

### 冒泡排序

```C++
void bubble(int *arr, int len)
{
	int t;
	for (int i = 0; i < len - 1; ++i)
		for (int j = 0; j < len - i - 1; ++j)
			if (arr[j] > arr[j + 1])
				t = arr[j], arr[j] = arr[j + 1], arr[j + 1] = t;
}
```

### 选择排序

```C++
void select(int *arr, int len)
{
	int i, j, k, t;
	for (i = 0; i < len - 1; ++i)
	{
		k = i;
		for (j = i + 1; j < len; j++)
			if (arr[j] < arr[k])
				k = j;
		if (k != i)
			t = arr[i], arr[i] = arr[k], arr[k] = t;
	}
}
```



### 快速排序

```C++
int partition(int *arr, int low, int high)
{
	int key = arr[low];
	while (low < high) {
		while (low < high && arr[high] >= key)
			high--;
		if (low < high)
			arr[low++] = arr[high];
		while (low < high && arr[low] <= key)
			low++;
		if (low < high)
			arr[high--] = arr[low];
	}
	arr[low] = key;
	return low;
}

void quick(int *arr, int start, int end)
{
	int pos;
	if (start < end)
	{
		pos = partition(arr, start, end);
		quick(arr, start, pos - 1);
		quick(arr, pos + 1, end);
	}
}
```

### 归并排序

```C++
void Merge(int *arr, int low, int mid, int high)
{
	int i, k;
	int *tmp = (int *)malloc((high - low + 1) * sizeof(int));
	int left_low = low, left_high = mid;
	int right_low = mid + 1, right_high = high;
	for (k = 0; left_low <= left_high && right_low <= right_high; k++)
		if (arr[left_low] <= arr[right_low])
			tmp[k] = arr[left_low++];
		else
			tmp[k] = arr[right_low++];
	if (left_low <= left_high)
		for (i = left_low; i <= left_high; i++)
			tmp[k++] = arr[i];
	if (right_low <= right_high)
		for (i = right_low; i <= right_high; i++)
			tmp[k++] = arr[i];
	for (i = 0; i<high - low + 1; i++)
		arr[low + i] = tmp[i];
	free(tmp);
}

void Merge_sort(int *arr, unsigned int first, unsigned int last)
{
	int mid = 0;
	if (first < last)
	{
		mid = (first + last) / 2;
		Merge_sort(arr, first, mid);
		Merge_sort(arr, mid + 1, last);
		Merge(arr, first, mid, last);
	}
}
```



## 基础操作

### 位运算交换两个数

```C++
void swap(int &x, int &y)
{
	x ^= y;
	y ^= x;
	x ^= y;
}
```



## 字符串库函数实现

### 交换两个字符串

```
// 引用符号 & 去掉就不能交换了，用引用指针代表传的指针是实参而不是形参，s1, s2便不是一个临时的拷贝。
void swap(char *&s1, char *&s2)  
{
	char *tmp;
	tmp = s1;
	s1 = s2;
	s2 = tmp;
}

int main(int argc, char* argv[]) {
	char * s1 = "hello ";
	char * s2 = "world ";
	cout << s1 << s2 << endl;
	swap(s1, s2);
	cout << s1 << s2 << endl;
	system("pause");
}
/* 打印
hello world
world hello
*/
```

### 将数字转化为字符串

```C++
void int2str(int n, char *str)
{
	int num = n > 0 ? n : -n;
	if (str == nullptr)
		return;

	char buf[10] = " ";
	int i = 0, j = 0;
	while(num)
	{
		buf[i++] = num % 10 + '0';
		num /= 10;
	}
	
	int len = n > 0 ? i : ++i;
	str[len] = '\0';
	if (n < 0)
	{
		j = 1;
		str[0] = '-';
	}

	for (; j < len; ++j)
	{
		str[j] = buf[len - 1 - j];
	}
}
```

### 将字符串转换为数字

```C++
int str2int(const char *str)
{
	int tmp = 0;
	const char *ptr = str;
	if (*ptr == '-' || *ptr == '+')
	{
		++ptr;
	}

	while (*ptr != '\0')
	{
		if (*ptr < '0' || *ptr > '9')
		{
			break;
		}
		tmp = tmp * 10 + *ptr - '0';
		++ptr;
	}
	ptr = str;  // 重新让 ptr 指向字符数组的首地址 
	if (*ptr == '-')
		tmp = -tmp;
	return tmp;
}
```

### 实现字符串赋值函数 strcpy

```C++
char *strcpy(char *strDst, char *strSrc)  // 返回 char* 的目的是可以链式使用
{
	if (strDst == nullptr || strSrc == nullptr)
		return nullptr;

	char *strDstCopy = strDst;
	while ((*strDst++ = *strSrc++) != '\0');
	return strDstCopy;
}
```

### 实现计算字符串长度的函数 strlen

```C++
int myStrlen(const char *str)
{
	assert(str != nullptr);			// 需要头文件 #include <assert.h>
	//if (str == nullptr) return 0;
	const char *p = str;
	while (*str++ != '\0');
	return str - p - 1;
}
```

### 实现字符串中子串的查找函数 strstr

[leetcode 28 实现 strStr()](https://leetcode-cn.com/problems/implement-strstr)

给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。

```C++
// 返回索引的形式：例如 haystack:“abcde”，needle:”bcd“，返回 1
int strStr(string haystack, string needle) {
        if (!needle.size())
            return 0;
        if (!haystack.size())
            return -1;
        
        int i = 0, j = 0;
    
    	// haystack.size() - needle.size() + 1是无符号整型，
        // 有符号与无符号比较，自动把有符号转换成无符号
        while (i < int(haystack.size() - needle.size() + 1))
        {
            while (j  < needle.size())
            {
                if (haystack[i] != needle[j])
                {
                    i = i - j + 1;
                    j = 0;
                    break;
                }
                else
                {
                    ++i;
                    ++j;  
                }
            }
            if (j == needle.size())
            return i - j;  
        }
        return -1;
    }
```

```C++
// 返回指针的形式:例如 src:"abcdef"，sub:"cde"，
// 那么 strstr(src, sub) 会返回 src 中的字符 'c' 的地址，打印出来就是 "cdef"
// 如果想得到偏移量（索引），让 strstr 的返回值减去 src 的首地址。
const char *strstr(const char *src, const char* sub)
{
	if (src == nullptr || sub == nullptr) 
		return src;
	const char *psrc, *psrcCopy = src;
	const char *psub;

	while (*src)
	{
		psrc = src;
		psub = sub;
		do
		{
			if (!*psub)
				return src;
		} while (*psub++ == *psrc++);
		src += 1;
	}
	return psrcCopy;
}
```

### 实现字符串比较函数 strcmp

```C++
int myStrcmp(const char *src, const char *dst)
{
	if (src != nullptr && dst == nullptr)
		return *src;
	else if (src == nullptr && dst == nullptr)
		return 0;
	else if (src == nullptr && dst != nullptr)
		return -*dst;

	while (*src && *dst && *src == *dst)
	{
		src++;
		dst++;
	}
	return *src - *dst;
}
```

### 实现字符串连接函数 strcat

```C++
char *myStrcat(char *dst, char *src)
{
	assert(src != nullptr && dst != nullptr);	// src 与 dst 非空
	assert(dst != src);							// 不能让一个字符串与其本身连接

	char *dstCopy = dst;
	while (*dst)
		dst++;
	while (*dst++ = *src++);
	return dstCopy;
}
```

### 字符串中各单词反转，而单词内部结构不变

例子：将` ”I am from Shanghai“ `转换为 `”Shanghai from an I“`。

思路：字符指针 start 指向单词首位，字符指针 end 指向空格的前一位，对 start 和 end 区间的单词反转。则原单词为转换为 `”I ma morf iahgnahs“`，再对整个字符串进行反转。