# getTagInfo

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getTagInfo

```TypeScript
function getTagInfo(want: Want): TagInfo
```

从Want中获取TagInfo，Want是被NFC服务初始化，包含了TagInfo所需的属性值。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 分发Ability时，在系统onCreate入口函数的参数中获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TagInfo](arkts-connectivity-tag-taginfo-i.md) | TagInfo对象，用于获取不同技术类型的Tag对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
