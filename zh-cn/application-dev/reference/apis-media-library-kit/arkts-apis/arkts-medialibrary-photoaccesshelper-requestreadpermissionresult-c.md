# RequestReadPermissionResult

包含已授权的uri列表和无效的uri列表。

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## authorizedUris

```TypeScript
authorizedUris?: Array<string>
```

返回已创建并授予保存权限的uri列表。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## invalidUris

```TypeScript
invalidUris?: Array<string>
```

返回可能被删除、隐藏或重命名的无效uri列表。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core
