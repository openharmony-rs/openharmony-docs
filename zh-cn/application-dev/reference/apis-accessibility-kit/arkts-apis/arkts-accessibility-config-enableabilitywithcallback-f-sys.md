# enableAbilityWithCallback（系统接口）

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## enableAbilityWithCallback

```TypeScript
function enableAbilityWithCallback(name: string, capability: Array<accessibility.Capability>, connectCallback: ConnectCallback): Promise<void>
```

启用辅助扩展，并指定[ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md)作为辅助扩展应用状态变化的回调函数。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-config-function enableAbilityWithCallback(name: string, capability: Array<accessibility.Capability>, connectCallback: ConnectCallback): Promise<void>--><!--Device-config-function enableAbilityWithCallback(name: string, capability: Array<accessibility.Capability>, connectCallback: ConnectCallback): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 辅助扩展应用的名称，格式为：'bundleName/abilityName'。 |
| capability | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<accessibility.Capability> | 是 | 辅助扩展应用的能力属性。 |
| connectCallback | [ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md) | 是 | 辅助扩展应用的状态发生变化时调用的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [9300001](../errorcode-accessibility.md#9300001-输入无效的包名称或者ability名称) | Invalid bundle name or ability name. |
| [9300002](../errorcode-accessibility.md#9300002-目标ability已启用) | Target ability already enabled. |

**示例：**

```TypeScript
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];
let connectCallback: config.ConnectCallback = {
  onDisconnect: () => {
    console.info(`Ability is disconnected.`)
  }
}

config.enableAbilityWithCallback(name, capability, connectCallback).then(() => {
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`);
}).catch((err: BusinessError) => {
  console.error(`failed to enable ability, Code is ${err.code}, message is ${err.message}`);
});

```

