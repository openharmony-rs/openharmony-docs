# 声明权限

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

应用在申请权限时，需在项目的配置文件中逐个声明所需权限，否则无法获取授权<!--RP2--><!--RP2End-->。

## 在配置文件中声明权限

应用必须在module.json5配置文件的requestPermissions标签中声明权限。

| 属性 | 含义 | 数据类型 | 取值范围 |
| -------- | -------- | -------- | -------- |
| name | 需要使用的权限名称。 | 字符串 | **必填**，需为系统已定义的权限，取值范围请参考[应用权限列表](app-permissions.md)。
| reason | 申请权限的原因。 | 字符串 | **可选填写**，该字段用于应用上架校验，申请user_grant权限时必填并需多语种适配。<br>格式为$string: \*\*\*。string资源引用需要在string.json文件配置标签"name": "reason"，配置样例可参考[资源文件示例](../../quick-start/resource-categories-and-access.md#资源文件示例)。<br/>reason填写内容可参考[权限使用理由的文案内容规范](#权限使用理由的文案内容规范)。 |
| usedScene | 权限使用的场景，该字段用于应用上架校验。包括abilities和when两个子项。<br/>- abilities：使用权限的UIAbility或者ExtensionAbility组件的名称。<br/>- when：调用时机。 | 对象 | **申请user_grant权限时，usedScene必填，其他情况下选填。<br>**<br/>- abilities：**可选填写**，可以配置为多个UIAbility或者ExtensionAbility名称的字符串数组。<br/>- when：**可选填写**，但如果配置此字段，只能填入固定值inuse（使用时）或always（始终），不能为空。<br/>当申请的权限为user_grant权限时建议填写。 |

> **说明：**
>
> 已在子模块中申请的权限无需在主项目中重复添加，权限将在整个应用中生效。

## 声明样例

> **说明：**
> 以下"ohos.permission.PERMISSION1"、"ohos.permission.PERMISSION2"仅为样例示意，不存在该权限。请开发者根据实际需要，参照上表要求填写对应属性。

```json
{
  "module" : {
    // ...
    "requestPermissions":[
      {
        "name" : "ohos.permission.PERMISSION1",
        "reason": "$string:reason",
        "usedScene": {
          "abilities": [
            "FormAbility"
          ],
          "when":"inuse"
        }
      },
      {
        "name" : "ohos.permission.PERMISSION2",
        "reason": "$string:reason",
        "usedScene": {
          "abilities": [
            "FormAbility"
          ],
          "when":"always"
        }
      }
    ]
  }
}
```

## 权限使用理由的文案内容规范

当申请user_grant权限时，字段reason（申请权限的原因）必填。开发者需在应用配置文件中配置每个需要的权限。

但在实际向用户弹窗申请授权时，user_grant权限将会以[权限组](app-permission-mgmt-overview.md#权限组和子权限)的形式向用户申请。当前支持的权限组请查看[应用权限组列表](app-permission-group-list.md)。

### reason字段的内容写作规范及建议
<!--RP1-->
1. 保持句子简洁，不要加入多余的分割符号。

   **建议句式**：用于某事。

   **示例**：用于扫码拍照。

2. 用途描述的字串建议小于72个字符（即36个中文字符，UI界面显示大约为两行）。不能超过256个字符，以保证多语言适配的体验。

3. 如果不填写，将展示默认的申请理由。
<!--RP1End-->
### 权限使用理由展示方式

权限使用理由有两个展示途径：授权弹窗界面和“设置（Settings）”界面。“设置”的具体路径：设置-隐私-权限管理-某应用某权限详情。

1. 如果申请的是“电话、信息、日历、通讯录、通话记录”这五个权限组中的权限，根据工信部要求，将展示具体子权限的内容与用途。

   **句式**：包括子权限A和子权限B，用于某事。

   **样例**：用于获取通话状态和移动网络信息，用于安全运营和统计计费服务。

2. 如果是申请其他权限组中的权限，系统将使用权限组内当前被申请的第一个子权限的使用理由，作为该权限组的使用理由进行展示。组内的排序固定按照权限管理内排列的权限组数组顺序。

   举例说明：权限组A = {权限A, 权限B, 权限C}；申请传入的权限是{权限C, 权限B}，界面将展示权限B的权限使用理由。

3. 如果应用内多包申请的权限名称相同，但权限使用理由不一致，系统返回的权限申请详细信息[ReqPermissionDetail](../../reference/apis-ability-kit/js-apis-bundleManager-bundleInfo.md#reqpermissiondetail)中只会显示一个权限申请理由。优先级从高到低为：entry类型HAP、feature类型HAP、应用内HSP。
