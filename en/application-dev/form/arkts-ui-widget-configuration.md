# Configuring ArkTS Widget Configuration Files
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

Widget-related configuration includes [FormExtensionAbility](../reference/apis-form-kit/js-apis-app-form-formExtensionAbility.md) configuration and widget configuration. A [standalone widget package](./arkts-ui-widget-creation.md) includes the [standalone widget package configuration](./arkts-ui-widget-configuration.md#standalone-widget-package-configuration).
> **NOTE**
>
> The widget five-tuple comprises the unique identifiers of a widget, including **bundleName**, **moduleName**, **abilityName**, **formName**, and **formDimension**. If the five-tuple is modified following an application upgrade, the corresponding widget will be removed from the system and no longer appear on the home screen. **bundleName** refers to the **bundleName** tag in the [app.json5 file](../quick-start/app-configuration-file.md#tags-in-the-configuration-file), **moduleName** corresponds to **name** tag in the [module.json5 file](../quick-start/module-configuration-file.md#tags-in-the-configuration-file), **abilityName** is the **name** property in the [abilities tag](../quick-start/module-configuration-file.md#abilities), **formName** denotes the **name** field specified in the [widget configuration file](#fields-in-configuration-file), and **formDimension** refers to the **supportDimensions** field in the [widget configuration file](#fields-in-configuration-file).

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
      "phone"
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

| Field| Description| Data Type| Default Value Allowed|
| -------- | -------- | -------- | -------- |
| forms | Configuration about all application widgets.<br>A maximum of 16 widgets can be configured. If more than 16 widgets are configured, the first 16 widgets are retained.| Array| No|
| name | Name of the widget. The value is a string with a maximum of 127 bytes. It is used to distinguish different widgets.| String| No|
| displayName | Display name of the widget. It is mainly displayed on the [widget management page](./formkit-overview.md#scenarios-for-widget-usage) and corresponds to <!--RP3-->"ArkTSCard"<!--RP3End--> in the preview. It is recommended that the name reflect the core functionalities or usage of the widget. The value can be a string or a resource index to the name in multiple languages, with the resource index recommended. The string must contain 1 to 30 bytes.| String| No|
| description | Description of the widget. It is used to display the widget description on the [widget management page](./formkit-overview.md#scenarios-for-widget-usage) and corresponds to <!--RP4-->"This is a ArkTS card game by canvas."<!--RP4End--> in the preview. The value can be a string or a resource index to the name in multiple languages, with the resource index recommended. The value is a string with a maximum of 255 bytes.| String| Yes (initial value: left empty)|
| src | Full path of the UI code corresponding to the widget. For an ArkTS widget, the full path must contain the widget file name extension, for example, **./ets/widget/pages/WidgetCard.ets**. For a JS widget, the full path does not need to contain the widget file name extension, for example, **./js/widget/pages/WidgetCard**.| String| No|
| uiSyntax | Type of the widget.<br>- **arkts**: ArkTS widget<br>- **hml**: JS widget| String| Yes (initial value: **hml**)|
| [window](#window-field)| Window-related configurations.<br>**Note:**<br>This field takes effect only for JS widgets.| Object| Yes (initial value: see Table 2)|
| isDefault | Whether the widget is the default one (the widget that appears first in the widget center). Each application supports only one default widget.<br>- **true**: The widget is the default one.<br>- **false**: The widget is not the default one.<br>**Note:**<br> 1. If multiple widgets are configured as default widgets during local debugging, the system will select the first one with **isDefault** set to **true** as the default widget.<br>2. When an application is released, only one default widget can be configured for the application.| Boolean| No|
| colorMode<sup>(deprecated)</sup> | Color mode of the widget.<br>- **auto**: following the system color mode<br>- **dark**: dark color mode<br>- **light**: light color mode<br>**Note:**<br>1. This configuration item is supported since API version 12 and deprecated since API version 20. The color mode follows the system color mode.<br>2. This field takes effect only for JS widgets.| String| Yes (initial value: **auto**)|
| supportDimensions | Supported widget dimensions. The options are as follows:<!--RP5--><!--RP5End--><br>- **1 * 2**: indicates a grid with one row and two columns.<br>- **2 * 2**: indicates a grid with two rows and two columns.<br>- **2 * 4**: indicates a grid with two rows and four columns.<br>- **2 * 3**: indicates a grid with two rows and three columns.<br>- **3 * 3**: indicates a grid with three rows and three columns.<br>- **4 * 4**: indicates a grid with four rows and four columns.<br>- **6 * 4**: indicates a grid with six rows and four columns.<br>**Note**: **2 * 3** and **3 * 3** support only watches<!--RP6--><!--RP6End-->.| String array| No|
| defaultDimension | Default dimensions of the widget. The value must be available in the **supportDimensions** array of the widget.| String| No|
| updateEnabled | Whether the widget can be updated periodically.<br>- **true**: The widget can be updated at a specified interval (**updateDuration**) or at the scheduled time (**scheduledUpdateTime**). **updateDuration** takes precedence over **scheduledUpdateTime**. If both are specified, the value specified by **updateDuration** is used.<br>- **false**: The widget cannot be updated periodically.| Boolean| No|
| scheduledUpdateTime | [Scheduled time](./arkts-ui-widget-passive-refresh.md#time-specific-update) to update the widget. The value is in 24-hour format and accurate to minute, for example, 10:30.<br>**Note:**<br>**updateDuration** takes precedence over **scheduledUpdateTime**. If both are specified, the value specified by **updateDuration** is used.| String| Yes (initial value: The widget is not updated at the scheduled time.)|
| updateDuration | [Interval to update](./arkts-ui-widget-passive-refresh.md#interval-based-update) the widget. The value is a natural number, in the unit of 30 minutes.<br>If the value is **0**, this field does not take effect.<br>If the value is a positive integer *N*, the interval is calculated by multiplying *N* and 30 minutes.<br>**Note:**<br>**updateDuration** takes precedence over **scheduledUpdateTime**. If both are specified, the value specified by **updateDuration** is used.| Number| Yes (initial value: **0**)|
| formConfigAbility | Ability path to be opened after the widget is tapped for editing. The value is in URI format.| String| Yes (initial value: left empty)|
| metadata | Metadata of the widget. For details, see [Metadata](../reference/apis-ability-kit/js-apis-bundleManager-metadata.md).| Object| Yes (initial value: left empty)|
| <!--DelRow-->dataProxyEnabled | Whether the widget supports the [update-through-proxy](./arkts-ui-widget-update-by-proxy-sys.md) feature.<br>- **true**: The widget supports the update-through-proxy feature.<br>- **false**: The widget does not support the update-through-proxy feature.<br>If it is set to **true**, the settings for the [interval-based update and next update](./arkts-ui-widget-passive-refresh.md#interval-based-update) will not take effect, and [Time-specific Update](./arkts-ui-widget-passive-refresh.md#time-specific-update) is not affected.| Boolean| Yes (initial value: **false**)|
| isDynamic | Whether the widget is a dynamic widget. This field applies only to ArkTS widgets.<br>- **true**: [dynamic widget](./arkts-form-overview.md#dynamic-widget).<br>- **false**: [static widget](./arkts-form-overview.md#static-widget).<br>| Boolean| Yes (initial value: **true**)|
| fontScaleFollowSystem | Whether the font size of the widget changes with the system font size.<br>- **true**: The font size varies with the system font size.<br>- **false**: The font size cannot change with the system font size.<br>| Boolean| Yes (initial value: **true**)|
| supportShapes | Shapes that the widget can be displayed. The options are as follows:<br>- **rect**: rectangular widget.<br>- **circle**: circular widget.| String array| Yes (initial value: **rect**)|
| previewImages | Preview images of the widget, corresponding to the `supportDimensions` parameter. It is mandatory for smart wearables and currently valid only for wearables.| String| Yes|
| <!--DelRow-->formVisibleNotify | Whether to notify the widget provider of the visible status change. This field is valid only for widgets of system applications.<br>- **true**: The widget provider is notified of the status change.<br>- **false**: The widget provider is not notified of the status change.| Boolean| Yes (initial value: **false**)|
| transparencyEnabled | Whether a transparent background is enabled for the widget. (valid only for system applications or ArkTS widgets that have requested the background transparency capability).<br>- **true**: A transparent background is enabled.<br>- **false**: A transparent background is disabled.<br>| Boolean| Yes (initial value: **false**)|
|enableBlurBackground|Whether a blur background is enabled for the widget.<br>- **true**: A blur background is enabled.<br>- **false**: A blur background is disabled.|Boolean|Yes (initial value: **false**)|
|renderingMode|Rendering mode of the widget.<br>- **autoColor**: automatic mode. The display effect can be determined by the widget host as either full-color or monochrome<!--RP7--><!--RP7End-->. In this mode, the colors and images in the widget can be modified by the widget host. The widget can be added to the home screen or lock screen.<br>- **fullColor**: full-color mode<!--RP7--><!--RP7End-->. In this mode, the colors and images in the widget cannot be modified by the widget host. The widget can be added to the home screen.<br>- **singleColor**: monochrome mode. Elements are distinguished by opacity and blur but not by hue<!--RP7--><!--RP7End-->. In this mode, the colors and images in the widget can be modified by the widget host. The widget can be added to the lock screen.<br>**Note:**<br>This field is supported since API version 15.|String|Yes (initial value: **fullColor**)|
|multiScheduledUpdateTime|Times for updating the widget. As an additional parameter for single-point update, it follows the 24-hour format, precise to the minute. It allows up to 24 distinct times, with every two times separated by a comma (,).<br>**Note:**<br>This field is supported since API version 18. It must be used together with **scheduledUpdateTime**.|String|Yes (initial value: The widget is not updated at the scheduled times.)|
|conditionUpdate|Conditional update capabilities supported by the widget (valid only for ArkTS widgets of system applications). The value can be:<br>- **network**: Network update is supported.<br>**Note:**<br>This field is supported since API version 18.|String|Yes (initial value: an empty string)|
|[funInteractionParams](#funinteractionparams-field)| Extended field of the fun-based widget. This field is supported since API version 20.| Object| Yes (initial value: left empty) If **funInteractionParams** and **sceneAnimationParams** are both configured, the interactive widget is a fun-based widget.|
|[sceneAnimationParams](#sceneanimationparams-field)| Extended field of the [scene-based widgets](./arkts-ui-liveform-sceneanimation-overview.md). This field is supported since API version 20.| Object| Yes (initial value: left empty) If **funInteractionParams** and **sceneAnimationParams** are both configured, the interactive widget is a fun-based widget.|
| resizable | Whether the widget can be resized by dragging. The value must be in the **supportDimensions** configuration list of the widget or the widget with the same **groupId**.<br>- **true**: The widget can be resized.<br>- **false**: The widget cannot be resized.<br>**Note:**<br>This field is supported since API version 20.| Boolean| Yes (initial value: **false**)|
| groupId | Common ID of a group of widgets. If the values of **groupId** of multiple widgets are the same and the value of **resizable** is **true**, the **supportDimensions** configuration of multiple widgets is shared. For example, if the **groupId** values of widgets A and B are the same and the **resizable** values are **true**, widget A can be adjusted to any size specified by **supportDimensions**.<br>It is recommended that this field be set when multiple widgets with the same functionality need to be resized.<br>**Note:**<br>This field is supported since API version 20.| String| Yes (initial value: **false**)|
| [supportDeviceTypes](#supportdevicetypes-field)| Device type supported by a widget. For example, if **supportDeviceTypes** is set to **phone**, **tablet**, and **tv**, the widget can be displayed on smartphones, tablets, and Visions.<br>**Note:**<br>This field is supported since API version 21.| String array| Yes. The default values are **phone**, **tablet**, **tv**, **wearable**, **car**, and **2in1**.|
| [supportDevicePerformanceClasses](#supportdeviceperformanceclasses-field)| Device performance class supported by a widget. For example, if **supportDevicePerformanceClasses** is set to **high**, **medium**, and **low**, the widget can be displayed on devices with the performance class of high, medium, and low.<br>**Note:**<br>This field is supported since API version 21.| String array| Yes. The default values are **high**, **medium**, and **low**.|
| [standby](#standby-field)| <!--RP8-->Landscape standby mode.<!--RP8End--> It is an extended widget field.<br>**Note:**<br>This field is supported since API version 23. Widgets can be displayed in landscape standby mode only when this feature is enabled.| Object| Yes. For details about the default value, see [standby Field](#standby-field).|

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
   | designWidth | Baseline width for page design. The size of an element is scaled by the actual device width.| Number| Yes (initial value: **720px**)|
   | autoDesignWidth | Whether to automatically calculate the baseline width for page design. If it is set to **true**, the **designWidth** attribute will be ignored, and the baseline width will be calculated based on the device width and screen density.| Boolean| Yes (initial value: **false**)|

### funInteractionParams Field

Specifies a fun-based widget. If **funInteractionParams** and **sceneAnimationParams** are both configured, the interactive widget is a fun-based widget.

| Name               | Type | Mandatory| Description                                                                                                                                 |
|-------------------|-----|----|-------------------------------------------------------------------------------------------------------------------------------------|
| abilityName       | String| No | LiveFormExtensionAbility name. This parameter is left empty by default.                                                                                             |
| targetBundleName  | String| Yes | Main bundle name.      |
| subBundleName     | String| No | Sub bundle name.|
| keepStateDuration | Number | No | Duration of the activated state when there is no interaction. The default value is **10000**, in ms. The value should be an integer within the range [0, 10000]. If the value exceeds this range, it defaults to 10000 milliseconds.                                              |

```json
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
| <!--DelRow-->disabledDesktopBehaviors | String array| No | The options are **SWIPE_DESKTOP**, **PULL_DOWN_SEARCH**, **LONG_CLICK**, and **DRAG**. You can select one or more options. By default, no operation is disabled.|

<!--RP2-->
   ```json
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
            ]
         }          
       }
     ]
   }
   ```
<!--RP2End-->

### standby Field

Defines the internal structure of the **standby** object. Widgets can be displayed in landscape standby mode only when the application obtains the required open capability and the **isSupported** property is set to **true**.

| Field| Description| Data Type| Default Value Allowed|
| -------- | -------- | -------- | -------- |
| isSupported | Whether a widget can be displayed in landscape standby mode.<br>- **true**: The widget can be displayed in landscape standby mode.<br>- **false**: The widget cannot be displayed in landscape standby mode.| Boolean| Yes (initial value: **true**)|
| isAdapted | Whether a widget has been adapted to the landscape standby mode. If it is set to **true**, the background image of the widget will be removed.<br>- **true**: The widget has been adapted to the landscape standby mode.<br>- **false**: The widget has not been adapted to the landscape standby mode.| Boolean| Yes (initial value: **false**)|
| isPrivacySensitive | Whether a widget is privacy-sensitive. Private widget data will be hidden with a mask in landscape standby mode.<br>- **true**: The widget is privacy-sensitive.<br>- **false**: The widget is not privacy-sensitive.| Boolean| Yes (initial value: **false**)|

   ```json
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
   ```json
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
