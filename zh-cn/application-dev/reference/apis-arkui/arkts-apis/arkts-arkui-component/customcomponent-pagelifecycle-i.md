# PageLifeCycle

Defining interface of PageLifeCycle for custom component, when decorate with @Entry.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface PageLifeCycle {  /**   * onPageShow Method.   *   * The page is triggered once each time it is displayed, including scenarios such as   *     the routing process and the application entering the foreground   *   ****/  onPageShow(): void--><!--Device-unnamed-export interface PageLifeCycle {  /**   * onPageShow Method.   *   * The page is triggered once each time it is displayed, including scenarios such as   *     the routing process and the application entering the foreground   *   ****/  onPageShow(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPageShow

```TypeScript
onPageShow(): void
```

onPageShow Method. The page is triggered once each time it is displayed, including scenarios such as the routing process and the application entering the foreground

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageLifeCycle-onPageShow(): void--><!--Device-PageLifeCycle-onPageShow(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

