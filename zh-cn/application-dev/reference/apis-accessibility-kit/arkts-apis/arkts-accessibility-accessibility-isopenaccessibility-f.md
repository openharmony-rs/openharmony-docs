# isOpenAccessibility

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## isOpenAccessibility

```TypeScript
function isOpenAccessibility(callback: AsyncCallback<boolean>): void
```

判断是否启用了辅助应用，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [isOpenAccessibilitySync](arkts-accessibility-accessibility-isopenaccessibilitysync-f.md#isopenaccessibilitysync-1)

<!--Device-accessibility-function isOpenAccessibility(callback: AsyncCallback<boolean>): void--><!--Device-accessibility-function isOpenAccessibility(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数，如果辅助应用已启用，则返回 true；否则返回 false。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`failed to isOpenAccessibility, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`);
});

```


## isOpenAccessibility

```TypeScript
function isOpenAccessibility(): Promise<boolean>
```

判断是否启用了辅助应用，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [isOpenAccessibilitySync](arkts-accessibility-accessibility-isopenaccessibilitysync-f.md#isopenaccessibilitysync-1)

<!--Device-accessibility-function isOpenAccessibility(): Promise<boolean>--><!--Device-accessibility-function isOpenAccessibility(): Promise<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象，如果辅助应用已启用，则返回 true；否则返回 false。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility().then((data: boolean) => {
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`)
}).catch((err: BusinessError) => {
  console.error(`failed to  isOpenAccessibility, Code is ${err.code}, message is ${err.message}`);
});

```

