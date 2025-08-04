# 选择申请权限的方式

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--SE: @linshuqing; @hehehe-li-->
<!--TSE: @leiyuqian-->

应用在访问数据或者执行操作时，需要评估该行为是否需要应用具备相关的权限。如果确认需要目标权限，则需要在应用安装包中申请目标权限。

每一个权限的权限等级、授权方式不同，申请权限的方式也不同，开发者在申请权限前，需要：

1. 确认目标权限的**权限类型**。可通过在对应的权限列表页面中检索确认。
2. 参考对应的操作路径，申请权限。

应用可根据目标权限的开放范围、授权方式，参考以下操作路径申请对应权限。

## <!--Del-->normal等级<!--DelEnd-->应用申请权限的方式

| 权限类型 | 授权方式 | 操作路径 |
| -------- | -------- | -------- |
| [开放权限（系统授权）](permissions-for-all.md) | system_grant | [声明权限](declare-permissions.md) &gt; 访问接口 | 
| [开放权限（用户授权）](permissions-for-all-user.md) | user_grant  | [声明权限](declare-permissions.md) &gt; [向用户申请授权](request-user-authorization.md) &gt; 访问接口 | 
| <!--Del-->[允许通过ACL申请的系统权限（系统授权）](permissions-for-system-apps.md)<br><!--DelEnd-->[受限开放权限](restricted-permissions.md) | system_grant | <!--RP1-->[申请使用受限权限](declare-permissions-in-acl.md)<!--RP1End--> &gt; [声明权限](declare-permissions.md) &gt; 访问接口 | 
| <!--Del-->[允许通过ACL申请的系统权限（用户授权）](permissions-for-system-apps-user.md)<br><!--DelEnd-->[受限开放权限](restricted-permissions.md) | user_grant | <!--RP1-->[申请使用受限权限](declare-permissions-in-acl.md)<!--RP1End--> &gt; [声明权限](declare-permissions.md) &gt; [向用户申请授权](request-user-authorization.md) &gt; 访问接口 |

<!--Del-->
> **说明：**
>
> - 如果system_basic等级的权限，ACL使能为false，则normal等级应用无法申请该权限。
> - 当前可通过DevEco Studio完成[ACL方式跨级别申请权限](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-signing)，但该方法仅用于应用调试阶段使用，不可用于发布上架应用市场。如果需要开发商用版本的应用，请在对应的应用市场进行发布证书和Profile文件的申请。

## system_basic等级应用申请权限的方式

| 权限等级 | 授权方式 | ACL使能 | 操作路径 | 
| -------- | -------- | -------- | -------- |
| normal、system_basic | system_grant | - | [声明权限](declare-permissions.md) &gt; 访问接口 | 
| normal、system_basic | user_grant | - | [声明权限](declare-permissions.md) &gt; [向用户申请授权](request-user-authorization.md) &gt; 访问接口 | 
| system_core | system_grant | true | [申请使用受限权限](declare-permissions-in-acl.md) &gt; [声明权限](declare-permissions.md) &gt; 访问接口 | 
| system_core | user_grant | true | [申请使用受限权限](declare-permissions-in-acl.md) &gt; [声明权限](declare-permissions.md) &gt; [向用户申请授权](request-user-authorization.md) &gt; 访问接口 | 

如果应用需要将自身的APL等级声明为system_basic及以上，在开发应用安装包时，需要修改应用的HarmonyAppProvision配置文件即SDK目录下的“`Toolchains / _{Version} _/ lib / UnsgnedReleasedProfileTemplate.json`”文件，并重新进行应用签名。

**修改方式：**

HarmonyAppProvision配置文件示例如下所示，修改"bundle-info" &gt; "apl" 字段。

```json
"bundle-info" : {
    // ...
    "apl": "system_basic",
    // ...
},
```

> **说明：**
> 直接修改HarmonyAppProvision配置文件的方式，仅用于应用调试阶段使用，不可用于发布上架应用市场。如果需要开发商用版本的应用，请在对应的应用市场进行发布证书和Profile文件的申请。

<!--DelEnd-->