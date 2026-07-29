# PermissionRequestResult

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## 模块简介

权限请求结果对象，在调用[requestPermissionsFromUser](js-apis-abilityAccessCtrl.md#requestpermissionsfromuser9)申请权限时返回此对象表明此次权限申请的结果。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
> - 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { PermissionRequestResult } from '@kit.AbilityKit';
```

## 属性

**系统能力：** 以下各项对应的系统能力均为SystemCapability.Security.AccessToken

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| permissions | Array&lt;string&gt; | 否 | 否 | 本次待申请的权限数组。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| authResults | ArkTS-Dyn: Array&lt;number&gt; <br> ArkTS-Sta: Array&lt;int&gt; | 否 | 否 | 每个请求权限对应的授权结果。<br>- -1：未授权。若 dialogShownResults为true，表示用户在本次申请中明确拒绝；若为false，表示当前状态无需再弹窗，通常需要用户前往系统设置修改。<br>- 0：已授权，应用可以继续访问与该权限关联的受保护资源。<br>- 2：请求无效，通常表示权限未声明、权限名非法，或未满足该权限的特殊申请条件。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 9<br>**ArkTS-Sta起始版本：** 23 |
| dialogShownResults<sup>12+</sup> | Array&lt;boolean&gt; | 否 | 是 | 表示每个权限在本次申请过程中是否真正展示过授权弹窗。<br>- true：系统已展示授权弹窗。<br>- false：系统未展示弹窗，通常是因为权限当前状态、权限类型或系统策略不允许继续走弹窗授权链路。<br>当authResults为-1时，结合本字段可进一步区分“本次被用户拒绝”与“当前已不再弹窗”。<br> **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| errorReasons<sup>18+</sup> | ArkTS-Dyn: Array&lt;number&gt; <br> ArkTS-Sta: Array&lt;int&gt; | 否 | 是 | 每个权限申请对应的原因码。主要用于解释授权失败、请求无效或无法展示弹窗的具体原因。<br>0：本次申请合法。<br>1：权限名非法。<br>2：权限未声明。<br>3：不满足对应权限的申请条件，例如部分位置权限需要满足额外前提。<br>4：用户未同意隐私声明。<br>5：该权限不支持通过权限弹窗进行申请，可能是申请方式受限或被系统策略管控。<br>6：该权限为 [manual_settings](../../security/AccessToken/app-permission-mgmt-overview.md#manual_settings手动设置授权)类型，只能通过设置页授权。<br>12：服务异常。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 18开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 18<br>**ArkTS-Sta起始版本：** 23 |

## 使用说明

PermissionRequestResult是权限申请的结果对象。开发者需先创建atManager实例，再调用requestPermissionsFromUser方法申请权限，该方法返回PermissionRequestResult对象，开发者可通过该对象的属性判断权限申请结果。权限申请整体流程及atManager的详细说明请参见[@ohos.abilityAccessCtrl (程序访问控制管理)](js-apis-abilityAccessCtrl.md)。

**示例：**

示例中context的获取方式请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。
<!--code_no_check-->
```ts
import { abilityAccessCtrl, Context, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager = abilityAccessCtrl.createAtManager();
try {
  // 请在组件内获取context
  let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  // 向用户申请相机权限
  atManager.requestPermissionsFromUser(context, ["ohos.permission.CAMERA"]).then((data) => {
      // 输出申请的权限列表
      console.info("data permissions:" + data.permissions);
      // 输出每个权限对应的授权结果
      console.info("data authResults:" + data.authResults);
      // 输出每个权限在本次申请中是否展示过弹窗
      console.info("data dialogShownResults:" + data.dialogShownResults);
      // 输出每个权限申请失败或异常时的原因码
      console.info("data errorReasons:" + data.errorReasons);
  }).catch((err: BusinessError) => {
      console.error(`code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  console.error(`catch errcode: ${err.code}, message: ${err.message}`);
}
```
