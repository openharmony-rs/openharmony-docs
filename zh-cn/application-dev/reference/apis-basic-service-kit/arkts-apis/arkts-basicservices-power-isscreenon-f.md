# isScreenOn

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## isScreenOn

```TypeScript
function isScreenOn(callback: AsyncCallback<boolean>): void
```

检测当前设备的亮灭屏状态。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isActive](arkts-basicservices-power-isactive-f.md#isactive)

<!--Device-power-function isScreenOn(callback: AsyncCallback<boolean>): void--><!--Device-power-function isScreenOn(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当检测成功，err为undefined，data为获取到的亮灭屏状态，返回true表示亮屏，返回false表示灭屏；否则为错误对象。 |

**示例：**

```TypeScript
power.isScreenOn((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`Failed to check screen status. Code: ${err.code}, message: ${err.message}`);
        return;
    }
    console.info('screen on status is ' + data);
});

```


## isScreenOn

```TypeScript
function isScreenOn(): Promise<boolean>
```

检测当前设备的亮灭屏状态。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isActive](arkts-basicservices-power-isactive-f.md#isactive)

<!--Device-power-function isScreenOn(): Promise<boolean>--><!--Device-power-function isScreenOn(): Promise<boolean>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示亮屏；返回false表示灭屏。 |

**示例：**

```TypeScript
power.isScreenOn()
.then((data: boolean) => {
    console.info('screen on status is ' + data);
})
.catch((err: BusinessError) => {
    console.error(`Failed to check screen status. Code: ${err.code}, message: ${err.message}`);
});

```

