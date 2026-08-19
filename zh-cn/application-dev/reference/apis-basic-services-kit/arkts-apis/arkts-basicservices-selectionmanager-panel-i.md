# Panel（系统接口）

划词面板对象，通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md)创建，提供面板内容设置、显示、隐藏、移动及事件订阅等管理能力，适用于在划词完成后向用户展示自定义操作界面的场景。

**起始版本：** 24

<!--Device-selectionManager-interface Panel--><!--Device-selectionManager-interface Panel-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## moveToGlobalDisplay

```TypeScript
moveToGlobalDisplay(x: int, y: int): Promise<void>
```

移动划词面板至屏幕全局坐标系下的指定位置，支持移动到扩展屏上。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md)获取到Panel实例后调用。使用Promise异步回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-moveToGlobalDisplay(x: int, y: int): Promise<void>--><!--Device-Panel-moveToGlobalDisplay(x: int, y: int): Promise<void>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | int | 是 | 目标位置在屏幕全局坐标系下的x轴坐标，单位为px。全局坐标系以主屏幕左上角为原点，x轴正方向向右；扩展屏的x坐标视屏幕布局可能为负值。 |
| y | int | 是 | 目标位置在屏幕全局坐标系下的y轴坐标，单位为px。全局坐标系以主屏幕左上角为原点，y轴正方向向下；扩展屏的y坐标视屏幕布局可能为负值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-划词服务调用异常) | Selection service exception. |
| [33600002](../errorcode-selection.md#33600002-划词面板已被销毁) | This selection window has been destroyed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 移动划词面板至屏幕指定位置。selectionPanel为createPanel创建出的panel实例
  selectionPanel.moveToGlobalDisplay(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 移动划词面板至屏幕指定位置。selectionPanel为createPanel创建出的panel实例
  selectionPanel?.moveToGlobalDisplay(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err) => {
    console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
}
```

## offDestroy

```TypeScript
offDestroy(callback?: Callback<void>): void
```

取消订阅划词面板销毁事件，与[onDestroy](#ondestroy)搭配使用。需通过 [createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md)获取到Panel实例后调用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-offDestroy(callback?: Callback<void>): void--><!--Device-Panel-offDestroy(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要取消的回调函数（即之前通过onDestroy方法订阅时的回调实例）。参数不填写时，取消订阅对应的所有回调事件。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 取消订阅划词面板销毁事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel?.offDestroy();
} catch (err) {
  console.error(`Failed to unregister destroyed. Error code: ${err.code}, error message: ${err.message}`);
}
```

## offHide

```TypeScript
offHide(callback?: Callback<void>): void
```

取消订阅划词面板隐藏事件，与[onHide](#onhide)搭配使用。需通过 [createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md)获取到Panel实例后调用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-offHide(callback?: Callback<void>): void--><!--Device-Panel-offHide(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要取消的回调函数（即之前通过onHide方法订阅时的回调实例）。参数不填写时，取消订阅对应的所有回调事件。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 取消订阅划词面板隐藏事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel?.offHide();
} catch (err) {
  console.error(`Failed to unregister hidden. Error code: ${err.code}, error message: ${err.message}`);
}
```

## onDestroy

```TypeScript
onDestroy(callback: Callback<void>): void
```

订阅划词面板销毁事件，与[offDestroy](#offdestroy)搭配使用。需通过 [createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md)获取到Panel实例后调用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-onDestroy(callback: Callback<void>): void--><!--Device-Panel-onDestroy(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，调用[destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f-sys.md)销毁面板时触发。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 订阅划词面板销毁事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel?.onDestroy(() => {
    console.info('Panel has been destroyed.');
  });
} catch (err) {
  console.error(`Failed to register destroyed callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

## onHide

```TypeScript
onHide(callback: Callback<void>): void
```

订阅划词面板隐藏事件，与[offHide](#offhide)搭配使用。需通过 [createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md)获取到Panel实例后调用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-onHide(callback: Callback<void>): void--><!--Device-Panel-onHide(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，面板隐藏时触发。面板可通过调用[hide](arkts-basicservices-selectionmanager-panel-i-sys.md#hide)主动隐藏，或在失焦时自动隐藏。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 订阅划词面板隐藏事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel?.onHide(() => {
    console.info('Panel has been hidden.');
  });
} catch (err) {
  console.error(`Failed to register hidden callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

