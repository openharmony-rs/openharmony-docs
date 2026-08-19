# AutoFillExtensionContext（系统接口）

AutoFillExtensionContext模块是AutoFillExtensionAbility的上下文环境，继承自 [ExtensionContext](arkts-ability-extensioncontext-c.md)。

**继承/实现关系：** AutoFillExtensionContext extends ExtensionContext

**起始版本：** 23

<!--Device-unnamed-declare class AutoFillExtensionContext--><!--Device-unnamed-declare class AutoFillExtensionContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## reloadInModal

```TypeScript
reloadInModal(customData: CustomData): Promise<void>
```

重新拉起模态页面。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutoFillExtensionContext-reloadInModal(customData: CustomData): Promise<void>--><!--Device-AutoFillExtensionContext-reloadInModal(customData: CustomData): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customData | [CustomData](arkts-ability-customdata-i-sys.md) | 是 | 拉起模态页面时的自定义信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

**示例**

当点击账号选择界面选择任意账号时，调用reloadInModal接口再次触发自动填充服务，在AutoFillExtensionAbility的onFillRequest生命周期中拉起模态页面。

```TypeScript
// AutoFillAbility.ts
import { AutoFillExtensionAbility, autoFillManager, UIExtensionContentSession } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class AutoFillAbility extends AutoFillExtensionAbility {
  // ...
  onFillRequest(session: UIExtensionContentSession,
    request: autoFillManager.FillRequest,
    callback: autoFillManager.FillRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onFillRequest');
    try {
      // 创建LocalStorage并存储自动填充所需的数据
      let storage_fill: LocalStorage = new LocalStorage(
        {
          'session': session,
          'message': "AutoFill Page",
          'fillCallback': callback,
          'viewData': request.viewData,
          'autoFillExtensionContext': this.context,
          'customData': request.customData
        } as Record<string, Object>);
      if (request.customData == undefined) {
        // 加载自动填充处理界面
        session.loadContent('pages/AccountPage', storage_fill);
      } else {
        // 拉起模态页面
        session.loadContent('pages/ReloadInModal', storage_fill);
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'autofill failed to load content');
    }
  }
}
```

当点击账号选择界面选择任意账号时，调用reloadInModal接口。

```TypeScript
// AccountPage.ets
import { autoFillManager, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct AccountPage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  viewData: autoFillManager.ViewData | undefined = this.storage?.get<autoFillManager.ViewData>('viewData');
  context: common.AutoFillExtensionContext | undefined = this.storage?.get<common.AutoFillExtensionContext>('autoFillExtensionContext');


  build() {
    Row() {
      Column() {
        List({ space: 10, initialIndex: 0 }) {
          ListItem() {
            Text('HelloWorld789456')
              .width('100%')
              .height(40)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(5)
          }
          .onClick(() => {
            if (this.viewData != undefined) {
              if (this.context != undefined) {
                // 调用reloadInModal接口重新触发自动填充，传递自定义数据用于模态页面
                this.context.reloadInModal({ data: { viewData: 20, text: 'HelloWorld789456' } }).then(() => {
                  console.info('reloadInModal successfully.')
                }).catch((err: BusinessError) => {
                  console.error(`reloadInModal failed. Code: ${err.code}, message: ${err.message}`);
                })
              }
            }
          });
        }
        // ...
      }
      .width('100%')
      .shadow(ShadowStyle.OUTER_FLOATING_SM)
    }
    .height('100%')
    .shadow(ShadowStyle.OUTER_FLOATING_SM)
  }
}
```

当点击账号选择界面选择任意账号时，调用reloadInModal接口再次触发自动填充服务，在AutoFillExtensionAbility的onFillRequest生命周期中拉起模态页面。

```TypeScript
'use static'
// AutoFillAbility.ts
import { autoFillManager, UIExtensionContentSession } from '@kit.AbilityKit';
import AutoFillExtensionAbility from '@ohos.app.ability.AutoFillExtensionAbility';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { LocalStorage } from '@kit.ArkUI';

export default class AutoFillAbility extends AutoFillExtensionAbility {
  // ...
  onFillRequest(session: UIExtensionContentSession,
    request: autoFillManager.FillRequest,
    callback: autoFillManager.FillRequestCallback) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'autofill onFillRequest');
    try {
      let storage_fill: LocalStorage = new LocalStorage();
      storage_fill.setOrCreate('session', session);
      storage_fill.setOrCreate('message', "AutoFill Page");
      storage_fill.setOrCreate('fillCallback', callback);
      storage_fill.setOrCreate('viewData', request.viewData);
      storage_fill.setOrCreate('autoFillExtensionContext', this.context);
      storage_fill.setOrCreate('customData', request.customData);
      if (request.customData == undefined) {
        // 加载自动填充处理界面
        session.loadContent('pages/AccountPage', storage_fill);
      } else {
        // 拉起模态页面
        session.loadContent('pages/ReloadInModal', storage_fill);
      }
    } catch (err) {
      hilog.error(0x0000, 'testTag', '%{public}s', 'autofill failed to load content');
    }
  }
}
```

当点击账号选择界面选择任意账号时，调用reloadInModal接口。

```TypeScript
// AccountPage.ets
import { autoFillManager, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Entry, Text, Column, Row, Component, List, ListItem, LocalStorage } from '@kit.ArkUI';

@Entry
@Component
struct AccountPage {
  storage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
  viewData: autoFillManager.ViewData | undefined = this.storage?.get<autoFillManager.ViewData>('viewData');
  context: common.AutoFillExtensionContext | undefined =
    this.storage?.get<common.AutoFillExtensionContext>('autoFillExtensionContext');

  build() {
    Row() {
      Column() {
        List({ space: 10, initialIndex: 0 }) {
          ListItem() {
            Text('HelloWorld789456')
              .width('100%')
              .height(40)
              .fontSize(16)
              .borderRadius(5)
          }
          .onClick(() => {
            this.clickFun();
          })
        }

        // ...
      }
      .width('100%')
    }
    .height('100%')
  }

  private clickFun(): void {
    if (this.context) {
      if (this.viewData) {
        this.context?.reloadInModal({}).then(() => {
          console.info('reloadInModal successfully.')
        }).catch((err) => {
          console.error('reloadInModal failed.')
        })
      }
    }
  }
}
```

