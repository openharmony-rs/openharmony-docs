# ArkTS卡片被动刷新
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @chenmingze-->
<!--Adviser: @Brilliantry_Rui-->

本文主要提供被动刷新的开发指导，刷新流程请参考[被动刷新概述](./arkts-ui-widget-interaction-overview.md#被动刷新)。

## 卡片定时刷新

当前卡片框架提供了如下两种按时间刷新卡片的方式：

- 定时刷新：表示在一定时间间隔内调用[onUpdateForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform)的生命周期回调函数自动刷新卡片内容。可以在[form_config.json](arkts-ui-widget-configuration.md#配置文件字段说明)配置文件的`updateDuration`字段中进行设置。例如，可以将`updateDuration`字段的值设置为2，表示刷新时间间隔为2个30分钟，即1小时。

  ```json
  {
    "forms": [
      {
        "name": "UpdateDuration",
        "description": "$string:widget_updateduration_desc",
        "src": "./ets/updateduration/pages/UpdateDurationCard.ets",
        "uiSyntax": "arkts",
        "window": {
          "designWidth": 720,
          "autoDesignWidth": true
        },
        "colorMode": "auto",
        "isDefault": true,
        "updateEnabled": true,
        "scheduledUpdateTime": "10:30",
        "updateDuration": 2,
        "defaultDimension": "2*2",
        "supportDimensions": [
          "2*2"
        ]
      }
    ]
  }
  ```
 > **说明：**
  >
  > 在使用定时刷新时，需要在form_config.json配置文件中设置`updateEnabled`字段为`true`，以启用周期性刷新功能。

- 下次刷新：表示指定卡片的下一次刷新时间。可以通过调用[setFormNextRefreshTime](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formprovidersetformnextrefreshtime)接口来实现。最短刷新时间为5分钟。例如，可以在接口调用后的5分钟内刷新卡片内容。

  ```ts
  import { FormExtensionAbility, formProvider } from '@kit.FormKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  
  const TAG: string = 'UpdateByTimeFormAbility';
  const FIVE_MINUTE: number = 5;
  const DOMAIN_NUMBER: number = 0xFF00;
  
  export default class UpdateByTimeFormAbility extends FormExtensionAbility {
    onFormEvent(formId: string, message: string): void {
      // Called when a specified message event defined by the form provider is triggered.
      hilog.info(DOMAIN_NUMBER, TAG, `FormAbility onFormEvent, formId = ${formId}, message: ${JSON.stringify(message)}`);
      try {
        // 设置过5分钟后更新卡片内容
        formProvider.setFormNextRefreshTime(formId, FIVE_MINUTE, (err: BusinessError) => {
          if (err) {
            hilog.info(DOMAIN_NUMBER, TAG, `Failed to setFormNextRefreshTime. Code: ${err.code}, message: ${err.message}`);
            return;
          } else {
            hilog.info(DOMAIN_NUMBER, TAG, 'Succeeded in setFormNextRefreshTiming.');
          }
        });
      } catch (err) {
        hilog.info(DOMAIN_NUMBER, TAG, `Failed to setFormNextRefreshTime. Code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
      }
    }
    // ... 
  }
  ```

在触发定时、下次刷新后，系统会调用FormExtensionAbility的[onUpdateForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform)生命周期回调，在回调中，可以使用[updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform)进行提供方刷新卡片。`onUpdateForm`生命周期回调的使用请参见[卡片生命周期管理](./arkts-ui-widget-lifecycle.md)。

**约束限制：**
1. 定时刷新有配额限制，每张卡片每天最多通过定时方式触发刷新50次，定时刷新次数可以通过修改[卡片配置项updateDuration字段](arkts-ui-widget-configuration.md#配置文件字段说明)、或调用[setFormNextRefreshTime](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formprovidersetformnextrefreshtime)接口两种方式进行设置，当达到50次配额后，无法通过定时方式再次触发刷新，刷新次数会在每天的0点重置。
>
2. 当前定时刷新使用同一个计时器进行计时，因此卡片定时刷新的第一次刷新会有最多30分钟的偏差。比如第一张卡片A（每隔半小时刷新一次）在3点20分添加成功，定时器启动并每隔半小时触发一次事件，第二张卡片B(每隔半小时刷新一次)在3点40分添加成功，在3点50分定时器事件触发时，卡片A触发定时刷新，卡片B会在下次事件（4点20分）中才会触发。
>
3. 定时刷新在卡片可见情况下才会触发，在卡片不可见时仅会记录刷新动作和刷新数据，待可见时统一刷新布局。
>
4. 如果使能了卡片代理刷新，定时刷新和下次刷新不生效。

## 卡片定点刷新

当前卡片框架提供了如下两种定点刷新卡片的方式：

- 单定点刷新：表示在每天的某个特定时间点自动刷新卡片内容。可以在form_config.json配置文件中的`scheduledUpdateTime`字段中进行设置。例如，可以将刷新时间设置为每天的上午10点30分。
 
  
  ```json
  {
    "forms": [
      {
        "name": "ScheduledUpdateTime",
        "description": "$string:widget_scheupdatetime_desc",
        "src": "./ets/scheduledupdatetime/pages/ScheduledUpdateTimeCard.ets",
        "uiSyntax": "arkts",
        "window": {
          "designWidth": 720,
          "autoDesignWidth": true
        },
        "colorMode": "auto",
        "isDefault": true,
        "updateEnabled": true,
        "scheduledUpdateTime": "10:30",
        "updateDuration": 0,
        "defaultDimension": "2*2",
        "supportDimensions": [
          "2*2"
        ]
      }
    ]
  }
  ```

- 多定点刷新：表示在每天的多个特定时间点自动刷新卡片内容。可以在form_config.json配置文件中的`multiScheduledUpdateTime`字段中进行设置，例如，可以将刷新时间设置为每天的上午11点30分和下午4点30分。
  ```json
  {
    "forms": [
    {
        "name": "ScheduledUpdateTime",
        "description": "$string:widget_scheupdatetime_desc",
        "src": "./ets/scheduledupdatetime/pages/ScheduledUpdateTimeCard.ets",
        "uiSyntax": "arkts",
        "window": {
          "designWidth": 720,
          "autoDesignWidth": true
        },
        "colorMode": "auto",
        "isDefault": true,
        "updateEnabled": true,
        "scheduledUpdateTime": "10:30",
        "multiScheduledUpdateTime": "11:30,16:30,",
        "updateDuration": 0,
        "defaultDimension": "2*2",
        "supportDimensions": [
          "2*2"
        ]
      }
    ]
  }
  ```

在触发定点刷新后，系统会调用FormExtensionAbility的[onUpdateForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform)生命周期回调，在回调中，可以使用[updateForm](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderupdateform)进行提供方刷新卡片。`onUpdateForm`生命周期回调的使用请参见[卡片生命周期管理](./arkts-ui-widget-lifecycle.md)。

> **说明：**
> 1. 当同时配置了定时刷新`updateDuration`和定点刷新`scheduledUpdateTime`时，定时刷新的优先级更高且定点刷新不会执行。如果想要配置定点刷新，则需要将`updateDuration`配置为0。
> 2. `multiScheduledUpdateTime`的配置最多可设置24个时间。
> 3. 同时配置了单定点和多定点刷新，多定点刷新配置生效，单定点刷新配置不生效。
> 4. 考虑到向前兼容的问题，尽量保留`scheduledUpdateTime`字段，不要直接删除。

**约束限制：**
1. 定点刷新在卡片可见情况下才会触发，在卡片不可见时仅会记录刷新动作和刷新数据，待可见时统一刷新布局。
<!--Del-->

## 卡片条件刷新

当前卡片框架提供了如下按条件刷新卡片的方式：
 
- 网络刷新：表示在网络变化的场景下调用[onUpdateForm](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md#formextensionabilityonupdateform)的生命周期回调函数自动刷新卡片内容。可以在[form_config.json](arkts-ui-widget-configuration.md)配置文件的`conditionUpdate`字段中进行设置，设置字段为network。
 
> **说明：**
> 1. 当从无网络到有网络连接时会触发刷新。而网络间切换（例如：WiFi间切换，WiFi到流量，流量到WiFi），或从有网络连接到无网络连接时不会触发刷新。
>
> 2. 为减少卡片在频繁开关网络场景进程启动次数，无网判定需要网络连续断开十分钟后，才会认为无网，下次联网后触发网络刷新。
>
> 3. 仅对系统应用的卡片生效。
 

  ```json
  {
    "forms": [
      {
        "name": "UpdateDuration",
        "description": "$string:widget_updateduration_desc",
        "src": "./ets/updateduration/pages/UpdateDurationCard.ets",
        "uiSyntax": "arkts",
        "window": {
          "designWidth": 720,
          "autoDesignWidth": true
        },
        "colorMode": "auto",
        "isDefault": true,
        "updateEnabled": true,
        "scheduledUpdateTime": "10:30",
        "updateDuration": 2,
        "defaultDimension": "2*2",
        "supportDimensions": [
          "2*2"
        ],
        "conditionUpdate": [
          "network"
        ]
      }
    ]
  }
  ```
  <!--DelEnd-->