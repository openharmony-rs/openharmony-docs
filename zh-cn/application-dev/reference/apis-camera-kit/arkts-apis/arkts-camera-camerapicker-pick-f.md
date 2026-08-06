# pick

## pick

```TypeScript
function pick(context: Context, mediaTypes: Array<PickerMediaType>, pickerProfile: PickerProfile): Promise<PickerResult>
```

拉起相机选择器，根据媒体类型进入相应的模式。使用Promise异步回调。 > **说明：** > > 当应用在阔折叠设备上运行时，如果已在设备展开态下启动相机picker，将设备由展开态切换到折叠态，相机picker被自动推至后台。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cameraPicker-function pick(context: Context, mediaTypes: Array<PickerMediaType>, pickerProfile: PickerProfile): Promise<PickerResult>--><!--Device-cameraPicker-function pick(context: Context, mediaTypes: Array<PickerMediaType>, pickerProfile: PickerProfile): Promise<PickerResult>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用上下文。 |
| mediaTypes | Array&lt;PickerMediaType&gt; | 是 | 媒体类型。 |
| pickerProfile | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | pickerProfile对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PickerResult&gt; | Promise对象，返回相机选择器的处理结果[PickerResult]{ |

**示例：**

```TypeScript
import { cameraPicker } from '@kit.CameraKit';
import { camera } from '@kit.CameraKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function demo(context: Context) {
  try {
    let pickerProfile: cameraPicker.PickerProfile = {
      cameraPosition: camera.CameraPosition.CAMERA_POSITION_BACK
    };
    let pickerResult: cameraPicker.PickerResult = await cameraPicker.pick(context,
      [cameraPicker.PickerMediaType.PHOTO, cameraPicker.PickerMediaType.VIDEO], pickerProfile);
    console.info("the pick pickerResult is:" + JSON.stringify(pickerResult));
  } catch (error) {
    let err = error as BusinessError;
    console.error(`the pick call failed. error code: ${err.code}`);
  }
}
```

