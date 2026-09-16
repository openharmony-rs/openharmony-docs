# @ohos.arkui.advanced.FullScreenLaunchComponent(Defines the fullScreen launch component)

## 子组件

无。

## 属性

不支持通用属性。

## 事件

不支持通用事件。

## 导入模块

```TypeScript
import { FullScreenLaunchComponent } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [FullScreenLaunchComponent](arkts-arkui-arkui-advanced-fullscreenlaunchcomponent-fullscreenlaunchcomponent-s.md) | 全屏启动原子化服务组件，当提供方授权使用方嵌入式运行原子化服务时，使用方全屏嵌入式运行原子化服务；未授权时，使用方跳出式拉起原子化服务。 |

## 示例

```TypeScript
本示例展示组件使用方法和提供方原子化服务的实现。实际运行时请使用开发者自己的原子化服务appId。

FullScreenLaunchComponent组件需要由使用方调用。在提供方完成本地的安装后，即可在使用方应用或者原子化服务中全屏嵌入式拉起提供方的原子化服务。

> 说明：
> 
> 由于嵌入式原子化服务运行在独立进程，其崩溃异常不会直接暴露在宿主的日志中。本地调试时可通过以下方式查看真实报错栈：
> 
> 打开DevEco Studio的HiLog面板。
> 
> 将左上角的模式切换为User logs of selected app。
> 
> 在右侧进程列表中，选择被拉起的原子化服务进程（被拉起原子化服务的包名，且后缀带有embeddable字样）。

使用方
```

```TypeScript
组件提供方

原子化服务提供方需要修改两个文件：

提供方入口文件：/src/main/ets/entryability/EntryAbility.ets。
```

```TypeScript
提供方扩展Ability入口页面文件：/src/main/ets/pages/Index.ets。
```
