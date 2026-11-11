# 查询与请求权限控制目标应用

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

从API版本26.1.0开始，安全访问围栏服务提供控制目标应用权限的查询与请求能力。

系统管控智能体通过模拟点击等方式操控目标应用的行为，并提供控制权限的查询与请求机制。智能体可先查询目标应用的控制权限状态，若为拒绝（DENY），再向用户请求控制授权，确保只有获得用户授权的应用才能控制目标应用。

## 基本概念

- **应用控制权限：** 允许外部工具对指定应用进行控制操作的授权，状态为允许（ALLOW）或拒绝（DENY），由用户决定。
- **分身应用：** 应用的多开实例，通过[AppInfo](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#appinfo)的index字段区分，0为主应用，大于0为分身应用。

## 实现原理

1. 调用[queryControlAppStatus()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlquerycontrolappstatus)传入应用信息列表，返回每个应用的控制权限状态（ALLOW或DENY）。
2. 若为ALLOW，可直接进行后续控制操作；若为DENY，调用[requestControlAppPermissionFromUser()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequestcontrolapppermissionfromuser)传入上下文和应用信息列表，弹出对话框请求授权。
3. 用户做出决定后，接口返回每个应用的最终控制权限状态。

## 开发步骤

调用接口需申请`ohos.permission.CONTROL_DEVICE`权限，申请方式请参考[声明权限](../AccessToken/declare-permissions.md)。

1. 导入模块。

   ```typescript
   import { abilityToolAccessCtrl, common } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. 构建应用信息列表。详细参数说明请参考[AppInfo](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#appinfo)。

   ```typescript
   let appInfo: abilityToolAccessCtrl.AppInfo[] = [{
     bundleName: 'com.example.demo',
     index: 0
   }];
   ```

3. 查询控制权限状态。

   ```typescript
   abilityToolAccessCtrl.queryControlAppStatus(appInfo).then((data: abilityToolAccessCtrl.ControlAppStatusResult[]) => {
     console.info('queryControlAppStatus success, data: ' + JSON.stringify(data));
     for (let i = 0; i < data.length; i++) {
       let bundleName = data[i].appInfo.bundleName;
       let status = data[i].status;
       console.info(`bundleName: ${bundleName}, status: ${status}`);
       if (status === abilityToolAccessCtrl.ControlAppStatus.DENY) {
         // 控制权限被拒绝，在步骤4中调用requestControlAppPermissionFromUser()向用户请求控制授权
       } else {
         // 状态为ALLOW，可直接进行后续控制操作
       }
     }
   }).catch((err: BusinessError): void => {
     console.error(`queryControlAppStatus fail, code: ${err.code}, message: ${err.message}`);
   });
   ```

   返回[ControlAppStatusResult](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#controlappstatusresult)数组，`status`取值为[ControlAppStatus](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#controlappstatus).ALLOW或.DENY。

4. 若状态为DENY，请求控制授权。

   `context`为应用上下文。FA模型见[Context](../../reference/apis-ability-kit/js-apis-inner-app-context.md)，Stage模型见[Context](../../reference/apis-ability-kit/js-apis-inner-application-context.md)，可通过`this.getUIContext().getHostContext() as common.UIAbilityContext`获取。

   ```typescript
   let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
   abilityToolAccessCtrl.requestControlAppPermissionFromUser(context, appInfo)
     .then((data: abilityToolAccessCtrl.ControlAppStatusResult[]) => {
       console.info('requestControlAppPermissionFromUser success, data: ' + JSON.stringify(data));
       for (let i = 0; i < data.length; i++) {
         let bundleName = data[i].appInfo.bundleName;
         let status = data[i].status;
         console.info(`bundleName: ${bundleName}, status: ${status}`);
       }
     })
     .catch((err: BusinessError): void => {
       console.error(`requestControlAppPermissionFromUser fail, code: ${err.code}, message: ${err.message}`);
     });
   ```

   > **说明：**
   >
   > - 24010000：入参错误。检查`appInfo`是否为空、`bundleName`是否合法、`context`是否有效。
   > - 24010001：系统服务异常。可稍后重试。
   > - 24010002：服务内部错误。可间隔重试。
   > - 完整错误码请参考[安全访问围栏服务错误码](../../reference/apis-ability-kit/errorcode-abilityToolAccessCtrl.md)。
