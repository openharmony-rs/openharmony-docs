# @ohos.util

/*
 Copyright (c) 2021-2022 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-unnamed-declare namespace util--><!--Device-unnamed-declare namespace util-End-->

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [callbackWrapper](arkts-arkts-util-callbackwrapper-f.md#callbackWrapper) | 对异步函数进行回调化处理，回调中第一个参数是拒绝原因（如果Promise已解决，则为null），第二个参数是已解决的值。 |
| [errnoToString](arkts-arkts-util-errnotostring-f.md#errnoToString) | 获取系统错误码对应的详细信息。适用于系统调用出错时将数字错误码转换为可读的描述信息，便于开发者快速定位和排查系统级错误，常用于错误日志记录和错误提示显示。 |
| [format](arkts-arkts-util-format-f.md#format) | 使用样式化字符串将输入内容按特定格式输出，适用于日志输出、用户界面文本格式化等场景。 |
| [generateRandomBinaryUUID](arkts-arkts-util-generaterandombinaryuuid-f.md#generateRandomBinaryUUID) | 使用加密安全随机数生成器生成随机的RFC 4122版本4的Uint8Array类型UUID。为了提升性能，此接口会默认使用缓存，即入参为true， 最多可缓存128个随机的UUID。当缓存中128个UUID用尽后，会重新生成，以保证UUID的随机性。如需禁用缓存，请将入参设置为false。 |
| [generateRandomUUID](arkts-arkts-util-generaterandomuuid-f.md#generateRandomUUID) | 使用加密安全随机数生成器生成随机的RFC 4122版本4的string类型UUID。为了提升性能，此接口会默认使用缓存，即入参为true， 最多可缓存128个随机的UUID。当缓存中128个UUID用尽后，会重新生成，以保证UUID的随机性。如需禁用缓存，请将入参设置为false。 |
| [getErrorString](arkts-arkts-util-geterrorstring-f.md#getErrorString) | 获取系统错误码的详细信息。 |
| [getHash](arkts-arkts-util-gethash-f.md#getHash) | 获取对象的哈希值。 如果尚未获取过哈希值，则生成一个随机哈希值，保存到对象的 **hash** 字段中并返回。如果已经获取过哈希值，则返回保存在 **hash** 字段中的哈希值（同一对象返回相同的值）。 |
| [getMainThreadStackTrace](arkts-arkts-util-getmainthreadstacktrace-f.md#getMainThreadStackTrace) | 获取主线程的栈追踪信息，最多返回 64 层调用帧。 该接口可能对主线程性能产生影响，建议仅在必要时使用，如日志记录、错误分析或调试场景。 |
| [parseUUID](arkts-arkts-util-parseuuid-f.md#parseUUID) | 将generateRandomUUID生成的string类型UUID转换为[generateRandomBinaryUUID](arkts-arkts-util-generaterandombinaryuuid-f.md#generateRandomBinaryUUID)生成的UUID， 符合RFC 4122版本规范。 |
| [printf](arkts-arkts-util-printf-f.md#printf) | 通过式样化字符串对输入的内容按特定格式输出。 |
| [promiseWrapper](arkts-arkts-util-promisewrapper-f.md#promiseWrapper) | 接收一个使用错误优先回调模式的函数（即最后一个参数为 `(err, value) => callback`），并通过 promise 返回结果。 |
| [promisify](arkts-arkts-util-promisify-f.md#promisify) | 接收一个采用"错误优先"回调模式的函数，即以`(err, value) => callback`作为最后一个参数，并返回其Promise函数。 适用于将旧版回调式异步API转换为Promise风格，以便使用async/await语法进行调用，从而简化异步代码编写。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [ArkTSVM](arkts-arkts-util-arktsvm-c.md) | 为开发者提供虚拟机维测能力的类。 |
| [Aspect](arkts-arkts-util-aspect-c.md) | 提供支持面向切面编程（AOP）的 API。这些 API 可用于对类方法进行插桩或替换。 |
| [AutoFinalizerCleaner](arkts-arkts-util-autofinalizercleaner-c.md) | 用于通过开发者自定义回调释放由开发者管理的资源的 cleaner。 |
| [Base64](arkts-arkts-util-base64-c.md) | 将包含 Base64 数据的字符串或 Uint8Array 解码为重新分配的 Uint8Array。 |
| [Base64Helper](arkts-arkts-util-base64helper-c.md) | 提供 Base64 和 Base64URL 的编解码。Base64 编码表包含 64 个字符，分别为大写字母（A-Z）、小写字母（a-z）、数字（0-9） 以及特殊字符加号（+）和斜杠（/）。编码时，原始数据按三个字节一组进行划分，每组包含一个 6 位的数字。然后使用 Base64 编码表中对应的字符来表示这些数字。如果最后一组只包含一个或两个字节，则使用等号（=）进行填充。Base64URL 编码表包含 64 个字符，分别为大写字母（A-Z）、小写字母（a-z）、数字（0-9）以及特殊字符加号（+）和斜杠（/）。Base64URL 编码结果 不包含等号（=）。 |
| [LRUCache](arkts-arkts-util-lrucache-c.md) | 提供在缓存已满时丢弃最近最少使用的数据以腾出空间给新元素的 API。此类使用最近最少使用（LRU）算法，该算法认为最近 使用的数据可能在不久的将来再次被访问，而最少访问的数据是最不具价值的数据，应从缓存中移除。 |
| [LruBuffer](arkts-arkts-util-lrubuffer-c.md) | LruBuffer 算法在缓存空间不足时使用新数据替换最不常使用的数据。 |
| [RationalNumber](arkts-arkts-util-rationalnumber-c.md) | 提供比较有理数、获取分子和分母的 API。例如，可以使用 **toString()** API 将有理数转换为字符串。 |
| [Scope](arkts-arkts-util-scope-c.md) | Scope 接口用于描述字段的有效范围。 |
| [ScopeHelper](arkts-arkts-util-scopehelper-c.md) | 提供定义字段有效范围的 API。此类的构造函数创建具有上下限的可比较对象。 |
| [StringDecoder](arkts-arkts-util-stringdecoder-c.md) | 提供将二进制流解码为字符串的能力。支持以下编码类型：utf-8、iso-8859-2、koi8-r、macintosh、windows-1250、 windows-1251、gbk、gb18030、big5、utf-16be 和 UTF-16le。 |
| [TextDecoder](arkts-arkts-util-textdecoder-c.md) | 提供将字节数组解码为字符串的 API。支持多种格式，包括 UTF-8、UTF-16LE、UTF-16BE、ISO-8859 和 Windows-1251。 |
| [TextEncoder](arkts-arkts-util-textencoder-c.md) | 提供将字符串编码为字节数组的 API。支持多种编码格式。 使用 **TextEncoder** 进行编码时，每个字符所占用的字节数因编码格式而异。必须显式指定编码格式以获取所需的编码结果。 |
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
| [MultithreadingDetectionOptions](arkts-arkts-util-multithreadingdetectionoptions-i.md) | 多线程安全检测功能参数配置。 |
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

