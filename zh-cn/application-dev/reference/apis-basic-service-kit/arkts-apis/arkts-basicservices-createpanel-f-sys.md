# createPanel（系统接口）

## createPanel

```TypeScript
function createPanel(ctx: Context, info: PanelInfo): Promise<Panel>
```

创建划词面板。使用Promise异步回调。
单个划词应用仅允许创建一个[MENU_PANEL](arkts-selectioninput-selectionpanel.md)和一个
[MAIN_PANEL](arkts-selectioninput-selectionpanel.md)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ctx | Context | 是 | 当前划词面板依赖的上下文信息。 |
| info | PanelInfo | 是 | 划词面板信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Panel&gt; | Promise对象，返回当前创建的划词面板对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务异常) | Selection service exception. |
| [33600003](../../apis-basic-services-kit/errorcode-selection.md#33600003-调用api的应用程序与系统设置中选择的应用程序不匹配) | The application calling the API does not match the applicationselected in the system settings. |

**示例：**

```TypeScript
import { selectionManager, SelectionExtensionAbility, PanelInfo, PanelType, BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class SelectionAbilityStub extends rpc.RemoteObject {
  constructor(des: string) {
    super(des);
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
    let panelInfo: PanelInfo = {
      panelType: PanelType.MENU_PANEL,
      x: 0,
      y: 0,
      width: 500,
      height: 200
    }
    let selectionPanel: selectionManager.Panel | undefined = undefined;
    selectionManager.createPanel(this.context, panelInfo)
      .then((panel: selectionManager.Panel) => {
        selectionPanel = panel;
        console.info('Succeed in creating panel.');
      }).catch((err: BusinessError) => {
      console.error(`Failed to create panel: ${err.code}, error message: ${err.message}`);
    });
    return new SelectionAbilityStub('remote');
  }
}
export default ServiceExtAbility;

```

