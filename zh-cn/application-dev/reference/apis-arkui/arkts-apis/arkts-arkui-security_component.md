# security_component

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SecurityComponentMethod](arkts-arkui-securitycomponentmethod-c.md) | 安全控件通用属性模块，提供安全控件的布局、尺寸、文字、图标、颜色、边框和交互等通用属性的统一配置能力。  - 为PasteButton、SaveButton等安全控件统一设置布局、尺寸、文字、图标、颜色、边框和交互相关属性。  - 在满足安全控件规范的前提下，调整安全控件显示效果和交互体验。具体约束请参见[约束与限制](../../../security/AccessToken/security-component-overview.md#约束与限制)。  - 通过链式调用方式复用安全控件通用属性能力。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SecurityComponentMethod](arkts-arkui-securitycomponentmethod-c-sys.md) | 安全控件通用属性模块，提供安全控件的布局、尺寸、文字、图标、颜色、边框和交互等通用属性的统一配置能力。  - 为PasteButton、SaveButton等安全控件统一设置布局、尺寸、文字、图标、颜色、边框和交互相关属性。  - 在满足安全控件规范的前提下，调整安全控件显示效果和交互体验。具体约束请参见[约束与限制](../../../security/AccessToken/security-component-overview.md#约束与限制)。  - 通过链式调用方式复用安全控件通用属性能力。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SecurityComponentLayoutDirection](arkts-arkui-securitycomponentlayoutdirection-e.md) | 安全控件上图标和文字的排列方向。 |
| [SecurityComponentRoleType](arkts-arkui-securitycomponentroletype-e.md) | 定义组件的屏幕朗读功能角色类型。 |

## 示例

```TypeScript
### 示例1

设置SecurityComponent的基础属性，生成一个保存控件。


```

```TypeScript
### 示例2

以容器和容器内组件作为锚点进行布局。


```

```TypeScript
### 示例3

安全控件文本高度自适应。


```

```TypeScript
### 示例4

设置安全控件系统焦点框样式。


```

```TypeScript
### 示例5

设置安全控件是否支持文字实际高度自适应及屏幕朗读模式下相关表现。
```
