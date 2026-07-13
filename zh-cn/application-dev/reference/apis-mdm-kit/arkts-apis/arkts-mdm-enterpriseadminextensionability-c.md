# EnterpriseAdminExtensionAbility

本模块提供[企业设备管理扩展能力](../../../../mdm/mdm-kit-term.md#企业设备管理扩展能力)。

设备管理应用需要存在一个EnterpriseAdminExtensionAbility并重写相关接口，以此具备模块提供的各项能力，比如接收由系统发送的该应用被激活或者解除激活的通知。

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。

**起始版本：** 12

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## onAccountAdded

```TypeScript
onAccountAdded(accountId: number): void
```

系统账号新增事件回调。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_ACCOUNT_ADDED事件才能收到此回调。企业设备管理场景下，设备管理应用订阅系统账号新增事件，系统账号新增事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | 新增的用户ID。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAccountAdded(accountId: number) {
    console.info(`Succeeded in calling onAccountAdded callback, added accountId: ${accountId}`);
  }
}

```

## onAccountRemoved

```TypeScript
onAccountRemoved(accountId: number): void
```

系统账号删除事件回调。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_ACCOUNT_REMOVED事件才能收到此回调。企业设备管理场景下，设备管理应用订阅系统账号删除事件，系统账号删除事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | 被删除的用户ID。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAccountRemoved(accountId: number) {
    console.info(`Succeeded in calling onAccountRemoved callback, removed accountId: ${accountId}`);
  }
}

```

## onAccountSwitched

```TypeScript
onAccountSwitched(accountId: number): void
```

系统账号切换事件回调。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_ACCOUNT_SWITCHED事件才能收到此回调。企业设备管理场景下，设备管理应用订阅系统账号切换事件，系统账号切换事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员
。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | 切换后的用户ID。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAccountSwitched(accountId: number) {
    console.info(`Succeeded in calling onAccountSwitched callback, switched accountId: ${accountId}`);
  }
}

```

## onAdminDisabled

```TypeScript
onAdminDisabled(): void
```

当前设备管理应用被解除激活后，触发该回调。企业管理员或者员工解除激活设备管理，系统通知设备管理应用已解除激活admin权限。设备管理应用可在此回调函数中通知企业管理员设备已脱管。无需注册，解除激活后默认触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAdminDisabled() {
  }
}

```

## onAdminEnabled

```TypeScript
onAdminEnabled(): void
```

当前设备管理应用被激活后，触发该回调。企业管理员或者员工部署并激活设备管理应用，系统通知设备管理应用已激活admin权限。设备管理应用可在此回调函数中进行初始化策略设置。无需注册，激活后默认触发该回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAdminEnabled() {
  }
}

```

## onAdminPolicyChanged

```TypeScript
onAdminPolicyChanged(event: common.PolicyChangedEvent): void
```

策略变更时回调

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | common.PolicyChangedEvent | 是 | 策略变更事件 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility, common } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAdminPolicyChanged(event: common.PolicyChangedEvent) {
    // 例如当MDM应用调用setPasswordPolicy接口设置密码策略时，输出示例为: Policy changed, bundleName : com.example.test, functionName: setPasswordPolicy, parameters: {"policy":{"complexityRegex":"^(?=.*[a-zA-Z])(?=.*\\d).{8},$","validityPeriod":1808309786000,"additionalDescription":"至少8个字符，且包含数字和字母。"}}, time: 1776773305379.
    console.info(`Policy changed, bundleName : ${event.bundleName}, functionName: ${event.functionName}, parameters: ${event.parameters}, time: ${event.time}.`);
  }
}

```

## onAppStart

```TypeScript
onAppStart(bundleName: string): void
```

应用启动事件回调。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_APP_START事件才能收到此回调。企业设备管理场景下，设备管理应用订阅应用启动事件，端侧应用启动事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 启动应用的包名。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAppStart(bundleName: string) {
    console.info(`Succeeded in calling onAppStart callback, started bundle name : ${bundleName}`);
  }
}

