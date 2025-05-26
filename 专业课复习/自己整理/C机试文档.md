[TOC]



# 一、排序

## 1、冒泡排序（Bubble Sort）

冒泡排序是一种简单的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果它们的顺序错误就把它们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端。 

1.1 算法描述

比较相邻的元素。如果第一个比第二个大，就交换它们两个；
对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对，这样在最后的元素应该会是最大的数；
针对所有的元素重复以上的步骤，除了最后一个；
重复步骤1~3，直到排序完成。
1.2 复杂程度

时间复杂度O(n^2)         空间复杂度O(1)

空间复杂度O(n^2)

1.3 代码实现

```
void BubbleSort(int *arr, int size)  
{  
    int i, j, tmp;  
    for (i = 0; i < size - 1; i++) {  
        for (j = 0; j < size - i - 1; j++) {  
            if (arr[j] > arr[j+1]) {  
                tmp = arr[j];  
                arr[j] = arr[j+1];  
                arr[j+1] = tmp;  
            }  
        }  
    }  
} 
```

 

## 2、选择排序（Selection Sort）

选择排序(Selection-sort)是一种简单直观的排序算法。它的工作原理：首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。 

2.1 算法描述

n个记录的直接选择排序可经过n-1趟直接选择排序得到有序结果。具体算法描述如下：

