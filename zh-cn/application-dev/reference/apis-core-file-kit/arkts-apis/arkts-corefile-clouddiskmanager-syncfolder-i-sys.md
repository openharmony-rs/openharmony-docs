# SyncFolder（系统接口）

```TypeScript
interface SyncFolder
```

表示同步根信息。

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## bundleName

```TypeScript
bundleName: string
```

同步根对应的包名。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## customAlias

```TypeScript
customAlias?: string
```

在文管列表显示的别名。默认值为undefined。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## displayNameResId

```TypeScript
displayNameResId?: number
```

资源ID，可以映射到文管列表显示的别名。默认值为undefined。

**类型：** number

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## isSupportPlaceHolder

```TypeScript
isSupportPlaceHolder?: boolean
```

同步根是否支持占位符。true：表示同步根支持占位符。 默认值：false，表示同步根不支持占位符。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## path

```TypeScript
path: string
```

同步根对应的URI。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: SyncFolderState
```

同步根对应的状态信息。

**类型：** [SyncFolderState](arkts-corefile-clouddiskmanager-syncfolderstate-e-sys.md)

**起始版本：** 21

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。
