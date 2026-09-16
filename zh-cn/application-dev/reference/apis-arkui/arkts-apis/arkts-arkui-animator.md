# @ohos.animator(动画)

本模块提供组件动画效果，包括定义动画、启动动画和以相反的顺序播放动画等。

> **说明：**
 >
 > - 本模块从API version 9开始支持在ArkTS中使用。
 >
 > - 该模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在创建组件实例后使用。
 >
 > - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见
 > [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)说明。
 >
 > - 自定义组件中通常会持有一个由[createAnimator](arkts-arkui-arkui-uicontext-uicontext-c.md#createanimator)接口返回的
 > [AnimatorResult](arkts-arkui-animator-animatorresult-i.md)对象，以确保动画对象在动画过程中不被析构，该对象通过回调捕获了自定义组件对象，因此需要在自定义组件销毁时的
 > aboutToDisappear生命周期中释放动画对象，以避免因循环依赖导致内存泄漏。详细示例可参考：
 > [基于ArkTS扩展的声明式开发范式](../../../reference/apis-arkui/js-apis-animator.md#基于arkts扩展的声明式开发范式)。
 >
 > - Animator对象析构或主动调用[cancel](arkts-arkui-animator-animatorresult-i.md#cancel)、[finish](arkts-arkui-animator-animatorresult-i.md#finish)方法时，都会触发一次额外的
 > [onFrame](arkts-arkui-animator-animatorresult-i.md#onframe)，返回值是动画终点值。因此，如果在动画过程中调用
 > [cancel](arkts-arkui-animator-animatorresult-i.md#cancel)、[finish](arkts-arkui-animator-animatorresult-i.md#finish)，会导致属性值在一帧内跳变至终点。若希望动画在中途暂停，可先将onFrame设置
 > 为空函数，再调用[finish](arkts-arkui-animator-animatorresult-i.md#finish)。
 >
 > - 对于无限循环的Animator动画，即使开发者选项中将全局动画速率设置为0（关闭动画），循环动画仍会继续执行。



## 导入模块

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Animator](arkts-arkui-animator-animator-c.md) | 定义Animator类。 |
| [SimpleAnimatorOptions](arkts-arkui-animator-simpleanimatoroptions-c.md) | animator简易动画参数对象。与AnimatorOptions相比，duration、easing、delay、fill、direction、iterations等动画参数有默认值，可不设置。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AnimatorOptions](arkts-arkui-animator-animatoroptions-i.md) | 定义动画选项。 |
| [AnimatorResult](arkts-arkui-animator-animatorresult-i.md) | 定义AnimatorResult接口，提供动画播放状态回调及动画控制方法。 |
