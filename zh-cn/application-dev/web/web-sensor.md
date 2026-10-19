# 使用运动和方向传感器监测设备状态
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhang-yinglie-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

## 概述

运动和方向传感器，如加速度计、陀螺仪等，能够监测设备的运动状态和方向变化，例如设备的旋转、倾斜等。

通过W3C标准协议接口，Web组件能够访问这些传感器的数据，进而实现更加丰富的用户交互功能。例如，开发者在网页应用中可以利用加速度计识别运动模式，指导用户进行健身运动，利用陀螺仪捕获玩家手中设备的倾斜和旋转动作，实现无按钮操控的游戏体验。

通过在JavaScript中调用以下支持的W3C标准协议接口，可以访问运动和方向传感器。

| 接口                      | 名称         | 说明                                                                                                                                                     |
| ------------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Accelerometer             | 加速度       | 可获取设备X、Y、Z轴方向的加速度数据。                                                                                                                    |
| Gyroscope                 | 陀螺仪       | 可获取设备X、Y、Z轴方向的角速度数据。                                                                                                                    |
| AbsoluteOrientationSensor | 绝对定向     | 可获取表示设备绝对定位方向的四元数，包含X、Y、Z和W分量。                                                                                                 |
| RelativeOrientationSensor | 相对定向     | 可获取表示设备相对定位方向的四元数，包含X、Y、Z和W分量。                                                                                                 |
| DeviceMotionEvent         | 设备运动事件 | 通过监听该事件，可获取设备在X、Y、Z轴方向上的加速度数据，设备在X、Y、Z轴方向上包含重力的加速度数据，以及设备在alpha、beta、gamma轴方向上旋转的速率数据。 |
| DeviceOrientationEvent    | 设备方向事件 | 通过监听该事件，可获取设备绕X、Y、Z轴的角度。                                                                                                            |

## 需要权限

使用加速度、陀螺仪及设备运动事件接口时，需在配置文件module.json5中声明相应的传感器权限。具体配置方法请参考[在配置文件中声明权限](../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

  <!-- @[declare_the_appropriate_sensor_permissions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsTwo/entry/src/main/module.json5) --> 
  
  ``` JSON5
  "requestPermissions": [
    // ...
    {
      "name" : "ohos.permission.ACCELEROMETER" // 加速度权限
    },
    {
      "name" : "ohos.permission.GYROSCOPE"     // 陀螺仪权限
    }
  ]
  ```
  

Web组件在对接运动和方向传感器时，需配置[onPermissionRequest](../reference/apis-arkweb/arkts-basic-components-web-events.md#onpermissionrequest9)接口，通过该接口接收权限请求通知。

## 开发步骤

1. 应用侧代码中，Web组件配置[onPermissionRequest](../reference/apis-arkweb/arkts-basic-components-web-events.md#onpermissionrequest9)接口，可通过[PermissionRequest](../reference/apis-arkweb/arkts-basic-components-web-PermissionRequest.md)的[getAccessibleResource](../reference/apis-arkweb/arkts-basic-components-web-PermissionRequest.md#getaccessibleresource9)接口获取请求权限的资源类型，当资源类型为TYPE_SENSOR时，进行传感器授权处理。

   <!-- @[the_type_of_resource_for_which_permission_is_requested](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsTwo/entry/src/main/ets/pages/UseMotionDirSensor.ets) -->  

2. 在前端页面代码中，利用JavaScript调用传感器相关的W3C标准协议接口。

   <!-- @[the_type_of_resource_for_which_permission_is_requested_html](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsTwo/entry/src/main/resources/rawfile/index.html) --> 