```

## onAppStop

```TypeScript
onAppStop(bundleName: string): void
```

应用停止事件回调。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_APP_STOP事件才能收到此回调。企业设备管理场景下，设备管理应用订阅应用停止事件，端侧应用停止事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 停止应用的包名。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAppStop(bundleName: string) {
    console.info(`Succeeded in calling onAppStop callback, stopped bundle name : ${bundleName}`);
  }
}

```

## onBundleAdded

```TypeScript
onBundleAdded(bundleName: string): void
```

应用安装事件回调，回调中包含应用包名。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_BUNDLE_ADDED事件才能收到此回调。企业设备管理场景下，设备管理应用订阅应用安装事件，端侧应用安装事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 被安装应用的包名。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onBundleAdded(bundleName: string) {
    console.info(`Succeeded in calling onBundleAdded callback, added bundle name : ${bundleName}`);
  }
}

```

## onBundleAdded

```TypeScript
onBundleAdded(bundleName: string, accountId: number): void
```

应用安装事件回调，回调中包含应用包名和账号ID。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_BUNDLE_ADDED事件才能收到此回调。企业设备管理场景下，设备管理应用订阅应用安装事件，端侧应用安装事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 被安装应用的包名。 |
| accountId | number | 是 | 被安装应用所在的用户ID。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  // 由于存在同名回调方法onBundleAdded(bundleName: string)，该回调方法无accountId参数，因此在实际调用时accountId必须为可选参数，写法请参考示例代码。如果删除accountId后的问号"?"，编译会报错。
  onBundleAdded(bundleName: string, accountId?: number) {
    console.info(`Succeeded in calling onBundleAdded callback, added bundle name : ${bundleName}, accountId: ${accountId}`);
  }
}

```

## onBundleRemoved

```TypeScript
onBundleRemoved(bundleName: string): void
```

应用卸载事件回调，回调中包含应用包名。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_BUNDLE_REMOVED事件才能收到此回调。企业设备管理场景下，设备管理应用订阅应用卸载事件，端侧应用卸载事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 被卸载应用的包名。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onBundleRemoved(bundleName: string) {
    console.info(`Succeeded in calling onBundleRemoved callback, removed bundle name : ${bundleName}`);
  }
}

```

## onBundleRemoved

```TypeScript
onBundleRemoved(bundleName: string, accountId: number): void
```

应用卸载事件回调，回调中包含应用包名和账号ID。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_BUNDLE_REMOVED事件才能收到此回调。企业设备管理场景下，设备管理应用订阅应用卸载事件，端侧应用卸载事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 被卸载应用的包名。 |
| accountId | number | 是 | 被卸载应用所在的用户ID。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  // 由于存在同名回调方法onBundleRemoved(bundleName: string)，该回调方法无accountId参数，因此在实际调用时accountId必须为可选参数，写法请参考示例代码。如果删除accountId后的问号"?"，编译会报错。
  onBundleRemoved(bundleName: string, accountId?: number) {
    console.info(`Succeeded in calling onBundleRemoved callback, removed bundle name : ${bundleName}, accountId: ${accountId}`);
  }
}

```

## onBundleUpdated

```TypeScript
onBundleUpdated(bundleName: string, accountId: number): void
```

应用更新事件回调，回调中包含应用包名和用户ID。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_BUNDLE_UPDATED事件才能收到此回调。企业设备管理场景下，设备管理应用可订阅所有用户下的应用更新事件，应用更新事件触发时会通知当前用户下的设备管理应用，设备管理应用可以在此回调函数中进行事
件上报，通知主用户下的企业管理员。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 被更新应用的包名。 |
| accountId | number | 是 | 被更新应用所在的用户ID<br>取值范围为全体整数。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onBundleUpdated(bundleName: string, accountId: number) {
    console.info(`Succeeded in calling onBundleUpdated callback, update bundle name : ${bundleName}, accountId: ${accountId}`);
  }
}

