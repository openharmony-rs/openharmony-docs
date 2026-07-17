# AuthParam（系统接口）

认证参数。

**起始版本：** 7

**废弃版本：** 11

<!--Device-deviceManager-interface AuthParam--><!--Device-deviceManager-interface AuthParam-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

## authType

```TypeScript
authType: number
```

认证类型。

**类型：** number

**起始版本：** 7

**废弃版本：** 11

<!--Device-AuthParam-authType: number--><!--Device-AuthParam-authType: number-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## extraInfo

```TypeScript
extraInfo: { [key: string]: any }
```

认证参数可扩展字段。可选，默认为undefined。

**类型：** { [key: string]: any }

**起始版本：** 7

**废弃版本：** 11

<!--Device-AuthParam-extraInfo: { [key: string]: any }--><!--Device-AuthParam-extraInfo: { [key: string]: any }-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

