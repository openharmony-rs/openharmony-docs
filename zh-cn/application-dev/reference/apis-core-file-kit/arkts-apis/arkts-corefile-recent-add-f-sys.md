# add（系统接口）

## 导入模块

```TypeScript
import { recent } from '@kit.CoreFileKit';
```

## add

```TypeScript
function add(uri: string): void
```

将uri对应的文件加入最近访问列表。

**起始版本：** 10

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-recent-function add(uri: string): void--><!--Device-recent-function add(uri: string): void-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 公共目录文件类URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let uri = 'file://docs/storage/Users/currentUser/<publicPath>';
recent.add(uri);

```

