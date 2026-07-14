# Panel（系统接口）

划词面板。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## hide

```TypeScript
hide(): Promise<void>
```

隐藏当前划词面板。使用Promise异步回调。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-此划词窗口已被销毁) | This selection window has been destroyed. |

**示例：**

```TypeScript
import { selectionManager, BusinessError } from '@kit.BasicServicesKit';

selectionPanel.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide panel: ${err.code}, error message: ${err.message}`);
});

```

## moveTo

```TypeScript
moveTo(x: number, y: number): Promise<void>
```

移动划词面板至屏幕指定位置。使用Promise异步回调。

> **说明：**
> 从API version 20开始支持，从API version 24开始废弃。建议使用
> [moveToGlobalDisplay](arkts-basicservices-panel-i.md#movetoglobaldisplay-1)替代。

**起始版本：** 20

**废弃版本：** 24

**替代接口：** [moveToGlobalDisplay](arkts-basicservices-panel-i.md#movetoglobaldisplay-1)

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | x轴方向移动的值，单位为px。 |
| y | number | 是 | y轴方向移动的值，单位为px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-此划词窗口已被销毁) | This selection window has been destroyed. |

**示例：**

```TypeScript
import { selectionManager, BusinessError } from '@kit.BasicServicesKit';

try {
  selectionPanel.moveTo(200, 200).then(() => {
    console.info('Succeeded in moving the panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to move panel: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to move panel: ${err.code}, error message: ${err.message}`);
}

```

## off('destroyed')

```TypeScript
off(type: 'destroyed', callback?: Callback<void>): void
```

取消订阅划词窗口销毁事件。使用callback异步回调。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'destroyed' | 是 | 设置监听类型，固定取值为'destroyed'。 |
| callback | Callback&lt;void&gt; | 否 | 回调函数，返回值为空。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { selectionManager, BusinessError } from '@kit.BasicServicesKit';

try {
  selectionPanel.off('destroyed');
} catch (err) {
  console.error(`Failed to unregister destroyed: ${err.code}, error message: ${err.message}`);
}

```

## off('hidden')

```TypeScript
off(type: 'hidden', callback?: Callback<void>): void
```

取消订阅划词窗口隐藏事件。使用callback异步回调。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hidden' | 是 | 设置监听类型，固定取值为'hidden'。 |
| callback | Callback&lt;void&gt; | 否 | 回调函数，返回值为空。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { selectionManager, BusinessError } from '@kit.BasicServicesKit';

try {
  selectionPanel.off('hidden');
} catch (err) {
  console.error(`Failed to unregister hidden: ${err.code}, error message: ${err.message}`);
}

```

## on('destroyed')

```TypeScript
on(type: 'destroyed', callback: Callback<void>): void
```

订阅划词窗口销毁事件。使用callback异步回调。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'destroyed' | 是 | 设置监听类型，固定取值为'destroyed'。 |
| callback | Callback&lt;void&gt; | 是 | 回调函数，返回值为空。 |

**示例：**

```TypeScript
import { selectionManager, BusinessError } from '@kit.BasicServicesKit';

try {
  selectionPanel.on('destroyed', () => {
    console.info('Panel has been destroyed.');
  });
} catch (err) {
  console.error(`Failed to register destroyed callback: ${err.code}, error message: ${err.message}`);
}

```

## on('hidden')

```TypeScript
on(type: 'hidden', callback: Callback<void>): void
```

订阅划词窗口隐藏事件。使用callback异步回调。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hidden' | 是 | 设置监听类型，固定取值为'hidden'。 |
| callback | Callback&lt;void&gt; | 是 | 回调函数，返回值为空。 |

**示例：**

```TypeScript
import { selectionManager, BusinessError } from '@kit.BasicServicesKit';

try {
  selectionPanel.on('hidden', () => {
    console.info('Panel has been hidden.');
  });
} catch (err) {
  console.error(`Failed to register hidden callback: ${err.code}, error message: ${err.message}`);
}

```

## setUiContent

```TypeScript
setUiContent(path: string): Promise<void>
```

为当前的划词面板加载具体页面内容。使用Promise异步回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

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
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-此划词窗口已被销毁) | This selection window has been destroyed. |

**示例：**

```TypeScript
import { selectionManager, BusinessError } from '@kit.BasicServicesKit';

try {
  selectionPanel.setUiContent('pages/Index').then(() => {
    console.info('Succeeded in setting the content.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to setUiContent: ${err.code}, error message: ${err.message}`);
  });
} catch (err) {
  console.error(`Failed to setUiContent: ${err.code}, error message: ${err.message}`);
}

```

## show

```TypeScript
show(): Promise<void>
```

显示划词面板。使用Promise异步回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-此划词窗口已被销毁) | This selection window has been destroyed. |

**示例：**

```TypeScript
import { selectionManager, BusinessError } from '@kit.BasicServicesKit';

selectionPanel.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show panel: ${err.code}, error message: ${err.message}`);
});

```

## startMoving

```TypeScript
startMoving(): Promise<void>
```

使当前划词面板可以随鼠标拖动位置。使用Promise异步回调。该接口需要写在onTouch的回调函数中，并且事件类型为TouchType.Down。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务异常) | Selection service exception. |
| [33600002](../../apis-basic-services-kit/errorcode-selection.md#33600002-此划词窗口已被销毁) | This selection window has been destroyed. |

**示例：**

```TypeScript
import { selectionManager, BusinessError } from '@kit.BasicServicesKit';

RelativeContainer() {
  /* 
   * 页面布局内容，需要开发者根据实际补充
   */
}
.onTouch((event: TouchEvent) => {
  if (event.type === TouchType.Down) {
    if (selectionPanel !== undefined) {
      selectionPanel.startMoving().then(() => {   // selectionPanel为createPanel创建出的panel实例
        console.info('Succeeded in startMoving the panel.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to startMoving panel: ${err.code}, error message: ${err.message}`);
      });
    }
  }
})

```

