# Panel（系统接口）

划词面板对象，通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)创建，提供面板内容设置、显示、隐藏、移动及事件订阅等管理能力，适用于在划词完成后向用户展示自定义操作界面的场景。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-selectionManager-interface Panel--><!--Device-selectionManager-interface Panel-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## hide

```TypeScript
hide(): Promise<void>
```

隐藏当前划词面板，与[show](#show)搭配使用。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)获取到 Panel实例后调用。使用Promise异步回调。如不主动调用，面板在失焦时会自动隐藏。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-Panel-hide(): Promise<void>--><!--Device-Panel-hide(): Promise<void>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务调用异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-划词面板已被销毁) | This selection window has been destroyed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 隐藏划词面板。selectionPanel为createPanel创建出的panel实例
selectionPanel.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 隐藏划词面板。selectionPanel为createPanel创建出的panel实例
selectionPanel?.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err) => {
  console.error(`Failed to hide panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

## moveTo

```TypeScript
moveTo(x: int, y: int): Promise<void>
```

移动划词面板至屏幕全局坐标系下的指定位置，支持移动到扩展屏上。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)获取到Panel实例后调用。使用Promise异步回调。 > **说明：** > > 从API version 20开始支持，从API version 24开始废弃。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** 24

**替代接口：** [moveToGlobalDisplay](arkts-basicservices-selectionmanager-panel-i.md#moveToGlobalDisplay)

<!--Device-Panel-moveTo(x: int, y: int): Promise<void>--><!--Device-Panel-moveTo(x: int, y: int): Promise<void>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

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
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务调用异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-划词面板已被销毁) | This selection window has been destroyed. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 移动划词面板至屏幕指定位置。selectionPanel为createPanel创建出的panel实例
  selectionPanel.moveTo(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel. Error code: ${err.code}, error message: ${err.message}`);
}
```

## off_destroyed

```TypeScript
off(type: 'destroyed', callback?: Callback<void>): void
```

取消订阅划词面板销毁事件，与[on('destroyed')](#on_destroyed)搭配使 用。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)获取到Panel实例后调用。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-Panel-off(type: 'destroyed', callback?: Callback<void>): void--><!--Device-Panel-off(type: 'destroyed', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'destroyed' | 是 | 取消订阅的事件类型，固定取值为'destroyed'。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要取消的回调函数（即之前通过on方法订阅时的回调实例）。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
try {
  // 取消订阅划词面板销毁事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel.off('destroyed');
} catch (err) {
  console.error(`Failed to unregister destroyed. Error code: ${err.code}, error message: ${err.message}`);
}
```

## off_hidden

```TypeScript
off(type: 'hidden', callback?: Callback<void>): void
```