```

## onDeviceAdminDisabled

```TypeScript
onDeviceAdminDisabled(bundleName: string): void
```

仅超级设备管理应用在普通设备管理应用被解除激活时会触发此回调。企业管理员或者员工解除激活普通设备管理应用，系统通知超级设备管理应用已解除激活admin权限。超级设备管理应用可在此回调函数中通知企业管理员设备已脱管。不需要注册，解除
激活后默认触发该回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 被解除激活应用的包名。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onDeviceAdminDisabled(bundleName: string) {
  }
}

```

## onDeviceAdminEnabled

```TypeScript
onDeviceAdminEnabled(bundleName: string): void
```

仅超级设备管理应用在普通设备管理应用被激活时会触发此回调。企业管理员或者员工部署并激活普通设备管理应用，系统通知超级设备管理应用已激活admin权限。超级设备管理应用可在此回调函数中进行初始化策略设置。不需要注册，激活后默认触发该
回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 被激活应用的包名。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onDeviceAdminEnabled(bundleName: string) {
  }
}

```

## onDeviceBootCompleted

```TypeScript
onDeviceBootCompleted(): void
```

设备开机完成事件回调。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_BOOT_COMPLETED事件才能收到此回调。企业设备管理场景下，设备管理应用订阅设备启动完成事件，端侧系统在设备开机完成后会通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业
管理员。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onDeviceBootCompleted() {
    console.info("EnterpriseAdminExtensionAbility onDeviceBootCompleted");
  }
}

```

## onKeyEvent

```TypeScript
onKeyEvent(keyEvent: systemManager.KeyEvent): void
```

按键事件发生时回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyEvent | systemManager.KeyEvent | 是 | Information about the current key event. |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';
import { systemManager } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {

 /* MDM应用下发按键事件监听后，用户按键行为匹配监听策略时，将触发该事件，事件回调携带当前匹配的按键信息。
  * 
  * 例如：
  * 1.用户短按电源键时触发回调（以电源键为例）
  * 1.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1。
  * 1.2 用户短按电源键
  * 1.3 触发回调
  * 结果：按下：onKeyEvent event:{"actionTime": 1895101259, "keyCode": 0, "keyAction": 0,
  *          "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 1895101259}]}
  *       抬起：onKeyEvent event:{"actionTime": 1895478977, "keyCode": 0, "keyAction": 1,
  *         "keyItems": [{"pressed": false, "keyCode": 0, "downTime": 1895101259}]}
  *
  * 2.用户长按电源键时触发回调（以电源键为例）
  * 2.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1。
  * 2.2 用户长按电源键
  * 2.3 触发回调
  * 结果：按下：onKeyEvent event:{"actionTime": 14468236859, "keyCode": 0, "keyAction": 0,
  *         "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 14468236859}]}
  *      长按：onKeyEvent event:{"actionTime": 14468236859, "keyCode": 0, "keyAction": 0,
  *         "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 14468236859}]}
  *          ......
  *       抬起：onKeyEvent event:{"actionTime": 14471425448, "keyCode": 0, "keyAction": 1,
  *         "keyItems": [{"pressed": false, "keyCode": 0, "downTime": 14468236859}]}
  * 
  * 组合键根据下发策略不同，分为下面多种场景：
  * 3.用户按组合键触发回调1（以电源键和音量+键为例）
  * 3.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1；keyCode为1，keyPolicy为1；
  * 3.2 用户同时按下电源键和音量+键
  * 3.3 触发回调
  * 结果：同时按下（电源键先，音量+键后）
  *      onKeyEvent event:{"actionTime": 20991450446, "keyCode": 1, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 20991432293}，
  *   {"pressed": true, "keyCode": 1, "downTime": 20991450446}]}
  *      同时抬起 （音量+键先，电源键后）
  *      onKeyEvent event:{"actionTime": 20590590293, "keyCode": 1, "keyAction": 1,
  *   "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 28588682984}，
  *   {"pressed": false, "keyCode": 1, "downTime": 21588900860}]}
  * 
  * 4.用户按组合键触发回调2（以电源键和音量+键为例）
  * 4.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1；keyCode为1，keyPolicy为0；
  * 4.2 用户同时按下电源键和音量+键
  * 4.3 触发回调
  * 结果：同时按下（音量+键先，电源键后）
  *      onKeyEvent event:{"actionTime": 28991115400, "keyCode": 0, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 1, "downTime": 28990731985}，
  *   {"pressed": true, "keyCode": 0, "downTime": 20991115400}]}
  *      同时抬起 （音量+键先，电源键后）
  *      onKeyEvent event:{"actionTime": 28992721560, "keyCode": 0, "keyAction": 1,
  *   "keyItems": [{"pressed": false, "keyCode": 0, "downTime": 28991115400}]}
  * 
  * 5.用户按组合键触发回调3（以电源键和音量+键为例）
  * 5.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1；
  * 5.2 用户同时按下电源键和音量+键
  * 5.3 触发回调
  * 结果：同时按下（音量+键先，电源键后）
  *      onKeyEvent event:{"actionTime": 29979014190, "keyCode": 0, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 1, "downTime": 29978420634}，
  *   {"pressed": true, "keyCode": 0, "downTime": 29979014190}]}
  *      同时抬起 （电源键先，音量+键后）
  *      onKeyEvent event:{"actionTime": 29982420773, "keyCode": 0, "keyAction": 1,
  *   "keyItems": [{"pressed": true, "keyCode": 1, "downTime": 29978420634}，
  *   {"pressed": false, "keyCode": 0, "downTime": 29979014190}]}
  * 
  * 6.用户按组合键触发回调4（以电源键和导航键-最近打开为例）
  * 6.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1；keyCode为5，keyPolicy为1；
  * 6.2 用户同时按下电源键和导航键-最近打开
  * 6.3 触发回调
  * 结果：同时按下（各自执行回调，互不影响）
  *      onKeyEvent event:{"actionTime": 34073626894, "keyCode": 0, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 34073626894}]}
  *      onKeyEvent event:{"actionTime": 34075144844, "keyCode": 5, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 5, "downTime": 0}]}
  */
  onKeyEvent(keyEvent: systemManager.KeyEvent): void {
    console.info(`Succeeded in calling onKeyEvent callback, key event:${JSON.stringify(keyEvent)}`);
  }
}

