# createImagePacker

## createImagePacker

```TypeScript
function createImagePacker(): ImagePacker
```

创建ImagePacker实例。 由于图片占用内存较大，所以当ImagePacker实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-image-function createImagePacker(): ImagePacker--><!--Device-image-function createImagePacker(): ImagePacker-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回ImagePacker实例。 |

**示例：**

ArkTS-Dyn示例:

```TypeScript
async function CreateImagePacker() {
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
}
```

ArkTS-Sta示例:

```TypeScript
const imagePacker: image.ImagePacker = image.createImagePacker();
```

