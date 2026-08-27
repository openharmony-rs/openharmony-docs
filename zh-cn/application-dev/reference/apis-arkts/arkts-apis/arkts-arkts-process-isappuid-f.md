# isAppUid

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## isAppUid

```TypeScript
function isAppUid(v: number): boolean
```

判断 uid 是否属于应用程序。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isAppUid](arkts-arkts-process-processmanager-c.md#isappuid)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| v | number | 是 | 应用程序的 uid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回判断结果。如果是应用程序的 uid 则返回 true； 否则返回 false。 |

**示例**

```TypeScript
// uid通过process.uid获取
let pres = process.uid;
let result = process.isAppUid(pres);
```

```TypeScript
// 创建ProcessManager实例
let processManager = new process.ProcessManager();
// uid通过process.uid获取
let pres = process.uid;
// 判断uid是否属于当前应用程序
let result = processManager.isAppUid(pres);
console.info("result:", result); // result: true
```
