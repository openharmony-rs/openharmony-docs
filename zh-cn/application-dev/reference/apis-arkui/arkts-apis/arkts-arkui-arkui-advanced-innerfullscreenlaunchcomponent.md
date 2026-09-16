# @ohos.arkui.advanced.InnerFullScreenLaunchComponent(系统接口)

## 子组件

无。

## 属性

不支持通用属性。

## 事件

不支持通用事件。

## 导入模块

```TypeScript
import { InnerFullScreenLaunchComponent, LaunchController } from '@kit.ArkUI';
```

## 汇总

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LaunchController](arkts-arkui-arkui-advanced-innerfullscreenlaunchcomponent-launchcontroller-c-sys.md) | 拉起原子化服务的控制器。 |
<!--DelEnd-->

<!--Del-->
### 结构体（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InnerFullScreenLaunchComponent](arkts-arkui-arkui-advanced-innerfullscreenlaunchcomponent-innerfullscreenlaunchcomponent-s-sys.md) | 非显式全屏拉起原子化服务组件，拉起方可以选择拉起原子化服务的时机。当被拉起方授权使用方嵌入式运行原子化服务时，使用方全屏嵌入式运行原子化服务；未授权时，使用方跳出式拉起原子化服务。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LaunchAtomicServiceCallback](arkts-arkui-launchatomicservicecallback-t-sys.md) | 拉起原子化服务触发的回调。 |
<!--DelEnd-->

## 示例

```TypeScript
> 说明：
> 
> 由于嵌入式原子化服务运行在独立进程，其崩溃异常不会直接暴露在宿主的日志中。本地调试时可通过以下方式查看真实报错栈：
> 
> 打开DevEco Studio的HiLog面板。
> 
> 将左上角的模式切换为User logs of selected app。
> 
> 在右侧进程列表中，选择被拉起的原子化服务进程（被拉起原子化服务的包名，且后缀带有embeddable字样）。
```
