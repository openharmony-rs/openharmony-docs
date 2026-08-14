# createAuxiliaryPicture

## createAuxiliaryPicture

```TypeScript
function createAuxiliaryPicture(buffer: ArrayBuffer, size: Size, type: AuxiliaryPictureType): AuxiliaryPicture
```

通过ArrayBuffer图片数据、辅助图尺寸、辅助图类型创建AuxiliaryPicture实例。该接口仅支持传入BGRA的连续像素数据，会创建出RGBA的辅助图。 由于图片占用内存较大，所以当AuxiliaryPicture实例使用完成后，应主动调用[release](arkts-image-image-auxiliarypicture-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法 均执行完成，且后续不再使用该实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createAuxiliaryPicture(buffer: ArrayBuffer, size: Size, type: AuxiliaryPictureType): AuxiliaryPicture--><!--Device-image-function createAuxiliaryPicture(buffer: ArrayBuffer, size: Size, type: AuxiliaryPictureType): AuxiliaryPicture-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 以buffer形式存放的图像数据。 |
| size | Size | 是 | 辅助图的尺寸。单位：像素（px）。 |
| type | [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md) | 是 | 辅助图类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) | 如果操作成功，则返回AuxiliaryPicture实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types; 3.Parameter verification failed. |

## 示例

ArkTS-Dyn示例:

```TypeScript
async function CreateAuxiliaryPicture(context: Context) {
  let funcName = "CreateAuxiliaryPicture";
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("hdr.jpg"); // 需要支持hdr的图片。
  let auxBuffer: ArrayBuffer = rawFile.buffer as ArrayBuffer;
  let auxSize: image.Size = {
    height: 180,
    width: 240
  };
  let auxType: image.AuxiliaryPictureType = image.AuxiliaryPictureType.GAINMAP;
  let auxPictureObj: image.AuxiliaryPicture | null = image.createAuxiliaryPicture(auxBuffer, auxSize, auxType);
  if(auxPictureObj != null) {
    let type: image.AuxiliaryPictureType = auxPictureObj.getType();
    console.info(funcName, `CreateAuxiliaryPicture succeeded this.Aux_picture.type ${type}`);
  } else {
    console.error(funcName, 'CreateAuxiliaryPicture failed');
  }
}
```

ArkTS-Sta示例:

```TypeScript
import { common } from '@kit.AbilityKit';
import { resourceManager } from '@kit.LocalizationKit';

function CreateAuxiliaryPictureFunc(context: common.UIAbilityContext): image.AuxiliaryPicture | undefined {
  const resourceMgr = context.resourceManager;
  // 此处'hdr_image.jpg'仅作示例，请开发者自行替换支持hdr的图片，否则auxiliaryPicture会创建失败导致后续无法正常执行。
  const rawFile = await resourceMgr.getRawFileContent("hdr_image.jpg");
  let auxBuffer: ArrayBuffer = rawFile.buffer as ArrayBuffer;
  let auxSize: image.Size = {
    height: 180,
    width: 240
  };
  let auxType: image.AuxiliaryPictureType = image.AuxiliaryPictureType.GAINMAP;
  try {
    let auxPicture: image.AuxiliaryPicture = image.createAuxiliaryPicture(auxBuffer, auxSize, auxType);
    if (auxPicture != undefined) {
      console.info(0x00000, 'CreateAuxiliaryPictureFunc', 'createAuxiliaryPicture success!');
    }
    return auxPicture;
  } catch (err) {
    console.error(0x00000, 'CreateAuxiliaryPictureFunc', 'CreateAuxiliaryPictureFunc failed: ' + err);
    return undefined;
  }
}
```

