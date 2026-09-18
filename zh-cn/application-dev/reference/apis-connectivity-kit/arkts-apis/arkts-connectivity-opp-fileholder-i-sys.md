# FileHolder（系统接口）

描述发送的文件信息。

**起始版本：** 16

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { opp } from '@kit.ConnectivityKit';
```

## fileFd

```TypeScript
fileFd: number
```

待传输文件的已打开的文件描述符（传输过程中需要保持打开直到传输完成）。

**类型：** number

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

## filePath

```TypeScript
filePath: string
```

待传输文件的URI，例如：file://media/Photo/1/IMG_1739266559_000/test.jpg 。

**类型：** string

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**测试接口：** 此接口仅在自动化测试脚本中使用。

## fileSize

```TypeScript
fileSize: number
```

待传输文件的大小，以字节为单位。

**类型：** number

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。
