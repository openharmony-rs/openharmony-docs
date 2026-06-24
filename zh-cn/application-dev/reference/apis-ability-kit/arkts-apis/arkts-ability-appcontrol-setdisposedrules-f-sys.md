# setDisposedRules（系统接口）

## setDisposedRules

```TypeScript
function setDisposedRules(disposedRuleConfigurations: Array<DisposedRuleConfiguration>): void
```

��������ָ��Ӧ�û����Ӧ�õ����ع���

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disposedRuleConfigurations | Array&lt;DisposedRuleConfiguration&gt; | 是 | ��ʾ�����������ع�������ã�����������Ӧ�õ�appId������Ӧ�����������ع���ÿ��<br/>�������ع����������������Ϊ1000��<br/>**˵����**<br/>1.��������д���appId��appIndex��ͬ��DisposedRuleConfigurationʱ�������<br/>DisposedRuleConfiguration�Ḳ��ǰ��ġ�<br/>2.���Ӧ�������ù����ع�������Ϊ��Ӧ���������ع��򣬻Ḳ��֮ǰ�ġ�appId��appIndexһ�����ʾͬһӦ�á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700005](../../errorcode-universal.md#17700005-The) | The specified app ID is invalid. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex is not in the valid range. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { appControl, Want, bundleManager } from '@kit.AbilityKit';

let want: Want = {
  bundleName: 'com.example.myapplication',
  moduleName: 'entry',
  abilityName: 'EntryAbility'
};
let elementName: bundleManager.ElementName = {
  bundleName: 'com.example.myapplication',
  moduleName: 'entry',
  abilityName: 'EntryAbility'
};
let rule: appControl.DisposedRule = {
  want: want,
  componentType: appControl.ComponentType.UI_ABILITY,
  disposedType: appControl.DisposedType.BLOCK_APPLICATION,
  controlType: appControl.ControlType.ALLOWED_LIST,
  elementList: [
    elementName
  ],
  priority: 100,
  pageJump: appControl.PageJumpMode.PAGE_JUMP_WINDOW_SHOW
};

let disposedRuleConfiguration: appControl.DisposedRuleConfiguration = {
  appId: 'com.example.myapplication_BInGTMPMdc6v55s/UFIJHL5NLREXjOuxm/DsyMhlFmLAZC9/Gk+ruqS9OZr/dvFuaIaQQL1pKolvzK/zYNHvJ/I=',
  appIndex: 0,
  disposedRule: rule,
};

let disposedRuleConfigurations: Array<appControl.DisposedRuleConfiguration> = [];
disposedRuleConfigurations.push(disposedRuleConfiguration);

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('setDisposedRules', { type: ButtonType.Normal })
          .onClick(() => {
            try {
              appControl.setDisposedRules(disposedRuleConfigurations);
              console.info('setDisposedRules success');
            } catch (error) {
              let err: BusinessError = error as BusinessError;
              console.error(`setDisposedRules failed, errCode:${err.code}, message:${err.message}`);
            }
          });
      }
    }
  }
}

```

