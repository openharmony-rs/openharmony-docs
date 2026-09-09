# @ohos.resourceschedule.backgroundProcessManager (后台子进程管控)(系统接口)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

本模块提供了后台子进程管控接口。开发者可以通过本模块接口对子进程进行压制、解压制，避免子进程过多占用系统资源，导致系统使用卡顿。本模块接口仅对通过[OH_Ability_StartNativeChildProcess](../apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocess)接口创建的子进程生效。

>  **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公开接口请参见[@ohos.resourceschedule.backgroundProcessManager (后台子进程管控)](js-apis-backgroundProcessManager.md)。

**起始版本：** 26.1.0

## 导入模块

```ts
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

## backgroundProcessManager.clearBackgroundApps

clearBackgroundApps(clearType: ClearType): Promise\<void>;

主动清理后台资源。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.CLEAR_BACKGROUND_APPS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| clearType | [ClearType](#cleartype) | 是 | 资源清理类型 |

**返回值：**

| 类型           | 说明                     |
| -------------- | ------------------------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[backgroundProcessManager错误码](errorcode-backgroundProcessManager.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                     |
| -------- | ---------------------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 31800002 | Parameter error. |

**示例：**

``` ts
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

backgroundProcessManager.clearBackgroundApps(backgroundProcessManager.ClearType.CLEAR_RECENT_CARDS).then(() => {
  console.info('clearBackgroundApps succeed');
}).catch((err: BusinessError) => {
  console.error('promise err code:' + err.code + ' message:' + err.message);
});
```


## ClearType

资源清理类型。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**系统接口：** 此接口为系统接口。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| CLEAR_RECENT_CARDS  | 1 | 清理多任务卡片。 |
