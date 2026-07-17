# copyFile

## copyFile

```TypeScript
declare function copyFile(src: string | number, dest: string | number, mode?: number): Promise<void>
```

复制文件，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile-1)

<!--Device-unnamed-declare function copyFile(src: string | number, dest: string | number, mode?: number): Promise<void>--><!--Device-unnamed-declare function copyFile(src: string | number, dest: string | number, mode?: number): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string \| number | 是 | 待复制文件的路径或待复制文件的描述符。 |
| dest | string \| number | 是 | 目标文件路径或目标文件描述符。 |
| mode | number | 否 | mode提供覆盖文件的选项，当前仅支持0，且默认为0。<br/>0：完全覆盖目标文件，未覆盖部分将被裁切掉。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回值。 |


## copyFile

```TypeScript
declare function copyFile(src: string | number, dest: string | number, callback: AsyncCallback<void>): void
```

copyFile.

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile-1)

<!--Device-unnamed-declare function copyFile(src: string | number, dest: string | number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function copyFile(src: string | number, dest: string | number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string \| number | 是 | 待复制文件的路径或待复制文件的描述符。 |
| dest | string \| number | 是 | 目标文件路径或目标文件描述符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 异步复制文件之后的回调。 |


## copyFile

```TypeScript
declare function copyFile(
  src: string | number,
  dest: string | number,
  mode: number,
  callback: AsyncCallback<void>
): void
```

复制文件，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile-1)

<!--Device-unnamed-declare function copyFile(
  src: string | number,
  dest: string | number,
  mode: number,
  callback: AsyncCallback<void>
): void--><!--Device-unnamed-declare function copyFile(
  src: string | number,
  dest: string | number,
  mode: number,
  callback: AsyncCallback<void>
): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string \| number | 是 | 待复制文件的路径或待复制文件的描述符。 |
| dest | string \| number | 是 | 目标文件路径或目标文件描述符。 |
| mode | number | 是 | mode提供覆盖文件的选项，当前仅支持0，且默认为0。<br/>0：完全覆盖目标文件，未覆盖部分将被裁切掉。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 异步复制文件之后的回调。 |

