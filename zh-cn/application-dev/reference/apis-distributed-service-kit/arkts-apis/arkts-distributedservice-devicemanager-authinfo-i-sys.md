# AuthInfo（系统接口）

认证信息。

**起始版本：** 7

**废弃版本：** 11

<!--Device-deviceManager-interface AuthInfo--><!--Device-deviceManager-interface AuthInfo-End-->

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

<!--Device-AuthInfo-authType: number--><!--Device-AuthInfo-authType: number-End-->

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

<!--Device-AuthInfo-extraInfo: { [key: string]: any }--><!--Device-AuthInfo-extraInfo: { [key: string]: any }-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## token

```TypeScript
token: number
```

认证Token。

**类型：** number

**起始版本：** 7

**废弃版本：** 11

<!--Device-AuthInfo-token: number--><!--Device-AuthInfo-token: number-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