取消订阅划词面板隐藏事件，与[on('hidden')](#on_destroyed)搭配使用。需通过 [createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)获取到Panel实例后调用。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-Panel-off(type: 'hidden', callback?: Callback<void>): void--><!--Device-Panel-off(type: 'hidden', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hidden' | 是 | 取消订阅的事件类型，固定取值为'hidden'。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要取消的回调函数（即之前通过on方法订阅时的回调实例）。参数不填写时，取消订阅type对应的所有回调事件。 |

## 示例

```TypeScript
try {
  // 取消订阅划词面板隐藏事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel.off('hidden');
} catch (err) {
  console.error(`Failed to unregister hidden. Error code: ${err.code}, error message: ${err.message}`);
}
```

## on_destroyed

```TypeScript
on(type: 'destroyed', callback: Callback<void>): void
```

订阅划词面板销毁事件，与[off('destroyed')](#off_destroyed)搭配使 用。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)获取到Panel实例后调用。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-Panel-on(type: 'destroyed', callback: Callback<void>): void--><!--Device-Panel-on(type: 'destroyed', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'destroyed' | 是 | 设置监听类型，固定取值为'destroyed'。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，调用[destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f-sys.md#destroyPanel（系统接口）)销毁面板时触发。 |

## 示例

```TypeScript
try {
  // 订阅划词面板销毁事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel.on('destroyed', () => {
    console.info('Panel has been destroyed.');
  });
} catch (err) {
  console.error(`Failed to register destroyed callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

## on_hidden

```TypeScript
on(type: 'hidden', callback: Callback<void>): void
```

订阅划词面板隐藏事件，与[off('hidden')](#off_destroyed)搭配使用。面板调用 [hide](#hide)隐藏或失焦自动隐藏时触发该事件。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)获取到 Panel实例后调用。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

<!--Device-Panel-on(type: 'hidden', callback: Callback<void>): void--><!--Device-Panel-on(type: 'hidden', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hidden' | 是 | 设置监听类型，固定取值为'hidden'。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，面板隐藏时触发。面板可通过调用[hide](#hide)主动隐藏，或在失焦时自动隐藏。 |

## 示例

```TypeScript
try {
  // 订阅划词面板隐藏事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel.on('hidden', () => {
    console.info('Panel has been hidden.');
  });
} catch (err) {
  console.error(`Failed to register hidden callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

## setUiContent

```TypeScript
setUiContent(path: string): Promise<void>
```

为当前的划词面板设置界面内容，例如展示翻译结果、搜索建议或自定义操作按钮等。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)获取到Panel实例后调用。使用Promise 异步回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-setUiContent(path: string): Promise<void>--><!--Device-Panel-setUiContent(path: string): Promise<void>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 要加载到面板中的页面内容的路径，Stage模型下该路径需添加到工程的resources/base/profile/main_pages.json文件中，不支持FA模型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务调用异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-划词面板已被销毁) | This selection window has been destroyed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 为划词面板加载页面内容。selectionPanel为createPanel创建出的panel实例
  selectionPanel.setUiContent('pages/Index').then(() => {
    console.info('Succeeded in setting the content.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 为划词面板加载页面内容。selectionPanel为createPanel创建出的panel实例
  selectionPanel?.setUiContent('pages/Index').then(() => {
    console.info('Succeeded in setting the content.');
  }).catch((err) => {
    console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to setUiContent. Error code: ${err.code}, error message: ${err.message}`);
}
```

## show

```TypeScript
show(): Promise<void>
```

显示划词面板，与[hide](#hide)搭配使用。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)获取到 Panel实例后调用。使用Promise异步回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-show(): Promise<void>--><!--Device-Panel-show(): Promise<void>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务调用异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-划词面板已被销毁) | This selection window has been destroyed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 显示划词面板。selectionPanel为createPanel创建出的panel实例
selectionPanel.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 显示划词面板。selectionPanel为createPanel创建出的panel实例
selectionPanel?.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err) => {
  console.error(`Failed to show panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

## startMoving

```TypeScript
startMoving(): Promise<void>
```

设置划词面板可随鼠标、触控板或触屏拖动移动位置，指针释放后自动停止移动。需通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)获取到Panel实例后调用。使用Promise异步 回调。该接口需在onTouch的回调函数中调用，并且事件类型为TouchType.Down。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Panel-startMoving(): Promise<void>--><!--Device-Panel-startMoving(): Promise<void>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务调用异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-划词面板已被销毁) | This selection window has been destroyed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 此代码需放置在ArkUI页面组件的build()方法中，RelativeContainer为ArkUI内置组件，TouchEvent和TouchType为ArkUI框架内置类型
RelativeContainer() {
  /* 
   * 页面布局内容，需要开发者根据实际补充
   */
}
.onTouch((event: TouchEvent) => {
  if (event.type === TouchType.Down) {
    if (selectionPanel !== undefined) {
      // 使划词面板可随鼠标、触控板或触屏拖动移动位置。selectionPanel为createPanel创建出的panel实例
      selectionPanel.startMoving().then(() => {
        console.info('Succeeded in startMoving the panel.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to startMoving panel. Error code: ${err.code}, error message: ${err.message}`);
      });
    }
  }
})
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 此代码需放置在ArkUI页面组件的build()方法中，RelativeContainer为ArkUI内置组件，TouchEvent和TouchType为ArkUI框架内置类型
RelativeContainer() {
  /* 
   * 页面布局内容，需要开发者根据实际补充
   */
}
.onTouch((event: TouchEvent) => {
  if (event.type === TouchType.Down) {
    if (selectionPanel !== undefined) {
      // 使划词面板可随鼠标、触控板或触屏拖动移动位置。selectionPanel为createPanel创建出的panel实例
      selectionPanel?.startMoving().then(() => {
        console.info('Succeeded in startMoving the panel.');
      }).catch((err) => {
        console.error(`Failed to startMoving panel. Error code: ${err.code}, error message: ${err.message}`);
      });
    }
  }
})
```

