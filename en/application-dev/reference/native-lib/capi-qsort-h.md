# qsort

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=eaf834c0e8a7b1d52ab7109799c81fa57c16f64e translatedAt=2026-11-03T13:44:02.137Z pushedAt=2026-11-04T07:07:35.138Z nl=1 -->

## Overview

`qsort` is a general-purpose sorting interface defined by the ISO C and POSIX standards, which sorts array elements according to a comparison function. This interface is natively supported by musl.

**Header file:** `<stdlib.h>`

**Library:** libc.so

**System capability:** SystemCapability.Base

**Since**: 12

**Related module:** [libc standard library](musl.md)

## Function Description

```c
void qsort(void *base, size_t nel, size_t width,
    int (*compar)(const void *, const void *));
```

Sorts the array pointed to by `base`, arranging the array elements in the order defined by the comparison function `compar`.

> **Note**
>
> The comparison function must not modify the array contents; the implementation may rearrange elements between comparison calls, but it will not modify the contents of any element itself.
> The comparison function must define a total order over the array elements, that is, multiple calls for the same pair of objects must return consistent results; inconsistent comparison results lead to undefined behavior.
> The relative order of elements that compare equal is undefined after sorting (stable sorting is not guaranteed).

**Parameters**

| Name | Description |
| --- | --- |
| `base` | Points to the starting address of the array to be sorted. |
| `nel` | Number of elements in the array. When it is 0, the comparison function is not called and no rearrangement occurs. |
| `width` | Number of bytes of each array element. |
| `compar` | Comparison function that receives two pointers to elements and returns an integer less than, equal to, or greater than 0, indicating that the first element is less than, equal to, or greater than the second element, respectively. |

**Returns**

No return value.

**Error codes**

POSIX does not define errors for this interface.

## Example

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

For more details, see the [musl official reference manual](https://musl.libc.org/manual.html).
