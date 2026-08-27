# getInfraredFrequencies

## 导入模块

```TypeScript
```

## getInfraredFrequencies

```TypeScript
function getInfraredFrequencies(): Array<InfraredFrequency>
```

查询设备支持的红外信号的频率范围。建议先使用[hasIrEmitter]接口查询设备是否支持红外发射器。

**起始版本：** 15

**需要权限：** ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

**系统能力：** SystemCapability.MultimodalInput.Input.InfraredEmitter

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[InfraredFrequency](arkts-input-infraredemitter-infraredfrequency-i.md)&gt; | 红外信号的频率范围，包含多组最大和最小频率。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application.<br>**适用版本：** 12 - 14 |

**示例**

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
