# @ohos.mediaquery

提供根据不同媒体类型定义不同的样式。

> **说明：**
>
> - 该模块不支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-app-ability-uiability.md)的文件声明处使用，即不能在UIAbility的生命周期中调用，需要在创建组件实例后使用。
>
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见
> [UIContext](arkts-arkui-uicontext.md)说明。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [matchMediaSync](arkts-arkui-matchmediasync-f.md#matchmediasync-1) | 设置媒体查询的查询条件，并返回对应的监听句柄。@link @ohos.arkui.UIContext}中的&gt; [getMediaQuery](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getmediaquery)方法获取&gt; [MediaQuery](arkts-arkui-uicontext.md)对象，然后通过该对象进行调用。&gt;&gt; - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的&gt; [getMediaQuery](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getmediaquery)方法获取当前UI上下文关联的&gt; [MediaQuery](arkts-arkui-uicontext.md)对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [MediaQueryListener](arkts-arkui-mediaquerylistener-i.md) | 媒体查询的句柄，并包含了申请句柄时的首次查询结果。媒体查询根据设置的条件语句，比如'(width &lt;= 600vp)'，比较系统信息，若首次查询时相关信息未初始化，matches返回false。继承自[MediaQueryResult](arkts-arkui-mediaqueryresult-i.md)。 |
| [MediaQueryResult](arkts-arkui-mediaqueryresult-i.md) | 用于执行媒体查询操作。 |

