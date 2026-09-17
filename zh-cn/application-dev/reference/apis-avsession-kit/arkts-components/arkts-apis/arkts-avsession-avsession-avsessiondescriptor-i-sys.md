# AVSessionDescriptor

会话的相关描述信息。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## outputDevice

```TypeScript
outputDevice: OutputDeviceInfo
```

分布式设备相关信息。

**系统接口：** 该接口为系统接口。

**类型：** [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

当前会话所属的userId

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。
