# SystemBarTintState（系统接口）

当前系统栏回调信息集合。

**起始版本：** 8

<!--Device-window-interface SystemBarTintState--><!--Device-window-interface SystemBarTintState-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## displayId

```TypeScript
displayId: number
```

当前窗口所在屏幕id，该参数应为整数。

**类型：** number

**起始版本：** 8

<!--Device-SystemBarTintState-displayId: long--><!--Device-SystemBarTintState-displayId: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## regionTint

```TypeScript
regionTint: Array<SystemBarRegionTint>
```

当前已改变的所有系统栏信息。

**类型：** Array&lt;SystemBarRegionTint&gt;

**起始版本：** 8

<!--Device-SystemBarTintState-regionTint: Array<SystemBarRegionTint>--><!--Device-SystemBarTintState-regionTint: Array<SystemBarRegionTint>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

