# SyncFolder（系统接口）

表示同步根信息。

**起始版本：** 21

<!--Device-cloudDiskManager-interface SyncFolder--><!--Device-cloudDiskManager-interface SyncFolder-End-->

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

<!--Device-SyncFolder-bundleName: string--><!--Device-SyncFolder-bundleName: string-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## customAlias

```TypeScript
customAlias?: string
```

在文管列表显示的别名。默认值为undefined。

**类型：** string

**起始版本：** 21

<!--Device-SyncFolder-customAlias?: string--><!--Device-SyncFolder-customAlias?: string-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## displayNameResId

```TypeScript
displayNameResId?: number
```

资源ID，可以映射到文管列表显示的别名。默认值为undefined。

**类型：** number

**起始版本：** 21

<!--Device-SyncFolder-displayNameResId?: int--><!--Device-SyncFolder-displayNameResId?: int-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## path

```TypeScript
path: string
```

同步根对应的URI。

**类型：** string

**起始版本：** 21

<!--Device-SyncFolder-path: string--><!--Device-SyncFolder-path: string-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: SyncFolderState
```

同步根对应的状态信息。

**类型：** SyncFolderState

**起始版本：** 21

<!--Device-SyncFolder-state: SyncFolderState--><!--Device-SyncFolder-state: SyncFolderState-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

