# alloc

## alloc

```TypeScript
function alloc(size: int, fill?: string | Buffer | int | double | long, encoding?: BufferEncoding): Buffer
```

创建指定字节长度的Buffer对象，并使用指定值进行初始化填充（默认填充0）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-buffer-function alloc(size: int, fill?: string | Buffer | int | double | long, encoding?: BufferEncoding): Buffer--><!--Device-buffer-function alloc(size: int, fill?: string | Buffer | int | double | long, encoding?: BufferEncoding): Buffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | int | 是 | 指定的Buffer对象长度，单位：字节。取值为正整数，最大值为2^32-1，即4294967295。 |
| fill | string \| [Buffer](arkts-arkts-buffer-buffer-c.md) \| int \| double \| long | 否 | 填充至新缓冲区的值。默认值：0。<br>**起始版本：** 9 - 10 |
| encoding | BufferEncoding | 否 | 编码格式（当fill为string时，才有意义）。默认值：'utf8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Buffer](arkts-arkts-buffer-buffer-c.md) | 返回一个Buffer对象。 |

