# CaptureOption

设置截取图像的信息。

**起始版本：** 14

<!--Device-screenshot-interface CaptureOption--><!--Device-screenshot-interface CaptureOption-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## blackWindowIds

```TypeScript
blackWindowIds?: Array<number>
```

表示截取图像时不显示的窗口ID列表，默认为空。窗口ID应为大于0的整数，目前仅[闪控球窗口](arkts-window-floatingball.md)生效，窗口ID为非闪控球窗口、非整数、小于等于0、或者不存在的窗口ID时报参数错误，错误码为401。推荐使用[getFloatingBallWindowInfo()](arkts-arkui-floatingball-floatingballcontroller-i.md#getfloatingballwindowinfo-1)方法获取闪控球窗口ID属性。

**类型：** Array<number>

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-CaptureOption-blackWindowIds?: Array<int>--><!--Device-CaptureOption-blackWindowIds?: Array<int>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## displayId

```TypeScript
displayId?: number
```

表示截取图像的显示设备[Display](arkts-arkui-display-displaystate-e.md)的ID号，默认为0，该参数应为大于或等于0的整数，非整数会报参数错误。

**类型：** number

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-CaptureOption-displayId?: long--><!--Device-CaptureOption-displayId?: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

