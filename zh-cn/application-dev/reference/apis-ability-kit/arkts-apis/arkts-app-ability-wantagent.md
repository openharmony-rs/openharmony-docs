# @ohos.app.ability.wantAgent

WantAgent模块封装了[Want](arkts-ability-app-ability-want-want-c.md)对象，允许应用程序在未来的某个时间点触发WantAgent实例执行指定操作（如启动Ability、发送公共事件等）。

该模块提供了创建WantAgent实例、获取WantAgent实例所属应用的包名、获取WantAgent实例所属应用的UID、主动触发WantAgent实例、判断两个WantAgent实例是否相等等功能。WantAgent的一个典型应用场景是通知处理。例如，当用户点击通知时，会触发WantAgent的[trigger](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-trigger-i-sys.md)接口，并拉起目标应用。具体使用请参考[Notification](../../../notification/notification-with-wantagent.md)。

## 导入模块

```TypeScript
import { WantAgent } from '@kit.AbilityKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [wantAgent](arkts-ability-wantagent-n.md) | WantAgent模块封装了[Want](arkts-ability-app-ability-want-want-c.md)对象，允许应用程序在未来的某个时间点触发WantAgent实例执行指定操作（如启动Ability、发送公共事件等）。  该模块提供了创建WantAgent实例、获取WantAgent实例所属应用的包名、获取WantAgent实例所属应用的UID、主动触发WantAgent实例、判断两个WantAgent实例是否相等等功能。WantAgent的一个典型应用场景是通知处理。例如，当用户点击通知时，会触发WantAgent的[trigger](../../apis-notification-kit/arkts-apis/arkts-notification-notificationrequest-trigger-i-sys.md)接口，并拉起目标应用。具体使用请参考[Notification](../../../notification/notification-with-wantagent.md)。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [WantAgent](arkts-ability-wantagent-t.md) | WantAgent对象。 |

