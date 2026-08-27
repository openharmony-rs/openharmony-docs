# @ohos.atomicservice.AtomicServiceWeb(Defines the atomicService web component)

###### 需要权限
 访问在线网页时需添加网络权限：ohos.permission.INTERNET，
 具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。
 ###### 子组件
 无
 ###### 属性
 不支持通用属性。
 ###### 事件
 不支持通用事件。


## 导入模块

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceWebController(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-atomicservicewebcontroller-c.md) | 通过AtomicServiceWebController可以控制AtomicServiceWeb组件各种行为。一个AtomicServiceWebController对象只能控制一个AtomicServiceWeb组件，且必须在 AtomicServiceWeb组件和AtomicServiceWebController绑定后，才能调用AtomicServiceWebController上的方法。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceWeb(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-atomicserviceweb-s.md) | 为开发者提供满足定制化诉求的Web高阶组件，屏蔽原生Web组件中无需关注的接口，并提供JS扩展能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [OnErrorReceiveEvent(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-onerrorreceiveevent-i.md) | 定义网页加载遇到错误时触发该回调。 |
| [OnHttpErrorReceiveEvent(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-onhttperrorreceiveevent-i.md) | 定义网页加载资源遇到HTTP错误时触发该回调。 |
| [OnLoadInterceptEvent(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-onloadinterceptevent-i.md) | 定义Web组件加载url之前触发的加载拦截事件。 |
| [OnMessageEvent(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-onmessageevent-i.md) | 定义页面返回或销毁时触发该回调。 |
| [OnPageBeginEvent(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-onpagebeginevent-i.md) | 定义网页加载开始时触发该回调。 |
| [OnPageEndEvent(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-onpageendevent-i.md) | 定义网页加载结束时触发该回调。 |
| [OnProgressChangeEvent(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-onprogresschangeevent-i.md) | 定义网页加载进度变化时触发该回调。 |
| [WebHeader(Defines the atomicService web component)](arkts-arkui-atomicservice-atomicserviceweb-webheader-i.md) | Web组件返回的请求/响应头对象。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnLoadInterceptCallback(Defines the atomicService web component)](arkts-arkui-onloadinterceptcallback-t.md) | 当Web组件加载url之前触发该回调，用于判断是否阻止此次访问。 |
