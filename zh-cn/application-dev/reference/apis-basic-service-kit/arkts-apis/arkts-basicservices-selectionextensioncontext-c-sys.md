# SelectionExtensionContext（系统接口）

SelectionExtensionContext是
[SelectionExtensionAbility](arkts-basicservices-selectionextensionability-c-sys.md#SelectionExtensionAbility)的上下文，继承自
[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext)。
每个SelectionExtensionAbility组件实例化时，系统都会自动创建对应的SelectionExtensionContext。开发者可以通过SelectionExtensionContext拉起同应用内其他
Ability。

> **说明：**
> - 本模块仅支持PC/2in1设备。

**继承/实现关系：** SelectionExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## startAbility

```TypeScript
startAbility(want: Want): Promise<void>
```

拉起目标应用。使用Promise异步回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | 想要被拉起的应用信息，包括Ability名称、Bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000005](../../errorcode-universal.md#16000005-The) | The specified process does not have the permission. |
| [16000006](../../errorcode-universal.md#16000006-Crossuser) | Cross-user operations are not allowed. |
| [16000008](../../errorcode-universal.md#16000008-The) | The crowdtesting application expires. |
| [16000009](../../errorcode-universal.md#16000009-An) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../errorcode-universal.md#16000010-The) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000012](../../errorcode-universal.md#16000012-The) | The application is controlled. |
| [16000013](../../errorcode-universal.md#16000013-The) | The application is controlled by EDM. |
| [16000019](../../errorcode-universal.md#16000019-No) | No matching ability is found. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16000053](../../errorcode-universal.md#16000053-The) | The ability is not on the top of the UI. |
| [16000055](../../errorcode-universal.md#16000055-Installationfree) | Installation-free timed out. |
| [16000061](../../errorcode-universal.md#16000061-Operation) | Operation not supported. |
| [16000069](../../errorcode-universal.md#16000069-The) | The extension cannot start the third party application. |
| [16000070](../../errorcode-universal.md#16000070-The) | The extension cannot start the service. |
| [16000083](../../errorcode-universal.md#16000083-The) | The ExtensionAbility cannot start the ability due to system control. |
| [16200001](../../errorcode-universal.md#16200001-The) | The caller has been released. |

**示例：**

```TypeScript
import { SelectionExtensionAbility, BusinessError } from '@kit.BasicServicesKit';
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
    console.info(`onRemoteMessageRequest code: ${code}`);
    return true;
  }
}

class SelectionExtAbility extends SelectionExtensionAbility {
  onConnect(want: Want): rpc.RemoteObject {
    try {
      let wantAbility: Want = {
        bundleName: "com.selection.selectionapplication",
        abilityName: "EntryAbility",
      };
      this.context.startAbility(wantAbility).then(() => {
        console.info(`startAbility success`);
      }).catch((err: BusinessError) => {
        console.error(`startAbility error: ${err.code}, error message: ${err.message}`);
      })
    } catch (err) {
      console.error(`startAbility error: ${err.code}, error message: ${err.message}`);
    }
    return new SelectionAbilityStub('remote');
  }
}

```

