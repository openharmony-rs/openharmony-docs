# UI组件适配（路由与导航）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @tsj_20201-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## @ohos.router

### push

ArkTS-Dyn接口声明：[push(options: RouterOptions): void](../reference/apis-arkui/js-apis-router.md#routerpushdeprecated)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushurl)

ArkTS-Dyn示例：

```ts
router.push({url: "url"})
```

ArkTS-Sta示例：

<!-- @[push](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().pushUrl({ url: "url" })
```

### pushUrl

ArkTS-Dyn接口声明：[pushUrl(options: RouterOptions): Promise\<void>](../reference/apis-arkui/js-apis-router.md#routerpushurldeprecated)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushurl)

ArkTS-Dyn示例：

```ts
router.pushUrl({url: "url"})
```

ArkTS-Sta示例：

<!-- @[pushUrl](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().pushUrl({url: "url"})
```

### pushUrl

ArkTS-Dyn接口声明：[pushUrl(options: RouterOptions, callback: AsyncCallback&lt;void&gt;): void](../reference/apis-arkui/js-apis-router.md#routerpushurldeprecated-1)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions, callback: AsyncCallback\<void>): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushurl-1)

ArkTS-Dyn示例：

```ts
router.pushUrl({url: "url"}, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().pushUrl({url: "url"}, ()=>{})
```


### pushUrl
ArkTS-Dyn接口声明：[pushUrl(options: RouterOptions, mode: RouterMode): Promise&lt;void&gt;](../reference/apis-arkui/js-apis-router.md#routerpushurldeprecated-2)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions, mode: router.RouterMode): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushurl-2)



ArkTS-Dyn示例：

```ts
router.pushUrl({url: "url"}, router.RouterMode.Standard)
```

ArkTS-Sta示例：

<!-- @[pushUrl2](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().pushUrl({url: "url"}, router.RouterMode.Standard)
```


### pushUrl
ArkTS-Dyn接口声明：[pushUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void](../reference/apis-arkui/js-apis-router.md#routerpushurldeprecated-3)

替代的ArkTS-Sta接口声明：[pushUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushurl-3)



ArkTS-Dyn示例：

```ts
router.pushUrl({url: "url"}, router.RouterMode.Standard, ()=>{})
```

ArkTS-Sta示例：

<!-- @[pushUrl3](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().pushUrl({url: "url"}, router.RouterMode.Standard, ()=>{})
```


### back
ArkTS-Dyn接口声明：[back(options?: RouterOptions): void](../reference/apis-arkui/js-apis-router.md#routerbackdeprecated)

替代的ArkTS-Sta接口声明：[back(options?: router.RouterOptions): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#back)



ArkTS-Dyn示例：

```ts
router.back({url: "url"})
```
ArkTS-Sta示例：

<!-- @[back](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().back({url: "url"})
```


### back
ArkTS-Dyn接口声明：[back(index: number, params?: Object): void](../reference/apis-arkui/js-apis-router.md#routerbackdeprecated-1)

替代的ArkTS-Sta接口声明：[back(index: number, params?: Object): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#back12)



ArkTS-Dyn示例：

```ts
router.back(1)
```

ArkTS-Sta示例：

<!-- @[back1](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().back(1)
```


### replace
ArkTS-Dyn接口声明：[replace(options: RouterOptions): void](../reference/apis-arkui/js-apis-router.md#routerreplacedeprecated)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#replaceurl)



ArkTS-Dyn示例：

```ts
router.replace({url: "url"})
```

ArkTS-Sta示例：

<!-- @[replace](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceUrl({url: "url"})
```


### replaceUrl
ArkTS-Dyn接口声明：[replaceUrl(options: RouterOptions): Promise\<void>](../reference/apis-arkui/js-apis-router.md#routerreplaceurldeprecated)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#replaceurl)



ArkTS-Dyn示例：

```ts
router.replaceUrl({url: "url"})
```

ArkTS-Sta示例：

<!-- @[replaceUrl](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceUrl({url: "url"})
```


### replaceUrl
ArkTS-Dyn接口声明：[replaceUrl(options: RouterOptions, callback: AsyncCallback&lt;void&gt;): void](../reference/apis-arkui/js-apis-router.md#routerreplaceurldeprecated-1)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions, callback: AsyncCallback&lt;void&gt;): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#replaceurl-1)



ArkTS-Dyn示例：

```ts
router.replaceUrl({url: "url"}, ()=>{})
```

ArkTS-Sta示例：

<!-- @[replaceUrl2](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceUrl({url: "url"}, ()=>{})
```


### replaceUrl
ArkTS-Dyn接口声明：[replaceUrl(options: RouterOptions, mode: RouterMode): Promise\<void>](../reference/apis-arkui/js-apis-router.md#routerreplaceurldeprecated-2)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions, mode: router.RouterMode): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#replaceurl-2)



ArkTS-Dyn示例：

```ts
router.replaceUrl({url: "url"}, router.RouterMode.Standard)
```

ArkTS-Sta示例：

<!-- @[replaceUrl3](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceUrl({url: "url"}, router.RouterMode.Standard)
```


### replaceUrl
ArkTS-Dyn接口声明：[replaceUrl(options: RouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void](../reference/apis-arkui/js-apis-router.md#routerreplaceurldeprecated-3)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#replaceurl-3)



ArkTS-Dyn示例：

```ts
router.replaceUrl({url: "url"}, router.RouterMode.Standard, ()=>{})
```

ArkTS-Sta示例：

<!-- @[replaceUrl4](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceUrl({url: "url"}, router.RouterMode.Standard, ()=>{})
```


### pushNamedRoute
ArkTS-Dyn接口声明：[pushNamedRoute(options: NamedRouterOptions): Promise\<void>](../reference/apis-arkui/js-apis-router.md#routerpushnamedroutedeprecated)

替代的ArkTS-Sta接口声明：[pushNamedRoute(options: router.NamedRouterOptions): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushnamedroute)



ArkTS-Dyn示例：

```ts
router.pushNamedRoute({name: "路由名"})
```

ArkTS-Sta示例：

<!-- @[pushNamedRoute](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().pushNamedRoute({name: "路由名"})
```


### pushNamedRoute
ArkTS-Dyn接口声明：[pushNamedRoute(options: NamedRouterOptions, callback: AsyncCallback\<void>): void](../reference/apis-arkui/js-apis-router.md#routerpushnamedroutedeprecated-1)

替代的ArkTS-Sta接口声明：[pushNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback\<void>): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushnamedroute-1)



ArkTS-Dyn示例：

```ts
router.pushNamedRoute({name: "路由名"}, ()=>{})
```

ArkTS-Sta示例：

<!-- @[pushNamedRoute2](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().pushNamedRoute({name: "路由名"}, ()=>{})
```


### pushNamedRoute
ArkTS-Dyn接口声明：[pushNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise\<void>](../reference/apis-arkui/js-apis-router.md#routerpushnamedroutedeprecated-2)

替代的ArkTS-Sta接口声明：[pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushnamedroute-2)



ArkTS-Dyn示例：

```ts
router.pushNamedRoute({name: "路由名"}, router.RouterMode.Standard)
```

ArkTS-Sta示例：

<!-- @[pushNamedRoute3](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().pushNamedRoute({name: "路由名"}, router.RouterMode.Standard)
```


### pushNamedRoute
ArkTS-Dyn接口声明：[pushNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback\<void>): void](../reference/apis-arkui/js-apis-router.md#routerpushnamedroutedeprecated-3)

替代的ArkTS-Sta接口声明：[pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback\<void>): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushnamedroute-3)



ArkTS-Dyn示例：

```ts
router.pushNamedRoute({name: "路由名"}, router.RouterMode.Standard, ()=>{})
```

ArkTS-Sta示例：

<!-- @[pushNamedRoute4](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().pushNamedRoute({name: "路由名"}, router.RouterMode.Standard, ()=>{})
```


### replaceNamedRoute
ArkTS-Dyn接口声明：[replaceNamedRoute(options: NamedRouterOptions): Promise\<void>](../reference/apis-arkui/js-apis-router.md#routerreplacenamedroutedeprecated)

替代的ArkTS-Sta接口声明：[replaceNamedRoute(options: router.NamedRouterOptions): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#replacenamedroute)



ArkTS-Dyn示例：

```ts
router.replaceNamedRoute({name: "路由名"})
```

ArkTS-Sta示例：

<!-- @[replaceNamedRoute](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceNamedRoute({name: "路由名"})
```


### replaceNamedRoute
ArkTS-Dyn接口声明：[replaceNamedRoute(options: NamedRouterOptions, callback: AsyncCallback\<void>): void](../reference/apis-arkui/js-apis-router.md#routerreplacenamedroutedeprecated-1)

替代的ArkTS-Sta接口声明：[replaceNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback\<void>): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#replacenamedroute-1)



ArkTS-Dyn示例：

```ts
router.replaceNamedRoute({name: "路由名"}, ()=>{})
```

ArkTS-Sta示例：

<!-- @[replaceNamedRoute2](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceNamedRoute({name: "路由名"}, ()=>{})
```


### replaceNamedRoute
ArkTS-Dyn接口声明：[replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode): Promise\<void>](../reference/apis-arkui/js-apis-router.md#routerreplacenamedroutedeprecated-2)

替代的ArkTS-Sta接口声明：[replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise\<void>](../reference/apis-arkui/arkts-apis-uicontext-router.md#replacenamedroute-2)



ArkTS-Dyn示例：

```ts
router.replaceNamedRoute({name: "路由名"}, router.RouterMode.Standard)
```

ArkTS-Sta示例：

<!-- @[replaceNamedRoute3](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceNamedRoute({name: "路由名"}, router.RouterMode.Standard)
```


### replaceNamedRoute
ArkTS-Dyn接口声明：[replaceNamedRoute(options: NamedRouterOptions, mode: RouterMode, callback: AsyncCallback&lt;void&gt;): void](../reference/apis-arkui/js-apis-router.md#routerreplacenamedroutedeprecated-3)

替代的ArkTS-Sta接口声明：[replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#replacenamedroute-3)



ArkTS-Dyn示例：

```ts
router.replaceNamedRoute({name: "路由名"}, router.RouterMode.Standard, ()=>{})
```

ArkTS-Sta示例：

<!-- @[replaceNamedRoute4](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceNamedRoute({name: "路由名"}, router.RouterMode.Standard, ()=>{})
```


### getParams
ArkTS-Dyn接口声明：[getParams(): Object](../reference/apis-arkui/js-apis-router.md#routergetparamsdeprecated)

替代的ArkTS-Sta接口声明：[getParams(): Object](../reference/apis-arkui/arkts-apis-uicontext-router.md#getparams)



ArkTS-Dyn示例：

```ts
router.getParams()
```

ArkTS-Sta示例：

<!-- @[getParams](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().getParams()
```


### getStateByUrl
ArkTS-Dyn接口声明：[getStateByUrl(url: string): Array&lt;RouterState&gt;](../reference/apis-arkui/js-apis-router.md#routergetstatebyurldeprecated)

替代的ArkTS-Sta接口声明：[getStateByUrl(url: string): Array<router.[RouterState](js-apis-router.md#routerstate)>](../reference/apis-arkui/arkts-apis-uicontext-router.md#getstatebyurl12)



ArkTS-Dyn示例：

```ts
router.getStateByUrl("url")
```

ArkTS-Sta示例：

<!-- @[getStateByUrl](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().getStateByUrl("url")
```


### getStateByIndex
ArkTS-Dyn接口声明：[getStateByIndex(index: number): RouterState | undefined](../reference/apis-arkui/js-apis-router.md#routergetstatebyindexdeprecated)

替代的ArkTS-Sta接口声明：[getStateByIndex(index: number): router.RouterState | undefined](../reference/apis-arkui/arkts-apis-uicontext-router.md#getstatebyindex12)



ArkTS-Dyn示例：

```ts
router.getStateByIndex(1)
```

ArkTS-Sta示例：

```ts
this.getUIContext().getRouter().getStateByIndex(1)
```


### getState
ArkTS-Dyn接口声明：[getState(): RouterState](../reference/apis-arkui/js-apis-router.md#routergetstatedeprecated)

替代的ArkTS-Sta接口声明：[getState(): router.RouterState](../reference/apis-arkui/arkts-apis-uicontext-router.md#getstate)



ArkTS-Dyn示例：

```ts
router.getState()
```

ArkTS-Sta示例：

<!-- @[getState](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().getState()
```


### getLength
ArkTS-Dyn接口声明：[getLength(): string](../reference/apis-arkui/js-apis-router.md#routergetlengthdeprecated)

替代的ArkTS-Sta接口声明：[getLength(): string](../reference/apis-arkui/arkts-apis-uicontext-router.md#getlengthdeprecated)



ArkTS-Dyn示例：

```ts
router.getLength()
```

ArkTS-Sta示例：

<!-- @[getLength](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().getLength()
```


### clear
ArkTS-Dyn接口声明：[clear(): void](../reference/apis-arkui/js-apis-router.md#routercleardeprecated)

替代的ArkTS-Sta接口声明：[clear(): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#clear)



ArkTS-Dyn示例：

```ts
router.clear()
```

ArkTS-Sta示例：

<!-- @[clear](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().clear()
```


### enableAlertBeforeBackPage
ArkTS-Dyn接口声明：[enableAlertBeforeBackPage(options: EnableAlertOptions): void](../reference/apis-arkui/js-apis-router.md#routerenablealertbeforebackpagedeprecated)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "1111" })
```

ArkTS-Sta示例：

<!-- @[enableAlertBeforeBackPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().showAlertBeforeBackPage({message: "1111"})
```


### showAlertBeforeBackPage
ArkTS-Dyn接口声明：[showAlertBeforeBackPage(options: EnableAlertOptions): void](../reference/apis-arkui/js-apis-router.md#routershowalertbeforebackpagedeprecated)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.showAlertBeforeBackPage({message: "1111"})
```

ArkTS-Sta示例：

<!-- @[enableAlertBeforeBackPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().showAlertBeforeBackPage({message: "1111"})
```


### disableAlertBeforeBackPage
ArkTS-Dyn接口声明：[disableAlertBeforeBackPage(): void](../reference/apis-arkui/js-apis-router.md#routerdisablealertbeforebackpagedeprecated)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage()
```

ArkTS-Sta示例：

<!-- @[disableAlertBeforeBackPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


### hideAlertBeforeBackPage
ArkTS-Dyn接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/js-apis-router.md#routerhidealertbeforebackpagedeprecated)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.hideAlertBeforeBackPage()
```

ArkTS-Sta示例：

<!-- @[hideAlertBeforeBackPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/ohosRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


## @system.router

### Router
ArkTS-Dyn接口声明：[@system.router](../reference/apis-arkui/js-apis-system-router.md)

替代的ArkTS-Sta接口声明：[getRouter](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)



ArkTS-Dyn示例：

```ts
import router from '@system.router'
```

ArkTS-Sta示例：

<!-- @[Router](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter()
```


### push
ArkTS-Dyn接口声明：[static push(options: RouterOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerpush)

替代的ArkTS-Sta接口声明：[pushUrl(options: router.RouterOptions, callback: AsyncCallback\<void>): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#pushurl-1)



ArkTS-Dyn示例：

```ts
router.push({ uri: "url" })
```

ArkTS-Sta示例：

<!-- @[push](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().pushUrl({ url: "url" }, () => {
})
```


### back
ArkTS-Dyn接口声明：[static back(options?: BackRouterOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerback)

替代的ArkTS-Sta接口声明：[back(options?: router.RouterOptions): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#back)



ArkTS-Dyn示例：

```ts
router.back() 
```

ArkTS-Sta示例：

<!-- @[back](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().back()
```


### replace
ArkTS-Dyn接口声明：[static replace(options: RouterOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerreplace)

替代的ArkTS-Sta接口声明：[replaceUrl(options: router.RouterOptions, callback: AsyncCallback\<void>): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#replaceurl-1)



ArkTS-Dyn示例：

```ts
router.replace({ uri: "url" })
```

ArkTS-Sta示例：

<!-- @[replace](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().replaceUrl({ url: "url" }, () => {
})
```


### clear
ArkTS-Dyn接口声明：[static clear(): void](../reference/apis-arkui/js-apis-system-router.md#routerclear)

替代的ArkTS-Sta接口声明：[clear(): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#clear)



ArkTS-Dyn示例：

```ts
router.clear()
```

ArkTS-Sta示例：

<!-- @[clear](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().clear()
```


### enableAlertBeforeBackPage
ArkTS-Dyn接口声明：[enableAlertBeforeBackPage(options: EnableAlertBeforeBackPageOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerenablealertbeforebackpage6)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "" })
```

ArkTS-Sta示例：

<!-- @[enableAlertBeforeBackPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().showAlertBeforeBackPage({ message: "" })
```


### disableAlertBeforeBackPage
ArkTS-Dyn接口声明：[disableAlertBeforeBackPage(options?: DisableAlertBeforeBackPageOptions): void](../reference/apis-arkui/js-apis-system-router.md#routerdisablealertbeforebackpage6)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage()
```

ArkTS-Sta示例：

<!-- @[disableAlertBeforeBackPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


### getLength
ArkTS-Dyn接口声明：[static getLength(): string](../reference/apis-arkui/js-apis-system-router.md#routergetlength)

替代的ArkTS-Sta接口声明：[getLength(): string](../reference/apis-arkui/arkts-apis-uicontext-router.md#getlengthdeprecated)



ArkTS-Dyn示例：

```ts
let length: string = router.getLength()
```

ArkTS-Sta示例：

<!-- @[getLength](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let length: string = this.getUIContext().getRouter().getLength()
```


### getParams
ArkTS-Dyn接口声明：[getParams(): ParamsInterface](../reference/apis-arkui/js-apis-system-router.md#routergetparams7)

替代的ArkTS-Sta接口声明：[getParams(): Object](../reference/apis-arkui/arkts-apis-uicontext-router.md#getparams)



ArkTS-Dyn示例：

```ts
router.getParams()
```

ArkTS-Sta示例：

<!-- @[getParams](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
this.getUIContext().getRouter().getParams()
```


### getState
ArkTS-Dyn接口声明：[static getState(): RouterState](../reference/apis-arkui/js-apis-system-router.md#routergetstate)

替代的ArkTS-Sta接口声明：[getState(): router.RouterState](../reference/apis-arkui/arkts-apis-uicontext-router.md#getstate)



ArkTS-Dyn示例：

```ts
router.getState()
```

ArkTS-Sta示例：

<!-- @[getState](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
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

<!-- @[BackRouterOptions](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let options: router.RouterOptions = { url: "url" }
```


### uri
ArkTS-Dyn接口声明：[uri](../reference/apis-arkui/js-apis-system-router.md#backrouteroptions)

替代的ArkTS-Sta接口声明：[url](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: BackRouterOptions = { uri: "url" }
```

ArkTS-Sta示例：

<!-- @[BackRouterOptions_uri](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let options: router.RouterOptions = { url: "url" }
```


### params
ArkTS-Dyn接口声明：[params](../reference/apis-arkui/js-apis-system-router.md#backrouteroptions)

替代的ArkTS-Sta接口声明：[params](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: BackRouterOptions = {uri: "url", params: ""}
```

ArkTS-Sta示例：

<!-- @[BackRouterOptions_params](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let options: router.RouterOptions = { url: "url", params: "" }
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

<!-- @[RouterOptions](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let options: router.RouterOptions = { url: "url" }
```


### uri
ArkTS-Dyn接口声明：[uri](../reference/apis-arkui/js-apis-system-router.md#routeroptions)

替代的ArkTS-Sta接口声明：[url](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: RouterOptions = { uri: "url" }
```

ArkTS-Sta示例：

<!-- @[RouterOptions_uri](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let options: router.RouterOptions = { url: "url" }
```


### params
ArkTS-Dyn接口声明：[params](../reference/apis-arkui/js-apis-system-router.md#routeroptions)

替代的ArkTS-Sta接口声明：[params](../reference/apis-arkui/js-apis-router.md#routeroptions)



ArkTS-Dyn示例：

```ts
let options: RouterOptions = {url: "url", params: ""}
```

ArkTS-Sta示例：

<!-- @[RouterOptions_params](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let options: router.RouterOptions = { url: "url", params: "" }
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

<!-- @[RouterState](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let state: router.RouterState = { index: 0, name: "name", path: "url", params: {} }
```


### index
ArkTS-Dyn接口声明：[index](../reference/apis-arkui/js-apis-system-router.md#routerstate)

替代的ArkTS-Sta接口声明：[index](../reference/apis-arkui/js-apis-router.md#routerstate)



ArkTS-Dyn示例：

```ts
let state: RouterState = router.getState()
let index: number = state.index
```

ArkTS-Sta示例：

<!-- @[RouterState_index](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let state: router.RouterState = this.getUIContext().getRouter().getState()
let index: number = state.index
```


### name
ArkTS-Dyn接口声明：[name](../reference/apis-arkui/js-apis-system-router.md#routerstate)

替代的ArkTS-Sta接口声明：[name](../reference/apis-arkui/js-apis-router.md#routerstate)



ArkTS-Dyn示例：

```ts
let state: RouterState = router.getState()
let name: string = state.name
```

ArkTS-Sta示例：

<!-- @[RouterState_name](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let state: router.RouterState = this.getUIContext().getRouter().getState()
let name: string = state.name
```


### path
ArkTS-Dyn接口声明：[path](../reference/apis-arkui/js-apis-system-router.md#routerstate)

替代的ArkTS-Sta接口声明：[path](../reference/apis-arkui/js-apis-router.md#routerstate)



ArkTS-Dyn示例：

```ts
let state: RouterState = router.getState()
let path: string = state.path
```

ArkTS-Sta示例：

<!-- @[RouterState_path](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let state: router.RouterState = this.getUIContext().getRouter().getState()
let path: string = state.path
```


## EnableAlertBeforeBackPageOptions

### EnableAlertBeforeBackPageOptions
ArkTS-Dyn接口声明：[EnableAlertBeforeBackPageOptions](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[EnableAlertOptions](../reference/apis-arkui/js-apis-router.md#enablealertoptions)



ArkTS-Dyn示例：

```ts
let options: EnableAlertBeforeBackPageOptions = { message: "" }
```

ArkTS-Sta示例：

<!-- @[EnableAlertBeforeBackPageOptions](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let options: router.EnableAlertOptions = { message: "" }
```


### message
ArkTS-Dyn接口声明：[message](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[message](../reference/apis-arkui/js-apis-router.md#enablealertoptions)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "" })
```

ArkTS-Sta示例：

<!-- @[EnableAlertBeforeBackPageOptions_message](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let options: router.EnableAlertOptions = { message: "" }
```


### success
ArkTS-Dyn接口声明：[success](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "", success: (err: string)=>{} })
```

ArkTS-Sta示例：

<!-- @[EnableAlertBeforeBackPageOptions_success](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().showAlertBeforeBackPage({ message: "" })
```


### cancel
ArkTS-Dyn接口声明：[cancel](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "", cancel: (err: string)=>{} })
```

ArkTS-Sta示例：

<!-- @[EnableAlertBeforeBackPageOptions_cancel](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().showAlertBeforeBackPage({ message: "" })
```


### complete
ArkTS-Dyn接口声明：[complete](../reference/apis-arkui/js-apis-system-router.md#enablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[showAlertBeforeBackPage(options: router.EnableAlertOptions): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#showalertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.enableAlertBeforeBackPage({ message: "", complete: ()=>{} })
```

ArkTS-Sta示例：

<!-- @[EnableAlertBeforeBackPageOptions_complete](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().showAlertBeforeBackPage({ message: "" })
```


## DisableAlertBeforeBackPageOptions

### DisableAlertBeforeBackPageOptions
ArkTS-Dyn接口声明：[DisableAlertBeforeBackPageOptions](../reference/apis-arkui/js-apis-system-router.md#disablealertbeforebackpageoptions6)

暂无替代的ArkTS-Sta接口。

### success
ArkTS-Dyn接口声明：[success](../reference/apis-arkui/js-apis-system-router.md#disablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage({ success: (err: string)=>{} })
```

ArkTS-Sta示例：

<!-- @[DisableAlertBeforeBackPageOptions_success](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


### cancel
ArkTS-Dyn接口声明：[cancel](../reference/apis-arkui/js-apis-system-router.md#disablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage({ cancel: (err: string)=>{} })
```

ArkTS-Sta示例：

<!-- @[DisableAlertBeforeBackPageOptions_cancel](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
// ArkTS-Sta版本，默认用户选择success，不再接受success、cancel、complete回调
this.getUIContext().getRouter().hideAlertBeforeBackPage()
```


### complete
ArkTS-Dyn接口声明：[complete](../reference/apis-arkui/js-apis-system-router.md#disablealertbeforebackpageoptions6)

替代的ArkTS-Sta接口声明：[hideAlertBeforeBackPage(): void](../reference/apis-arkui/arkts-apis-uicontext-router.md#hidealertbeforebackpage)



ArkTS-Dyn示例：

```ts
router.disableAlertBeforeBackPage({ complete: ()=>{} })
```

ArkTS-Sta示例：

<!-- @[DisableAlertBeforeBackPageOptions_complete](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
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

<!-- @[ParamsInterface](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/systemRouter.ets) -->

``` TypeScript
let params: Object = this.getUIContext().getRouter().getParams()
```


## Navigation

### toolBar

ArkTS-Dyn接口声明：[toolBar(value: object | CustomBuilder)](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#toolbardeprecated)

替代的ArkTS-Sta接口声明：[toolbarConfiguration(value: Array&lt;ToolbarItem&gt; | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined)](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#toolbarconfiguration10)



ArkTS-Dyn示例：

```ts
@Builder
MyToolBar(name: string) {
    // ...
}
build(){
    Navigation().toolBar(this.MyToolBar)
}
```

ArkTS-Sta示例：

<!-- @[toolBar](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/navigationDep.ets) -->

``` TypeScript
@Builder
MyToolBar() {
  // ...
}

build() {
  Navigation().toolbarConfiguration(this.MyToolBar).width('100%').height('25%')
}
```

### subTitle

ArkTS-Dyn接口声明：[subTitle(value: string)](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#subtitledeprecated)

替代的ArkTS-Sta接口声明：[title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle, options?: NavigationTitleOptions): NavigationAttribute](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#title)



ArkTS-Dyn示例：

```ts
Navigation().subTitle("子标题")
```

<!-- @[subTitle](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/navigationDep.ets) -->

``` TypeScript
@Entry
@Component
struct NavigationTitle {
  @State message: string = "NavigationTitle"

  build() {
    Column({ space: 8 } as ColumnOptions) {
      Navigation().title({ main: "标题", sub: "子标题" }).width('100%').height('25%')
      NavigatorExample()
      NavigationExample()
    }
    .width('100%')
  }
}
```


## Navigator

ArkTS-Dyn接口声明：[Navigator(value?: {target: string, type?: NavigationType})](../reference/apis-arkui/arkui-ts/ts-container-navigator.md#navigatordeprecated)

替代的ArkTS-Sta接口声明：[getRouter](../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter)



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

ArkTS-Dyn接口声明：[NavRouter()](../reference/apis-arkui/arkui-ts/ts-basic-components-navrouter.md#navrouterdeprecated)

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

<!-- @[navRouter](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/NavigationDeprecatedSta/entry/src/main/ets/pages/routerAndNavigation/navRouterExample.ets) -->

``` TypeScript
import {
  Entry,
  Text,
  Column,
  Component,
  Button,
  ClickEvent,
  NavPathStack,
  Navigation,
  NavPathInfo,
  NavDestination,
  State,
} from '@kit.ArkUI';
import hilog from '@ohos.hilog';

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

  build() {
    Navigation(this.pageInfos) {
      Text("pageOne").onClick(() => {
        this.pageInfos.pushPath(new NavPathInfo("pageOne", undefined));
      })
      Text("pageTwo").onClick(() => {
        this.pageInfos.pushPath(new NavPathInfo("pageTwo", undefined));
      })
    }.navDestination(this.MyPageMap)
  }
}

@Component
export struct PageOne {
  build(): void {
    NavDestination() {
      Text("当前页面为pageOne")
    }.title("PageOne")
  }
}

@Component
export struct PageTwo {
  build(): void {
    NavDestination() {
      Text("当前页面为pageTwo")
    }.title("PageTwo")
  }
}
```