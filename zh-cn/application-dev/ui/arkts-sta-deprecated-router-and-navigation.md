# UI组件适配（路由与导航）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## @ohos.router

### push
ArkTS-Dyn接口声明：[push(options: RouterOptions): void](../reference/apis-arkui/js-apis-router.md#routerpushdeprecated)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushurl)



ArkTS-Dyn示例：

```ts
router.push({url: "url"})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushUrl({url: "url"})
```


### pushUrl
ArkTS-Dyn接口声明：[pushUrl(options: RouterOptions): Promise<void>](../reference/apis-arkui/js-apis-router.md#routerpushurldeprecated)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushurl)



ArkTS-Dyn示例：

```ts
router.pushUrl({url: "url"})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushUrl({url: "url"})
```


### pushUrl
ArkTS-Dyn接口声明：[pushUrl(options: RouterOptions, callback: AsyncCallback<void>):void](../reference/apis-arkui/js-apis-router.md#routerpushurldeprecated-1)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushurl-1)



ArkTS-Dyn示例：

```ts
router.pushUrl({url: "url"}, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushUrl({url: "url"}, ()=>{})
```


### pushUrl
ArkTS-Dyn接口声明：[pushUrl(options: RouterOptions, mode: RouterMode): Promise<void>](../reference/apis-arkui/js-apis-router.md#routerpushurldeprecated-2)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions, mode: router.RouterMode): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushurl-2)



ArkTS-Dyn示例：

```ts
router.pushUrl({url: "url"}, router.RouterMode.Standard)
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushUrl({url: "url"}, router.RouterMode.Standard)
```


### pushUrl
ArkTS-Dyn接口声明：[pushUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback<void>):void](../reference/apis-arkui/js-apis-router.md#routerpushurldeprecated-3)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushurl-3)



ArkTS-Dyn示例：

```ts
router.pushUrl({url: "url"}, router.RouterMode.Standard, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushUrl({url: "url"}, router.RouterMode.Standard, ()=>{})
```


### back
ArkTS-Dyn接口声明：[back(options?: RouterOptions):void](../reference/apis-arkui/js-apis-router.md#routerbackdeprecated)

替代的ArkTS-Sta接口声明：[back(options?: router.RouterOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#back)



ArkTS-Dyn示例：

```ts
router.back({url: "url"})
```
ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().back({url: "url"})
```


### back
ArkTS-Dyn接口声明：[back(index: number, params?: Object): void](../reference/apis-arkui/js-apis-router.md#routerbackdeprecated-1)

替代的ArkTS-Sta接口声明：[back(index: number, params?: Object): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#back12)



ArkTS-Dyn示例：

```ts
router.back(1)
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().back(1)
```


### replace
ArkTS-Dyn接口声明：[replace(options: RouterOptions): void](../reference/apis-arkui/js-apis-router.md#routerreplacedeprecated)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#replaceurl)



ArkTS-Dyn示例：

```ts
router.replace({url: "url"})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceUrl({url: "url"})
```


### replaceUrl
ArkTS-Dyn接口声明：[replaceUrl(options: RouterOptions): Promise<void>](../reference/apis-arkui/js-apis-router.md#routerreplaceurldeprecated)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#replaceurl)



ArkTS-Dyn示例：

```ts
router.replaceUrl({url: "url"})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceUrl({url: "url"})
```


### replaceUrl
ArkTS-Dyn接口声明：[replaceUrl(options: RouterOptions, callback: AsyncCallback<void>):void](../reference/apis-arkui/js-apis-router.md#routerreplaceurldeprecated-1)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#replaceurl-1)



ArkTS-Dyn示例：

```ts
router.replaceUrl({url: "url"}, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceUrl({url: "url"}, ()=>{})
```


### replaceUrl
ArkTS-Dyn接口声明：[replaceUrl(options: RouterOptions, mode: RouterMode): Promise<void>](../reference/apis-arkui/js-apis-router.md#routerreplaceurldeprecated-2)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions, mode: router.RouterMode): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#replaceurl-2)



ArkTS-Dyn示例：

```ts
router.replaceUrl({url: "url"}, router.RouterMode.Standard)
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceUrl({url: "url"}, router.RouterMode.Standard)
```


### replaceUrl
ArkTS-Dyn接口声明：[replaceUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback<void>):void](../reference/apis-arkui/js-apis-router.md#routerreplaceurldeprecated-3)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#replaceurl-3)



ArkTS-Dyn示例：

```ts
router.replaceUrl({url: "url"}, router.RouterMode.Standard, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceUrl({url: "url"}, router.RouterMode.Standard, ()=>{})
```


### pushNamedRoute
ArkTS-Dyn接口声明：[pushNamedRoute(options: NamedRouterOptions): Promise<void>](../reference/apis-arkui/js-apis-router.md#routerpushnamedroutedeprecated)

替代的ArkTS-Sta接口声明：[pushNamedRoute(options: router.NamedRouterOptions): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushnamedroute)



ArkTS-Dyn示例：

```ts
router.pushNamedRoute({name: "路由名"})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushNamedRoute({name: "路由名"})
```


### pushNamedRoute
ArkTS-Dyn接口声明：[pushNamedRoute(options: NamedRouterOptions, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-router.md#routerpushnamedroutedeprecated-1)

替代的ArkTS-Sta接口声明：[pushNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushnamedroute-1)



ArkTS-Dyn示例：

```ts
router.pushNamedRoute({name: "路由名"}, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushNamedRoute({name: "路由名"}, ()=>{})
```


### pushNamedRoute
ArkTS-Dyn接口声明：[pushNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise<void>](../reference/apis-arkui/js-apis-router.md#routerpushnamedroutedeprecated-2)

替代的ArkTS-Sta接口声明：[pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushnamedroute-2)



ArkTS-Dyn示例：

```ts
router.pushNamedRoute({name: "路由名"}, router.RouterMode.Standard)
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushNamedRoute({name: "路由名"}, router.RouterMode.Standard)
```


### pushNamedRoute
ArkTS-Dyn接口声明：[pushNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-router.md#routerpushnamedroutedeprecated-3)

替代的ArkTS-Sta接口声明：[pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushnamedroute-3)



ArkTS-Dyn示例：

```ts
router.pushNamedRoute({name: "路由名"}, router.RouterMode.Standard, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushNamedRoute({name: "路由名"}, router.RouterMode.Standard, ()=>{})
```


### replaceNamedRoute
ArkTS-Dyn接口声明：[replaceNamedRoute(options: NamedRouterOptions): Promise<void>](../reference/apis-arkui/js-apis-router.md#routerreplacenamedroutedeprecated)

替代的ArkTS-Sta接口声明：[replaceNamedRoute(options: router.NamedRouterOptions): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#replacenamedroute)



ArkTS-Dyn示例：

```ts
router.replaceNamedRoute({name: "路由名"})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceNamedRoute({name: "路由名"})
```


### replaceNamedRoute
ArkTS-Dyn接口声明：[replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-router.md#routerreplacenamedroutedeprecated-1)

替代的ArkTS-Sta接口声明：[replaceNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#replacenamedroute-1)



ArkTS-Dyn示例：

```ts
router.replaceNamedRoute({name: "路由名"}, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceNamedRoute({name: "路由名"}, ()=>{})
```


### replaceNamedRoute
ArkTS-Dyn接口声明：[replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise<void>](../reference/apis-arkui/js-apis-router.md#routerreplacenamedroutedeprecated-2)

替代的ArkTS-Sta接口声明：[replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise<void>](../reference/apis-arkui/js-apis-arkui-UIContext.md#replacenamedroute-2)



ArkTS-Dyn示例：

```ts
router.replaceNamedRoute({name: "路由名"}, router.RouterMode.Standard)
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceNamedRoute({name: "路由名"}, router.RouterMode.Standard)
```


### replaceNamedRoute
ArkTS-Dyn接口声明：[replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-router.md#routerreplacenamedroutedeprecated-3)

替代的ArkTS-Sta接口声明：[pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#replacenamedroute-3)



ArkTS-Dyn示例：

```ts
router.replaceNamedRoute({name: "路由名"}, router.RouterMode.Standard, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceNamedRoute({name: "路由名"}, router.RouterMode.Standard, ()=>{})
```


### getParams
ArkTS-Dyn接口声明：[getParams(): Object](../reference/apis-arkui/js-apis-router.md#routergetparamsdeprecated)

替代的ArkTS-Sta接口声明：[getParams(): Object](../reference/apis-arkui/js-apis-arkui-UIContext.md#getparams)



ArkTS-Dyn示例：

```ts
router.getParams()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().getParams()
```


### getStateByUrl
ArkTS-Dyn接口声明：[getStateByUrl(url: string): Array\<RouterState>](../reference/apis-arkui/js-apis-router.md#routergetstatebyurldeprecated)

替代的ArkTS-Sta接口声明：[getStateByUrl(url: string): Array<router.RouterState>](../reference/apis-arkui/js-apis-arkui-UIContext.md#getstatebyurl12)



ArkTS-Dyn示例：

```ts
router.getStateByUrl("url")
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().getStateByUrl("url")
```


### getStateByIndex
ArkTS-Dyn接口声明：[getStateByIndex(index: number): RouterState | undefined](../reference/apis-arkui/js-apis-router.md#routergetstatebyindexdeprecated)

替代的ArkTS-Sta接口声明：[getStateByIndex(index: number): router.RouterState | undefined](../reference/apis-arkui/js-apis-arkui-UIContext.md#getstatebyindex12)



ArkTS-Dyn示例：

```ts
router.getStateByIndex(1)
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().getStateByIndex(1)
```


### getState
ArkTS-Dyn接口声明：[getState():RouterState](../reference/apis-arkui/js-apis-router.md#routergetstatedeprecated)

替代的ArkTS-Sta接口声明：[getState(): router.RouterState](../reference/apis-arkui/js-apis-arkui-UIContext.md#getstate)



ArkTS-Dyn示例：

```ts
router.getState()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().getState()
```


### getLength
ArkTS-Dyn接口声明：[getLength():string](../reference/apis-arkui/js-apis-router.md#routergetlengthdeprecated)

替代的ArkTS-Sta接口声明：[getLength(): string](../reference/apis-arkui/js-apis-arkui-UIContext.md#getlength)



ArkTS-Dyn示例：

```ts
router.getLength()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().getLength()
```


### clear
ArkTS-Dyn接口声明：[clear():void](../reference/apis-arkui/js-apis-router.md#routercleardeprecated)

替代的ArkTS-Sta接口声明：[clear(): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#clear)



ArkTS-Dyn示例：

```ts
router.clear()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().clear()
```


### enableAlertBeforeBackPage
ArkTS-Dyn接口声明：[enableAlertBeforeBackPage(options: EnableAlertOptions): void](../reference/apis-arkui/js-apis-router.md#routerenablealertbeforebackpagedeprecated)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "1111" })
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().showAlertBeforeBackPage({message: "1111"})
```


### showAlertBeforeBackPage
ArkTS-Dyn接口声明：[showAlertBeforeBackPage(options: EnableAlertOptions):void](../reference/apis-arkui/js-apis-router.md#routershowalertbeforebackpagedeprecated)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.showAlertBeforeBackPage({message: "1111"})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().showAlertBeforeBackPage({message: "1111"})
```


### disableAlertBeforeBackPage
ArkTS-Dyn接口声明：[disableAlertBeforeBackPage(): void](../reference/apis-arkui/js-apis-router.md#routerdisablealertbeforebackpagedeprecated)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


### hideAlertBeforeBackPage
ArkTS-Dyn接口声明：[hideAlertBeforeBackPage():void](../reference/apis-arkui/js-apis-router.md#routerhidealertbeforebackpagedeprecated)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.hideAlertBeforeBackPage()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


## @system.router

### Router
ArkTS-Dyn接口声明：[export default class Router](../reference/apis-arkui/js-apis-system-router.md#导入模块)

替代的ArkTS-Sta接口声明：[export class Router](../reference/apis-arkui/js-apis-arkui-UIContext.md#router)



ArkTS-Dyn示例：

```ts
import router from '@system.router'
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter()
```


### push
ArkTS-Dyn接口声明：[static push(options: RouterOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerpush)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#pushurl-1)



ArkTS-Dyn示例：

```ts
router.push({ uri: "url" })
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushUrl({url: "url"}, ()=>{})
```


### back
ArkTS-Dyn接口声明：[static back(options?: BackRouterOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerback)

替代的ArkTS-Sta接口声明：[back(options?: router.RouterOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#back)



ArkTS-Dyn示例：

```ts
router.back() 
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().back()
```


### replace
ArkTS-Dyn接口声明：[static replace(options: RouterOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerreplace)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions, callback: AsyncCallback<void>): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#replaceUrl-1)



ArkTS-Dyn示例：

```ts
router.replace({ uri: "url" })
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().replaceUrl({ url: "url" }, ()=>{})
```


### clear
ArkTS-Dyn接口声明：[static clear(): void](../reference/apis-arkui/js-apis-system-router.md#routerclear)

替代的ArkTS-Sta接口声明：[clear(): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#clear)



ArkTS-Dyn示例：

```ts
router.clear()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().clear()
```


### enableAlertBeforeBackPage
ArkTS-Dyn接口声明：[static enableAlertBeforeBackPage(options: EnableAlertBeforeBackPageOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerenablealertbeforebackpage6)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "" })
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().showAlertBeforeBackPage({ message: "" })
```


### disableAlertBeforeBackPage
ArkTS-Dyn接口声明：[static disableAlertBeforeBackPage(options?: DisableAlertBeforeBackPageOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerdisablealertbeforebackpage6)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


### getLength
ArkTS-Dyn接口声明：[static getLength(): string](../reference/apis-arkui/js-apis-system-router.md#routergetlength)

替代的ArkTS-Sta接口声明：[getLength(): string](../reference/apis-arkui/js-apis-arkui-UIContext.md#getlength)



ArkTS-Dyn示例：

```ts
let length: string = router.getLength()
```

ArkTS-Sta示例：

```ts
let length: string = this.getUIContext().getRouter().getLength()
```


### getParams
ArkTS-Dyn接口声明：[static getParams(): ParamsInterface](../reference/apis-arkui/js-apis-system-router.md#routergetparams7)

替代的ArkTS-Sta接口声明：[getParams(): Object](../reference/apis-arkui/js-apis-arkui-UIContext.md#getparams)



ArkTS-Dyn示例：

```ts
router.getParams()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().getParams()
```


### getState
ArkTS-Dyn接口声明：[static getState(): RouterState](../reference/apis-arkui/js-apis-system-router.md#routergetstate)

替代的ArkTS-Sta接口声明：[getState(): router.RouterState](../reference/apis-arkui/js-apis-arkui-UIContext.md#getstate)



ArkTS-Dyn示例：

```ts
router.getState()
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().getState()
```


## BackRouterOptions

### BackRouterOptions
ArkTS-Dyn接口声明：[export interface BackRouterOptions](../reference/apis-arkui/js-apis-system-router.md#backrouteroptions)

替代的ArkTS-Sta接口声明：[interface RouterOptions](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: BackRouterOptions = { uri: "url" }
```

ArkTS-Sta示例：

```ts
let options: router.RouterOptions = { url: "url" }
```


### uri
ArkTS-Dyn接口声明：[uri: string ](../reference/apis-arkui/js-apis-system-router.md#backrouteroptions)

替代的ArkTS-Sta接口声明：[url: string ](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: BackRouterOptions = { uri: "url" }
```

ArkTS-Sta示例：

```ts
let options: router.RouterOptions = { url: "url" }
```


### params
ArkTS-Dyn接口声明：[params?: Object](../reference/apis-arkui/js-apis-system-router.md#backrouteroptions)

替代的ArkTS-Sta接口声明：[params?: Object](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: BackRouterOptions = {uri: "url", params: ""}
```

ArkTS-Sta示例：

```ts
let options: router.RouterOptions = {uri: "url", params: ""}
```


## RouterOptions

### RouterOptions
ArkTS-Dyn接口声明：[export interface RouterOptions](../reference/apis-arkui/js-apis-system-router.md#routeroptions)

替代的ArkTS-Sta接口声明：[interface RouterOptions](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: RouterOptions = { uri: "url" }
```

ArkTS-Sta示例：

```ts
let options: router.RouterOptions = { url: "url" }
```


### uri
ArkTS-Dyn接口声明：[uri: string](../reference/apis-arkui/js-apis-system-router.md#routeroptions)

替代的ArkTS-Sta接口声明：[url: string](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: RouterOptions = { uri: "url" }
```

ArkTS-Sta示例：

```ts
let options: router.RouterOptions = { url: "url" }
```


### params
ArkTS-Dyn接口声明：[params?: Object](../reference/apis-arkui/js-apis-system-router.md#routeroptions)

替代的ArkTS-Sta接口声明：[params?: Object](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: RouterOptions = {url: "url", params: ""}
```

ArkTS-Sta示例：

```ts
let options: router.RouterOptions = {url: "url", params: ""}
```


## RouterState

### RouterState
ArkTS-Dyn接口声明：[export interface RouterState](../reference/apis-arkui/js-apis-system-router.md#routerstate)

替代的ArkTS-Sta接口声明：[interface RouterState](../reference/apis-arkui/js-apis-router.md#routerstate)



ArkTS-Dyn示例：

```ts
let state: RouterState = { uri: "url" }
```

ArkTS-Sta示例：

```ts
let state: router.RouterState = { url: "url" }
```


### index
ArkTS-Dyn接口声明：[index: number](../reference/apis-arkui/js-apis-system-router.md#routerstate)

替代的ArkTS-Sta接口声明：[index: number](../reference/apis-arkui/js-apis-router.md#routerstate)



ArkTS-Dyn示例：

```ts
let state: RouterState = router.getState()
let index: number = state.index
```

ArkTS-Sta示例：

```ts
let state: router.RouterState = this.getUIContext().getRouter().getState()
let index: number = state.index
```


### name
ArkTS-Dyn接口声明：[name: string](../reference/apis-arkui/js-apis-system-router.md#routerstate)

替代的ArkTS-Sta接口声明：[name: string](../reference/apis-arkui/js-apis-router.md#routerstate)



ArkTS-Dyn示例：

```ts
let state: RouterState = router.getState()
let name: string = state.name
```

ArkTS-Sta示例：

```ts
let state: router.RouterState = this.getUIContext().getRouter().getState()
let name: string = state.name
```


### path
ArkTS-Dyn接口声明：[path: string](../reference/apis-arkui/js-apis-system-router.md#routerstate)

替代的ArkTS-Sta接口声明：[path: string](../reference/apis-arkui/js-apis-router.md#routerstate)



ArkTS-Dyn示例：

```ts
let state: RouterState = router.getState()
let path: string = state.path
```

ArkTS-Sta示例：

```ts
let state: router.RouterState = this.getUIContext().getRouter().getState()
let path: string = state.path
```


## EnableAlertBeforeBackPageOptions

### EnableAlertBeforeBackPageOptions
ArkTS-Dyn接口声明：[export interface EnableAlertBeforeBackPageOptions](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[interface EnableAlertOptions](../reference/apis-arkui/js-apis-router.md#enablealertoptions)



ArkTS-Dyn示例：

```ts
let options: EnableAlertBeforeBackPageOptions = { message: "" }
```

ArkTS-Sta示例：

```ts
let options: EnableAlertOptions = { message: "" }
```


### message
ArkTS-Dyn接口声明：[message: string ](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[message: string ](../reference/apis-arkui/js-apis-router.md#enablealertoptions)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "" })
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().showAlertBeforeBackPage({ message: "" })
```


### success
ArkTS-Dyn接口声明：[success?: (errMsg: string) => void](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "", success: (err: string)=>{} })
```

ArkTS-Sta示例：

```ts
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().showAlertBeforeBackPage({ message: "" })
```


### cancel
ArkTS-Dyn接口声明：[cancel?: (errMsg: string) => void](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "", cancel: (err: string)=>{} })
```

ArkTS-Sta示例：

```ts
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().showAlertBeforeBackPage({ message: "" })
```


### complete
ArkTS-Dyn接口声明：[complete?: () => void](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "", complete: ()=>{} })
```

ArkTS-Sta示例：

```ts
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().showAlertBeforeBackPage({ message: "" })
```


## DisableAlertBeforeBackPageOptions

### DisableAlertBeforeBackPageOptions
ArkTS-Dyn接口声明：[export interface DisableAlertBeforeBackPageOptions](../reference/apis-arkui/js-apis-system-router.md#disablealertbeforebackpageoptions6)

暂无替代的ArkTS-Sta接口。

### success
ArkTS-Dyn接口声明：[success?: (errMsg: string) => void](../reference/apis-arkui/js-apis-system-router.md#disablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage({ success: (err: string)=>{} })
```

ArkTS-Sta示例：

```ts
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


### cancel
ArkTS-Dyn接口声明：[cancel?: (errMsg: string) => void](../reference/apis-arkui/js-apis-system-router.md#disablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage({ cancel: (err: string)=>{} })
```

ArkTS-Sta示例：

```ts
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


### complete
ArkTS-Dyn接口声明：[complete?: () => void](../reference/apis-arkui/js-apis-system-router.md#disablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage({ complete: ()=>{} })
```

ArkTS-Sta示例：

```ts
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


## ParamsInterface

### ParamsInterface
ArkTS-Dyn接口声明：[type ParamsInterface = {[key: string]: Object}](../reference/apis-arkui/js-apis-system-router.md#paramsinterface)

替代的ArkTS-Sta接口声明：interface Object



ArkTS-Dyn示例：

```ts
let params: ParamsInterface = router.getParams()
```

ArkTS-Sta示例：

```ts
let params: Object = this.getUIContext().getRouter().getParams()
```


## Navigation

### toolBar

ArkTS-Dyn接口声明：[toolBar(value: object | CustomBuilder): NavigationAttribute](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#toolbardeprecated)

替代的ArkTS-Sta接口声明：[toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions): NavigationAttribute](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#toolbarconfiguration10)



ArkTS-Dyn示例：

```ts
@Builder
MyToolBar(name: string) {
    //...
}
build(){
    Navigation().toolBar(this.MyToolBar)
}
```

ArkTS-Sta示例：

```ts
@Builder
MyToolBar(name: string) {
    //...
}
build(){
    Navigation().toolbarConfiguration(this.MyToolBar)
}
```


### subTitle

ArkTS-Dyn接口声明：[subTitle(value: string): NavigationAttribute](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#subtitledeprecated)

替代的ArkTS-Sta接口声明：[title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle, options?: NavigationTitleOptions): NavigationAttribute](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#title)



ArkTS-Dyn示例：

```ts
Navigation().subTitle("子标题")
```

ArkTS-Sta示例：
```ts
Navigation().title({main: "标题", sub: "子标题"})
```


## Navigator

ArkTS-Dyn接口声明：[Navigator(value?: {target: string, type?: NavigationType})](../reference/apis-arkui/arkui-ts/ts-container-navigator.md#navigator)

替代的ArkTS-Sta接口声明：[export class Router](../reference/apis-arkui/js-apis-arkui-UIContext.md#router)



ArkTS-Dyn示例：

```ts
Navigator({ target: "url", type: NavigationType.Push}){
    Text("Push")
}
Navigator({ target: "url", type: NavigationType.Back}){
    Text("Back")
}
Navigator({ target: "url", type: NavigationType.Replace}){
    Text("Replace")
}
```

ArkTS-Sta示例：

```ts
// ArkTS-Sta版本Navigator组件全面废弃，将由router进行替代
Text("Push").onClick(()=>{
    this.getUIContext().getRouter().pushUrl({ url: "url"});
})
Text("Back").onClick(()=> {
    this.getUIContext().getRouter().back({ url: "url"});
})
Text("Replace").onClick(()=>{
    this.getUIContext().getRouter().replaceUrl({ url: "url"});
})
```


## NavRouter

ArkTS-Dyn接口声明：[NavRouter()](../reference/apis-arkui/arkui-ts/ts-basic-components-navrouter.md#navrouter-1)

替代的ArkTS-Sta接口声明：[Navigation(pathInfos: NavPathStack)](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigation10)



ArkTS-Dyn示例：

```ts
@Entry
@Component
struct Index {
  build(){
    Column(){
      Navigation(){
        NavRouter(){
          Row(){
            Row()
            Text("pageOne")
          }
          NavDestination(){
            Text("当前页面为pageOne")
          }.title("pageOne")
        }
        NavRouter(){
          Row(){
            Row()
            Text("pageTwo")
          }
          NavDestination(){
            Text("当前页面为pageTwo")
          }.title("pageTwo")
        }
      }
    }
  }
}
```

ArkTS-Sta示例：

```ts
// ArkTS-Sta版本NavRouter组件全面废弃，将由Navigation进行替代
@Entry
@Component
struct Index {
  private pageInfos: NavPathStack = new NavPathStack();

  @Builder
  MyPageMap(name: string) {
    if (name === 'pageOne') {
      PageOne()
    } else if (name === 'pageTwo') {
      PageTwo()
    }
  }

  build(){
    Navigation(this.pageInfos){
      Text("pageOne").onClick(()=>{
        this.pageInfos.pushPath({name : "pageOne"});
      })
      Text("pageTwo").onClick(()=>{
        this.pageInfos.pushPath({name : "pageTwo"});
      })
    }.navDestination(this.MyPageMap)
  }
}

@Component
export struct PageOne {
  build() {
    NavDestination() {
      Text("当前页面为pageOne")
    }.title("PageOne")
  }
}

@Component
export struct PageTwo {
  build() {
    NavDestination() {
      Text("当前页面为pageTwo")
    }.title("PageTwo")
  }
}
```