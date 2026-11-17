# 拍摄成片内容证真溯源设置(ArkTS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

从API版本26.0.1开始，支持为拍摄成片添加内容凭证，用于认证图片来源与完整性。开发者可调用相关接口完成签名，并可选携带作者姓名与作者ID。签名结果可在图库中查看。内容认证是一项由众多领先企业共同支持的行业标准，用于安全地传递媒体文件的来源与历史记录，该标准由内容溯源与真实性联盟（Coalition for Content Provenance and Authenticity, C2PA）制定。

## 使用场景

当应用需要证明“这张照片由本设备、本应用、该用户拍摄，且拍摄后未被篡改”时，应开启内容凭证签名。签名在拍摄成片生成阶段完成，随成片一并产出。

签名后的效果：

- 成片文件中携带C2PA内容凭证，包含签名信息，以及开发者传入的作者姓名与作者ID（可选）。

- 系统图库中可查看该图片的签名信息。

- 支持C2PA校验的工具或平台可读取凭证，验证图片来源与完整性，内容被篡改时校验将失败。

## 约束与限制

- 该能力依赖网络，调用相关接口时设备需保持联网，无网络环境下功能可能失效。

- 作者姓名与作者ID为可选参数。未传入时，签名信息中不包含作者信息；传入后，签名信息将携带该内容，请确保信息真实、可追溯。

- 内容凭证仅用于证明来源与完整性，不对图片内容加密，不影响图片的正常读取与分享。

> **注意：**
>
> - 开启内容凭证会增加成片生成耗时，建议在非连续拍摄场景下使用。
>
> - 作者姓名与作者ID由开发者传入，系统不做真实性校验。
>
> - 若图片经过二次编辑，原有凭证可能失效，需重新签名。

## 开发步骤

详细的API说明请参考[@ohos.multimedia.camera (相机管理)](../../reference/apis-camera-kit/arkts-apis-camera.md)。

1. 导入camera接口，接口中提供相机相关的属性和方法。

   ```ts
   import { camera } from '@kit.CameraKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. 设置签名内容。

   ```ts
   private signature: camera.C2PASignatureConfig = {
     // 以下签名信息仅为示例，实际使用请替换真实签名信息。
     authorName: 'wang',
     authorID: '1234'
   };
   ```

3. 调用设置C2PA签名的相关方法，该功能提供两个接口：

   - [isC2PASignatureSupported](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#isc2pasignaturesupported)用来判断该设备是否支持C2PA签名功能。
   - [configureC2PASignature](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#configurec2pasignature)用来开启/关闭C2PA签名功能；如需传入作者姓名和ID，则可将相应信息写入签名中。

   <!-- @[enable_c2pa](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoAndVideoCamera/camera/src/main/ets/cameramanagers/PhotoManager.ets) -->

   ``` TypeScript
   public configC2PA() {
     if (this.output && this.output.isC2PASignatureSupported()) {
       this.output.configureC2PASignature(true, this.signature);
     }
   }
   ```
