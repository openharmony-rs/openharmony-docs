# transmitInfrared（系统接口）

## transmitInfrared

```TypeScript
function transmitInfrared(infraredFrequency: long, pattern: Array<long>): void
```

产生特定频率和特定电平大小的红外信号。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_INPUT_INFRARED_EMITTER

<!--Device-infraredEmitter-function transmitInfrared(infraredFrequency: long, pattern: Array<long>): void--><!--Device-infraredEmitter-function transmitInfrared(infraredFrequency: long, pattern: Array<long>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InfraredEmitter

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| infraredFrequency | long | 是 | 红外频率，单位：Hz。 |
| pattern | Array&lt;long&gt; | 是 | 红外电平信号，单位为微秒（μs）。电平信号的数量取值范围为[0,1024]，取值为0时，接口调用不生效。电平信号的取值需大于0。&lt;br/&gt;比如 [100,200,300,400]该电平信号数组，其中100μs为高电平信号、200μs为低电平信号、300μs为高电平信号、400μs为低电平信号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
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
            // 设置红外频率及红外电平信号模式
            infraredEmitter.transmitInfrared(38000, [100, 200, 300, 400]);
          } catch (error) {
            console.error(`Failed to transmit infrared signal, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
            // 设置红外载波频率及红外电平信号模式
            infraredEmitter.transmitInfrared(38000, [100, 200, 300, 400]);
          } catch (error) {
            console.error(`Failed to set infrared frequencies, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

