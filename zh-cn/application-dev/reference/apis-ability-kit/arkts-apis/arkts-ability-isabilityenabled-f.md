# isAbilityEnabled

## isAbilityEnabled

```TypeScript
function isAbilityEnabled(info: AbilityInfo, callback: AsyncCallback<boolean>): void
```

根据给定的AbilityInfo查询ability是否已经启用，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | Ability的配置信息。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数，返回boolean代表是否启用。 |


## isAbilityEnabled

```TypeScript
function isAbilityEnabled(info: AbilityInfo): Promise<boolean>
```

根据给定的AbilityInfo查询ability是否已经启用，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | Ability的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise形式返回boolean代表是否启用。 |

