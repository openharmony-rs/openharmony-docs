# VirtualScreenOption（系统接口）

创建虚拟屏幕的参数。

**起始版本：** 9

<!--Device-screen-interface VirtualScreenOption--><!--Device-screen-interface VirtualScreenOption-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
```

## density

```TypeScript
density: number
```

指定虚拟屏幕的密度，该参数为浮点数。

**类型：** number

**起始版本：** 9

<!--Device-VirtualScreenOption-density: double--><!--Device-VirtualScreenOption-density: double-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## height

```TypeScript
height: number
```

指定虚拟屏幕的高度，单位为px，该参数应为整数。

**类型：** number

**起始版本：** 9

<!--Device-VirtualScreenOption-height: long--><!--Device-VirtualScreenOption-height: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

指定虚拟屏幕的名称。

**类型：** string

**起始版本：** 9

<!--Device-VirtualScreenOption-name: string--><!--Device-VirtualScreenOption-name: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## supportsFocus

```TypeScript
supportsFocus?: boolean
```

指定虚拟屏幕是否可获得焦点。true表示可获焦，false表示不可获焦，默认值为true。

**类型：** boolean

**起始版本：** 22

<!--Device-VirtualScreenOption-supportsFocus?: boolean--><!--Device-VirtualScreenOption-supportsFocus?: boolean-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## surfaceId

```TypeScript
surfaceId: string
```

指定虚拟屏幕的surfaceId。

**类型：** string

**起始版本：** 9

<!--Device-VirtualScreenOption-surfaceId: string--><!--Device-VirtualScreenOption-surfaceId: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

指定虚拟屏幕的用户ID，该参数为整数。默认值为-1。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VirtualScreenOption-userId?: int--><!--Device-VirtualScreenOption-userId?: int-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## width

```TypeScript
width: number
```

指定虚拟屏幕的宽度，单位为px，该参数应为整数。

**类型：** number

**起始版本：** 9

<!--Device-VirtualScreenOption-width: long--><!--Device-VirtualScreenOption-width: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

