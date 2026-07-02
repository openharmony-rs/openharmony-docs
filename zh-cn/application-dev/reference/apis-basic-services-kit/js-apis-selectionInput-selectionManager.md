# @ohos.selectionInput.selectionManager (划词管理)

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @no86-->
<!--Designer: @mmwwbb-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

本模块提供划词管理能力，包括创建面板、显示面板、移动面板、隐藏面板、销毁面板、监听鼠标/触控板划词事件、获取选中文本等。典型使用流程为：先通过[on('selectionCompleted')](#selectionmanageronselectioncompleted)订阅划词完成事件，在回调中调用[getSelectionContent](#getselectioncontent)获取选中文本，然后通过[createPanel](#createpanel)创建划词面板，调用[setUiContent](#setuicontent)加载页面内容，再调用[moveToGlobalDisplay](#movetoglobaldisplay)移动面板到指定位置，最后通过[show](#show)显示面板。如不主动调用[hide](#hide)，面板在失焦时会自动隐藏。

> **说明：**
>
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块仅支持PC/2in1设备。开发者可通过canIUse('SystemCapability.SelectionInput.Selection')判断当前设备是否支持该功能。
> - 仅支持集成了划词扩展的应用调用，划词扩展的实现请参见[SelectionExtensionAbility](js-apis-selectionInput-selectionExtensionAbility.md)。

## 导入模块

```ts
import { selectionManager } from '@kit.BasicServicesKit';
```

## selectionManager

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

### selectionManager.on('selectionCompleted')

on(type: 'selectionCompleted', callback: Callback\<SelectionInfo>): void

订阅划词完成事件。使用callback异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                           |
| -------- | ------------------------------------------- | ---- | ---------------------------------------------- |
| type     | string                                      | 是   | 设置监听类型，固定取值为'selectionCompleted'。 |
| callback | Callback\<[SelectionInfo](#selectioninfo)> | 是   | 回调函数，返回[SelectionInfo](#selectioninfo)。该回调仅在用户通过鼠标或触控板选中文本（鼠标左键双击/三击/按下滑动）后按下Ctrl键时触发。       |

**错误码：**

以下错误码的详细介绍请参见[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600003   | The application calling the API does not match the application selected in the system settings. |

**示例：**

```ts
import { selectionManager } from '@kit.BasicServicesKit';

try {
  // 订阅划词完成事件
  selectionManager.on('selectionCompleted', (info: selectionManager.SelectionInfo) => {
    console.info('Enter the callback function.');
  });
} catch (err) {
  console.error(`Failed to register selectionCompleted callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

### selectionManager.off('selectionCompleted')

off(type: 'selectionCompleted', callback?: Callback\<SelectionInfo>): void

取消订阅划词完成事件。使用callback异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                      | 是   | 设置监听类型，固定取值为'selectionCompleted'。               |
| callback | Callback\<[SelectionInfo](#selectioninfo)> | 否   | 需要取消的回调函数（即之前通过on方法订阅时的回调实例），返回[SelectionInfo](#selectioninfo)。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
import { selectionManager } from '@kit.BasicServicesKit';

// 定义划词完成事件回调函数，用于订阅和取消订阅
let selectionChangeCallback = (info: selectionManager.SelectionInfo) => {
  console.info('Enter the callback function.');
};

// 先订阅划词完成事件回调，为后续取消订阅做准备
selectionManager.on('selectionCompleted', selectionChangeCallback);
try {
  // 取消订阅划词完成事件
  selectionManager.off('selectionCompleted', selectionChangeCallback);
} catch (err) {
  console.error(`Failed to unregister selectionCompleted. Error code: ${err.code}, error message: ${err.message}`);
}
```

### getSelectionContent()

getSelectionContent(): Promise\<string>

获取选中文本的内容。使用Promise异步回调。需在[on('selectionCompleted')](#selectionmanageronselectioncompleted)回调中调用，且仅在划词完成事件触发后有效。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**
| 类型   | 说明                                                                 |
| ------- | ------------------------------------------------------------------ |
| Promise\<string> | Promise对象，返回当前选中文本的内容。  |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service exception. |
| 33600004   | The interface is called too frequently. |
| 33600005   | The interface is called at the wrong time. |
| 33600006   | The current application is prohibited from accessing content. |
| 33600007   | The length of selected content is out of range. |
| 33600008   | Getting the selected content times out. |

**示例：**

```ts
import { selectionManager } from '@kit.BasicServicesKit';

// 订阅划词完成事件，在回调中获取选中文本
selectionManager.on('selectionCompleted', async (info: selectionManager.SelectionInfo) => {
  try {
    // 获取选中文本内容
    let content = await selectionManager.getSelectionContent();
    console.info(`Succeeded in getting selection content: ${content}`);
  } catch (err) {
    console.error(`Failed to get selection content. Error code: ${err.code}, error message: ${err.message}`);
  }
});
```

### createPanel

createPanel(ctx: Context, info: PanelInfo): Promise\<Panel>

创建划词面板。使用Promise异步回调。

单个划词应用仅允许创建一个[MENU_PANEL](js-apis-selectionInput-selectionPanel.md#paneltype)和一个[MAIN_PANEL](js-apis-selectionInput-selectionPanel.md#paneltype)。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型        | 必填 | 说明                     |
| ------- | ----------- | ---- | ------------------------ |
| ctx     | [Context](../apis-ability-kit/js-apis-inner-application-context.md#context) | 是   | 当前划词面板依赖的上下文信息，需使用SelectionExtensionAbility提供的上下文。 |
| info    | [PanelInfo](js-apis-selectionInput-selectionPanel.md#panelinfo)   | 是   | 划词面板的配置信息，用于指定面板类型、位置和尺寸等属性。 |

**返回值：**
| 类型   | 说明                                                                 |
| ------- | ------------------------------------------------------------------ |
| Promise\<[Panel](#panel)> | Promise对象，返回当前创建的划词面板对象。  |

**错误码：**

以下错误码的详细介绍请参见[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service exception. |
| 33600003   | The application calling the API does not match the application selected in the system settings. |

**示例：**

```ts
import { selectionManager, SelectionExtensionAbility, PanelInfo, PanelType, BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class SelectionAbilityStub extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(
    code: number,
    data: rpc.MessageSequence,
    reply: rpc.MessageSequence,
    options: rpc.MessageOption
  ): boolean | Promise<boolean> {
    return true;
  }
}

class ServiceExtAbility extends SelectionExtensionAbility {
  onConnect(want: Want): rpc.RemoteObject {
    // 配置划词面板信息，包括面板类型、位置和尺寸
    let panelInfo: PanelInfo = {
      panelType: PanelType.MENU_PANEL,
      x: 0,
      y: 0,
      width: 500,
      height: 200
    };
    let selectionPanel: selectionManager.Panel | undefined = undefined;
    // 创建划词面板
    selectionManager.createPanel(this.context, panelInfo)
      .then((panel: selectionManager.Panel) => {
        selectionPanel = panel;
        console.info('Succeed in creating panel.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to create panel. Error code: ${err.code}, error message: ${err.message}`);
    });
    return new SelectionAbilityStub('remote');
  }
}
export default ServiceExtAbility;
```

### destroyPanel

destroyPanel(panel: Panel): Promise\<void>

销毁划词面板。与[createPanel](#createpanel)配对使用，用于销毁由createPanel()创建的面板对象。使用Promise异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型        | 必填 | 说明                     |
| ---------| ----------- | ---- | ------------------------ |
| panel    | [Panel](#panel)       | 是   | 要销毁的面板对象。      |

**返回值：**
| 类型    | 说明                                                                 |
| ------- | -------------------------------------------------------------------- |
| Promise\<void> | Promise对象，无返回结果。|

**错误码：**

以下错误码的详细介绍请参见[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service exception. |

**示例：**

```ts
import { selectionManager, SelectionExtensionAbility, PanelInfo, PanelType, BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class SelectionAbilityStub extends rpc.RemoteObject {
  constructor(descriptor: string) {
    super(descriptor);
  }
  onRemoteMessageRequest(
    code: number,
    data: rpc.MessageSequence,
    reply: rpc.MessageSequence,
    options: rpc.MessageOption
  ): boolean | Promise<boolean> {
    return true;
  }
}

class ServiceExtAbility extends SelectionExtensionAbility {
  onConnect(want: Want): rpc.RemoteObject {
    // 配置划词面板信息，包括面板类型、位置和尺寸
    let panelInfo: PanelInfo = {
      panelType: PanelType.MENU_PANEL,
      x: 0,
      y: 0,
      width: 500,
      height: 200
    };
    let selectionPanel: selectionManager.Panel | undefined = undefined;
    // 先创建划词面板，获取面板实例用于后续销毁
    selectionManager.createPanel(this.context, panelInfo)
      .then((panel: selectionManager.Panel) => {
        console.info('Succeed in creating panel.');
        selectionPanel = panel;
        try {
          if (selectionPanel) {
            // 销毁划词面板
            selectionManager.destroyPanel(selectionPanel).then(() => {
              console.info('Succeed in destroying panel.');
            }).catch((err: BusinessError) => {
              console.error(`Failed to destroy panel. Error code: ${err.code}, error message: ${err.message}`);
            });
          }
        } catch (err) {
          console.error(`Failed to destroy panel. Error code: ${err.code}, error message: ${err.message}`);
        }
      }).catch((err: BusinessError) => {
        console.error(`Failed to create panel. Error code: ${err.code}, error message: ${err.message}`);
    });
    return new SelectionAbilityStub('remote');
  }
}
export default ServiceExtAbility;
```

## SelectionInfo

划词事件信息。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称      | 类型 | 只读 | 可选 | 说明         |
| --------- | -------- | ---- | ---- | ------------ |
| selectionType |[SelectionType](#selectiontype)   | 否   | 否   | 触发划词类型。 |
| startDisplayX |number| 否   | 否   | 划词起始位置的屏幕x轴坐标，单位为px。 |
| startDisplayY |number| 否   | 否   | 划词起始位置的屏幕y轴坐标，单位为px。 |
| endDisplayX   |number| 否   | 否   | 划词结束位置的屏幕x轴坐标，单位为px。 |
| endDisplayY   |number| 否   | 否   | 划词结束位置的屏幕y轴坐标，单位为px。 |
| startWindowX  |number| 否   | 否   | 划词起始位置的窗口x轴坐标，单位为px。 |
| startWindowY  |number| 否   | 否   | 划词起始位置的窗口y轴坐标，单位为px。 |
| endWindowX    |number| 否   | 否   | 划词结束位置的窗口x轴坐标，单位为px。 |
| endWindowY    |number| 否   | 否   | 划词结束位置的窗口y轴坐标，单位为px。 |
| displayID     |number| 否   | 否   | 被划词应用窗口的屏幕ID。 |
| windowID      |number| 否   | 否   | 被划词应用的窗口ID。 |
| bundleName    |string| 否   | 否   | 被划词应用的bundleName。 |

## Panel

划词面板对象，通过[createPanel](#createpanel)创建，提供面板内容设置、显示、隐藏、移动及事件订阅等管理能力。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

下列API均需使用[createPanel](#createpanel)获取到Panel实例后，通过实例调用。

### setUiContent

setUiContent(path: string): Promise\<void>

为当前的划词面板加载具体页面内容。使用Promise异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| path | string | 是   |  要加载到面板中的页面内容的路径，Stage模型下该路径需添加到工程的resources/base/profile/main_pages.json文件中，不支持FA模型。 |

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise对象，无返回结果。  |

**错误码：**

以下错误码的详细介绍请参见[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service exception. |
| 33600002   | This selection window has been destroyed. |

**示例：**
<!--code_no_check-->
```ts
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

### show

show(): Promise\<void>

显示划词面板。使用Promise异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise对象，无返回结果。  |

**错误码：**

以下错误码的详细介绍请参见[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service exception. |
| 33600002   | This selection window has been destroyed. |

**示例：**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 显示划词面板。selectionPanel为createPanel创建出的panel实例
selectionPanel.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

### hide

hide(): Promise\<void>

隐藏当前划词面板。使用Promise异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise对象，无返回结果。  |

**错误码：**

以下错误码的详细介绍请参见[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service exception. |
| 33600002   | This selection window has been destroyed. |

**示例：**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 隐藏划词面板。selectionPanel为createPanel创建出的panel实例
selectionPanel.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide panel. Error code: ${err.code}, error message: ${err.message}`);
});
```

### startMoving

startMoving(): Promise\<void>

设置划词面板可随鼠标拖动移动位置。使用Promise异步回调。该接口需要写在onTouch的回调函数中，并且事件类型为TouchType.Down。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise对象，无返回结果。  |

**错误码：**

以下错误码的详细介绍请参见[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service exception. |
| 33600002   | This selection window has been destroyed. |

**示例：**
<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';

RelativeContainer() {
  /* 
   * 页面布局内容，需要开发者根据实际补充
   */
}
.onTouch((event: TouchEvent) => {
  if (event.type === TouchType.Down) {
    if (selectionPanel !== undefined) {
      // 使划词面板可随鼠标拖动位置。selectionPanel为createPanel创建出的panel实例
      selectionPanel.startMoving().then(() => {
        console.info('Succeeded in startMoving the panel.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to startMoving panel. Error code: ${err.code}, error message: ${err.message}`);
      });
    }
  }
})
```

<!--Del-->
### moveTo<sup>(deprecated)</sup>

moveTo(x: number, y: number): Promise\<void>

移动划词面板至屏幕指定位置。使用Promise异步回调。

> **说明：**
>
> 从API version 20开始支持，从API version 24开始废弃。建议使用[moveToGlobalDisplay](#movetoglobaldisplay)替代。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| x | number | 是   |目标位置的x轴坐标，单位为px。|
| y | number | 是   |目标位置的y轴坐标，单位为px。|

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise对象，无返回结果。  |

**错误码：**

以下错误码的详细介绍请参见[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service exception. |
| 33600002   | This selection window has been destroyed. |

**示例：**
<!--code_no_check-->
```ts
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
<!--DelEnd-->

### moveToGlobalDisplay

moveToGlobalDisplay(x: number, y: number): Promise\<void>

移动划词面板至屏幕全局坐标系下的指定位置，支持移动到扩展屏上。使用Promise异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| x | number | 是   |目标位置的x轴坐标，单位为px。|
| y | number | 是   |目标位置的y轴坐标，单位为px。|

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise对象，无返回结果。  |

**错误码：**

以下错误码的详细介绍请参见[划词服务错误码](errorcode-selection.md)。

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 33600001   | Selection service exception. |
| 33600002   | This selection window has been destroyed. |

**示例：**
<!--code_no_check-->
```ts
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

### on('destroyed')

on(type: 'destroyed', callback: Callback\<void>): void

订阅划词面板销毁事件。使用callback异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                           |
| -------- | ------------------------------------------- | ---- | ---------------------------------------------- |
| type     | string                                      | 是   | 设置监听类型，固定取值为'destroyed'。 |
| callback | Callback\<void> | 是   | 回调函数，面板销毁时触发，返回值为空。       |

**示例：**
<!--code_no_check-->
```ts
try {
  // 订阅划词面板销毁事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel.on('destroyed', () => {
    console.info('Panel has been destroyed.');
  });
} catch (err) {
  console.error(`Failed to register destroyed callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

### off('destroyed')

off(type: 'destroyed', callback?: Callback\<void>): void

取消订阅划词面板销毁事件。使用callback异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                      | 是   | 设置监听类型，固定取值为'destroyed'。               |
| callback | Callback\<void> | 否   | 需要取消的回调函数（即之前通过on方法订阅时的回调实例），返回值为空。参数不填写时，取消订阅type对应的所有回调事件。|

**示例：**
<!--code_no_check-->
```ts
try {
  // 取消订阅划词面板销毁事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel.off('destroyed');
} catch (err) {
  console.error(`Failed to unregister destroyed. Error code: ${err.code}, error message: ${err.message}`);
}
```

### on('hidden')

on(type: 'hidden', callback: Callback\<void>): void

订阅划词面板隐藏事件。使用callback异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                           |
| -------- | ------------------------------------------- | ---- | ---------------------------------------------- |
| type     | string                                      | 是   | 设置监听类型，固定取值为'hidden'。 |
| callback | Callback\<void> | 是   | 回调函数，返回值为空。       |

**示例：**
<!--code_no_check-->
```ts
try {
  // 订阅划词面板隐藏事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel.on('hidden', () => {
    console.info('Panel has been hidden.');
  });
} catch (err) {
  console.error(`Failed to register hidden callback. Error code: ${err.code}, error message: ${err.message}`);
}
```

### off('hidden')

off(type: 'hidden', callback?: Callback\<void>): void

取消订阅划词面板隐藏事件。使用callback异步回调。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                      | 是   | 设置监听类型，固定取值为'hidden'。               |
| callback | Callback\<void> | 否   | 需要取消的回调函数（即之前通过on方法订阅时的回调实例），返回值为空。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**
<!--code_no_check-->
```ts
try {
  // 取消订阅划词面板隐藏事件。selectionPanel为createPanel创建出的panel实例
  selectionPanel.off('hidden');
} catch (err) {
  console.error(`Failed to unregister hidden. Error code: ${err.code}, error message: ${err.message}`);
}
```

## SelectionType

定义触发划词的类型枚举。

**系统能力：** SystemCapability.SelectionInput.Selection

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称         | 值 | 说明               |
| ------------ | -- | ------------------ |
| MOUSE_MOVE | 1 | 滑动划词类型。 |
| DOUBLE_CLICK   | 2 | 双击划词类型。 |
| TRIPLE_CLICK   | 3 | 三击划词类型。 |
