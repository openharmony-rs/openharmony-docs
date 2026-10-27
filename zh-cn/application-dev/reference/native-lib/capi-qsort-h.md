# qsort

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

## 概述

`qsort` 是ISO C与POSIX标准定义的通用排序接口，依据比较函数对数组元素排序。该接口为musl原生支持。

**引用文件：** `<stdlib.h>`

**库：** libc.so

**系统能力：** SystemCapability.Base

**起始版本：** 12

**相关模块：** [libc标准库](musl.md)

## 函数说明

```c
void qsort(void *base, size_t nel, size_t width,
    int (*compar)(const void *, const void *));
```

对`base`指向的数组进行排序，依据比较函数`compar`定义的顺序排列数组元素。

> **注意**
>
> 比较函数不得修改数组内容；实现可能在比较调用之间重排元素，但不会修改任一元素本身的内容。
> 比较函数须对数组元素定义全序关系，即对相同对象对的多次调用结果须一致；不一致的比较结果会导致未定义行为。
> 比较结果相等的元素在排序后的相对顺序未定义（不保证稳定排序）。

**参数：**

| 参数项 | 描述 |
| --- | --- |
| `base` | 指向待排序数组起始地址。 |
| `nel` | 数组元素个数。为0时不调用比较函数，也不发生重排。 |
| `width` | 每个数组元素的字节数。 |
| `compar` | 比较函数，接收两个指向元素的指针，返回小于、等于或大于0的整数，分别表示第一个元素小于、等于或大于第二个元素。 |

**返回值：**

无返回值。

**错误码：**

POSIX未为该接口定义错误。

## 示例

```c
#include <stdio.h>
#include <stdlib.h>

static int compare_ints(const void *left, const void *right)
{
    const int *lhs = (const int *)left;
    const int *rhs = (const int *)right;
    return (*lhs > *rhs) - (*lhs < *rhs);
}

int main(void)
{
    int values[] = {9, 2, 7, 11, 3};
    size_t nel = sizeof(values) / sizeof(values[0]);
    size_t i;

    qsort(values, nel, sizeof(values[0]), compare_ints);

    for (i = 0; i < nel; ++i) {
        printf("%d ", values[i]);
    }
    printf("\n");
    return 0;
}
```

更多详细信息参考[musl官方参考手册](https://musl.libc.org/manual.html)。
