# getAbilityLists

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [accessibility.getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md#getaccessibilityextensionlist)(abilityType:

<!--Device-accessibility-function getAbilityLists(    abilityType: AbilityType,    stateType: AbilityState,    callback: AsyncCallback<Array<AccessibilityAbilityInfo>>  ): void--><!--Device-accessibility-function getAbilityLists(    abilityType: AbilityType,    stateType: AbilityState,    callback: AsyncCallback<Array<AccessibilityAbilityInfo>>  ): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 辅助应用的类型。 |
| stateType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 辅助应用的状态。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt; | 是 | 回调函数，返回辅助应用信息列表。若返回成功，err为undefined，data为辅助应用信息列表；否则为错误对象。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState, (err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
});
```


## getAbilityLists

```TypeScript
function getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise<Array<AccessibilityAbilityInfo>>
```

查询辅助应用列表，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [accessibility.getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md#getaccessibilityextensionlist)(abilityType:

<!--Device-accessibility-function getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise<Array<AccessibilityAbilityInfo>>--><!--Device-accessibility-function getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise<Array<AccessibilityAbilityInfo>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 辅助应用的类型。 |
| stateType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 辅助应用的状态。 |

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
  console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
});
```

