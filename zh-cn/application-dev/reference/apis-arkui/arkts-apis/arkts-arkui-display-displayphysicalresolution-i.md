# DisplayPhysicalResolution

设备的显示模式以及对应的物理屏幕分辨率信息。

**起始版本：** 12

<!--Device-display-interface DisplayPhysicalResolution--><!--Device-display-interface DisplayPhysicalResolution-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## foldDisplayMode

```TypeScript
foldDisplayMode: FoldDisplayMode
```

设备的显示模式，非折叠设备时值为0。

**类型：** FoldDisplayMode

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayPhysicalResolution-foldDisplayMode: FoldDisplayMode--><!--Device-DisplayPhysicalResolution-foldDisplayMode: FoldDisplayMode-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## physicalHeight

```TypeScript
physicalHeight: number
```

设备的高度，单位为px，该参数为大于0的整数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayPhysicalResolution-physicalHeight: long--><!--Device-DisplayPhysicalResolution-physicalHeight: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## physicalWidth

```TypeScript
physicalWidth: number
```

设备的宽度，单位为px，该参数为大于0的整数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayPhysicalResolution-physicalWidth: long--><!--Device-DisplayPhysicalResolution-physicalWidth: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

