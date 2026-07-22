# CustomDialogControllerOptions

自定义弹窗的样式。
> **说明：**  
>  
> - 按下返回键和ESC键时会让弹窗退出。  
>  
> - 弹窗在避让软键盘时到达极限高度之后会压缩高度。  
> > 需要注意：高度压缩生效在外层容器上，如果容器根节点中的子组件设置了较大的固定高度，由于容器默认不裁剪，依然可能存在超出屏幕显示的情况。  
>  
> - 自定义弹窗仅适用于简单提示场景，不能替代页面使用。弹窗避让软键盘时，与软键盘之间存在16vp的安全间距。  
>  
> - 为了达成良好的视觉体验，弹窗的显示和关闭存在默认动画，动画时长不同设备间可能存在差异。  
> > 需要注意：在动画播放过程中，页面不响应触摸、滑动、点击操作。关闭默认弹窗动画效果可设置openAnimation和closeAnimation的duration为0。  
>  
> - 当前，ArkUI弹出框默认为非页面级弹出框，在页面路由跳转时，如果开发者未调用close方法将其关闭，弹出框将不会自动关闭。若需实现在跳转页面时覆盖弹出框的场景，可以使用  
> [组件导航子页面显示类型的弹窗类型](../../../ui/arkts-navigation-navdestination.md#页面显示类型)或者  
> [页面级弹出框](../../../ui/arkts-embedded-dialog.md)。

**起始版本：** 7

<!--Device-unnamed-declare interface CustomDialogControllerOptions--><!--Device-unnamed-declare interface CustomDialogControllerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Sets the distortion animation Mode of the dialog.

**类型：** DistortionMode

**默认值：** DistortionMode.DISTORTION_AUTO

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-distortionMode?: DistortionMode--><!--Device-CustomDialogControllerOptions-distortionMode?: DistortionMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Sets the edgeLight animation Mode of the dialog.

**类型：** EdgeLightMode

**默认值：** EdgeLightMode.EDGELIGHT_AUTO

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomDialogControllerOptions-edgeLightMode?: EdgeLightMode--><!--Device-CustomDialogControllerOptions-edgeLightMode?: EdgeLightMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

