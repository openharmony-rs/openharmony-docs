# transferStatic

## 导入模块

```TypeScript
import { transfer } from '@kit.ArkTS';
```

## transferStatic

```TypeScript
function transferStatic(input: Any, inputName: string): Object
```

将1.0对象转换为1.2对象。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-transfer-function transferStatic(input: Any, inputName: string): Object--><!--Device-transfer-function transferStatic(input: Any, inputName: string): Object-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | Any | 是 | 需要转换的1.0对象。 |
| inputName | string | 是 | 子系统注册的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 转换后的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 10200067 | 转换错误，不支持的输入名称！ |

