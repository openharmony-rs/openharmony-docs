# RemoteWindow（系统接口）

## RemoteWindow

```TypeScript
@ComponentBuilder
export declare function RemoteWindow(
    target: WindowAnimationTarget
): RemoteWindowAttribute
```

远程控制窗口组件，可以通过此组件控制应用窗口，提供启动退出过程中控件动画和应用窗口联动动画的能力。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function RemoteWindow(    target: WindowAnimationTarget): RemoteWindowAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function RemoteWindow(    target: WindowAnimationTarget): RemoteWindowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [WindowAnimationTarget](arkts-na-remotewindow-windowanimationtarget-i-sys.md) | 是 | 需要控制的动画窗口的描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RemoteWindowAttribute |  |

