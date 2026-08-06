# createImageCreator

## createImageCreator

```TypeScript
function createImageCreator(width: number, height: number, format: number, capacity: number): ImageCreator
```

通过宽、高、图片格式、容量创建ImageCreator实例。 由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法 及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。 > **说明：** > > 从API version 9开始支持，从API version 11废弃，建议使用[createImageCreator]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_代替。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 11

**替代接口：** [image.createImageCreator](arkts-image-image-createimagecreator-f.md#createimagecreator)(size:

<!--Device-image-function createImageCreator(width: number, height: number, format: number, capacity: number): ImageCreator--><!--Device-image-function createImageCreator(width: number, height: number, format: number, capacity: number): ImageCreator-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 图像的默认宽度。单位：像素（px）。 |
| height | number | 是 | 图像的默认高度。单位：像素（px）。 |
| format | number | 是 | 图像格式，如YCBCR\_\_\_ESCAPED\_UNDERSCORE\_\_\_422\_\_\_ESCAPED\_UNDERSCORE\_\_\_SP，JPEG。 |
| capacity | number | 是 | 同时访问的最大图像数。该参数仅作为期望值，实际capacity由设备硬件决定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 如果操作成功，则返回ImageCreator实例。 |

**示例：**

```TypeScript
let creator: image.ImageCreator = image.createImageCreator(8192, 8192, image.ImageFormat.JPEG, 8);
```


## createImageCreator

```TypeScript
function createImageCreator(size: Size, format: ImageFormat, capacity: int): ImageCreator
```

通过图片大小、图片格式、容量创建ImageCreator实例。 由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法 及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-image-function createImageCreator(size: Size, format: ImageFormat, capacity: int): ImageCreator--><!--Device-image-function createImageCreator(size: Size, format: ImageFormat, capacity: int): ImageCreator-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 图像的默认大小。单位：像素（px）。 |
| format | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 图像格式，如YCBCR\_\_\_ESCAPED\_UNDERSCORE\_\_\_422\_\_\_ESCAPED\_UNDERSCORE\_\_\_SP，JPEG。 |
| capacity | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 同时访问的最大图像数。该参数仅作为期望值，实际capacity由设备硬件决定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 如果操作成功，则返回ImageCreator实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types; |

**示例：**

```TypeScript
let size: image.Size = {
  height: 8192,
  width: 8192
}
let creator: image.ImageCreator = image.createImageCreator(size, image.ImageFormat.JPEG, 8);
```

