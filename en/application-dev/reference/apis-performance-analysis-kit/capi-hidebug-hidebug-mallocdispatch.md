# HiDebug_MallocDispatch

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

```c
typedef struct HiDebug_MallocDispatch {...} HiDebug_MallocDispatch
```

## Overview

Defines the struct types of the replaceable/restorable **HiDebug_MallocDispatch** table of the application process.

**Since**: 20

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Function

| Name| Description|
| -- | -- |
| [void* (\*malloc)(size_t)](#malloc) | Pointer to the custom **malloc** function.|
| [void* (\*calloc)(size_t, size_t)](#calloc) | Pointer to the custom **calloc** function.|
| [void* (\*realloc)(void*, size_t)](#realloc) | Pointer to the custom **realloc** function.|
| [void (\*free)(void*)](#free) | Pointer to the custom **free** function.|
| [void* (\*mmap)(void*, size_t, int, int, int, off_t)](#mmap) | Pointer to the custom **mmap** function.|
| [int (\*munmap)(void*, size_t)](#munmap) | Pointer to the custom **munmap** function.|

## Member Function Description

### malloc()

```c
void* (*malloc)(size_t)
```

**Description**

Pointer to the custom **malloc** function.

### calloc()

```c
void* (*calloc)(size_t, size_t)
```

**Description**

Pointer to the custom **calloc** function.

### realloc()

```c
void* (*realloc)(void*, size_t)
```

**Description**

Pointer to the custom **realloc** function.

### free()

```c
void (*free)(void*)
```

**Description**

Pointer to the custom **free** function.

### mmap()

```c
void* (*mmap)(void*, size_t, int, int, int, off_t)
```

**Description**

Pointer to the custom **mmap** function.

### munmap()

```c
int (*munmap)(void*, size_t)
```

**Description**

Pointer to the custom **munmap** function.
