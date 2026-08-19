# @ohos.buffer

Buffer对象用于表示固定长度的字节序列，是专门存放二进制数据的缓冲区。 **推荐使用场景：** 适用于处理大量二进制数据，如图片处理、文件接收上传、网络通信数据传输、二进制协议解析和编解码转换等。

**起始版本：** 23

<!--Device-unnamed-declare namespace buffer--><!--Device-unnamed-declare namespace buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [alloc](arkts-arkts-buffer-alloc-f.md) | 创建指定字节长度的Buffer对象，并使用指定值进行初始化填充（默认填充0）。 |
| [allocUninitialized](arkts-arkts-buffer-allocuninitialized-f.md) | 创建指定大小未初始化的Buffer对象。内存不从缓冲池分配，适用于需要创建较大Buffer或希望精确控制内存分配的场景，如一次性分配较大内存区域（避免缓冲池可能导致的内存碎片累积和缓存性能损耗）。 创建的Buffer的内容未知，需要使用[fill](arkts-arkts-buffer-buffer-c.md#fill)函数来初始化Buffer对象。 |
| [allocUninitializedFromPool](arkts-arkts-buffer-allocuninitializedfrompool-f.md) | 创建指定大小未初始化的Buffer对象。内存从缓冲池分配，缓冲池为预分配的内存区域，适用于创建较小Buffer时减少频繁内存分配的开销，提升性能。对于需要独立内存的场景，建议使用[allocUninitialized](arkts-arkts-buffer-allocuninitialized-f.md)。 创建的Buffer内容未知，需要使用[fill](arkts-arkts-buffer-buffer-c.md#fill)函数来初始化Buffer对象。 |
| [byteLength](arkts-arkts-buffer-bytelength-f.md) | 根据不同的编码格式，返回指定数据的字节数。 |
| [byteLength](arkts-arkts-buffer-bytelength-f.md) | 根据不同的编码格式，返回指定数据的字节数。 |
| [compare](arkts-arkts-buffer-compare-f.md) | 返回两个Buffer或Uint8Array对象的比较结果，通常用于对Buffer或Uint8Array对象数组进行排序。 |
| [compare](arkts-arkts-buffer-compare-f.md) | 返回两个Buffer或Uint8Array对象的比较结果，通常用于对Buffer或Uint8Array对象数组进行排序。 |
| [concat](arkts-arkts-buffer-concat-f.md) | 将数组中的内容复制（默认复制全部内容，或复制指定字节长度）到新的Buffer对象中并返回。 |
| [from](arkts-arkts-buffer-from-f.md) | 根据指定数组创建新的Buffer对象，数组中的每个元素作为对应位置的字节存储。 |
| [from](arkts-arkts-buffer-from-f.md) | 创建与`arrayBuffer`共享内存的指定长度的Buffer对象。共享内存意味着Buffer与arrayBuffer引用同一块内存区域，对Buffer数据的修改将同步反映到arrayBuffer中，反之亦然（注意：此方式避免内存拷贝，提升性能，但需注意内存释放时机）。 |
| [from](arkts-arkts-buffer-from-f.md) | 创建ArrayBuffer的视图，不复制底层内存。 |
| [from](arkts-arkts-buffer-from-f.md) | 当入参为Buffer对象时，创建新的Buffer对象并复制入参Buffer对象的数据，然后返回新对象。 基于Uint8Array对象的内存创建新的Buffer对象并返回，新Buffer与原Uint8Array共享同一底层ArrayBuffer内存区域。 |
| [from](arkts-arkts-buffer-from-f.md) | 根据指定的`object`类型数据，创建新的Buffer对象。当object的valueOf()返回ArrayBuffer时，按字节偏移量和长度创建Buffer；其他类型则根据编码格式将对象值转换为Buffer。 |
| [from](arkts-arkts-buffer-from-f.md) | 根据指定编码格式的字符串，创建新的Buffer对象，字符串按编码格式转换为字节序列存入Buffer。 |
| [isBuffer](arkts-arkts-buffer-isbuffer-f.md) | 判断`obj`是否为Buffer。 |
| [isEncoding](arkts-arkts-buffer-isencoding-f.md) | 判断`encoding`是否为支持的编码格式。 |
| [transcode](arkts-arkts-buffer-transcode-f.md) | 将Buffer或Uint8Array对象从一种字符编码重新编码为另一种。适用于需要在不同编码格式之间转换已有Buffer数据的场景。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Blob](arkts-arkts-buffer-blob-c.md) | 将数据处理为blob类型。 |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | Buffer对象是处理二进制数据的缓冲区。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BlobOptions](arkts-arkts-buffer-bloboptions-i.md) | 定义Blob相关的options参数。 |
| [TypedArray](arkts-arkts-buffer-typedarray-i.md) | TypedArray继承Int8Array的特性与方法。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ArrayUnionType](arkts-arkts-buffer-arrayuniontype-t.md) | ArrayUnionType的特性与方法。 |
| [BufferEncoding](arkts-arkts-buffer-bufferencoding-t.md) | 表示支持的编码格式类型。 |
| [TypedArray](arkts-arkts-buffer-typedarray-t.md) | TypedArray的特性与方法。 |