```

## onKioskModeEntering

```TypeScript
onKioskModeEntering(bundleName: string, accountId: number): void
```

应用进入Kiosk模式回调，回调中包含应用包名和用户ID。

Kiosk模式为系统层面提供的一种应用运行模式，该模式下会将设备锁定在单个应用或者一组应用运行，同时对锁屏状态、状态栏、手势操作和关键功能进行控制，防止用户在设备上启动其它应用或执行其它操作。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 进入Kiosk模式应用的包名。 |
| accountId | number | 是 | 进入Kiosk模式应用所在的用户ID。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onKioskModeEntering(bundleName: string, accountId: number): void {
    console.info(`Succeeded in calling onKioskModeEntering callback, bundleName:${bundleName}, accountId:${accountId}`);
  }
}

```

## onKioskModeExiting

```TypeScript
onKioskModeExiting(bundleName: string, accountId: number): void
```

应用退出Kiosk模式回调，回调中包含应用包名和用户ID。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 退出Kiosk模式应用的包名。 |
| accountId | number | 是 | 退出Kiosk模式应用所在的用户ID。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onKioskModeExiting(bundleName: string, accountId: number): void {
    console.info(`Succeeded in calling onKioskModeExiting callback, bundleName:${bundleName}, accountId:${accountId}`);
  }
}

