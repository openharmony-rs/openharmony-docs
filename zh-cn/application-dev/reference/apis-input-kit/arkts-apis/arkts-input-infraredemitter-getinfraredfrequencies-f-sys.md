# getInfraredFrequencies（系统接口）

## 导入模块

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
```

## getInfraredFrequencies

```TypeScript
function getInfraredFrequencies(): Array<InfraredFrequency>
```

查询设备支持的红外信号的频率范围。

**起始版本：** 15

**需要权限：** ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

<!--Device-infraredEmitter-function getInfraredFrequencies(): Array<InfraredFrequency>--><!--Device-infraredEmitter-function getInfraredFrequencies(): Array<InfraredFrequency>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InfraredEmitter

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<InfraredFrequency> | 红外信号的频率范围，包含多组最大和最小频率。<br/>从API version 23开始，当设备不具有红外发射器，返回一组最大和最小频率，且均为0Hz。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application.<br>**适用版本：** 12 - 14 |

**示例：**

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let frequencies = infraredEmitter.getInfraredFrequencies();
            console.info(`Succeeded in getting infrared frequencies, frequencies: ${JSON.stringify(frequencies)}.`);
          } catch (error) {
            console.error(`Failed to get infrared frequencies, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

