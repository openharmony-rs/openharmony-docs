# SystemDefinedPixelMap

与系统侧定义的[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)数据类型对应的图片数据类型，是 [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)的子类，仅保存PixelMap的二进制数据。

**继承/实现关系：** SystemDefinedPixelMap extends [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## rawData

```TypeScript
set rawData(value: Uint8Array)
```

PixelMap对象的二进制数据。

**类型：** Uint8Array

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**示例**

```TypeScript
import { image } from '@kit.ImageKit'; // PixelMap类定义所在模块
import { unifiedDataChannel, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

const color = new ArrayBuffer(96); // 创建pixelMap对象
let opts: image.InitializationOptions = {
  editable: true, pixelFormat: 3, size: {
    height: 4, width: 6
  }
}
image.createPixelMap(color, opts, (error, pixelMap) => {
  if (error) {
    console.error('Failed to create pixelMap.');
  } else {
    console.info('Succeeded in creating pixelMap.');
    let arrayBuf = new ArrayBuffer(pixelMap.getPixelBytesNumber());
    pixelMap.readPixelsToBuffer(arrayBuf);
    let u8Array = new Uint8Array(arrayBuf);
    let sdPixel = new unifiedDataChannel.SystemDefinedPixelMap();
    sdPixel.rawData = u8Array;
    let unifiedData = new unifiedDataChannel.UnifiedData(sdPixel);

    // 从unifiedData中读取pixelMap类型的record
    let records = unifiedData.getRecords();
    for (let i = 0; i < records.length; i++) {
      if (records[i].getType() === uniformTypeDescriptor.UniformDataType.OPENHARMONY_PIXEL_MAP) {
        let pixelMapRecord = records[i] as unifiedDataChannel.SystemDefinedPixelMap;
        let newArrayBuf = pixelMapRecord.rawData.buffer;
        pixelMap.writeBufferToPixels(newArrayBuf).then(() => {
          console.info('Succeeded in writing data from buffer to a pixelMap');
        }).catch((error: BusinessError) => {
          console.error(`Failed to write data from a buffer to a PixelMap. code is ${error.code}, message is ${error.message}`);
        })
      }
    }
  }
})
```
