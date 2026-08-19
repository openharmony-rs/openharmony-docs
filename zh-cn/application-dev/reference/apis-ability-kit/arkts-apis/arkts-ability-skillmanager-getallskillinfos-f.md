# getAllSkillInfos

## 导入模块

```TypeScript
import { skillManager } from '@kit.AbilityKit';
```

## getAllSkillInfos

```TypeScript
function getAllSkillInfos(flags: int, userId?: int): Promise<Array<SkillInfo>>
```

获取设备上安装应用的所有技能信息。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_SKILL_PRIVILEGE or ohos.permission.MANAGE_SKILL

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-skillManager-function getAllSkillInfos(flags: int, userId?: int): Promise<Array<SkillInfo>>--><!--Device-skillManager-function getAllSkillInfos(flags: int, userId?: int): Promise<Array<SkillInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flags | int | 是 | { |
| userId | int | 否 | 指定查询的用户ID，可以通过getOsAccountLocalId获取。默认值：调用方所在用户。取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;SkillInfo&gt;&gt; | Promise对象，返回所有应用的技能信息数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |

