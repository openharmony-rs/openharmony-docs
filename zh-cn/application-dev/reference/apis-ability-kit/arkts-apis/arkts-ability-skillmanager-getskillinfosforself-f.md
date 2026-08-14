# getSkillInfosForSelf

## getSkillInfosForSelf

```TypeScript
function getSkillInfosForSelf(flags: int): Promise<Array<SkillInfo>>
```

获取本应用的所有技能信息。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-skillManager-function getSkillInfosForSelf(flags: int): Promise<Array<SkillInfo>>--><!--Device-skillManager-function getSkillInfosForSelf(flags: int): Promise<Array<SkillInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flags | int | 是 | { |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;SkillInfo&gt;&gt; | Promise对象，返回调用方所在应用的所有技能信息数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700101](../errorcode-bundle.md#17700101-包管理服务异常) | Bundle manager service is exception. Possible causes: 1. Failed to connect to the system service. 2. IPC data transmission failed. 3. Failed to obtain the object constructor. |

