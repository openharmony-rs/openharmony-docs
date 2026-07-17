# isOpenTouchGuide

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

## isOpenTouchGuide

```TypeScript
function isOpenTouchGuide(callback: AsyncCallback<boolean>): void
```

判断触摸浏览模式是否开启，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [isOpenTouchGuideSync](arkts-accessibility-accessibility-isopentouchguidesync-f.md#isopentouchguidesync-1)

<!--Device-accessibility-function isOpenTouchGuide(callback: AsyncCallback<boolean>): void--><!--Device-accessibility-function isOpenTouchGuide(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Vision

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数，如果触摸浏览模式已开启，则返回 true；否则返回 false。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`failed to isOpenTouchGuide, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
});

```


## isOpenTouchGuide

```TypeScript
function isOpenTouchGuide(): Promise<boolean>
```

判断触摸浏览模式是否开启，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [isOpenTouchGuideSync](arkts-accessibility-accessibility-isopentouchguidesync-f.md#isopentouchguidesync-1)

<!--Device-accessibility-function isOpenTouchGuide(): Promise<boolean>--><!--Device-accessibility-function isOpenTouchGuide(): Promise<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Vision

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象，如果触摸浏览模式已开启，则返回 true；否则返回 false。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide().then((data: boolean) => {
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to  isOpenTouchGuide, Code is ${err.code}, message is ${err.message}`);
});

```

