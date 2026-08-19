# @ohos.fastbuffer

FastBuffer对象是比Buffer性能更优的Buffer容器，用于表示固定长度的字节序列，是专门存放二进制数据的缓冲区。 FastBuffer通过from构造时，仅支持FastBuffer、Uint8Array、string、Array、ArrayBuffer和SharedArrayBuffer类型的参数。 需要高效处理二进制数据（如图片、文件传输、网络通信等）时，推荐使用FastBuffer以获得更好的性能。

**起始版本：** 20

<!--Device-unnamed-declare namespace fastbuffer--><!--Device-unnamed-declare namespace fastbuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [alloc](arkts-arkts-fastbuffer-alloc-f.md) | 创建指定字节长度的FastBuffer对象并初始化。调用后，FastBuffer对象的每个字节将被填充为指定的fill值，未指定fill时默认填充为0。 |
| [allocUninitialized](arkts-arkts-fastbuffer-allocuninitialized-f.md) | 创建指定大小未初始化的FastBuffer对象。调用[fill](arkts-arkts-fastbuffer-fastbuffer-c.md#fill)函数初始化该对象。 |
| [allocUninitializedFromPool](arkts-arkts-fastbuffer-allocuninitializedfrompool-f.md) | 从缓冲池中创建指定大小未初始化的FastBuffer对象。调用[fill](arkts-arkts-fastbuffer-fastbuffer-c.md#fill)函数初始化该对象。 |
| [byteLength](arkts-arkts-fastbuffer-bytelength-f.md) | 根据不同的编码格式，返回指定内容的字节数。 |
| [compare](arkts-arkts-fastbuffer-compare-f.md) | 返回两个FastBuffer对象的比较结果，通常用于对FastBuffer对象数组进行排序。 |
| [concat](arkts-arkts-fastbuffer-concat-f.md) | 将数组中指定字节长度的内容复制并拼接后，返回新的FastBuffer对象。 当数组中所有对象的长度总和大于totalLength时，返回结果的长度将被截断为totalLength。 当数组中所有对象的长度总和小于totalLength时，返回结果的多余部分将会被填充为0。 |
| [from](arkts-arkts-fastbuffer-from-f.md) | 根据指定数组创建新的FastBuffer对象。 |
| [from](arkts-arkts-fastbuffer-from-f.md) | 创建与`arrayBuffer`共享内存的指定长度的FastBuffer对象。 |
| [from](arkts-arkts-fastbuffer-from-f.md) | 当入参为FastBuffer对象时，创建新的FastBuffer对象并复制入参数据。新旧对象数据独立，互不影响。 当入参为Uint8Array对象时，基于其内存创建新的FastBuffer对象。两个对象保持内存关联，修改任一对象的数据会同步影响另一对象。 |
| [from](arkts-arkts-fastbuffer-from-f.md) | 根据指定编码格式的字符串，创建新的FastBuffer对象。 |
| [isBuffer](arkts-arkts-fastbuffer-isbuffer-f.md) | 判断`obj`是否为FastBuffer。 |
| [isEncoding](arkts-arkts-fastbuffer-isencoding-f.md) | 判断`encoding`是否为支持的编码格式。 |
| [transcode](arkts-arkts-fastbuffer-transcode-f.md) | 将FastBuffer或Uint8Array对象从fromEnc编码转换为toEnc编码。适用于需要在不同编码格式之间转换数据的场景。例如，将UTF-8编码的数据转换为Latin1编码，以便在仅支持ASCII的系统中处理。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | FastBuffer对象是比Buffer性能更优的Buffer容器，用于表示固定长度的字节序列，是专门存放二进制数据的缓冲区。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [TypedArray](arkts-arkts-fastbuffer-typedarray-i.md) | TypedArray 继承 Int8Array 的特性与方法。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 表示支持的编码格式类型。 |

