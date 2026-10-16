# 管理位置权限
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhang-yinglie-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

从API version 9开始，支持Web组件的[GeolocationPermissions](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md)类和[onGeolocationShow](../reference/apis-arkweb/arkts-basic-components-web-events.md#ongeolocationshow)方法对网页进行位置权限管理。更多信息请参见<!--RP1-->[隐私保护说明](../../device-dev/security/security-privacy-protection.md)<!--RP1End-->。

Web组件根据[GeolocationPermissions](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md)类和[onGeolocationShow](../reference/apis-arkweb/arkts-basic-components-web-events.md#ongeolocationshow)方法的响应结果，决定是否赋予前端页面权限。用户可以获取位置信息，以便使用出行导航、天气预报等服务。

## 需要权限
使用获取位置功能，需在module.json5中配置位置权限。具体添加方法请参考[在配置文件中声明权限](../security/AccessToken/declare-permissions.md#在配置文件中声明权限)。

   ``` JSON5
   "requestPermissions":[
      {
        "name" : "ohos.permission.LOCATION" // 精准定位
      },
      {
        "name" : "ohos.permission.APPROXIMATELY_LOCATION" // 模糊定位
      },
      {
        "name" : "ohos.permission.LOCATION_IN_BACKGROUND" // 后台定位
      }
    ]
   ```

## 申请位置权限
在下面的示例中，用户点击前端页面"获取位置"按钮，Web组件通过弹窗通知应用侧位置权限请求消息。


- 前端页面代码。

 <!-- @[getLocation_html](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsOne/entry/src/main/resources/rawfile/getLocation.html) -->
 
 ``` HTML
 <!DOCTYPE html>
 <html lang="en">
 <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>位置信息</title>
 </head>
 <body>
     <p id="locationInfo">位置信息</p>
     <button onclick="getLocation()">获取位置</button>
 
     <script>
         let locationInfo = document.getElementById('locationInfo');
         function getLocation() {
             if (navigator.geolocation) {
                 // 访问设备地理位置
                 navigator.geolocation.getCurrentPosition(showPosition);
             }
         }
         function showPosition(position) {
             locationInfo.innerHTML = 'Latitude: ' + position.coords.latitude + '<br />Longitude: ' + position.coords.longitude;
         }
     </script>
 </body>
 </html>
 ```
 

- 应用代码。

<!-- @[a_pop_up_window_is_used_to_notify_the_app_side_location_permission_request_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsOne/entry/src/main/ets/pages/ManageLocPerms.ets) -->

## 管理位置权限
通过Web组件的[GeolocationPermissions](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md)类管理网页的位置权限，提供了新增（[allowGeolocation](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md#allowgeolocation)）、查看（[getAccessibleGeolocation](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md#getaccessiblegeolocation)）和删除（[deleteGeolocation](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md#deletegeolocation)）网页位置权限的方法。例如查看网页是否已申请位置权限、将网页已申请的位置权限删除。

<!-- @[create_a_web_component_use_GeolocationPermissions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsOne/entry/src/main/ets/pages/GeolocationPermissions.ets) -->