# @ohos.arkui.WithEnv(定义WithEnv组件，允许为子组件设置环境属性。)

## 导入模块

```TypeScript
import { WithEnv, WithEnvAttribute} from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [WithEnvAttribute](arkts-arkui-arkui-withenv-withenvattribute-c.md) | 定义WithEnv组件的属性功能。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [WithEnvInterface](arkts-arkui-withenvinterface-t.md) | 定义WithEnv组件的类型。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [WithEnv](arkts-arkui-arkui-withenv-con.md) | WithEnv组件用于为子组件树设置局部环境变量作用域。开发者可以通过该组件为后代组件提供自定义环境变量，或设置系统环境变量。 |
| [WithEnvInstance](arkts-arkui-arkui-withenv-con.md#withenvinstance) | 定义WithEnv逻辑组件实例。 |

## 示例

```TypeScript
### 示例1（设置局部字体缩放）

该示例通过为作用域内组件设置局部字体缩放比例。

从API版本26.0.0开始，新增env属性和键值WritableEnvKey.FONT_SCALE。


```

```TypeScript
### 示例2（设置局部布局方向）

该示例通过为作用域内组件设置局部布局方向。

从API版本26.0.0开始，新增env属性和键值WritableEnvKey.DIRECTION。
```
