# Animator

```TypeScript
export default class Animator
```

定义Animator类。

**起始版本：** 6

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## create

```TypeScript
static create(options: AnimatorOptions): AnimatorResult
```

创建animator动画结果对象（AnimatorResult）。

> **说明：** 
> 
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的[createAnimator](arkts-arkui-arkui-uicontext-uicontext-c.md#createanimator)来明确UI的执行上下文。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** createAnimator

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 是 | 动画配置选项，包含播放时长、插值曲线、延时、填充模式、播放方向、播放次数及插值起止值等参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | 动画控制对象，可用于设置动画过程中的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

> 说明：
> 
> 推荐通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的createAnimator接口明确UI上下文。

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

<a id="create-1"></a>

## create

```TypeScript
static create(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult
```

创建animator动画结果对象（AnimatorResult）。与[create](#create)相比，新增对[SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md)类型入参的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) &#124; [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | 是 | 定义动画选项。AnimatorOptions适用于需要完整自定义所有动画参数的场景；SimpleAnimatorOptions适用于仅需指定起点和终点的简易动画场景，其余参数使用默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | 动画控制对象，可设置动画过程中的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

> 说明：
> 
> 推荐通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的createAnimator接口明确UI上下文。

```TypeScript
import { Animator as animator, SimpleAnimatorOptions } from '@kit.ArkUI';
let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).duration(2000);
animator.create(options); // 建议使用 UIContext.createAnimator()接口
```

## createAnimator

```TypeScript
static createAnimator(options: AnimatorOptions): AnimatorResult
```

创建动画。本模块功能依赖UI的执行上下文，不可在UI上下文不明确的地方使用，推荐通过使用UIContext中的createAnimator接口明确UI上下文。

> **说明：** 
> 
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的[createAnimator](arkts-arkui-arkui-uicontext-uicontext-c.md#createanimator)来明确UI的执行上下文。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** create

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 是 | 动画配置选项，用于定义动画的播放时长、插值曲线、延时、填充模式、播放方向、播放次数及插值起止值等参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | 动画控制对象，可设置动画过程中的回调函数。 |

**示例**

完整示例请参考基于ArkTS扩展的声明式开发范式。

```TypeScript
import { Animator as animator, AnimatorOptions } from '@kit.ArkUI';

let options: AnimatorOptions = { // xxx.js文件中不需要强调显式类型AnimatorOptions
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
