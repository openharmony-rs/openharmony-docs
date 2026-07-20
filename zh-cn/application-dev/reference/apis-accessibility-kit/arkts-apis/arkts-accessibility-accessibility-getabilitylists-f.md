# getAbilityLists

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

<a id="getabilitylists"></a>
## getAbilityLists

```TypeScript
function getAbilityLists(
    abilityType: AbilityType,
    stateType: AbilityState,
    callback: AsyncCallback<Array<AccessibilityAbilityInfo>>
  ): void
```

查询辅助应用列表，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getAccessibilityExtensionList(abilityType:](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md#getaccessibilityextensionlist-1)

<!--Device-accessibility-function getAbilityLists(
    abilityType: AbilityType,
    stateType: AbilityState,
    callback: AsyncCallback<Array<AccessibilityAbilityInfo>>
  ): void--><!--Device-accessibility-function getAbilityLists(
    abilityType: AbilityType,
    stateType: AbilityState,
    callback: AsyncCallback<Array<AccessibilityAbilityInfo>>
  ): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityType | [AbilityType](arkts-accessibility-accessibility-abilitytype-t.md) | 是 | 辅助应用的类型。 |
| stateType | [AbilityState](arkts-accessibility-accessibility-abilitystate-t.md) | 是 | 辅助应用的状态。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt; | 是 | 回调函数，返回辅助应用信息列表。若返回成功，err为undefined，data为辅助应用信息列表；否则为错误对象。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState, (err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
})

```


<a id="getabilitylists-1"></a>
## getAbilityLists

```TypeScript
function getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise<Array<AccessibilityAbilityInfo>>
```

查询辅助应用列表，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getAccessibilityExtensionList(abilityType:](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md#getaccessibilityextensionlist-1)

<!--Device-accessibility-function getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise<Array<AccessibilityAbilityInfo>>--><!--Device-accessibility-function getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise<Array<AccessibilityAbilityInfo>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityType | [AbilityType](arkts-accessibility-accessibility-abilitytype-t.md) | 是 | 辅助应用的类型。 |
| stateType | [AbilityState](arkts-accessibility-accessibility-abilitystate-t.md) | 是 | 辅助应用的状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt; | Promise对象，返回辅助应用信息列表。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
});

```