初始状态：无序区为R[1..n]，有序区为空；
第i趟排序(i=1,2,3…n-1)开始时，当前有序区和无序区分别为R[1..i-1]和R(i..n）。该趟排序从当前无序区中-选出关键字最小的记录 R[k]，将它与无序区的第1个记录R交换，使R[1..i]和R[i+1..n)分别变为记录个数增加1个的新有序区和记录个数减少1个的新无序区；n-1趟结束，数组有序化了。
2.2 复杂程度

时间复杂度O(n^2)         空间复杂度O(1)

空间复杂度O(1)

2.3 代码实现

```
void SelectionSort(int *arr, int size)
{
    int i, j, k, tmp;
    for (i = 0; i < size - 1; i++) {
        k = i;
        for (j = i + 1; j < size; j++) {
            if (arr[j] < arr[k]) {
                k = j;
            }
        }
        tmp = arr[k];
        arr[k] = arr[i];
        arr[i] = tmp;
    }
}
```

## 3、插入排序（Insertion Sort）

插入排序（Insertion-Sort）的算法描述是一种简单直观的排序算法。它的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。

3.1 算法描述

一般来说，插入排序都采用in-place在数组上实现。具体算法描述如下：

从第一个元素开始，该元素可以认为已经被排序；
取出下一个元素，在已经排序的元素序列中从后向前扫描；
如果该元素（已排序）大于新元素，将该元素移到下一位置；
重复步骤3，直到找到已排序的元素小于或者等于新元素的位置；
将新元素插入到该位置后；
重复步骤2~5。
3.2 复杂程度

时间复杂度O(n^2)                 空间复杂度O(1)

3.3 代码实现

```
void InsertionSort(int *arr, int size)    
{    
    int i, j, tmp;    
    for (i = 1; i < size; i++) {    
        if (arr[i] < arr[i-1]) {    
            tmp = arr[i];    
            for (j = i - 1; j >= 0 && arr[j] > tmp; j--) {  
                arr[j+1] = arr[j];    
            }  
            arr[j+1] = tmp;    
        }          
    }    
}    

```

## 4、希尔排序（Shell Sort）

1959年Shell发明，第一个突破O(n^2)的排序算法，是简单插入排序的改进版。它与插入排序的不同之处在于，它会优先比较距离较远的元素。希尔排序又叫缩小增量排序。

4.1 算法描述

先将整个待排序的记录序列分割成为若干子序列分别进行直接插入排序，具体算法描述：

选择一个增量序列t1，t2，…，tk，其中ti>tj，tk=1；
按增量序列个数k，对序列进行k 趟排序；
每趟排序，根据对应的增量ti，将待排序列分割成若干长度为m 的子序列，分别对各子表进行直接插入排序。仅增量因子为1 时，整个序列作为一个表来处理，表长度即为整个序列的长度。
4.2 复杂程度

时间复杂度O(n^1.3)                 空间复杂度O(1)

4.3 代码实现

```
void ShellSort(int *arr, int size)  
{  
    int i, j, tmp, increment;  
    for (increment = size/ 2; increment > 0; increment /= 2) {    
        for (i = increment; i < size; i++) {  
            tmp = arr[i];  
            for (j = i - increment; j >= 0 && tmp < arr[j]; j -= increment) {  
                arr[j + increment] = arr[j];  
            }  
            arr[j + increment] = tmp;
        }  
    }  
}  

```

## 5.归并排序（Merge Sort）

归并排序是建立在归并操作上的一种有效的排序算法。该算法是采用分治法（Divide and Conquer）的一个非常典型的应用。将已有序的子序列合并，得到完全有序的序列；即先使每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，称为2-路归并。 

5.1 算法描述

把长度为n的输入序列分成两个长度为n/2的子序列；
对这两个子序列分别采用归并排序；
将两个排序好的子序列合并成一个最终的排序序列。
5.2 复杂程度

时间复杂度O(nlog2n)                 空间复杂度O(n)

5.3 代码实现

```
#include<stdio.h>
#define ArrLen 20
void printList(int arr[], int len) {
	int i;
	for (i = 0; i < len; i++) {
		printf("%d\t", arr[i]);
	}
}
void merge(int arr[], int start, int mid, int end) {
	int result[ArrLen];
	int k = 0;
	int i = start;
	int j = mid + 1;
	while (i <= mid && j <= end) {
		if (arr[i] < arr[j]){
			result[k++] = arr[i++];
        }
		else{
			result[k++] = arr[j++];
        }
	}
	if (i == mid + 1) {
		while(j <= end)
			result[k++] = arr[j++];
	}
	if (j == end + 1) {
		while (i <= mid)
			result[k++] = arr[i++];
	}
	for (j = 0, i = start ; j < k; i++, j++) {
		arr[i] = result[j];
	}
}
 
void mergeSort(int arr[], int start, int end) {
	if (start >= end)
		return;
	int mid = ( start + end ) / 2;
	mergeSort(arr, start, mid);
	mergeSort(arr, mid + 1, end);
	merge(arr, start, mid, end);
}
 
int main()
{
	int arr[] = {4, 7, 6, 5, 2, 1, 8, 2, 9, 1};
	mergeSort(arr, 0, 9);
	printList(arr, 10);
	system("pause");
	return 0;
}
```

## 6、快速排序（Quick Sort）

快速排序的基本思想：通过一趟排序将待排记录分隔成独立的两部分，其中一部分记录的关键字均比另一部分的关键字小，则可分别对这两部分记录继续进行排序，以达到整个序列有序。

6.1 算法描述

快速排序使用分治法来把一个串（list）分为两个子串（sub-lists）。具体算法描述如下：

从数列中挑出一个元素，称为 “基准”（pivot）；
重新排序数列，所有元素比基准值小的摆放在基准前面，所有元素比基准值大的摆在基准的后面（相同的数可以到任一边）。在这个分区退出之后，该基准就处于数列的中间位置。这个称为分区（partition）操作；
递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数列排序。
6.2 复杂程度

时间复杂度O(nlog2n)                 空间复杂度O(nlog2n)

6.3 代码实现

```
void QuickSort(int *arr, int maxlen, int begin, int end)  
{  
    int i, j;  
    if (begin < end) {  
        i = begin + 1;  
        j = end;        
        while (i < j) {  
            if(arr[i] > arr[begin]) {  
                swap(&arr[i], &arr[j]); 
                j--;  
            } else {  
                i++; 
            }  
        }  
        if (arr[i] >= arr[begin]) {  
            i--;  
        }  
        swap(&arr[begin], &arr[i]);      
        QuickSort(arr, maxlen, begin, i);  
        QuickSort(arr, maxlen, j, end);  
    }  
}  

void swap(int *a, int *b)    
{  
    int temp;  
    temp = *a;  
    *a = *b;  
    *b = temp;  
}  
```

## 7、堆排序（Heap Sort）

堆排序（Heapsort）是指利用堆这种数据结构所设计的一种排序算法。堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点。

7.1 算法描述

将初始待排序关键字序列(R1,R2….Rn)构建成大顶堆，此堆为初始的无序区；
将堆顶元素R[1]与最后一个元素R[n]交换，此时得到新的无序区(R1,R2,……Rn-1)和新的有序区(Rn),且满足R[1,2…n-1]<=R[n]；
由于交换后新的堆顶R[1]可能违反堆的性质，因此需要对当前无序区(R1,R2,……Rn-1)调整为新堆，然后再次将R[1]与无序区最后一个元素交换，得到新的无序区(R1,R2….Rn-2)和新的有序区(Rn-1,Rn)。不断重复此过程直到有序区的元素个数为n-1，则整个排序过程完成。
7.2 复杂程度

时间复杂度O(nlog2n)                 空间复杂度O(1)

7.3 代码实现

```
void Heapify(int *arr, int m, int size)  
{  
    int i, tmp;  
    tmp = arr[m];  
    for (i = 2 * m; i <= size; i *= 2) {  
        if (i + 1 <= size && arr[i] < arr[i+1]) {  
            i++;  
        }  
        if (arr[i] < tmp) {  
            break;  
        }  
        arr[m] = arr[i];  
        m = i;  
    }  
    arr[m] = tmp;  
}  

void BulidHeap(int *arr, int size)
{  
    int i;  
    for (i = n / 2; i > 0; i--) {  
        Heapify(arr, i, size);  
    }  
}  
    
void swap(int *arr, int i, int j)  
{  
    int tmp;  
    tmp = arr[i];  
    arr[i] = arr[j];  
    arr[j] = tmp;  
}  

void HeapSort(int *arr, int size)  
{  
    int i;  
    BulidHeap(arr, size);  
    for (i = size; i > 1; i--) {  
        swap(arr, 1, i);
        Heapify(arr, 1, i - 1);
    }  
}  
```

## 8、计数排序（Counting Sort）

计数排序不是基于比较的排序算法，其核心在于将输入的数据值转化为键存储在额外开辟的数组空间中。 作为一种线性时间复杂度的排序，计数排序要求输入的数据必须是有确定范围的整数。

8.1 算法描述

找出待排序的数组中最大和最小的元素；
统计数组中每个值为i的元素出现的次数，存入数组C的第i项；
对所有的计数累加（从C中的第一个元素开始，每一项和前一项相加）；
反向填充目标数组：将每个元素i放在新数组的第C(i)项，每放一个元素就将C(i)减去1。
8.2 复杂程度

时间复杂度O(n+k)                 空间复杂度O(n+k)

8.3 代码实现

```
void CountingSort(int *A, int *B, int n, int k)  
{  
    int *C = (int *)malloc(sizeof(int) * (k + 1));  
    int i;  
    for (i = 0; i <= k; i++) {  
        C[i] = 0;  
    }  
    for (i = 0; i < n; i++) {  
        C[A[i]]++;  
    }  
    for (i = 1; i <= k; i++) {  
        C[i] = C[i] + C[i - 1];  
    }  
    for (i = n - 1; i >= 0; i--) {  
        B[C[A[i]] - 1] = A[i];  
        C[A[i]]--;  
    }  
}  
```

## 9、桶排序（Bucket Sort）

桶排序是计数排序的升级版。它利用了函数的映射关系，高效与否的关键就在于这个映射函数的确定。桶排序 (Bucket sort)的工作的原理：假设输入数据服从均匀分布，将数据分到有限数量的桶里，每个桶再分别排序（有可能再使用别的排序算法或是以递归方式继续使用桶排序进行排）。

9.1 算法描述

设置一个定量的数组当作空桶；
遍历输入数据，并且把数据一个一个放到对应的桶里去；
对每个不是空的桶进行排序；
从不是空的桶里把排好序的数据拼接起来。 
9.2 复杂程度

时间复杂度O(n+k)                 空间复杂度O(n+k)

9.3 代码实现

```
void bucketSort(int *arr, int size, int max)
{
    int i,j;
    int buckets[max];
    memset(buckets, 0, max * sizeof(int));
    for (i = 0; i < size; i++) {
        buckets[arr[i]]++; 
    }
    for (i = 0, j = 0; i < max; i++) {
        while((buckets[i]--) >0)
            arr[j++] = i;
    }
}
```

## 10、基数排序（Radix Sort）

基数排序是按照低位先排序，然后收集；再按照高位排序，然后再收集；依次类推，直到最高位。有时候有些属性是有优先级顺序的，先按低优先级排序，再按高优先级排序。最后的次序就是高优先级高的在前，高优先级相同的低优先级高的在前。

10.1 算法描述

取得数组中的最大数，并取得位数；
arr为原始数组，从最低位开始取每个位组成radix数组；
对radix进行计数排序（利用计数排序适用于小范围数的特点）；
10.2 复杂程度

时间复杂度O(n*k)                 空间复杂度O(n+k)

10.3 代码实现

```
int get_index(int num, int dec, int order)
{
    int i, j, n;
    int index;
    int div;
    for (i = dec; i > order; i--) {
        n = 1;
        for (j = 0; j < dec - 1; j++)
            n *= 10;
        div = num / n;
        num -= div * n;
        dec--;
    }
    n = 1;
    for (i = 0; i < order - 1; i++)
        n *= 10;
    index = num / n;
    return index;
}

void RadixSort(int *arr, int len, int dec, int order)
{
    int i, j;
    int index; 
    int tmp[len]; 
    int num[10];
    memset(num, 0, 10 * sizeof(int)); 
    memset(tmp, 0, len * sizeof(int));

    if (dec < order) {
        return;
    }
    for (i = 0; i < len; i++) {
        index = get_index(arr[i], dec, order);
        num[index]++; 
    }
     
    for (i = 1; i < 10; i++) {
        num[i] += num[i-1];
    }
    for (i = len - 1; i >= 0; i--) {
        index = get_index(arr[i], dec, order); 
        j = --num[index]; 
        tmp[j] = arr[i]; 
    }
     
    for (i = 0; i < len; i++) {
        arr[i] = tmp[i]; 
    }
    RadixSort(arr, len, dec, order+1);

}
```

# 二、字符串

在C语言里边是没有字符串数据类型的，但在平时开发中肯定是少不了字符串操作的。因为字符串都是有字符组成的，所以在C语言中字符串是通过一维字符数组来实现的。

## 字符串

字符串常量就是用一对双引号括起来的字符序列，即一串字符，它有一个结束标志’ \0 '。例如，字符串 “happy” 有6字符组成，分别为 ’ h ‘、’ a ‘、’ p ‘、’ p ‘、’ y ’ 和 ’ \0 ‘，其中5个是字符串的有效字符，’ \0 ’ 是字符串结束符。

字符串的有效长度就是有效字符的个数，例如，“happy”的有效长度是5。

字符串的存储——数组初始化
字符串可以放在一维字符数组中。例如：

```
static char s[6] = { 'h', 'a', 'p', 'p', 'y', '\0' };
```


数组 s 中存放了字符串“happy”。

字符数组的初始化还可以使用字符串常量，上述初始化等价于：

```
static char s[6] = { "happy" };
或
static char s[6] = "happy";
```


将字符串存入字符数组时，由于它有一个结束符’ \0 '，数组长度至少是字符串的有效长度+1。例如，字符串“happy”的有效长度为5，存储它的数组的长度至少应为6。

如果数组长度大于字符串的有效长度+1，则数组中除了存入的字符串，还有其他内容，即字符串只占用了数组的一部分。例如：

```
char str[90] = "happy“;
```

上述代码只对数组的前6个元素(str[0] ~ str[5])赋初值，其他元素的值不确定。但这并不会影响对字符串“happy”的处理，由于字符串遇‘ \0 ’结束，所以，数组中第一个’ \0 ’ 前面的所有字符和第一个’ \0 ’ 一起构成了字符串“happy”，也就是说，第一个‘ \0 ’之后的其他数组与该字符串无关。

字符串由有效字符和字符串结束符’ \0 '组成。

字符串的存储——赋值和输入
将字符串存入数组，除了上面介绍的初始化数组，还可以采用赋值和输入的方法。例如：

```
static char s[80];
s[0] = 'a';
s[1] = '\0';
```


采用赋值的方法将字符串 “a” 存入数组s。它等价于：

```
static char s[80] = "a";
```

区分 “a” 和 ‘a’，前者是字符串常量，包括 ‘a’ 和 ‘\0’ 两个字符，用一维字符数组存放；后者是字符常量，只有一个字符，可以赋给字符变量。

输入的情况有些特殊，由于字符串结束符 ‘\0’ 代表空操作，无法输入，因此，输入字符串时，需要事先设定一个输入结束符。一旦输入它，就表示字符串输入结束，并将输入结束符转换为字符串结束符 ‘\0’。例如：

```
#include<stdio.h>

//定义输出函数
void pin(char str[]);

int main(){
    int i = 0;
    //定义字符数组
    char str[80] = "a";

    //输出字符串
    pin(str);
    
    //输入字符串，重新赋值，输入回车结束
    while((str[i] = getchar()) != '\n'){
        i++;
    }
    str[i] = '\0';  //将结束符'\0'存入数组
    
    //输出新字符串
    pin(str);
    
    return 0;

}

//输出字符串函数
void pin(char str[]){
    int i;
    for(i = 0; str[i] != '\0'; i++){    //当字符为'\0'时字符串结束
        printf("%c", str[i]);
    }
    printf("\n");
}
```


先定义一个字符数组赋值为“a”，调用输出函数输出字符串“a”，之后在输入一个新的字符串到字符数组中，回车结束输入，调用输出函数，输出新的字符串。运行结果如下：

## 常用的字符串处理函数

在使用字符串处理函数之前，需要引入stdio.h和string.h头文件。

1、字符串的输入和输出
函数输入和输出最常见的就是scanf()和printf()。除此之外字符串还可以用gets()和puts()函数输入输出。

### 1、scanf(格式控制字符串， 输入参数)

格式控制字符串中使用格式控制说明%s，输入参数必须是字符型数组名。改该函数遇回车或空格输入结束，并自动将输入的数据和字符串结束符 ‘\0’ 存入数组中。例如：

```
scanf("%s", s);		//s为字符型数组
```



### 2、printf(格式控制字符串，输出参数表)

格式控制字符串中相应的格式控制说明用%s，输出参数可以是字符数组名或字符串常量。输出 ‘\0’ 结束。例如：

```
printf("%s", s);
```


由于在C语言中是使用一维字符数组存放字符串的，因此可以在字符串操作函数中直接使用数组名进行输入与输出。

### 3、字符串输入函数gets(s)

参数s是字符数组名。函数从输入得到一个字符串，输入回车结束，自动输入的数据和 ‘\0’ 送入数组中。采用函数gets()输入的字符串允许带空格。
实际上函数gets()有返回值，如果输入成功则返回值是字符串第一个字符的地址，如果输入失败则返回NULL。但一般情况下使用gets()主要是为了输入字符串，并不会关心它的返回值。

### 4、字符串输出函数puts(s)

参数s可以是字符数组名或字符串常量。输出时遇’\0’自动将其转换为’\n’，即输出字符串后换行。同样函数puts()也有返回值，如果成功执行了输出字符串的操作，则返回换行符号’\n’，否则返回EOF。

scanf和printf函数输入与输出案例：

```
#include<stdio.h>

int main(){
    //定义一个字符数组
    char str[80];

    scanf("%s", str);
    printf("%s", str);
    printf("hello");
    
    return 0;

}
```

![img](https://img-blog.csdnimg.cn/20200514143559777.png)

printf()函数输出遇 ‘\0’ 结束。但不会自动将其转换为’\n’。所以不会换行。

scanf和printf函数输入与输出案例：

```
#include<stdio.h>

int main(){
    //定义一个字符数组
    char str[80];

    gets(str);
    puts(str);
    puts("Hello");
    
    return 0;

}
```

![img](https://img-blog.csdnimg.cn/20200514143932925.png)

puts()函数输出时遇 ‘\0’ 自动将其转换为 ‘\n’，即输出字符串后换行。

## 字符串的复制、连接和比较及字符串的长度

字符串复制、连接、和比较以及计算字符串长度的函数，在系统头文件string.h中定义。所以在使用之前，需要先引入string.h头文件。

### 1、字符串复制函数 char *strcpy(char *s1, char *s2)

该函数把字符串s2复制到s1，直到遇到s2中 ‘\0’ 为止。s1要有足够的空间容纳s2，且s1中的内容被覆盖，函数返回s1。同样可以简化以上函数的表达形式为：strcpy(s1, s2);

参数s1必须是字符型数组基地址，参数2可以是字符数组名或字符串常量。 例如：

```
int i;
char str1[80], str2[80], from[80] = "happy";		/* 初始化数组from */
strcpy(str1, from);
strcpy(str2, "key");
```


上述代码中，第三条语句调用了函数strcpy()把from中的字符串复制给str1; 第四条语句把字符串常量“key”复制给str2后，数组str1中存放了“happy”，数组str2中存放了“key”。

### 2、字符串连接函数strcat(s1, s2)

参数s1必须是字符数组基地址，参数s2可以是字符数组名或字符串常量。 strcat()函数将字符串s2接到字符串s1的后面，此时，s1中原有的结束符 ‘\0’ 被放置在连接后的结束位置上。数组s1的长度要足够大，以便存放连接后的新字符串。例如：

```
char str1[80] = "hello ", str2[80], t[80] = "world";
strcat(str1, t);
strcpy(str2, str1);
strcat(str2, "!");
```


先调用函数strcat()连接str1和t，结果放在str1中。如下图：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200514152819530.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwMjA1MTE2,size_16,color_FFFFFF,t_70#pic_center)

在调用函数strcpy()将str1中的字符串赋给str2，最后调用函数strcat()连接str2和字符串常量 “!” 后，str2中存放了“Hello world!”。

C语言中不允许使用算术运算符加将字符串数组直接连接。即str1 = str1 + t是错误的。

### 3、字符串比较函数strcmp(s1, s2)

和函数strcpy()中对参数的要求不同，函数strcmp()中的参数s1和s2可以是字符数组名或字符串常量。函数strcmp()返回一个整数，给出字符串s1和s2的比较结果：

若s1和s2相等，返回0。
若s1大于s2，返回一个正数。
若s1小于s2，返回一个负数。
设str1和str2都是字符串，在C语言中，str1 == str2、str1 > str2 和 str1 <= str2比较的是两个字符串的起始地址，而strcmp(str1， str2) == 0、strcmp(str1， str2) > 0 和 strcmp(str1， str2) <= 0 比较两个字符串的内容。

字符串比较的规则是：从两个字符串的首字符开始，依次比较相对应的字符(比较字符的ASCII码)，直接出现不同的字符或遇 ‘\0’ 为止。如果所有的字符都相同，返回0；否则，以第一个不相同字符的比较结果为准，返回这两个字符的差，即第一个字符串中的字符减去第二个字符串中的字符得到的差。例如：

```
strcmp("sea", "sea");   //值为0，说明“sea”, "sea"相等
strcmp("compute", "compare");  //值为('u' - 'a')是个正数，说明"compute"大于"compare"。
strcmp("happy", "z")   //值为('h' - 'z')是个负数，说明"happy"小于"z"。
strcmp("sea", "seat")  //值为('\0' - 't')是个负数，说明“sea”小于“seat”。
```



### 4、字符串长度函数strlen(s1)

参数s1可以是字符数组名或字符串常量。函数strlen()返回字符串s1的‘\0’之前的字符个数。即字符串有效字符的个数(不包括字符结束符’\0’)。

例如：strlen(“happy”)的值是5，strlen(“A”)的值是1。

字符串和字符指针
上面字符串都是以一维字符数组实现的。除了字符数组还可以使用字符型指针去接收字符串常量值。

如果定义一个字符指针接收字符串常量的值，该指针就指向字符串的首字符。这样，字符数组和字符指针都可以用来处理字符串。例如：

```
char sa[] = "array";
char *sp = "point";
printf("%s ", sa);	/* 数组名sa作为输出参数 */
printf("%s ", sp);	/* 字符指针sp作为输出的参数 */
printf("%s\n", "string"); 	/* 字符串常量作为输出的参数 */
```


运行结果如下：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200516182543751.png)

调用printf()函数，以%s的格式输出字符串时，作为输出参数，数组名sa，指针sp和字符串“string”的值都是地址（起始地址），从该地址所指定的单元开始连续输出其中的内容，直到遇到 ‘\0’ 结束。因此，字符串中其他字符的地址也能作为输出参数。例如：

```
printf("%s ", sa+2);	/* 数组元素sa[2]的地址作为输出参数 */
printf("%s ", sp+3); 	/* sp+3作为起始地址 */
printf("%s\n", "string" + 1);
```

运行结果如下：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200516183636207.png)

字符数组与字符指针都可以处理字符串，但两者之间还是有区别的。例如：

```
char sa[] = "This is a string";
char *sp = "This is a string";
```


字符数组sa在内存中占用了一块连续的单元，有确定的地址，每个数组元素放字符串的一个字符，字符串就存放在数组中。字符指针sp只占用一个可以存放地址的内存单元，存储字符串首字符的地址，而不是将字符串放到字符指针变量中去。如图：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517140741575.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwMjA1MTE2,size_16,color_FFFFFF,t_70#pic_center)

如果需要改变数组sa所代表的字符串，只能改变数组元素的内容。如果要改变指针sp所代表的字符串，通常直接改变指针的值，让它指向新的字符串。因为sp是指针变量，它的值可以改变，指向其他单元。例如：

```
strcpy(sa, "Hello");
sp = "Hello";
```


分别改变了sa和sp所表示的字符串。而sa = “Hello”; 是错误的，因为数组名是常量，不能对它赋值。

定义字符指针后，如果没有对它赋值，指针的值是不确定的，不能明确它指向的内存单元。因此，如果引用未赋值的指针，对指针指向的单元赋值会出现问题。例如：

```
char *s;
scanf("%s", s);
```


没有对指针s赋值，却对s指向的单元赋值。如果该单元已分配给其他变量，其值就改变了。

```
char *s, str[20];
s = str;
scanf("%s", s);
```


上述定义是正确的。数组str有确定的存储单元，s指向数组str的首元素，并对数组赋值。

为了尽量避免引用未赋值的指针所造成的错误，在定义指针时，可以先将它的初值置为空，如char *s = NULL。

## 字符串数组

在C语言当中，字符串数组可以使用： char a[] [10]; 或者 char *a[]; 表示
第一种表示方式固定了每个字符串的最大大小。第二种没有字符串的大小限制。

```
#include <stdio.h>
#include <string.h>

//该程序的功能是 输入阿拉伯数字的月份数 输出英文月份


int main()
{
    //一个字符串数组 它的下标代表英文月份的阿拉伯数字 
    char *month[] = {"January","February","March","April",
            "May","June","July","August","September","October",
            "November","December"};
    char *curMonth = month[0];
    int mon = 0;
    printf("请输入阿拉伯数字的月份数:");
    scanf("%d",&mon);
    switch(mon){
        case 1: curMonth = month[0];    break;
        case 2: curMonth = month[1];    break;
        case 3: curMonth = month[2];    break;
        case 4: curMonth = month[3];    break;
        case 5: curMonth = month[4];    break;
        case 6: curMonth = month[5];    break;
        case 7: curMonth = month[6];    break;
        case 8: curMonth = month[7];    break;
        case 9: curMonth = month[8];    break;
        case 10: curMonth = month[9];   break;
        case 11: curMonth = month[10];  break;
        case 12: curMonth = month[11];  break; 
        default : curMonth = "No this month"; 
    }
    if( strcmp(curMonth,"No this month") == 0 ){
        printf("没有这个月份\n");
    }else{
        printf("当前月份为:%s\n",curMonth);
    }

    return 0;

}
```



# 三、链表

```
#include <stdio.h>
#include <stdlib.h>
#include<string.h>
typedef struct{  //定义每个人员信息结构体 
	char name[21];//姓名 
	char phone[21]; //电话 
}DataType;
typedef struct node{  //定义链表类型 
 	DataType data; //数据域 
 	struct node *next; //指针域 
}ListNode,*LinkList;
LinkList CreateList(LinkList L,int m){ //通讯录链表的建立 ,这里要返回链表类型，否则链表内数据没有变化 
	LinkList r,s;
	L=(ListNode*)malloc(sizeof(ListNode));
	L->next=NULL;
	r=L; //尾节点 
	for(int i=0;i<m;i++){  
		s=(LinkList)malloc(sizeof(ListNode)); //新建的节点 
		scanf("%s",&s->data.name);
		scanf("%s",&s->data.phone);
		//printf("%s %s\n",s->data.name,s->data.phone);
		s->next=NULL;  
		r->next=s; //插入尾节点之后 
		r=s;
	}	
	return L;
}
int ListLength(LinkList L){ //求通讯录链表的长度 
	LinkList p;
	int length=0;
	p=L->next;
	while(p){ 
		length++;
		p=p->next;
	}
	return length;	
} 
LinkList ListInsert(LinkList L,int i,DataType d){  //通讯录链表的插入 
	LinkList p,s;
	int length = ListLength(L); 
	p=L->next;
	int j=1;
	if(!p||i>length+1) //如果是空表或者查询位置不符合要求 
		return 0;
	while(p&&j<i-1){  //使p指向要添加位置的前一个元素 
		p=p->next;
		j++;
	}
	s=(LinkList)malloc(sizeof(LinkList));
	s->data=d;
	s->next=p->next;
	p->next=s;
	return L; 
}
LinkList ListDelete(LinkList L,int i){
	LinkList p,q;//p为要删除的前一个节点，q为要删除的节点 
	p=L;
	int j=0,length=ListLength(L); 
	if(!p||i>length) //如果是空表或者查询位置不符合要求 
		return 0;
	while(p&&j<i-1){ //使p指向要删除位置的前一个元素 
		p=p->next;
		j++;
	}
	q=p->next; //q指向后一个元素  
	printf("\n被删除的人员信息为：\n");
	printf("\n姓名:%s  电话:%s ",q->data.name,q->data.phone);
	p->next=q->next; 
	return L; 	
} 
void GetElem(LinkList L,char s[]){ //查询第i个成员信息 
	int flag = 0;
	ListNode* p=(ListNode*)malloc(sizeof(ListNode));
	p=L->next;
	while(p){
		if(!strcmp(p->data.name,s)){
			printf("%s\n",p->data.phone);
			flag =1;
			break;
		}
		p=p->next;
	}
	if(!flag) printf("Not found\n");
}

void print(LinkList L){  //打印通讯录人员信息 
	//printf("yes");
	LinkList p;
	p=L->next;
	while(p){
		printf("\n姓名:%s  电话:%s ",p->data.name,p->data.phone);
		p=p->next;
	}
} 
int main(){
	LinkList L;
	int n,m;
	char choose[21];
	scanf("%d %d",&n,&m);
	L = CreateList(L,n);
	//printf("%d\n",ListLength(L));
	print(L);
	DataType d;
	strcpy(d.name,"bob");//要用strcpy赋值，不能用=
	strcpy(d.phone,"1314144");
	L = ListInsert(L,ListLength(L),d);
	print(L);
	L = ListDelete(L,ListLength(L));
	print(L);
//	for(int i = 0;i < m;++i){
//		scanf("%s",choose);
//		GetElem(L,choose);
//	}
	return 0;
}
```

# 四、类型转换 stdlib.h

## int/float to string/array

整数转化为字符串 to
a:字符串
i：整型int
l：长整形 long
ul：无符号长整形 unsigned long

小数转化为字符串 cvt （略）
g：浮点数 ，包含小数点
e：双精度浮点数，没有小数点,如果超过value的数字长度不补零。
f：浮点数，没有小数点,如果超过value的数字长度将补零。

曲线救国：sprintf( )

### itoa()：将整型值转换为字符串。

```
char *itoa (int value, char *str, int base );
```

【参数】

int value 被转换的整数
char *string 转换后储存的字符数组
int radix 转换进制数，如2,8,10,16 进制等
【返回值】：返回指向str的指针，无错误返回。

```
#include <stdlib.h>//cstdlib和stdlib.h都可以
#include <stdio.h>//cstdio和stdio.h都可以
//如果用的是cstdio和cstdlib，要加上 using namespace std;
int main(void)
{
    int number = 123456;
    char string[25];
    itoa(number, string,10);
    printf("integer=%d string=%s\n", number, string);
    return 0;
}
```

### ltoa()：将长整型值转换为字符串。

【功能】把value的值转换为以NULL结束的字符串，并把结果存在string中。radix是转换的基数值

char *ltoa(long value,char *string,int radix)
【参数】

value ：要转换的数值
string ： 转换后指向字符串的指针
radix ： 进制
ultoa()：将无符号长整型值转换为字符串。
【功能】说明:ultoa函数把 value转换成一个以空字符结尾的radix进制的字符串,并存储在string中(至多33个字节),不执行上溢出检查。radix指出value的基数

```
char *ultoa(unsigned long value, char *string, int radix);
```


【参数】

value要转换的数
String 字符串结果
radix ： 进制

```
#include
#include
int main( void )
{
    unsigned long lnumber = 3123456789L;
    char string[25];
    ultoa(lnumber,string,10);
    printf("string = %s unsigned long = %lu\n",string,lnumber);
    return 0;
}
```



### gcvt()：将浮点型数转换为字符串，取四舍五入。

### ecvt()：将双精度浮点型值转换为字符串，转换结果中不包含十进制小数点。

### fcvt()：指定位数为转换精度，其余同ecvt()。



## string/array to int/float

字符串转其他 to
a:字符串 ascii
f：浮点数
i：整型
str：字符串
d：双精度浮点数

### atof()：将字符串转换为浮点型值。

```
double atof(const char *nptr);
```


【函数说明】atof()会扫描参数nptr字符串，跳过前面的空格字符，直到遇上数字或正负符号才开始做转换，而再遇到非数字或字符串结束时(’\0’)才结束转换，并将结果返回。参数nptr字符串可包含正负号、小数点或E(e)来表示指数部分，如123.456或123e-2。
【返回值】：返回转换后的浮点型数。

```
#include<stdlib.h>
int main()
{
    char*a="-100.23";
    char*b="200e-2";
    double c;
    c=atof(a)+atof(b);
    printf(“c=%.2lf\n”,c);
    return 0;
}
```


结果为 c=-98.23


### atoi()：将字符串转换为整型值。

```
int atoi(const char *str)
```

【参数】
str：要转换为整数的字符串。

【返回值】

该函数返回转换后的长整数
如果没有执行有效的转换，则返回零

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
   int val;
   char str[20];

   strcpy(str, "98993489");
   val = atoi(str);
   printf("字符串值 = %s, 整型值 = %d\n", str, val);

   strcpy(str, "runoob.com");
   val = atoi(str);
   printf("字符串值 = %s, 整型值 = %d\n", str, val);

   return(0);
}
```

字符串值 = 98993489, 整型值 = 98993489
字符串值 = runoob.com, 整型值 = 0


### atol()：将字符串转换为长整型值。

### strtod()：将字符串转换为双精度浮点型值，并报告不能被转换的所有剩余数字。

### strtol()：将字符串转换为长整值，并报告不能被转换的所有剩余数字。

### strtoul()：将字符串转换为无符号长整型值，并报告不能被转换的所有剩余数字。

曲线救国：sprintf() 把数据写入某个字符串缓冲区 stdio.h
【功能】主要功能是把格式化的数据写入某个字符串中，即发送格式化输出到 string 所指向的字符串。

```
int sprintf(char *string, char *format [,argument,...]);
```

【参数】

string-- 这是指向一个字符数组的指针，该数组存储了 C 字符串。
format-- 这是字符串，包含了要被写入到字符串 str 的文本。它可以包含嵌入的 format 标签，format 标签可被随后的附加参数中指定的值替换，并按需求进行格式化。

```
format 标签属性是%[flags][width][.precision][length]specifier
```

[argument]…：根据不同的 format 字符串，函数可能需要一系列的附加参数，每个参数包含了一个要被插入的值，替换了 format 参数中指定的每个 % 标签。参数的个数应与 % 标签的个数相同。
【返回值】

如果成功，则返回写入的字符总数，不包括字符串追加在字符串末尾的空字符。
如果失败，则返回一个负数。
【例】

```
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various

