# ICameraVendorTag


## 概述

Camera metadata模块接口定义。

获取所有厂商标签、获取厂商标签名称等相关操作。

**起始版本：**  6.1

**相关模块：**  [Camera](_metadata_camera_v10.md)


## 汇总


### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [GetVendorTagName](#getvendortagname) ([in] unsigned int tagId, [out] Pointer tagName) | 获取厂商标签名称。 |
| [GetVendorTagType](#getvendortagtype) ([in] unsigned int tagId, [out] byte tagType) | 获取厂商标签类型。 |
| [GetAllVendorTags](#getallvendortags) ([out] List&lt; [VendorTag](_metadata_vendor_tag_v10.md) &gt; tagVec) | 获取所有厂商标签。 |


## 成员函数说明


### GetAllVendorTags()

```idl
ICameraVendorTag::GetAllVendorTags([out] List< VendorTag > tagVec)
```

**描述**

获取所有厂商标签。

**起始版本：**  6.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| tagVec | 获取到的所有厂商标签。 |

**返回：**

NO_ERROR 表示执行成功。

其他值表示执行失败，具体错误码查看[**CamRetCode**](_camera_v12.md#camretcode)。


### GetVendorTagName()

```idl
ICameraVendorTag::GetVendorTagName([in] unsigned int tagId, [out] Pointer tagName )
```

**描述**

获取厂商标签名称。

**起始版本：**  6.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| tag | 厂商标签ID。 |
| vendorTagName | 获取到的厂商标签名称。 |

**返回：**

NO_ERROR 表示执行成功。

其他值表示执行失败，具体错误码查看[**CamRetCode**](_camera_v12.md#camretcode)。


### GetVendorTagType()

```idl
ICameraVendorTag::GetVendorTagType([in] unsigned int tagId, [out] byte tagType )
```

**描述**

获取厂商标签类型。

**起始版本：**  6.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| tag | 厂商标签ID。 |
| vendorTagType | 获取到的厂商标签类型。 |

**返回：**

NO_ERROR 表示执行成功。

其他值表示执行失败，具体错误码查看[**CamRetCode**](_camera_v12.md#camretcode)。
