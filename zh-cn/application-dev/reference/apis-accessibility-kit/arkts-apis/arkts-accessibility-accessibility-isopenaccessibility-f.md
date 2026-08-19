# isOpenAccessibility

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
import { GesturePath } from '@kit.AccessibilityKit';
import { GesturePoint } from '@kit.AccessibilityKit';
```

## isOpenAccessibility

```TypeScript
function isOpenAccessibility(callback: AsyncCallback<boolean>): void
```

判断是否启用了辅助应用。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [isOpenAccessibilitySync](arkts-accessibility-accessibility-isopenaccessibilitysync-f.md)

<!--Device-accessibility-function isOpenAccessibility(callback: AsyncCallback<boolean>): void--><!--Device-accessibility-function isOpenAccessibility(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示辅助应用已启用；返回false表示辅助应用未启用。 |

**示例**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`Failed to isOpenAccessibility. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`);
});
```


## isOpenAccessibility

```TypeScript
function isOpenAccessibility(): Promise<boolean>
```

判断是否启用了辅助应用。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [isOpenAccessibilitySync](arkts-accessibility-accessibility-isopenaccessibilitysync-f.md)

<!--Device-accessibility-function isOpenAccessibility(): Promise<boolean>--><!--Device-accessibility-function isOpenAccessibility(): Promise<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示辅助应用已启用；返回false表示辅助应用未启用。 |

**示例**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility().then((data: boolean) => {
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to isOpenAccessibility. Code: ${err.code}, message: ${err.message}`);
});
```

