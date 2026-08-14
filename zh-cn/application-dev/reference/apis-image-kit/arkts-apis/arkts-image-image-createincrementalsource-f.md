# createIncrementalSource

## createIncrementalSource

```TypeScript
function createIncrementalSource(buf: ArrayBuffer): ImageSource | undefined
```

Creates an ImageSource instance based on the buffer in incremental.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createIncrementalSource(buf: ArrayBuffer): ImageSource | undefined--><!--Device-image-function createIncrementalSource(buf: ArrayBuffer): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | The buffer of the image. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | Returns the ImageSource instance if the operation is successful; returns undefined otherwise. |


## createIncrementalSource

```TypeScript
function createIncrementalSource(buf: ArrayBuffer, 
      options?: SourceOptions): ImageSource | undefined
```

Creates an ImageSource instance based on the buffer in incremental.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createIncrementalSource(buf: ArrayBuffer,       options?: SourceOptions): ImageSource | undefined--><!--Device-image-function createIncrementalSource(buf: ArrayBuffer,       options?: SourceOptions): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | The buffer of the image. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 否 | The config of source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | Returns the ImageSource instance if the operation is successful; returns undefined otherwise. |

