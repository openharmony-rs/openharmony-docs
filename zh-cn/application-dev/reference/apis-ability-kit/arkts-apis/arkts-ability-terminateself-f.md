# terminateSelf

## terminateSelf

```TypeScript
function terminateSelf(callback: AsyncCallback<void>): void
```

销毁当前particleAbility。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当销毁当前particleAbility成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { particleAbility } from '@kit.AbilityKit';

particleAbility.terminateSelf(
  (error) => {
    if (error && error.code !== 0) {
      console.error(`terminateSelf fail, error: ${JSON.stringify(error)}`);
    }
  }
);

```


## terminateSelf

```TypeScript
function terminateSelf(): Promise<void>
```

销毁当前particleAbility。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { particleAbility } from '@kit.AbilityKit';

particleAbility.terminateSelf().then(() => {
  console.info('particleAbility terminateSelf');
});

```

