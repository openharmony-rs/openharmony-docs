# @ohos.fastbuffer

FastBuffer对象是更高效的Buffer容器，用于表示固定长度的字节序列，是专门存放二进制数据的缓存区。

**起始版本：** 20

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [alloc](arkts-arkts-fastbuffer-alloc-f.md#alloc-1) | 创建指定字节长度的FastBuffer对象并初始化。<br/> |
| [allocUninitialized](arkts-arkts-fastbuffer-allocuninitialized-f.md#allocUninitialized-1) | 创建指定大小未初始化的FastBuffer对象，需要使用fill函数来初始化FastBuffer对象。<br/> |
| [allocUninitializedFromPool](arkts-arkts-fastbuffer-allocuninitializedfrompool-f.md#allocUninitializedFromPool-1) | 从缓冲池中创建指定大小未初始化的FastBuffer对象，需要使用fill函数来初始化FastBuffer对象。<br/> |
| [byteLength](arkts-arkts-fastbuffer-bytelength-f.md#byteLength-1) | 根据不同的编码格式，返回指定字符串的字节数。<br/> |
| [compare](arkts-arkts-fastbuffer-compare-f.md#compare-1) | 返回两个FastBuffer对象的比较结果，通常用于对FastBuffer对象数组进行排序。<br/> |
| [concat](arkts-arkts-fastbuffer-concat-f.md#concat-1) | 将数组中指定字节长度的内容复制到新的FastBuffer对象中并返回拼接后的FastBuffer对象。<br/> |
| [from](arkts-arkts-fastbuffer-from-f.md#from-1) | 根据指定数组创建新的FastBuffer对象。<br/> |
| [from](arkts-arkts-fastbuffer-from-f.md#from-2) | 创建与`arrayBuffer`共享内存的指定长度的FastBuffer对象。<br/> |
| [from](arkts-arkts-fastbuffer-from-f.md#from-3) | 当入参为FastBuffer对象时，创建新的FastBuffer对象并复制入参FastBuffer对象的数据，然后返回新对象。<br/><br/>当入参为Uint8Array对象时，基于Uint8Array对象的内存创建新的FastBuffer对象并返回，保持数据的内存关联。<br/> |
| [from](arkts-arkts-fastbuffer-from-f.md#from-4) | 根据指定编码格式的字符串，创建新的FastBuffer对象。<br/> |
| [isBuffer](arkts-arkts-fastbuffer-isbuffer-f.md#isBuffer-1) | 判断`obj`是否为FastBuffer。<br/> |
| [isEncoding](arkts-arkts-fastbuffer-isencoding-f.md#isEncoding-1) | 判断`encoding`是否为支持的编码格式。<br/> |
| [transcode](arkts-arkts-fastbuffer-transcode-f.md#transcode-1) | 将FastBuffer或Uint8Array对象从fromEnc编码转换为toEnc编码。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | FastBuffer对象是更高效的Buffer容器，用于表示固定长度的字节序列，是专门存放二进制数据的缓存区。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [TypedArray](arkts-arkts-fastbuffer-typedarray-i.md) | TypedArray 继承 Int8Array 的特性与方法。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BufferEncoding](arkts-arkts-fastbuffer-bufferencoding-t.md) | 表示支持的编码格式类型。<br/> |

