# createPanel

## createPanel

```TypeScript
function createPanel(ctx: Context, info: PanelInfo): Promise<Panel>
```

创建划词面板。使用Promise异步回调。 单个划词应用仅允许创建一个[MENU\_PANEL]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和一个 [MAIN\_PANEL]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-selectionManager-function createPanel(ctx: Context, info: PanelInfo): Promise<Panel>--><!--Device-selectionManager-function createPanel(ctx: Context, info: PanelInfo): Promise<Panel>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前划词面板依赖的上下文信息。 |
| info | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 划词面板信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Panel&gt; | Promise对象，返回当前创建的划词面板对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务调用异常) | Selection service exception. |
| [33600003](../../apis-basic-services-kit/errorcode-selection.md#33600003-调用接口的应用与系统设置中选择的应用不匹配) | The application calling the API does not match the application selected in the system settings. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
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
    // 创建划词面板。this.context通过继承SelectionExtensionAbility获取
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

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import SelectionExtensionAbility from '@ohos.selectionInput.SelectionExtensionAbility';
import { PanelInfo, PanelType } from '@ohos.selectionInput.SelectionPanel';
import selectionManager from '@ohos.selectionInput.selectionManager';
import rpc from '@ohos.rpc';
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
      }).catch((err) => {
      console.error(`Failed to create panel. Error code: ${err.code}, error message: ${err.message}`);
    });
    return new SelectionAbilityStub('remote');
  }
}
export default ServiceExtAbility;
```

