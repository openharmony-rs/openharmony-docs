# animateTo

## animateTo

```TypeScript
declare function animateTo(value: AnimateParam, event: () => void): void
```

显式动画接口。在需要动画时，显式调用该接口改变状态以产生动画。 > > - 从API version 10开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_来明确UI的执行上下文。 > > - 不推荐在aboutToAppear、aboutToDisappear中调用动画。 > > - 如果在\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中调用动画，自 > 定义组件内的build还未执行，内部组件还未创建，动画时机过早，动画属性没有初值无法对组件产生动画。 > > - 执行\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_时， > 组件即将销毁，不能在aboutToDisappear里面做动画。 > > - 在组件出现和消失时，可以通过[组件内转场]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_添加动画效果。 > > - 组件内转场不支持的属性，可以参考\_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_，使用 > animateTo实现动画执行结束后组件消失的效果。 > > - 某些场景下，在\_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_中使用animateTo动画，会产生异常效果，具体 > 可参考：\_\_\_MD\_LINK\_DESC\_USD\_5\_\_\_。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 18

**替代接口：** ohos.arkui.UIContext.UIContext#animateTo

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare function animateTo(value: AnimateParam, event: () => void): void--><!--Device-unnamed-declare function animateTo(value: AnimateParam, event: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |
| event | () =&gt; void | 是 |  |

