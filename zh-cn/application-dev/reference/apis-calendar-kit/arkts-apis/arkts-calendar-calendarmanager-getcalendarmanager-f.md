# getCalendarManager

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## getCalendarManager

```TypeScript
function getCalendarManager(context: Context) : CalendarManager
```

根据上下文获取CalendarManager对象，用于管理日历。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-calendarManager-function getCalendarManager(context: Context) : CalendarManager--><!--Device-calendarManager-function getCalendarManager(context: Context) : CalendarManager-End-->

**系统能力：** SystemCapability.Applications.CalendarData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CalendarManager](arkts-calendar-calendarmanager-calendarmanager-i.md) | 返回创建的CalendarManager对象。 |

**示例：**

示例中的mContext的获取方式请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// 获取上下文mContext
// 获取日历管理器calendarMgr
// 该文件为系统生成，目录：entry/src/main/ets/entryability/EntryAbility.ets
// 文档后续示例代码都需要配置此文件才能正常运行
import {
  abilityAccessCtrl,
  AbilityConstant, 
  common, 
  PermissionRequestResult, 
  Permissions, 
  UIAbility, 
  Want
} from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { calendarManager } from '@kit.CalendarKit';
import { window } from '@kit.ArkUI';

export let calendarMgr: calendarManager.CalendarManager | null = null;
export let mContext: common.UIAbilityContext | null = null;
export default class EntryAbility extends UIAbility {

  onWindowStageCreate(windowStage: window.WindowStage): void {

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
    mContext = this.context;
    const permissions: Permissions[] = ['ohos.permission.READ_CALENDAR', 'ohos.permission.WRITE_CALENDAR'];
    let atManager = abilityAccessCtrl.createAtManager();
    atManager.requestPermissionsFromUser(mContext, permissions).then((result: PermissionRequestResult) => {
      console.info(`get Permission success, result: ${JSON.stringify(result)}`);
      calendarMgr = calendarManager.getCalendarManager(mContext);
    }).catch((error: BusinessError) => {
      console.error(`get Permission error, error. Code: ${error.code}, message: ${error.message}`);
    })
  }

}

```