//data and place them in the string named buffer.
// 程序使用sprintf 将各种数据格式化后置于字符数组buffer中
#include <stdio.h>
int main( void )

{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;
   // 格式化并打印各种数据到buffer
   j  = sprintf( buffer,    "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
    
   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
   return 0;
}
```


输出结果：
Output:
String: computer
Character: l
Integer: 35
Real: 1.732053
character count = 79





## **`A` 220713-数组与堆**

时间限制：1000ms 内存限制：65536kb

**题目描述**

在各类实现堆的代码中，通常选择使用一维数组去模拟堆的结构。如果在堆构建好之后，将这个一维数组输出，可以观察到他们有一些有趣的性质。我们将小根堆（最小堆）构建完成后所对应的数列，称为小根堆数列，大根堆（最大堆）构建完成后所对应的数列称为大根堆数列。

堆是最重要的数据结构之一，堆的类型有2种：最大堆和最小堆。对于最大堆，父结点的键值总是大于或等于任何一个子节点的键值。对于最小堆，父结点的键值总是小于或等于任何一个子节点的键值。通常堆的实现是用一维数组完成的。

给定一个长度为 n 的一维数组，请判断该一维数组是否实现了最大堆或者最小堆。如果该一维数组实现了最大堆，请输出`Max heap`；如果该一维数组实现了最小堆，请输出`Min heap`；如果该一维数组既没实现最大堆，也没实现最小堆，请输出`Not a heap!`。

**输入格式**

第一行是一个正整数 T，表示数据组数。

接下来有 T 组数据：每组数据包含2行，其中第1行为正整数 n，表示一维数组的长度；第2行为 n 个正整数（每个正整数之间用空格隔开），表示该一维数组。

**输出格式**

对于每一组数据，输出`Max heap`，`Min heap`或者`Not a heap!`，每个一行。

**输入样例**

```text
3
6
1 2 6 5 7 13
3
5 2 1
9
3 1 4 1 5 9 2 6 5
```

**输出样例**

```text
Min heap
Max heap
Not a heap!
```

**数据范围**

T≤20

2≤n≤100000

数据保证不会有一维数组，既实现最大堆，又实现最小堆。

```
#include<stdlib.h>
#include<stdio.h> 
int main(){
	int T,n;
	scanf("%d",&T);
	int flag = 0;//Max heap
	int notheap=0;
	while(T--){
		scanf("%d",&n);
		int arr[n + 2] ;
		flag = 0,notheap = 0;
		for(int i = 0;i < n + 2;++i) arr[i] = 0;
		
		if(n >= 3)
			for(int i = 1;i <= 3;++i)
				scanf("%d",&arr[i]);
		else if(n == 2){
			if(arr[0] < arr[1]) printf("Min heap!\n");
			else printf("Max heap!\n");
			continue;
		}
		if(arr[1] >= arr[2] && arr[1] >= arr[3]) flag = 1;//Max heap 
		for(int i = 4;i <= n;++i)
			scanf("%d",&arr[i]);
		if(n % 2 == 1){
			for(int i = 2;i <= n/2 ;++i){
				if(arr[i] <= arr[2*i] && arr[i] <= arr[2*i+1] && flag == 0) continue;
				else if(arr[i] >= arr[2*i] && arr[i] >= arr[2*i+1] && flag == 1) continue;
				else {
					notheap=1;
					printf("Not a heap!\n");
					break;	
				}	
			}				
		}
		else {
			for(int i = 2;i <= n/2 - 1;++i){
				if(arr[i] <= arr[2*i] && arr[i] <= arr[2*i+1] && flag == 0) continue;
				else if(arr[i] >= arr[2*i] && arr[i] >= arr[2*i+1] && flag == 1) continue;
				else {
					notheap=1;
					printf("Not a heap!\n");
					break;	
				}
			}	
		
			if(arr[n/2] <= arr[n] && flag == 0) flag =0 ;
			else if(arr[n/2] >= arr[n] && flag == 1) flag =1;
			else {
				notheap=1;
				printf("Not a heap!\n");
				break;	
			}
		}
		if(!notheap){
			if(flag == 0) printf("Min heap!\n");
			else printf("Max heap!\n");
		}
	}
		
	
	return 0;
}
	
```



## **`B` 220713-通讯录**

时间限制：1000ms 内存限制：204800kb

**题目描述**

小明同学有一个通讯录，通讯录中有 n 条记录。对于每一条记录，分别有对方的姓名和电话号码。假设**通讯录中所有的姓名都不重复**，请你帮小明同学写一个程序，以姓名为输入，查询该姓名对应的电话号码。

**输入**

第一行为两个整数 n 和 m，其中 n 表示通讯录中记录的数量，m 表示查询的数量。

接下来的 n 行，每行2个字符串 name 和 number，其中 name 表示姓名，number 表示 name 对应的电话号码。**字符串 name 和字符串 number 均不含空格。**

之后出现的 m 行，每行1个字符串 query，表示需要查询的姓名。

**输出**

对于每一次需要查询的姓名，输出对应的电话号码。如果通讯录中没有改姓名，则输出`Not Found`。

**输入样例**

```text
2 3
alice 1234567
bob 7654321
alice
bob
catherine
```

**输出样例**

```text
1234567
7654321
Not Found
```

**数据范围**

1≤n≤500000。

1≤m≤10000。

query 的每一位是26个小写英文字母（即a到z）之一，且字符串 name 和字符串 query 的长度不超过20。

字符串 number 的每一位是10个阿拉伯数字（即0到9）之一，且字符串 number 的长度不超过 20。



## **`C` 220713-数据位置**

时间限制：1000ms 内存限制：65536kb

**题目描述**

给定整数 t 和一个整数数组`data`，查找 t 在数组`data`中第1次出现的位置。

**输入**

第1行，一个正整数 n（n≤1000000）。

第2行，n 个`int`型整数（可能有重复的数），这 n 个`int`型整数组成了数组`data`。

第3行，多个`int`型整数（可能有重复的数，但总数不超过1000000个），其中第 i 个数记为 ti。输入的数之间用空白符号（空格、换行、或制表符）分隔。

**输出**

对每一个`int`型整数 t ，若其出现在数组`data`中，则输出其第一次出现在数组`data`的位置（出现在`data`中第几个输入的数）；否则（即其未出现在数组`data`中），输出`NO`。每一个输出占一行。

**输入样例**1

```text
5
1 2 3 4 5
4 5 6 7 1
```

**输出样例**1

```text
4
5
NO
NO
1
```

**输入样例**2

```text
9
1 2 3 4 5 5 5 5 1
4 5 5 5 1
```

**输出样例**2

```text
4
5
5
5
1
```

```
#include <stdio.h>
#include<stdlib.h>
int t[1000000];
int main(){
	int n,len = 0;
	scanf("%d",&n);
	char c;
	int data[n];
	for(int i = 0;i < n;++i)
		scanf("%d",&data[i]);
	do{
		scanf("%d",&t[len]);
		//printf("%d",t[len]);
		len++; 
		c = getchar();
	}while(c!='\n');
    for(int i = 0;i < len ;++i){
    	int flag = 0;
    	for(int j = 0;j < n;++j){
    		if(data[j] == t[i]){
    			printf("%d\n",j + 1);
    			flag = 1;
    			break;
			}
		}
		if(!flag) printf("NO\n");
	}
	return 0;
}
```

## **`D` 220713-是否互通**

时间限制：1000ms 内存限制：65536kb

**题目描述**

给定图 G，G 包含 n 个顶点。

现在有两种操作：

第一种：在两个顶点间添加一条边（该边是双向的，且不保证两个顶点间只会有一条相连的边）。

第二种：询问两个顶点之间是否存互通的路径。

**输入**

第一行2个数，顶点个数 n (2≤n≤100000)，操作个数 m (1≤m≤1000000)。

接下来 m 行，每行3个整数，分别为：操作种类 op（op=1为添加新边操作，op=2为询问操作），第一个顶点编号 u (1≤u≤n)，第二个顶点编号 v (1≤v≤n)。（保证 u 和 v 不相等）

**输出**

对于每次询问操作（op=2时），输出一行，YES表示互通，NO表示不互通。

**输入样例**

```text
3 3
2 1 2
1 1 2
2 1 2
```

**输出样例**

```text
NO
YES
```



```
#include <stdio.h>
#include <stdlib.h>
int rank[100001],fa[100001];//rank[]记录每个根节点对应的树的深度 
void init(int n){
	for(int i = 1;i <= n;++i){
		rank[i] = 1;//
		fa[i] = i;
	}
}
int find(int x){//查询 
	return x == fa[x]?x:(fa[x] = find(fa[x]));
}
void merge(int i,int j){//rank较小的往较大的合并，这样到根节点距离变长的节点个数比较少 
	int x = find(i),y = find(j);
	if(rank[x] <= rank[y]) fa[x] = y;
	else fa[y] = x;
	if(rank[x] == rank[y] && x!=y) rank[y]++; //如果两个树相同高度，合并后高度会加1 
}
int main(){
	int n,m,op;
	int u,v;
	scanf("%d %d",&n,&m);
	init(n);
	for(int i = 0;i < m;++i){
		scanf("%d %d %d",&op,&u,&v);
		if(op == 1){
			merge(u,v);
		}
		else{
			if(find(u) == find(v)) printf("YES\n");
			else printf("NO\n");
		}
	}
	return 0;
}
```



## **`E` 220713-二进序列**

时间限制：1000ms 内存限制：65536kb

**题目描述**

给定一个二进制数（该二进制数的长度可能非常长），可以对该二进制数进行以下4种操作：

（1）操作`+`：将该二进制数加1；

（2）操作`-`：将该二进制数减1；

（3）操作`*`：将该二进制数乘2；

（4）操作`/`：将该二进制数整除2；

给定一个二进制数以及包含多个操作的操作序列，求经过运算后的二进制数。

**输入格式**

输入包含3行：

第一行包含2个正整数n和m：n表示输入的二进制数的长度，m表示输入的操作序列所包含操作的个数。

第二行为1个字符串，用来表示输入的二进制数。该字符串的长度为n，且该字符串的每一个字符是`0`或者`1`。**保证输入的二进制数不包含前导零**。

第三行为1个字符串，用来表示输入的操作序列。该字符串的长度为mm，且该字符串的每一个字符为`+`、`-`、`*`、`/`种的其中之一。**保证运算过程不会出现负数**。

**输出格式**

输出仅包含1行：一个字符序列，表示经过运算后的二进制数（**不包含前导零**）；如果运算结果为0，则输出0即可。

**样例输入**1

```text
4 10
1101
*/-*-*-/*/
```

**样例输出**1

```text
10110
```

**样例输入**2

```text
5 4
10010
+//-
```

**样例输出**2

```text
11
```

**样例输入**3

```text
3 14
101
+////**++***++
```

**样例输出**3

```text
10010
```

**数据范围**

1≤n,m≤5×104。

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* performOperations(char* binary, char* operations) {
    int length = strlen(binary);

    // 创建一个动态数组来存储二进制数
    char* result = (char*)malloc((length + 1) * sizeof(char));
    strcpy(result, binary);

    // 执行操作序列
    for (int i = 0; i < strlen(operations); i++) {
        char operation = operations[i];
        if (operation == '+') {
            // 将二进制数加1
            int carry = 1;
            for (int j = length - 1; j >= 0; j--) {
                if (binary[j] == '0' && carry == 1) {
                    result[j] = '1';
                    carry = 0;
                } else if (binary[j] == '1' && carry == 1) {
                    result[j] = '0';
                }
            }
            if (carry == 1) {
                // 需要扩展结果数组
                length++;
                result = (char*)realloc(result, (length + 1) * sizeof(char));
                for(int j = length - 1; j >= 1; j--) {
                	result[j] = result[j - 1];
				}
                result[0] = '1';
                result[length] = '\0';
            }
            binary=result;//每次要更新binary 
            printf("+:%s\n", result);
        } else if (operation == '-') {
        	printf("%d\n",length);
            // 将二进制数减1
            int borrow = 1;
            for (int j = length - 1; j >= 0; j--) {
            	//printf("%d\n",j);
            	//printf("%c\n",binary[j]);
                if (binary[j] == '1' && borrow == 1) {
                    result[j] = '0';
                    borrow = 0;
                } else if (binary[j] == '0' && borrow == 1) {
                	//printf("%d %c : %c\n",j,binary[j],result[j]);
                    result[j] = '1';
                }
            }
            int j = 0;
            for(int i = 0;i < length - 1;++i){
            	if(result[i] == '0') {//把前缀0去掉 
            		++j;
				}
			}
			for(int i = 0;i <= length - 1 - j;++i){
				result[i] = result[i + j];
			}
			result = (char*)realloc(result, (length - j) * sizeof(char));
			result[length-j]='\0';
            binary=result;
            printf("-:%s\n", result);
        } else if (operation == '*') {
        	if(length == 1 && result[0] == '0'){//如果是0，不用左移 
        		printf("*:%s\n", result);
			}
            else{// 将二进制数乘2，左移一位
	            length++;
	            result = (char*)realloc(result, (length + 1) * sizeof(char));
	            result[length - 1] = '0';
	            result[length] = '\0';
	            printf("*:%s\n", result);
	            
	    	}
			binary=result;
        } else if (operation == '/') {
            // 将二进制数除以2，右移一位
            //printf("len:%d\n",length);
            if(length == 1){
            	if(result[0] == '1') result[0] = '0'; 
            	printf("/:%s\n", result);
			}
			else {
				result[length - 1] = '\0';
	            length--;
	            result = (char*)realloc(result, (length + 1) * sizeof(char));
	            printf("/:%s\n", result);
	            
			}
			binary=result;
        }
    }

    return result;
}

int main() {
    int n, m;
    scanf("%d %d", &n, &m);

    char binary[100];
    scanf("%s", binary);

    char operations[100];
    scanf("%s", operations);

    char* result = performOperations(binary, operations);
    printf("%s\n", result);

    free(result);

    return 0;
}

```



## **`G` 220713-神奇2的幂**

时间限制：1000ms 内存限制：65536kb

**题目描述**

任意一个正整数n都可以表达成若干个2的幂相加。例如，整数9有以下10种不同的与加数排序无关的表达方式：

```text
(1)  9=1+1+1+1+1+1+1+1+1
(2)  9=2+1+1+1+1+1+1+1
(3)  9=2+2+1+1+1+1+1
(4)  9=2+2+2+1+1+1
(5)  9=2+2+2+2+1
(6)  9=4+1+1+1+1+1
(7)  9=4+2+1+1+1
(8)  9=4+2+2+1
(9)  9=4+4+1
(10) 9=8+1
```

**注意：在本题中，`9=8+1`和`9=1+8`被认为是相同的与加数排序无关的表达方式。因为它们的加数均为8和1，仅加数的顺序不同。**

**输入**

输入仅1行：一个正整数n。

**输出**

输出仅1行：正整数n的与加数排序无关的表达方式的个数（由于输出的数值可能会非常大，因此输出的数值需要对1000007取模）。

**输入样例**

```text
9
```

**输出样例**

```text
10
```

**数据范围**

1≤n≤5000000。

```
#include<stdio.h>
#include<stdlib.h>
int res[5000000];
int main(){
	int n;
	scanf("%d",&n);
	res[1] = 1;
	res[2] = 2;
	for(int i = 3;i <= n;++i){
		if(i % 2 == 0){
			res[i] = res[i - 1] % 1000007 + res[i/2] % 1000007;
		}
		else res[i] = res[i - 1];
	}
	printf("%d",res[n] );
	return 0;
}
```

