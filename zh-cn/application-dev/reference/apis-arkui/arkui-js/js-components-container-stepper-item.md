# stepper-item
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--SE: @jiangdayuan-->
<!--TSE: @lxl007-->

>  **说明：**
> 从API version 5开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

步骤导航器子组件，作为步骤导航器某一个步骤的内容展示组件。


## 权限列表

无


## 子组件

支持。


## 属性

除支持[通用属性](js-components-common-attributes.md)外，还支持如下属性：

| 名称 | 类型 | 必填 | 描述 |
| -------- | -------- | -------- | -------- |
| label | Label | &nbsp;&nbsp;否&nbsp;&nbsp; | 自定义步骤导航器底部步骤提示文本按钮属性，不支持动态修改。如果没有定义该属性，步骤导航器在中文语言环境下，使用"返回"和"下一步"文本按钮，在非中文语言环境下，使用"BACK"和"NEXT"文本按钮。针对第一个步骤，没有"返回"文本按钮；针对最后一个步骤，"下一步"文本按钮文本使用"开始"（中文语言）或者"START"（非中文语言）。 |

**表1** Label对象定义

| 名称 | 类型 | 默认值 | 描述 |
| -------- | -------- | -------- | -------- |
| prevLabel | string | - | 步骤导航器底部回退文本按钮的描述文本。 |
| nextLabel | string | - | 步骤导航器底部下一步文本按钮的描述文本。 |
| status | string | normal | 步骤导航器当前步骤的初始状态，可选值为：<br/>-&nbsp;normal：正常状态，右侧文本按钮正常显示，可点击进入下一个步骤。<br/>-&nbsp;disabled：不可用状态，右侧文本按钮灰度显示，不可点击进入下一个步骤。<br/>-&nbsp;waiting：等待状态，右侧文本按钮不显示，使用等待进度条，不可点击进入下一个步骤。 |


## 样式

除支持[通用样式](js-components-common-styles.md)外，还支持如下样式：

| 名称 | 类型 | 默认值 | 必填 | 描述 |
| -------- | -------- | -------- | -------- | -------- |
| color | &lt;color&gt; | - | 否 | 文本颜色。 |
| font-size | &lt;length&gt; | - | 否 | 文本大小。 |
| allow-scale | boolean | true | 否 | 文本尺寸是否跟随系统设置字体缩放尺寸进行放大缩小。<br>默认值：true。<br>true：表示文本尺寸跟随系统设置字体缩放尺寸进行放大缩小。<br>false：表示文本尺寸不跟随系统设置字体缩放尺寸进行放大缩小。 |
| font-style | string | normal | 否 | 文本字体样式，可选值为：<br/>-&nbsp;normal:&nbsp;标准的字体样式；<br/>-&nbsp;italic:&nbsp;斜体的字体样式。 |
| font-weight | number\|string | normal | 否 | 文本字体粗细，number类型取值[100,&nbsp;900]的整数（被100整除），默认为400，取值越大，字体越粗。string类型取值为：lighter、normal、bold、bolder。 |
| text-decoration | string | none | 否 | 文本修饰，可选值为：<br/>-&nbsp;underline:&nbsp;文本下划线修饰。<br/>-&nbsp;line-through:&nbsp;穿过文本的修饰线。<br/>-&nbsp;none:&nbsp;标准文本。 |
| font-family | string | sans-serif | 否 | 字体列表，用逗号分隔，每个字体用字体名或者字体族名设置。列表中第一个系统中存在的或者通过[自定义字体](js-components-common-customizing-font.md)指定的字体，会被选中作为文本的字体。 |

>  **说明：**
> - 不支持长宽样式，宽和父容器stepper一样，高是父容器stepper减去底部导航按钮的高度。
> 
> - 不支持position样式。


## 事件

除支持[通用事件](js-components-common-events.md)外，还支持如下事件：

| 名称 | 参数 | 描述 |
| -------- | -------- | -------- |
| appear | - | 当该步骤出现时触发。 |
| disappear | - | 当该步骤消失时触发。 |


## 方法

不支持[通用方法](js-components-common-methods.md)。


## 示例

详见[stepper示例](js-components-container-stepper.md)。
