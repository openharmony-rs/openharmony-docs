# VendorTag


## 概述

Camera模块涉及相机设备的厂商标签的数据结构。

**起始版本：**  6.1

**相关模块：**  [Camera](_metadata_camera_v10.md)


## 汇总


### 成员变量

| 名称 | 描述 |
| -------- | -------- |
| unsigned int [tagId](#tagid) | 厂商标签ID。 |
| Pointer [tagName](#tagname) | 厂商标签名称。 |
| byte [tagType](#tagtype) | 厂商标签类型。 |


## 结构体成员变量说明


### tagId

```idl
unsigned int VendorTag::tagId
```

**描述**

厂商标签ID。


### tagName

```idl
Pointer VendorTag::tagName
```

**描述**

厂商标签名称。


### tagType

```idl
byte VendorTag::tagType
```

**描述**

厂商标签类型。
