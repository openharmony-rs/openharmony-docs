# Managing Location Permissions
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhang-yinglie-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=47c341fd96878f63302426cc10515b4a7384fa50 translatedAt=2026-11-12T04:42:27.229Z pushedAt=2026-11-12T08:26:00.597Z nl=1 -->

Since API version 9, the **Web** component supports the [GeolocationPermissions](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md) class and [onGeolocationShow](../reference/apis-arkweb/arkts-basic-components-web-events.md#ongeolocationshow) method for managing web page location permissions. For details, see <!--RP1-->[Privacy Protection](../../device-dev/security/security-privacy-protection.md)<!--RP1End-->.

The **Web** component determines whether to grant the frontend page permission based on the response of the [GeolocationPermissions](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md) class and [onGeolocationShow](../reference/apis-arkweb/arkts-basic-components-web-events.md#ongeolocationshow) method. Users can grant applications access to their location for services such as navigation and weather forecasts.

## Required Permissions
To obtain the location, you need to configure the location permission in **module.json5**. For details, see [Declaring Permissions in the Configuration File](../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file).

   ``` JSON5
   "requestPermissions":[
      {
        "name" : "ohos.permission.LOCATION" // Precise location
      },
      {
        "name" : "ohos.permission.APPROXIMATELY_LOCATION" // Approximate location
      },
      {
        "name" : "ohos.permission.LOCATION_IN_BACKGROUND" // Background location
      }
    ]
   ```

## Requesting Location Permissions
In the following example, when a user clicks the **Get Location** button on the frontend page, the **Web** component notifies the application of the location permission request in a dialog box.


- Frontend page code:

``` HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Location Information</title>
</head>
<body>
    <p id="locationInfo">Location Information</p>
    <button onclick="getLocation()">Get Location</button>

    <script>
        let locationInfo = document.getElementById('locationInfo');
        function getLocation() {
            if (navigator.geolocation) {
                // Access the device's geographic location.
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
 
- Application code:

<!-- @[a_pop_up_window_is_used_to_notify_the_app_side_location_permission_request_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsOne/entry/src/main/ets/pages/ManageLocPerms.ets) -->

``` TypeScript
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { abilityAccessCtrl, common } from '@kit.AbilityKit';

let atManager = abilityAccessCtrl.createAtManager();

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  uiContext: UIContext = this.getUIContext();

  // Lifecycle function of the component, triggered after the component instance is created.
  aboutToAppear(): void {
    let context : Context | undefined = this.uiContext.getHostContext() as common.UIAbilityContext;
    if (!context) {
      console.error('context is undefined');
      return;
    }
    // Request location permission from the user, which takes effect for the entire application.
    atManager.requestPermissionsFromUser(context, ['ohos.permission.APPROXIMATELY_LOCATION']).then((data) => {
      console.info('data:' + JSON.stringify(data));
      console.info('data permissions:' + data.permissions);
      console.info('data authResults:' + data.authResults);
    }).catch((error: BusinessError) => {
      console.error(`Failed to request permissions from user. Code is ${error.code}, message is ${error.message}`);
    })  
  }

  build() {
    Column() {
      // The geolocationAccess attribute of the Web component defaults to true. You can explicitly set it to false to prohibit the Web component from obtaining geolocation information.
      Web({ src: $rawfile('getLocation.html'), controller: this.controller })
        .geolocationAccess(true)
        .onGeolocationShow((event) => {
          // The location permission request notification takes effect only for the current Web component and does not affect other Web components in the application.
          this.uiContext.showAlertDialog({
            title: 'Location permission request',
            message: 'Allow access to location information?',
            primaryButton: {
              value: 'cancel',
              action: () => {
                if (event) {
                  // Deny the location permission request of this site.
                  // Note that the third parameter of invoke indicates whether to remember the current selection. If true is passed, the dialog box will not be displayed next time.
                  event.geolocation.invoke(event.origin, false, false);
                }
              }
            },
            secondaryButton: {
              value: 'ok',
              action: () => {
                if (event) {
                  // Allow the location permission request for this site.
                  // Note that the third parameter of invoke indicates whether to remember the current choice. If true is passed, the dialog will not be displayed again next time.
                  event.geolocation.invoke(event.origin, true, false);
                }
              }
            },
            cancel: () => {
              if (event) {
                // Deny the location permission request for this site.
                // Note that the third parameter of invoke indicates whether to remember the current choice. If true is passed, the dialog will not be displayed again next time.
                event.geolocation.invoke(event.origin, false, false);
              }
            }
          })
        })
    }
  }
}
```


## Managing Location Permissions
You can manage the location permissions of web pages through the [GeolocationPermissions](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md) class of the Web component. This class provides methods for adding ([allowGeolocation](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md#allowgeolocation)), viewing ([getAccessibleGeolocation](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md#getaccessiblegeolocation)), and deleting ([deleteGeolocation](../reference/apis-arkweb/arkts-apis-webview-GeolocationPermissions.md#deletegeolocation)) the location permissions of web pages. For example, you can check whether a web page has applied for the location permission and delete the location permission that a web page has applied for.

<!-- @[create_a_web_component_use_GeolocationPermissions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/SetBasicAttrsEvts/SetBasicAttrsEvtsOne/entry/src/main/ets/pages/GeolocationPermissions.ets) -->

``` TypeScript
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  origin: string = 'www.example.com';

  build() {
    Column() {
      // Add the location permission for the specified source so that the onGeolocationShow callback is not triggered when location information is obtained again.
      Button('allowGeolocation')
        .onClick(() => {
          try {
            webview.GeolocationPermissions.allowGeolocation(this.origin);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })

      // Delete the location permission for the specified source so that the onGeolocationShow callback is triggered when location information is obtained again.
      Button('deleteGeolocation')
        .onClick(() => {
          try {
            webview.GeolocationPermissions.deleteGeolocation(this.origin);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })

      // Query the location permission of the specified source.
      Button('getAccessibleGeolocation')
        .onClick(() => {
          try {
            webview.GeolocationPermissions.getAccessibleGeolocation(this.origin)
              .then(result => {
                console.info('getAccessibleGeolocationPromise result: ' + result);
              }).catch((error: BusinessError) => {
              console.error(`getAccessibleGeolocationPromise error, ErrorCode: ${error.code},  Message: ${error.message}`);
            });
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })

      // Add the network permission ohos.permission.INTERNET.
      Web({ src: 'www.example.com', controller: this.controller })
    }
  }
}
```