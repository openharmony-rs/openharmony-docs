# getPowerConfig（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

<a id="getpowerconfig"></a>
## getPowerConfig

```TypeScript
function getPowerConfig(sceneName: string): string
```

按场景名称查询电源配置值。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.POWER_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-power-function getPowerConfig(sceneName: string): string--><!--Device-power-function getPowerConfig(sceneName: string): string-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sceneName | string | 是 | 电源配置的场景名称。最大长度128字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回电源配置值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../../apis-basic-services-kit/errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
| [4900400](../../apis-basic-services-kit/errorcode-power.md#4900400-接口入参无效) | Invalid parameter. Possible causes:1. The sceneName parameter is an empty string;2. The length of sceneName parameter exceeds 128 bytes. |
| [4900501](../../apis-basic-services-kit/errorcode-power.md#4900501-读电源配置值失败) | Failed to read the power configuration value. |

**示例：**

```TypeScript
try {
    let configVal = power.getPowerConfig('scene_name_test');
    console.info('get power config success, configVal: ' + configVal);
} catch (err) {
    console.error(`Failed to get power config. Code: ${err.code}, message: ${err.message}`);
}

```

