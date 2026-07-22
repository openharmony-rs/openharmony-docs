# Animator

定义Animator类。

**起始版本：** 6

<!--Device-unnamed-export default class Animator--><!--Device-unnamed-export default class Animator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AnimatorOptions, SimpleAnimatorOptions, AnimatorResult } from '@kit.ArkUI';
```

## create

```TypeScript
static create(options: AnimatorOptions): AnimatorResult
```

创建animator动画结果对象（AnimatorResult）。
> **说明：**  
>  
> -  
>  
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [createAnimator](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#createanimator)来明确UI的执行上下文。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** createAnimator

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Animator-static create(options: AnimatorOptions): AnimatorResult--><!--Device-Animator-static create(options: AnimatorOptions): AnimatorResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 是 | 定义动画选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator结果接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

**示例：**

推荐通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[createAnimator](arkts-apis-uicontext-uicontext.md#createanimator)接口明确UI上下文。

```TypeScript
import { Animator as animator, AnimatorOptions } from '@kit.ArkUI';

let options: AnimatorOptions = {
  duration: 1500,
  easing: 'friction',
  delay: 0,
  fill: "forwards",
  direction: "normal",
  iterations: 3,
  begin: 200.0,
  end: 400.0
};
animator.create(options); // 建议使用 UIContext.createAnimator()接口

```

## create

```TypeScript
static create(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult
```

创建animator动画结果对象（AnimatorResult）。与[create](arkts-arkui-animator-animator-c.md#create)相比，新增对[SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md)类型入参的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Animator-static create(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult--><!--Device-Animator-static create(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) \| SimpleAnimatorOptions | 是 | 定义动画参数选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator结果接口。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

**示例：**

推荐通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[createAnimator](arkts-apis-uicontext-uicontext.md#createanimator)接口明确UI上下文。

```TypeScript
import { Animator as animator, SimpleAnimatorOptions } from '@kit.ArkUI';
let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).duration(2000);
animator.create(options); // 建议使用 UIContext.createAnimator()接口

```

## createAnimator

```TypeScript
static createAnimator(options: AnimatorOptions): AnimatorResult
```

创建动画。
> **说明：**

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [create(options:](arkts-arkui-animator-animator-c.md#create)

<!--Device-Animator-static createAnimator(options: AnimatorOptions): AnimatorResult--><!--Device-Animator-static createAnimator(options: AnimatorOptions): AnimatorResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 是 | 定义动画选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | Animator结果接口。 |

**示例：**

完整示例请参考[基于ArkTS扩展的声明式开发范式](#基于arkts扩展的声明式开发范式)。

```TypeScript
import { Animator as animator } from '@kit.ArkUI';

let options: AnimatorOptions = {
  // xxx.js文件中不需要强调显式类型AnimatorOptions
  duration: 1500,
  easing: "friction",
  delay: 0,
  fill: "forwards",
  direction: "normal",
  iterations: 3,
  begin: 200.0,
  end: 400.0,
};
this.animator = animator.createAnimator(options);

```

