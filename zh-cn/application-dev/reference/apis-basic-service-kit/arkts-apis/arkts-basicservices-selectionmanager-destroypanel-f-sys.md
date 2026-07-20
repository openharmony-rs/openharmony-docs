# destroyPanel（系统接口）

## 导入模块

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

<a id="destroypanel"></a>
## destroyPanel

```TypeScript
function destroyPanel(panel: Panel): Promise<void>
```

销毁划词面板。使用Promise异步回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-selectionManager-function destroyPanel(panel: Panel): Promise<void>--><!--Device-selectionManager-function destroyPanel(panel: Panel): Promise<void>-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| panel | [Panel](arkts-basicservices-selectionmanager-panel-i-sys.md) | 是 | 要销毁的面板对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33600001](../../apis-basic-services-kit/errorcode-selection.md#33600001-划词服务异常) | Selection service exception. |

**示例：**

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
    // 先创建划词面板，获取面板实例用于后续销毁。this.context通过继承SelectionExtensionAbility获取
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

