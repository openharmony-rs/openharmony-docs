# Configuring ArkTS Widget Configuration Files
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=f66217a374191afa08e6502e3cd59173c85fd1ac translatedAt=2026-08-26T04:46:59.288Z pushedAt=2026-08-28T08:25:49.692Z -->

Widget-related configuration files include the [FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md) configuration and the widget configuration. For [standalone widget packages](./arkts-ui-widget-creation.md#method-2-creating-a-standalone-package), the [standalone widget package configuration](./arkts-ui-widget-configuration.md#standalone-widget-package-configuration) is also included.
> **NOTE**
>
> - The widget quintuple is the set of elements that uniquely identify a widget. The quintuple consists of `bundleName`, `moduleName`, `abilityName`, `formName`, and `formDimension`. Specifically, `bundleName` corresponds to the `bundleName` configuration item in the [app.json5 configuration file tags](../quick-start/app-configuration-file.md#tags-in-the-configuration-file), `moduleName` corresponds to the `name` configuration item in the [module.json5 configuration file tags](../quick-start/module-configuration-file.md#tags-in-the-configuration-file), `abilityName` corresponds to the `name` configuration item in the [abilities tag](../quick-start/module-configuration-file.md#abilities), `formName` corresponds to the `name` configuration item in [fields in the configuration file](#fields-in-configuration-file), and `formDimension` corresponds to the `supportDimensions` configuration item in [fields in the configuration file](#fields-in-configuration-file).
> - It is not recommended to use resource file imports for the quintuple. When resource files are used for import, any addition of fields in the resource file will cause the corresponding IDs to change, which will be considered a change in the quintuple.
> - If the quintuple changes after an app upgrade, the corresponding widget in the system will be deleted and will disappear from the screen.

## FormExtensionAbility Configuration
Configure `FormExtensionAbility` information under `extensionAbilities` in the [module.json5 file](../quick-start/module-configuration-file.md). For `FormExtensionAbility`, you must specify `metadata`. Specifically, set **name** to **ohos.extension.form** (fixed), and set **resource** to the [index of the widget configuration information](#widget-configuration).

   Example:


  <!-- @[module_config_formCreate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormStandaloneDemo/entry/src/main/module.json5) --> 

  ``` JSON5
  {
    "module": {
      // ...
      "extensionAbilities": [
        {
          "name": "EntryFormAbility",
          "srcEntry": "./ets/entryformability/EntryFormAbility.ets",
          "label": "$string:EntryFormAbility_label",
          "description": "$string:EntryFormAbility_desc",
          "type": "form",
          "metadata": [
            {
              "name": "ohos.extension.form",
              "resource": "$profile:form_config"
            }
          ]
        }
      ],
      // This configuration is only applicable to the standalone widget package form and is used to associate the corresponding widget package module.
      "formWidgetModule": "library"
    }
  }
  ```


## Standalone Widget Package Configuration
In the [module.json5 file](../quick-start/module-configuration-file.md) of a widget package, the `formExtensionModule` field is used to associate with the `module` of the application bundle.<br>
Example:
<!-- @[standalone_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Form/FormStandaloneDemo/library/src/main/module.json5) -->

``` JSON5
{
  "module": {
    "name": "library",
    "type": "shared",
    "description": "$string:shared_desc",
    "deviceTypes": [
      "default"
    ],
    "deliveryWithInstall": true,
    // This configuration is only applicable to the standalone widget package form and is used to associate the corresponding application bundle module.
    "formExtensionModule": "entry"
  }
}
```


## Widget Configuration

In the **metadata** configuration item of FormExtensionAbility, you can specify the resource index of specific configuration information of the widget. For example, if **resource** is set to **$profile:form_config**, **form_config.json** in the **resources/base/profile/** directory of the development view is used as the profile configuration file of the widget. The **form_config.json** configuration file is automatically generated when you [create a widget](./arkts-ui-widget-creation.md).

### Fields in Configuration File

**Table 1** form_config.json file

| Name | Description | Data Type | Whether Optional |
| -------- | -------- | -------- | -------- |
| forms | Indicates all card configuration information of the application.<br/>A maximum of 16 cards can be configured. If more than 16 are configured, only the first 16 are retained. | Array | No |
| name | Indicates the name of the card. The maximum length of the string is 127 bytes. It is used to distinguish different cards.<br/>**Note:**<br/>It is not recommended to reference a resource file for this field. | String | No |
| displayName | Indicates the display name of the card. It is mainly displayed on the card management page, corresponding to <!--RP3-->"ArkTSCard"<!--RP3End--> on the [card management page](./formkit-overview.md#scenarios-for-widget-usage) in the card preview. It is used to display card information and should reflect the core function or purpose of the card. It supports a string or a string resource index. It is recommended to declare it using a string resource index to support full multilingual capabilities. The minimum length of the string is 1 byte and the maximum length is 30 bytes. | String | No |
| description | Indicates the description of the card. It is used to display the card function description on the card management page, corresponding to <!--RP4-->"This is a ArkTS card game by canvas."<!--RP4End--> on the [card management page](./formkit-overview.md#scenarios-for-widget-usage) in the card preview. It supports a string or a string resource index. It is recommended to declare it using a string resource index to support full multilingual capabilities. The maximum length of the string is 255 bytes. | String | Optional. The default is empty. |
| src | Indicates the complete path of the UI code corresponding to the card. For an ArkTS card, the complete path must include the file name extension of the card file, for example, "./ets/widget/pages/WidgetCard.ets". For a JS card, the complete path does not need to include the file name extension of the card file, for example, "./js/widget/pages/WidgetCard". | String | No |
| uiSyntax | Indicates the type of the card. The following two types are supported:<br/>-&nbsp;arkts: The card is an ArkTS card.<br/>-&nbsp;hml: The card is a JS card. | String | Optional. The default value is "hml". |
| window | Defines the configuration related to the display window.<br/>**Note:**<br/>This field takes effect only for JS cards. | Object | Optional. For the default value, see the [window field](#window-field) table. |
| isDefault | Indicates whether the card is the default card (the card that is preferentially displayed in the card center). Each application has one and only one default card.<br/>-&nbsp;true: The card is the default card.<br/>-&nbsp;false: The card is not the default card.<br/>**Note:**<br/>When an application is released, only one default card is allowed to be configured for each application. | Boolean | No |
| colorMode<sup>(deprecated)</sup> | Indicates the theme style of the card. The value range is as follows:<br/>-&nbsp;auto: The theme is selected based on the color mode of the system.<br/>-&nbsp;dark: Dark theme.<br/>-&nbsp;light: Light theme.<br/>**Note:**<br/>1. This configuration item is supported since API version 12 and deprecated since API version 20. The card theme style uniformly follows the color mode of the system.<br/>2. This field takes effect only for JS cards. | String | Optional. The default value is "auto". |
| supportDimensions | Indicates the appearance specifications supported by the card. The value range is as follows:<!--RP5--><!--RP5End--><br/>-&nbsp;1&nbsp;\*&nbsp;2: A 2-grid layout with 1 row and 2 columns.<br/>-&nbsp;2&nbsp;\*&nbsp;2: A 4-grid layout with 2 rows and 2 columns.<br/>-&nbsp;2&nbsp;\*&nbsp;4: An 8-grid layout with 2 rows and 4 columns.<br/>-&nbsp;2&nbsp;\*&nbsp;3: A 6-grid layout with 2 rows and 3 columns.<br/>-&nbsp;3&nbsp;\*&nbsp;3: A 9-grid layout with 3 rows and 3 columns.<br/>-&nbsp;4&nbsp;\*&nbsp;4: A 16-grid layout with 4 rows and 4 columns.<br/>-&nbsp;6&nbsp;\*&nbsp;4: A 24-grid layout with 6 rows and 4 columns.<br>**Note:** For the support on specific devices, see [supportDimensions field and device support relationship table](#supportdimensions-field-and-device-support-relationship-table). | String array | No |
| defaultDimension | Indicates the default size of the card. The value must be in the supportDimensions configuration list of the card. | String | No |
| updateEnabled | Indicates whether the card supports periodic refresh (including scheduled refresh and fixed-time refresh). The value range is as follows:<br/>-&nbsp;true: Periodic refresh is supported. You can choose either scheduled refresh (updateDuration) or fixed-time refresh (scheduledUpdateTime). When both are configured, scheduled refresh takes effect first.<br/>-&nbsp;false: Periodic refresh is not supported. | Boolean | No |
| scheduledUpdateTime | Indicates the time for [fixed-time refresh](./arkts-ui-widget-passive-refresh.md#time-specific-update) of the card. It uses the 24-hour format and is accurate to the minute, for example, "10:30".<br/>**Note:**<br/>The updateDuration parameter has a higher priority than scheduledUpdateTime. When both are configured, the refresh time configured by updateDuration takes effect. | String | Optional. The default value is "0:0", which means fixed-time refresh is not performed. |
| updateDuration | Indicates the update interval for [scheduled refresh](./arkts-ui-widget-passive-refresh.md#interval-based-update) of the card. The unit is 30 minutes, and the value is a natural number.<br/>When the value is 0, this parameter does not take effect.<br/>When the value is a positive integer N, the refresh interval is 30\*N minutes.<br/>**Note:**<br/>The updateDuration parameter has a higher priority than scheduledUpdateTime. When both are configured, the refresh time configured by updateDuration takes effect. | Number | Optional. The default value is 0. |
| formConfigAbility | Indicates the path of the ability to be started after the user taps Edit on the home screen. It uses the URI format. | String | Optional. The default is empty. |
| metadata | Indicates the custom information of the card. For details, see the [Metadata](../reference/apis-ability-kit/js-apis-bundleManager-metadata.md) array tag. | Object | Optional. The default is empty. |
| dataProxyEnabled | Indicates whether the card supports proxy refresh. The value range is as follows:<br/>-&nbsp;true: Proxy refresh is supported.<br/>-&nbsp;false: Proxy refresh is not supported.<br/>When this parameter is set to true, [scheduled refresh and next refresh](./arkts-ui-widget-passive-refresh.md#interval-based-update) do not take effect, but [fixed-time refresh](./arkts-ui-widget-passive-refresh.md#time-specific-update) is not affected.<br/>**Note:**<br/>This field is supported since API version 12. | Boolean | Optional. The default value is false. |
| isDynamic | Indicates whether the card is a dynamic card (takes effect only for ArkTS cards).<br/>-&nbsp;true: The card is a [dynamic card](./arkts-form-overview.md#dynamic-widget).<br/>-&nbsp;false: The card is a [static card](./arkts-form-overview.md#static-widget).<br/> | Boolean | Optional. The default value is true. |
| fontScaleFollowSystem | Indicates whether the font of the card set by the card user supports following system changes.<br/>-&nbsp;true: The font size follows system changes.<br/>-&nbsp;false: The font size does not follow system changes.<br/> | Boolean | Optional. The default value is true. |
| supportShapes | Indicates the display shape of the card. The value range is as follows:<br/>-&nbsp;rect: A rectangular card.<br/>-&nbsp;circle: A circular card. | String array | Optional. The default value is ["rect"]. |
| previewImages | Indicates the preview images of the card, which correspond one-to-one with the `supportDimensions` configuration item. This field must be configured for wearable cards and is currently supported only on wearables. | String array | Optional. The default value is []. |
| <!--DelRow-->formVisibleNotify | Indicates whether to notify the card provider of visibility state changes (takes effect only for cards of system applications).<br/>-&nbsp;true: The card provider is notified of visibility state changes.<br/>-&nbsp;false: The card provider is not notified of visibility state changes. | Boolean | Optional. The default value is false. |
| transparencyEnabled | Indicates whether the card is a transparent-backplane card (takes effect only for system applications or ArkTS cards that have applied for the transparent-backplane card capability).<br/>-&nbsp;true: The card is a transparent-backplane card.<br/>-&nbsp;false: The card is not a transparent-backplane card.<br/> | Boolean | Optional. The default value is false. |
| enableBlurBackground | Indicates whether the card uses a blurred backplane.<br/>-&nbsp;true: The blurred backplane is enabled.<br/>-&nbsp;false: The blurred backplane is disabled.<br/>**Note:**<br/>This feature has high requirements on product power consumption and performance. Since API version 23, it is supported only on flagship models. On unsupported models, calling it does not take effect. | Boolean | Optional. The default value is false. |
| renderingMode | Indicates the rendering mode of the card. The value range is as follows:<br/>-&nbsp;autoColor: Automatic mode. The final rendering effect, whether full-color or single-color, is determined by the card user<!--RP7--><!--RP7End-->. In this mode, the colors and images in the card can be modified by the card user. A card configured with this mode can be added to the home screen or lock screen.<br/>-&nbsp;fullColor: Full-color mode<!--RP7--><!--RP7End-->. In this mode, the colors and images in the card cannot be modified by the card user. A card configured with this mode can be added to the home screen.<br/>-&nbsp;singleColor: Single-color mode, which distinguishes elements by transparency and blur without using any hue<!--RP7--><!--RP7End-->. In this mode, the colors and images in the card can be modified by the card user. A card configured with this mode can be added to the lock screen.<br/>**Note:**<br/>This field is supported since API version 15. | String | Optional. The default value is "fullColor". |
| multiScheduledUpdateTime | Indicates the times for multiple fixed-time refreshes of the card, as an additional parameter for single-time refresh. It uses the 24-hour format and is accurate to the minute. Multiple times are separated by commas, and a maximum of 24 times can be written, for example, "10:30,10:50,11:00".<br/>**Note:**<br/>This field is supported since API version 18. multiScheduledUpdateTime must be used together with scheduledUpdateTime. | String | Optional. When omitted, multiple fixed-time refresh is not performed. |
| conditionUpdate | Indicates the conditional refresh supported by the card. The currently supported values are as follows:<br/>-&nbsp;network: Network refresh is supported.<br/>**Note:**<br/>This field is supported since API version 18<!--Del-->, and the feature is supported only for system applications<!--DelEnd-->. Since API version 26.0.0, the feature takes effect after being set. | String array | Optional. The default value is an empty string array. |
| [funInteractionParams](#funinteractionparams-field) | Extended field for interactive experience type interaction cards.<br/>**Note:**<br/>This field is supported since API version 20. | Object | Optional. The default is empty. When both funInteractionParams and sceneAnimationParams are configured, the card is identified as an interactive experience type interaction card. |
| [sceneAnimationParams](#sceneanimationparams-field) | Extended field for [scene animation type interaction cards](./arkts-ui-liveform-sceneanimation-development.md).<br/>**Note:**<br/>This field is supported since API version 20. | Object | Optional. The default is empty. When both funInteractionParams and sceneAnimationParams are configured, the card is identified as an interactive experience type interaction card. |
| resizable | Indicates whether the card can be dragged to adjust its size. The adjusted value must be in the supportDimensions configuration list of the card or of cards with the same groupId.<br/>-&nbsp;true: The size can be adjusted.<br/>-&nbsp;false: The size cannot be adjusted.<br/>**Note:**<br/>This field is supported since API version 20. | Boolean | Optional. The default value is false. |
| groupId | Indicates the common ID of a group of cards. When multiple cards have the same groupId and resizable is set to true, the supportDimensions configurations of these cards are shared. It is recommended to configure this field when multiple cards have the same function and need to adjust the card size.<br>Example 1: Card A has groupId set to '1', resizable set to true, and supportDimension set to 2\*2. Card B has groupId set to '1', resizable set to true, and supportDimension set to 2\*4. In this case, size adjustment between cards A and B is supported.<br>Example 2: When supportDimension has multiple values and resizable is set to true, size adjustment within the same card takes priority. Card A has resizable set to true and supportDimension set to 2\*2 and 2\*4, so size adjustment between the two sizes of card A is supported.<br>Example 3: Card A has groupId set to '1', resizable set to true, and supportDimension set to 1\*2. Card B has groupId set to '1', resizable set to true, and supportDimension set to 2\*2, 2\*4, and 4\*4. Card A can be adjusted to the default size of card B, while card B supports size adjustment only among the three sizes supported by card B and cannot be adjusted to card A.<br/>**Note:**<br/>This field is supported since API version 20. | String | Optional. Empty string. |
| [supportDeviceTypes](#supportdevicetypes-field) | Indicates the device types supported by a specific card. For example, if the supportDeviceTypes field of a card is configured with "phone", "tablet", and "tv", the card can be displayed on phones, tablets, and large screens.<br/>**Note:**<br/>This field is supported since API version 22. | String array | Optional. The default value is ["phone", "tablet", "tv", "wearable", "car", "2in1"]. |
| [supportDevicePerformanceClasses](#supportdeviceperformanceclasses-field) | Indicates the device performance class information supported by a specific card. For example, if the supportDevicePerformanceClasses field of a card is configured with "high", "medium", and "low", the card can be displayed on devices with the performance classes "high", "medium", and "low".<br/>**Note:**<br/>This field is supported since API version 22. | String array | Optional. The default value is ["high", "medium", "low"]. |
| [standby](#standby-field) | Extended field for the standby screensaver display page card.<br/>**Note:**<br/>This field is supported since API version 23. It depends on the system implementing the standby screensaver display application before it is displayed. | Object | Optional. For the default values of the attributes, see the [standby field](#standby-field). |

### supportDeviceTypes Field

Specifies the device type supported by the widget.

   | Field| Description  | Data Type                     |
   | ---- | ---- | -------------------------- |
   | phone | Smartphone| String|
   | tablet | Tablet| String|
   | tv | Vision| String|
   | wearable | Wearable| String|
   | car | Head unit| String|
   | 2in1 | PC/2-in-1 device| String|

### supportDevicePerformanceClasses Field

Specifies the device performance class supported by the widget.

   | Field| Description  | Data Type                     |
   | ---- | ---- | -------------------------- |
   | high | High| String|
   | medium | Medium| String|
   | low | Low| String|

### window Field

Defines the internal structure of the **window** object. This field is supported only in JS widgets.

   | Field| Description| Data Type| Default Value Allowed|
   | -------- | -------- | -------- | -------- |
   | designWidth | Specifies the base width for page design. Based on this width, element sizes are scaled according to the actual device width. The value range is greater than or equal to 0 and less than 2^16. Unit: px. | Number | Yes (initial value: 720px) |
   | autoDesignWidth | Whether to automatically calculate the baseline width for page design. If it is set to **true**, the **designWidth** attribute will be ignored, and the baseline width will be calculated based on the device width and screen density.| Boolean| Yes (initial value: **false**)|

### funInteractionParams Field

Specifies a fun-based widget. If **funInteractionParams** and **sceneAnimationParams** are both configured, the interactive widget is a fun-based widget.

| Name               | Type | Mandatory| Description                                                                                                                                 |
|-------------------|-----|----|-------------------------------------------------------------------------------------------------------------------------------------|
| abilityName       | String| No | LiveFormExtensionAbility name. This parameter is left empty by default.                                                                                             |
| targetBundleName  | String| Yes | Main bundle name.      |
| subBundleName     | String| No | Sub bundle name.|
| keepStateDuration | Number | No | Duration for which the active state is retained when there is no interaction in an interactive scenario. The default value is 10000, in ms. The value is an integer in the range (0, 60000]. If the value exceeds this range, the maximum value 60000 is used.<br/>**Note:** Before API version 26.0.0, this field is an integer in the range (0, 10000]. If the value exceeds this range, the default value 10000 is used. |

```json5
{
  "forms": [
    {
       // ...
      "funInteractionParams": {
         "targetBundleName": "com.example.funInteraction",
         "subBundleName": "com.example.subFunInteraction"
      }
    }
  ]
}
```

### sceneAnimationParams Field

Specifies a scene-based widget. If **funInteractionParams** and **sceneAnimationParams** are both configured, the interactive widget is a fun-based widget.

| Name                                   | Type    | Mandatory| Description|
|---------------------------------------|--------|----|----------------------------|
| abilityName                           | String| Yes | LiveFormExtensionAbility name of the scene-based widget.|
| disabledDesktopBehaviors | Array of strings | No | Supported values include SWIPE_DESKTOP (swipe on the home screen), PULL_DOWN_SEARCH (pull down for global search), LONG_CLICK (long press), and DRAG (drag). One or more values can be specified. The default value means no behavior is disabled.<br/>**Note:**<br/>This field is supported since API version 20 and is effective only for system apps. |
| triggerTypes | Array of strings | No | Scene animation trigger type. Supported values include shake.<br/>**Note:**<br/>This field is supported since API version 26.0.0. |

<!--RP2-->
   ```json5
   {
     "forms": [
       {
          // ...
         "sceneAnimationParams": {
            "abilityName": "MyLiveFormExtensionAbility",
            "disabledDesktopBehaviors": [
              "SWIPE_DESKTOP",
              "PULL_DOWN_SEARCH",
              "LONG_CLICK",
              "DRAG"
            ],
            "triggerTypes": [
              "shake"
            ]
         }          
       }
     ]
   }
   ```
<!--RP2End-->

### standby Field

This tag identifies the internal structure of the standby object. The app must apply for the open capability, and the widget's isSupported configuration must be set to true for it to be displayed on the standby screen saver display interface.

| Field| Description| Data Type| Default Value Allowed|
| -------- | -------- | -------- | -------- |
| isSupported | Whether the widget supports display on the standby screen saver interface.<br/>-&nbsp;true: The widget supports display on the standby screen saver interface.<br/>-&nbsp;false: The widget does not support display on the standby screen saver interface. | Boolean | Yes. The default value is **true**. |
| isAdapted | Whether the widget has been adapted for the standby screen saver interface. If set to **true**, the `backgroundImage` in the widget layout component will be removed.<br/>-&nbsp;true: The widget has been adapted for the standby screen saver interface.<br/>-&nbsp;false: The widget has not been adapted for the standby screen saver interface. | Boolean | Yes. The default value is **false**. |
| isPrivacySensitive | Whether the widget is privacy-sensitive. A privacy-sensitive widget displayed on the standby screen saver interface will be covered by a mask layer.<br/>-&nbsp;true: The widget is privacy-sensitive.<br/>-&nbsp;false: The widget is not privacy-sensitive. | Boolean | Yes. The default value is **false**. |

   ```json5
   {
     "forms": [
       {
         // ...
         "standby": {
           "isSupported": true,
           "isAdapted": false,
           "isPrivacySensitive": false
         }          
       }
     ]
   }
   ```

### Configuration File Example

<!--RP1-->
   ```json5
   {
     "forms": [
       {
         "name": "widget",
         "displayName": "$string:widget_display_name",
         "description": "$string:widget_desc",
         "src": "./ets/widget/pages/WidgetCard.ets",
         "uiSyntax": "arkts",
         "window": {
           "designWidth": 720,
           "autoDesignWidth": true
         },
         "renderingMode": "fullColor",
         "isDefault": true,
         "updateEnabled": true,
         "scheduledUpdateTime": "10:30",
         "updateDuration": 1,
         "defaultDimension": "2*2",
         "supportDimensions": [
           "2*2"
         ],
         "formConfigAbility": "ability://EntryAbility",
         "isDynamic": true,
         "metadata": []
       }
     ]
   }
   ```
<!--RP1End-->

### supportDimensions Field and Device Support Relationship Table

Widget size specifications supported by each device type. "Lock screen only" indicates that the size is applicable only to lock screen scenarios. "Some models" indicates that specific support depends on the device's home screen grid configuration.

| Card Size Information | Phone | PC | 2-in-1 | Tablet | TV | Car | Wearable |
|-------------|-------|----|------|------|------|------|------|
|"1*2"|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
|"2*2"|Yes|Yes|Yes|Yes|Yes|Yes|Yes|
|"2*4"|Yes|Yes|Yes|Yes|Yes|Yes|No|
|"4*4"|Yes|Yes|Yes|Yes|Yes|Yes|No|
|"1*1"|Yes (lock screen only)|No|No|Yes (lock screen only)|No|No|Yes|
|"6*4"|Yes (some models)|Yes|Yes|Yes (some models)|No|No|No|
|"2*3"|No|No|No|No|No|No|Yes|
|"3*3"|No|No|No|No|No|No|Yes|