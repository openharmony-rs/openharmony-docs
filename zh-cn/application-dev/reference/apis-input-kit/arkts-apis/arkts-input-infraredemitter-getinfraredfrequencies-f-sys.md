# getInfraredFrequencies（系统接口）

## getInfraredFrequencies

```TypeScript
function getInfraredFrequencies(): Array<InfraredFrequency>
```

查询设备支持的红外信号的频率范围。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

<!--Device-infraredEmitter-function getInfraredFrequencies(): Array<InfraredFrequency>--><!--Device-infraredEmitter-function getInfraredFrequencies(): Array<InfraredFrequency>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InfraredEmitter

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[InfraredFrequency](arkts-input-infraredemitter-infraredfrequency-i-sys.md)&gt; | 红外信号的频率范围，包含多组最大和最小频率。&lt;br/&gt;从API version 23开始，当设备不具有红外发射器，返回一组最大和最小频率，且均为0Hz。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application.<br>**适用版本：** 12 - 14 |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
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

