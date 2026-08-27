# LiveFormExtensionContext

LiveFormExtensionContext是[LiveFormExtensionAbility](arkts-form-app-form-liveformextensionability-liveformextensionability-c.md)的上下文，继承自 [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。它提供访问特定于LiveFormExtensionAbility资源的能力，支持在互动卡片中拉起应用页面，适用 于需要在互动卡片中响应用户点击并跳转到应用页面的场景，解决了互动卡片无法主动拉起应用页面的限制问题。

**继承/实现关系：** LiveFormExtensionContext extends ExtensionContext

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

## startAbilityByLiveForm

```TypeScript
startAbilityByLiveForm(want: Want): Promise<void>
```

拉起互动卡片提供方（应用）的页面，使用Promise异步回调。该接口仅支持拉起互动卡片提供方（应用）的页面，不支持拉起其他应用的页面，否则会抛出错误码16501011。该接口仅限在点击事件回调中调用，且需要直接调用，不支持延时后调用，否则会抛出错误码16501011。  
- 互动卡片激活态中点击跳转到应用主页或详情页。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 需要被拉起的应用页面信息。取值原则：仅支持使用显式Want，必须包含bundleName和abilityName字段。详见 [使用显式Want启动应用组件](../../../application-models/ability-startup-with-explicit-want.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported due to limited device capabilities. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | An IPC connection error happened. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501011](../errorcode-form.md#16501011-卡片不支持调用当前接口) | The form can not support this operation |

**示例**

```TypeScript
// MyLiveFormExtensionAbility.ets
import { LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MyLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    // 1.将LiveFormExtensionContext传给互动卡片的页面组件
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('context', this.context);
    session.loadContent('pages/MyLiveFormPage', storage);
  }
};
```

```TypeScript
// pages/MyLiveFormPage.ets
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct MyLiveFormPage {
  private storageForMyLiveFormPage: LocalStorage | undefined = undefined;
  private liveFormContext: common.LiveFormExtensionContext | undefined = undefined;

  aboutToAppear(): void {
    // 2.获取LiveFormExtensionContext
    this.storageForMyLiveFormPage = this.getUIContext().getSharedLocalStorage();
    this.liveFormContext = this.storageForMyLiveFormPage?.get<common.LiveFormExtensionContext>('context');
  }

  private startAbilityByLiveForm(): void {
    try {
      // 请开发者替换为实际的want信息
      this.liveFormContext?.startAbilityByLiveForm({
        bundleName: 'com.example.liveformdemo',
        abilityName: 'EntryAbility',
      })
        .then(() => {
          console.info('startAbilityByLiveForm succeed');
        })
        .catch((err: BusinessError) => {
          console.error(`startAbilityByLiveForm failed, code is ${err?.code}, message is ${err?.message}`);
        });
    } catch (err) {
      console.error(`startAbilityByLiveForm failed, code is ${err?.code}, message is ${err?.message}`);
    }
  }

  build() {
    // 请开发者替换为实际的页面
    Stack() {
      Column()
        .width('50%')
        .height('50%')
        .backgroundColor('#2875F5')
    }
    .width('100%')
    .height('100%')
    .onClick(() => {
      // 3.在点击事件回调中直接使用该接口
      console.info('MyLiveFormPage click to start ability');
      if (!this.liveFormContext) {
        console.info('MyLiveFormPage liveFormContext is empty');
        return;
      }
      this.startAbilityByLiveForm();
    });
  }
}
```
