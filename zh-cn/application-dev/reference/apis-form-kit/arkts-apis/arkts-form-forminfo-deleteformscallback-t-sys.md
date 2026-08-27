# DeleteFormsCallback（系统接口）

```TypeScript
type DeleteFormsCallback = (formIds: Array<string>) => void
```

卡片删除回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 被删除的卡片标识列表。 |

**示例**

```TypeScript
import { formInfo } from '@kit.FormKit';

let deleteFormsCallback: formInfo.DeleteFormsCallback =
  (formIds: Array<string>): void => {
    console.info('delete forms callback, form count: ' + formIds.length);
  };
```
