# FileMapping

文件映射对象，在调用FileMapping的方法前，需要先通过[mmap()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或方法[mmapSync()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_构建一个FileMapping实例。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-fileIo-interface FileMapping--><!--Device-fileIo-interface FileMapping-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## capacity

```TypeScript
capacity(): int
```

获取文件映射区的容量。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-capacity(): int--><!--Device-FileMapping-capacity(): int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 文件映射区的容量，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

## flip

```TypeScript
flip(): void
```

翻转文件映射区，将写入准备状态切换为读取准备状态。调用后，limit被设置为当前position的值，position被重置为0。 推荐在一系列 [write()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 操作完成后，调用此方法准备后续的 [read()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 操作。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-flip(): void--><!--Device-FileMapping-flip(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

## getLimit

```TypeScript
getLimit(): int
```

获取文件映射区可读写区域的上界。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-getLimit(): int--><!--Device-FileMapping-getLimit(): int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 当前可读写区域上界值，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

## getPosition

```TypeScript
getPosition(): int
```

获取文件映射区的当前位置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-getPosition(): int--><!--Device-FileMapping-getPosition(): int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 文件映射区的当前位置，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

## msync

```TypeScript
msync(): Promise<void>
```

将整个文件映射区的数据同步到磁盘文件。使用Promise异步回调。 > **说明：** > > 如果文件不在本地设备上，调用此接口不保证所有更改都已持久化存储。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-msync(): Promise<void>--><!--Device-FileMapping-msync(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900011 | Out of memory |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |

## msync

```TypeScript
msync(position: int, length: int): Promise<void>
```

将文件映射区指定范围内的数据同步到磁盘文件。使用Promise异步回调。 > **说明：** > > 如果文件不在本地设备上，调用此接口不保证所有更改都已持久化存储。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-msync(position: int, length: int): Promise<void>--><!--Device-FileMapping-msync(position: int, length: int): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | int | 是 | 期望同步的起始位置，单位为Byte。 |
| length | int | 是 | 期望同步的数据长度，单位为Byte。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900011 | Out of memory |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |

## msyncSync

```TypeScript
msyncSync(): void
```

以同步方法将整个文件映射区的数据同步到磁盘文件。 > **说明：** > > 如果文件不在本地设备上，调用此接口不保证所有更改都已持久化存储。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-msyncSync(): void--><!--Device-FileMapping-msyncSync(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900011 | Out of memory |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |

## msyncSync

```TypeScript
msyncSync(position: int, length: int): void
```

以同步方法将文件映射区指定范围内的数据同步到磁盘文件。 > **说明：** > > 如果文件不在本地设备上，调用此接口不保证所有更改都已持久化存储。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-msyncSync(position: int, length: int): void--><!--Device-FileMapping-msyncSync(position: int, length: int): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | int | 是 | 期望同步的起始位置，单位为Byte。 |
| length | int | 是 | 期望同步的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900011 | Out of memory |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |
| 13900055 | Mmap operation not supported |

## read

```TypeScript
read(buffer: ArrayBuffer, length?: int): int
```

从当前位置读取数据，并将位置后移实际读取的字节数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-read(buffer: ArrayBuffer, length?: int): int--><!--Device-FileMapping-read(buffer: ArrayBuffer, length?: int): int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| length | int | 否 | 期望读取数据的长度，单位为Byte。默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回实际读取的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |
| 13900052 | Mmap buffer released |
| 13900054 | Mmap buffer is inaccessible |

## read

```TypeScript
read(position: int, buffer: ArrayBuffer, length?: int): int
```

从指定位置读取数据，当前位置不会发生移动。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-read(position: int, buffer: ArrayBuffer, length?: int): int--><!--Device-FileMapping-read(position: int, buffer: ArrayBuffer, length?: int): int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | int | 是 | 期望读取的起始位置，单位为Byte。 |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| length | int | 否 | 期望读取数据的长度，单位为Byte。默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回实际读取的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |
| 13900052 | Mmap buffer released |
| 13900054 | Mmap buffer is inaccessible |

## remaining

```TypeScript
remaining(): int
```

获取从当前位置（position）到可读写区域的上界（limit）之间的剩余字节数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-remaining(): int--><!--Device-FileMapping-remaining(): int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 剩余可读或可写的字节数，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

## setLimit

```TypeScript
setLimit(limit: int): void
```

设置文件映射区可读写区域的上界。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-setLimit(limit: int): void--><!--Device-FileMapping-setLimit(limit: int): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| limit | int | 是 | 要设置的可读写区域上界值，单位为Byte。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值需大于等于0，且小于等于当前[capacity]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。若所设值小于文件映射区的当前位置，则当前位置将自动调整至该值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

## setPosition

```TypeScript
setPosition(position: int): void
```

设置文件映射区的当前位置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-setPosition(position: int): void--><!--Device-FileMapping-setPosition(position: int): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | int | 是 | 期望设置的目标位置，单位为Byte。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_必须为非负数且不大于当前可读写上界的limit，可通过[getLimit()]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获得可读写上界的limit。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900052 | Mmap buffer released |

## unmap

```TypeScript
unmap(): Promise<void>
```

释放文件映射区。使用Promise异步回调。调用后，position、limit和capacity均被重置为0，FileMapping对象不可再进行任何操作。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-unmap(): Promise<void>--><!--Device-FileMapping-unmap(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |

## unmapSync

```TypeScript
unmapSync(): void
```

以同步方法释放文件映射区。调用后，position、limit和capacity均被重置为0，FileMapping对象不可再进行任何操作。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-unmapSync(): void--><!--Device-FileMapping-unmapSync(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |

## write

```TypeScript
write(data: ArrayBuffer, length?: int): int
```

从当前位置写入数据，并将位置后移实际写入的字节数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-write(data: ArrayBuffer, length?: int): int--><!--Device-FileMapping-write(data: ArrayBuffer, length?: int): int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | ArrayBuffer | 是 | 待写入文件的缓冲区数据。 |
| length | int | 否 | 期望写入数据的长度，单位为Byte。默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回实际写入的长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |
| 13900052 | Mmap buffer released |
| 13900053 | Read-only mmap buffer |
| 13900054 | Mmap buffer is inaccessible |

## write

```TypeScript
write(position: int, data: ArrayBuffer, length?: int): int
```

从指定位置写入数据，当前位置不会发生移动。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMapping-write(position: int, data: ArrayBuffer, length?: int): int--><!--Device-FileMapping-write(position: int, data: ArrayBuffer, length?: int): int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | int | 是 | 期望写入的起始位置，单位为Byte。 |
| data | ArrayBuffer | 是 | 待写入文件的缓冲区数据。 |
| length | int | 否 | 期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回实际写入的长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900050 | Internal resource error |
| 13900051 | Buffer read/write out of bounds |
| 13900052 | Mmap buffer released |
| 13900053 | Read-only mmap buffer |
| 13900054 | Mmap buffer is inaccessible |

