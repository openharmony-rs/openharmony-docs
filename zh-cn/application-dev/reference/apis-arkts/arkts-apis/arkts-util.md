# @ohos.util

util模块提供了一系列常用的工具函数，包括用于字符串编码解码的[TextEncoder](arkts-arkts-util-textencoder-c.md)和[TextDecoder](arkts-arkts-util-textdecoderoptions-i.md)、用于有理数运算的[RationalNumber<sup>8+</sup>](arkts-arkts-util-rationalnumber-c.md)、用于缓存管理的[LRUCache<sup>9+</sup>](arkts-arkts-util-lrucache-c.md)、用于范围判定的[ScopeHelper<sup>9+</sup>](arkts-arkts-util-scopehelper-c.md)、用于Base64编解码的[Base64Helper<sup>9+</sup>](arkts-arkts-util-base64helper-c.md)、用于内置对象类型判断的[types<sup>8+</sup>](arkts-arkts-util-types-c.md)，以及用于方法插桩和替换的[Aspect<sup>11+</sup>](arkts-arkts-util-aspect-c.md)。

**起始版本：** 7

<!--Device-unnamed-declare namespace util--><!--Device-unnamed-declare namespace util-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [callbackWrapper](arkts-arkts-util-callbackwrapper-f.md#callbackwrapper-1) | 回调一个异步函数。在回调中，第一个参数表示拒绝的原因（如果 promise 已经 resolved，该值为 **null**），第二个参数表示 resolved 的值。 |
| [errnoToString](arkts-arkts-util-errnotostring-f.md#errnotostring-1) | 获取系统错误码的详细信息。 |
| [format](arkts-arkts-util-format-f.md#format-1) | 通过替换字符串中的占位符进行字符串格式化。 |
| [generateRandomBinaryUUID](arkts-arkts-util-generaterandombinaryuuid-f.md#generaterandombinaryuuid-1) | 使用安全随机数生成器生成 RFC 4122 版本 4 的随机通用唯一识别码（UUID）。 |
| [generateRandomUUID](arkts-arkts-util-generaterandomuuid-f.md#generaterandomuuid-1) | 使用安全随机数生成器生成 RFC 4122 版本 4 的随机通用唯一识别码（UUID，字符串类型）。为了提升性能，本接口默认使用缓存的 uuid，其中 **entropyCache** 设置为 **true**。最多可缓存 128 个随机 uuid。当缓存的 128 个 uuid 全部用完后，会再生成一组新的 uuid 以保持随机分布。如果不需要使用缓存的 uuid，可将 **entropyCache** 设置为 **false**。 |
| [getErrorString](arkts-arkts-util-geterrorstring-f.md#geterrorstring-1) | 获取系统错误码的详细信息。 |
| [getHash](arkts-arkts-util-gethash-f.md#gethash-1) | 获取对象的哈希值。如果尚未获取过哈希值，则生成一个随机哈希值，保存到对象的 **hash** 字段中并返回。如果已经获取过哈希值，则返回保存在**hash** 字段中的哈希值（同一对象返回相同的值）。 |
| [getMainThreadStackTrace](arkts-arkts-util-getmainthreadstacktrace-f.md#getmainthreadstacktrace-1) | 获取主线程的栈追踪信息，最多返回 64 层调用帧。该接口可能对主线程性能产生影响，建议仅在必要时使用，如日志记录、错误分析或调试场景。 |
| [parseUUID](arkts-arkts-util-parseuuid-f.md#parseuuid-1) | 将 **generateRandomUUID** 生成的字符串类型的 UUID 转换为 **generateRandomBinaryUUID** 生成的 UUID，如 RFC 4122所述。 |
| [printf](arkts-arkts-util-printf-f.md#printf-1) | 通过替换字符串中的占位符进行字符串格式化。 |
| [promiseWrapper](arkts-arkts-util-promisewrapper-f.md#promisewrapper-1) | 接收一个使用错误优先回调模式的函数（即最后一个参数为 `(err, value) =&gt; callback`），并通过 promise 返回结果。 |
| [promisify](arkts-arkts-util-promisify-f.md#promisify-1) | 接收一个使用错误优先回调模式的函数（即最后一个参数为 `(err, value) =&gt; callback`），并通过 promise 返回结果。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [ArkTSVM](arkts-arkts-util-arktsvm-c.md) | 为开发者提供虚拟机维测能力的类。 |
| [Aspect](arkts-arkts-util-aspect-c.md) | 提供支持面向切面编程（AOP）的 API。这些 API 可用于对类方法进行插桩或替换。 |
| [AutoFinalizerCleaner](arkts-arkts-util-autofinalizercleaner-c.md) | 用于通过开发者自定义回调释放由开发者管理的资源的 cleaner。 |
| [Base64](arkts-arkts-util-base64-c.md) | 将包含 Base64 数据的字符串或 Uint8Array 解码为重新分配的 Uint8Array。 |
| [Base64Helper](arkts-arkts-util-base64helper-c.md) | 提供 Base64 和 Base64URL 的编解码。Base64 编码表包含 64 个字符，分别为大写字母（A-Z）、小写字母（a-z）、数字（0-9）以及特殊字符加号（+）和斜杠（/）。编码时，原始数据按三个字节一组进行划分，每组包含一个 6 位的数字。然后使用 Base64编码表中对应的字符来表示这些数字。如果最后一组只包含一个或两个字节，则使用等号（=）进行填充。Base64URL 编码表包含64 个字符，分别为大写字母（A-Z）、小写字母（a-z）、数字（0-9）以及特殊字符加号（+）和斜杠（/）。Base64URL 编码结果不包含等号（=）。 |
| [LRUCache](arkts-arkts-util-lrucache-c.md) | 提供在缓存已满时丢弃最近最少使用的数据以腾出空间给新元素的 API。此类使用最近最少使用（LRU）算法，该算法认为最近使用的数据可能在不久的将来再次被访问，而最少访问的数据是最不具价值的数据，应从缓存中移除。 |
| [LruBuffer](arkts-arkts-util-lrubuffer-c.md) | LruBuffer 算法在缓存空间不足时使用新数据替换最不常使用的数据。 |
| [RationalNumber](arkts-arkts-util-rationalnumber-c.md) | 提供比较有理数、获取分子和分母的 API。例如，可以使用 **toString()** API 将有理数转换为字符串。 |
| [Scope](arkts-arkts-util-scope-c.md) | Scope 接口用于描述字段的有效范围。 |
| [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 提供定义字段有效范围的 API。此类的构造函数创建具有上下限的可比较对象。 |
| [StringDecoder](arkts-arkts-util-stringdecoder-c.md) | 提供将二进制流解码为字符串的能力。支持以下编码类型：utf-8、iso-8859-2、koi8-r、macintosh、windows-1250、windows-1251、gbk、gb18030、big5、utf-16be 和 UTF-16le。 |
| [TextDecoder](arkts-arkts-util-textdecoder-c.md) | 提供将字节数组解码为字符串的 API。支持多种格式，包括 UTF-8、UTF-16LE、UTF-16BE、ISO-8859 和 Windows-1251。 |
| [TextEncoder](arkts-arkts-util-textencoder-c.md) | 提供将字符串编码为字节数组的 API。支持多种编码格式。使用 **TextEncoder** 进行编码时，每个字符所占用的字节数因编码格式而异。必须显式指定编码格式以获取所需的编码结果。 |
| [types](arkts-arkts-util-types-c.md) | 提供检查不同内置对象类型的 API，例如 ArrayBuffer、Map 和 Set，以避免类型错误导致的异常。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AutoFinalizer](arkts-arkts-util-autofinalizer-i.md) | 提供一个可通过开发者自定义回调释放由开发者管理的资源的接口。 |
| [DecodeToStringOptions](arkts-arkts-util-decodetostringoptions-i.md) | 描述 **decodeToString** 方法在解码字节流时的行为参数。 |
| [DecodeWithStreamOptions](arkts-arkts-util-decodewithstreamoptions-i.md) | 定义解码是否跟随数据块。 |
| [EncodeIntoUint8ArrayInfo](arkts-arkts-util-encodeintouint8arrayinfo-i.md) | 编码信息，包含已读取的字符数和已写入的字节数。 |
| [HeapMemoryInfo](arkts-arkts-util-heapmemoryinfo-i.md) | 描述 ArkTS-VM 的堆内存信息，或当前进程的共享堆内存信息。 |
| [HeapMemoryThreshold](arkts-arkts-util-heapmemorythreshold-i.md) | 描述 GC 后触发已注册回调的堆内存预警阈值。 |
| [MultithreadingDetectionOptions](arkts-arkts-util-multithreadingdetectionoptions-i.md) | 多线程检测功能参数配置。 |
| [ScopeComparable](arkts-arkts-util-scopecomparable-i.md) | **ScopeComparable** 类型的值用于实现 **compareTo** 方法。因此，请确保输入参数是可比较的。 |
| [TextDecoderOptions](arkts-arkts-util-textdecoderoptions-i.md) | 描述解码相关的选项，包含 **fatal** 和 **ignoreBOM**。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Type](arkts-arkts-util-type-e.md) | Base64 编码格式枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ScopeType](arkts-arkts-util-scopetype-t.md) | 定义 **Scope** 对象中的值类型。 |

