# White Balance Settings (ArkTS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=132342cdd19e09e8d1c7a964e48a57b6cf30fc8d translatedAt=2026-09-28T02:43:21.164Z pushedAt=2026-09-29T08:04:34.351Z -->

Starting from API version 20, white balance effects are supported. White balance is a camera color correction technique that produces different effects in photos by adjusting the white balance settings. Currently, white balance effects are supported for photo capture ([PhotoSession](../../reference/apis-camera-kit/arkts-apis-camera-PhotoSession.md)), video recording ([VideoSession](../../reference/apis-camera-kit/arkts-apis-camera-VideoSession.md)), and secure camera mode ([SecureSession](../../reference/apis-camera-kit/arkts-apis-camera-SecureSession.md)).

## How to Develop

Read [Camera](../../reference/apis-camera-kit/arkts-apis-camera.md) for the API reference.

1. Import the camera module, which provides camera-related properties and methods.

    ```ts
    import { camera } from '@kit.CameraKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    ```

2. Set white balance. Two methods are provided for setting white balance.

   - Method 1: Call [isWhiteBalanceModeSupported](../../reference/apis-camera-kit/arkts-apis-camera-WhiteBalanceQuery.md#iswhitebalancemodesupported20) to check whether a specific white balance mode is supported. Then, call [setWhiteBalanceMode](../../reference/apis-camera-kit/arkts-apis-camera-WhiteBalance.md#setwhitebalancemode20) and [getWhiteBalanceMode](../../reference/apis-camera-kit/arkts-apis-camera-WhiteBalance.md#getwhitebalancemode20) to set and obtain the white balance mode. Note that you can only view the currently set white balance mode. The available white balance modes include automatic, manual, cloudy, incandescent, fluorescent, daylight, and locked. If both a white balance mode and a white balance value are set, only one takes effect, with the white balance mode taking precedence by default.
      ```ts
      function isWhiteBalanceModeSupported(session: camera.PhotoSession | camera.VideoSession): boolean {
         let status: boolean = false;
         let whiteBalanceMode: camera.WhiteBalanceMode | undefined = undefined;
         try {
            let mode: camera.WhiteBalanceMode = camera.WhiteBalanceMode.DAYLIGHT;
            status = session.isWhiteBalanceModeSupported(mode);
            if(status){
               session.setWhiteBalanceMode(mode);
            }
            whiteBalanceMode = session.getWhiteBalanceMode();
         } catch (error) {
            let err = error as BusinessError;
            console.error(`The isWhiteBalanceModeSupported call failed. error code: ${err.code}`);
         }
         return status;
      }
      ```

   - Method 2: Call [getWhiteBalanceRange](../../reference/apis-camera-kit/arkts-apis-camera-WhiteBalanceQuery.md#getwhitebalancerange20) to obtain the range of white balance values supported by the device. Then, call [setWhiteBalance](../../reference/apis-camera-kit/arkts-apis-camera-WhiteBalance.md#setwhitebalance20) and [getWhiteBalance](../../reference/apis-camera-kit/arkts-apis-camera-WhiteBalance.md#getwhitebalance20) to set and obtain the white balance value. Note that you can only view the currently set white balance value.
      ```ts
      function getWhiteBalanceRange(session: camera.PhotoSession | camera.VideoSession): Array<number> {
         let range: Array<number> = [];
         try {
            range = session.getWhiteBalanceRange();
            let whiteBalance: number = 3000;
            if(whiteBalance >= range[0] && whiteBalance <= range[1]) {
               session.setWhiteBalance(whiteBalance);
            }
            whiteBalance = session.getWhiteBalance();
         } catch (error) {
           let err = error as BusinessError;
           console.error(`The getWhiteBalanceRange call failed. error code: ${err.code}`);
         }
         return range;
      }
      ```