```

## onLogCollected

```TypeScript
onLogCollected(result: common.Result): void
```

日志收集完成回调

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | common.Result | 是 | Log collection result. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { EnterpriseAdminExtensionAbility, common, systemManager } from '@kit.MDMKit';
import { fileIo as fs } from '@kit.CoreFileKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  /**
   * MDM应用调用systemManager.startCollectLog接口启动日志收集任务后，将触发该回调函数，回调携带日志收集结果。
   * 若result为common.Result.SUCCESS，表示日志收集成功。请取走日志，并调用systemManager.finishLogCollected删除已收集到的日志。
   * 若result为common.Result.FAIL，表示日志收集失败。
   */
  onLogCollected(result: common.Result): void {
    console.info(`Succeeded in calling onLogCollected callback, result:${result}`);
    if (result === common.Result.SUCCESS) {
      let filesDir = '/data/edm/log';
      // 应用沙箱路径，需根据实际情况进行替换
      let targetPath = this.context.tempDir;
      try {
        let files: string[] = fs.listFileSync(filesDir);
        // 从/data/edm/log沙箱目录取走日志
        files.forEach(value => {
          fs.copyFileSync(filesDir + '/' + value, targetPath + '/' + value);
        });
        let wantTemp: Want = {
          // 需根据实际情况进行替换
          bundleName: 'com.example.myapplication',
          abilityName: 'EnterpriseAdminAbility'
        };
        systemManager.finishLogCollected(wantTemp);
      } catch (error) {
        console.info("onLogCollected", "error: " + JSON.stringify(error))
      }
    }
    if (result === common.Result.FAIL) {
      console.error("onLogCollected", "Failed to collect log.")
    }
  }
}

```

## onMarketAppInstallResult

```TypeScript
onMarketAppInstallResult(bundleName: string, result: common.InstallationResult): void
```

安装应用市场应用接口[bundleManager.installMarketApps](arkts-mdm-installmarketapps-f.md#installmarketapps-1)安装
结果回调，回调中包含应用包名和安装结果。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用市场应用包名。 |
| result | common.InstallationResult | 是 | 安装结果。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility, common } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onMarketAppInstallResult(bundleName: string, result: common.InstallationResult): void {
    console.info(`Succeeded in calling onMarketAppInstallResult callback, bundleName:${bundleName}, result:${result}`);
  }
}

```

## onStart

```TypeScript
onStart(): void
```

EnterpriseAdminExtensionAbility启动事件回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onStart() {
    console.info(`Succeeded in calling onStart callback.`);
  }
}

```

## onStartupGuideCompleted

```TypeScript
onStartupGuideCompleted(scene: common.StartupScene): void
```

开机向导完成事件回调。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_STARTUP_GUIDE_COMPLETED事件才能收到此回调。企业设备管理场景下，设备管理应用订阅开机向导完成事件，端侧系统在首次切换子用户完成（仅限PC）、OTA升级完成、首次开机完成开机向导
时会通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scene | common.StartupScene | 是 | 开机向导完成场景。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility, common } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onStartupGuideCompleted(scene: common.StartupScene) {
    if (scene === common.StartupScene.USER_SETUP) {
      console.info('onStartupGuideCompleted scene is USER_SETUP');
    } else if (scene === common.StartupScene.OTA) {
      console.info('onStartupGuideCompleted scene is OTA');
    } else if (scene === common.StartupScene.DEVICE_PROVISION) {
      console.info('onStartupGuideCompleted scene is DEVICE_PROVISION');
    }
  }
}

```

## onSystemUpdate

```TypeScript
onSystemUpdate(systemUpdateInfo: systemManager.SystemUpdateInfo): void
```

系统更新事件回调。通过接口
[adminManager.subscribeManagedEventSync](arkts-mdm-subscribemanagedeventsync-f.md#subscribemanagedeventsync-1)
注册MANAGED_EVENT_SYSTEM_UPDATE事件才能收到此回调。企业设备管理场景下，设备管理应用订阅系统更新事件，端侧系统更新事件通知设备管理应用，设备管理应用可以在此回调函数中进行事件上报，通知企业管理员。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| systemUpdateInfo | systemManager.SystemUpdateInfo | 是 | 系统更新的版本信息。 |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';
import { systemManager } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onSystemUpdate(systemUpdateInfo: systemManager.SystemUpdateInfo) {
    console.info(`Succeeded in calling onSystemUpdate callback, version name  : ${systemUpdateInfo.versionName}`);
  }
}

```

## context

```TypeScript
context: EnterpriseAdminExtensionContext
```

EnterpriseAdminExtensionAbility的上下文。继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

**类型：** EnterpriseAdminExtensionContext

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

