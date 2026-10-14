# Starting a Camera and Microphone
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @qq_42700029-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=4d6ab311d7751b63c4e4e5de32383be189abffd1 translatedAt=2026-09-21T02:30:33.892Z pushedAt=2026-09-21T14:03:00.475Z -->

Web Real-Time Communications (WebRTC) is a real-time communication technology that allows web applications or sites to establish peer-to-peer connections between browsers without an intermediary, enabling the transmission of video streams, audio streams, or any other data. The standards included in WebRTC allow users to create peer-to-peer data sharing and audio/video conferencing without installing any plug-ins or third-party software. WebRTC applies to all modern browsers and native clients on major platforms. The underlying technology is implemented as an open web standard and is provided as a regular JavaScript API in all major browsers.

## Applying for Permissions

The **Web** component can access the camera and microphone through W3C standard protocol APIs, and receive permission request notifications through the [onPermissionRequest](../reference/apis-arkweb/arkts-basic-components-web-events.md#onpermissionrequest9) API. You need to declare the corresponding audio and video permissions in the configuration file and perform system-side authorization and app-side authorization.

### Configuring Permissions in module.json5
- Before using the camera and microphone, add the audio and video permissions in **module.json5**. For details about how to add permissions, see [Declaring Permissions in the Configuration File](../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file).

  ```json5
    // src/main/resources/base/element/string.json
    "string":[
      {
        "name": "reason_for_camera",
        "value": "reason_for_camera"
      },
      {
        "name": "reason_for_microphone",
        "value": "reason_for_microphone"
      }
    ]
  ```

  ```json5
    // src/main/module.json5
    "requestPermissions":[
      {
        "name" : "ohos.permission.CAMERA",
        "reason": "$string:reason_for_camera",
        "usedScene": {
          "abilities": [
            "EntryAbility"
          ],
          "when":"inuse"
        }
      },
      {
        "name" : "ohos.permission.MICROPHONE",
        "reason": "$string:reason_for_microphone",
        "usedScene": {
          "abilities": [
            "EntryAbility"
          ],
          "when":"inuse"
        }
      }
    ]
   ```

Call the W3C standard protocol API **navigator.mediaDevices.getUserMedia()** in JavaScript to open the camera and microphone. The **constraints** parameter is a **MediaStreamConstraints** object that contains two members, **video** and **audio**, and specifies the requested media types.

### System-Side Authorization
In the [sample code](../web/web-rtc.md#samples), **requestPermissionsFromUser** is called so that after the app is opened, a dialog box asking whether to allow the app to access the camera and microphone is displayed. Click **Always allow** or **Ask every time** to authorize the app to access the camera and microphone.

### App-Side Authorization
In the [sample code](../web/web-rtc.md#samples), after you click the **Enable Camera** button on the frontend page, a permission request is triggered through **onPermissionRequest**. After you click the **onConfirm** button in the dialog box, the camera and microphone are opened.

## Samples

  <!-- @[click_button_to_turn_on_camera_microphone](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/UsingWebMultimedia/entry/src/main/ets/pages/Index.ets) --> 

  ``` TypeScript
  import { webview } from '@kit.ArkWeb';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { abilityAccessCtrl } from '@kit.AbilityKit';
  
  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    uiContext: UIContext = this.getUIContext();
  
    aboutToAppear() {
      // Enable web frontend page debugging.
      webview.WebviewController.setWebDebuggingAccess(true);
      // Obtain the camera and microphone permissions and proactively request them when the component is created.
      let atManager = abilityAccessCtrl.createAtManager();
      atManager.requestPermissionsFromUser(this.uiContext.getHostContext(), ['ohos.permission.CAMERA', 'ohos.permission.MICROPHONE'])
        .then((data) => {
          console.info('data:' + JSON.stringify(data));
          console.info('data permissions:' + data.permissions);
          console.info('data authResults:' + data.authResults);
        }).catch((error: BusinessError) => {
        console.error(`Failed to request permissions from user. Code is ${error.code}, message is ${error.message}`);
      })
    }
  
    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onPermissionRequest((event) => {
            if (event) {
              this.uiContext.showAlertDialog({
                title: 'title',
                message: 'text',
                primaryButton: {
                  value: 'deny',
                  action: () => {
                    event.request.deny();
                  }
                },
                secondaryButton: {
                  value: 'onConfirm',
                  action: () => {
                    event.request.grant(event.request.getAccessibleResource());
                  }
                },
                cancel: () => {
                  event.request.deny();
                }
              })
            }
          })
      }
    }
  }
  ```

- Code of the **index.html** page.

  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <head>
    <meta charset="UTF-8">
  </head>
  <body>
  <video id="video" width="500px" height="500px" autoplay></video>
  <canvas id="canvas" width="500px" height="500px"></canvas>
  <br>
  <input type="button" title="HTML5 Camera" value="Enable Camera" onclick="getMedia()"/>
  <script>
    function getMedia()
    {
      let constraints = {
        video: {width: 500, height: 500},
        audio: true
      };
      // Obtain the video camera area.
      let video = document.getElementById("video");
      // Returned Promise object
      let promise = navigator.mediaDevices.getUserMedia(constraints);
      // then() is asynchronous. Invoke the MediaStream object as a parameter.
      promise.then(function(MediaStream) {
        video.srcObject = MediaStream;
        video.play();
      }).catch(function(err) {
          console.info(err.name + ": " + err.message);
      });
    }
  </script>
  </body>
  </html>
  ```

<!--RP1-->
<!--RP1End-->