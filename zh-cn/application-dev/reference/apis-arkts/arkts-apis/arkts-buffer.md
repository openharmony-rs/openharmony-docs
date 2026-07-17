# @ohos.buffer

Buffer对象用于表示固定长度的字节序列，是专门存放二进制数据的缓存区。**推荐使用场景**：适用于处理大量二进制数据，如图片处理和文件接收上传等。

**起始版本：** 9

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
| [alloc](arkts-arkts-buffer-alloc-f.md#alloc-1) | 创建指定字节长度的Buffer对象并初始化。 |
| [allocUninitialized](arkts-arkts-buffer-allocuninitialized-f.md#allocuninitialized-1) | 创建指定大小未初始化的Buffer对象。内存不从缓冲池分配。创建的Buffer内容未知，需要使用[fill()](arkts-arkts-buffer-buffer-c.md#fill-1)函数来初始化Buffer对象。 |
| [allocUninitializedFromPool](arkts-arkts-buffer-allocuninitializedfrompool-f.md#allocuninitializedfrompool-1) | 创建指定大小未初始化的Buffer对象。内存从缓冲池分配。创建的Buffer内容未知，需要使用[fill()](arkts-arkts-buffer-buffer-c.md#fill-1)函数来初始化Buffer对象。 |
| [byteLength](arkts-arkts-buffer-bytelength-f.md#bytelength-1) | 根据不同的编码格式，返回指定字符串的字节数。 |
| [compare](arkts-arkts-buffer-compare-f.md#compare-1) | 返回两个Buffer对象的比较结果，通常用于对Buffer对象数组进行排序。 |
| [concat](arkts-arkts-buffer-concat-f.md#concat-1) | 将数组中的内容复制指定字节长度到新的Buffer对象中并返回。 |
| [from](arkts-arkts-buffer-from-f.md#from-1) | 根据指定数组创建新的Buffer对象。 |
| [from](arkts-arkts-buffer-from-f.md#from-2) | 创建与arrayBuffer共享内存的指定长度的Buffer对象。 |
| [from](arkts-arkts-buffer-from-f.md#from-3) | 当入参为Buffer对象时，创建新的Buffer对象并复制入参Buffer对象的数据，然后返回新对象。当入参为Uint8Array对象时，基于Uint8Array对象的内存创建新的Buffer对象并返回，保持数据的内存关联。 |
| [from](arkts-arkts-buffer-from-f.md#from-4) | 根据指定的object类型数据，创建新的Buffer对象。 |
| [from](arkts-arkts-buffer-from-f.md#from-5) | 根据指定编码格式的字符串，创建新的Buffer对象。 |
| [isBuffer](arkts-arkts-buffer-isbuffer-f.md#isbuffer-1) | 判断obj是否为Buffer。 |
| [isEncoding](arkts-arkts-buffer-isencoding-f.md#isencoding-1) | 判断encoding是否为支持的编码格式。 |
| [transcode](arkts-arkts-buffer-transcode-f.md#transcode-1) | 将Buffer或Uint8Array对象从一种字符编码重新编码为另一种。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Blob](arkts-arkts-buffer-blob-c.md) | 将数据处理为blob类型。 |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | Buffer对象是处理二进制数据的缓存区。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [TypedArray](arkts-arkts-buffer-typedarray-i.md) | TypedArray继承Int8Array的特性与方法。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [BufferEncoding](arkts-arkts-buffer-bufferencoding-t.md) | 表示支持的编码格式类型。 |

