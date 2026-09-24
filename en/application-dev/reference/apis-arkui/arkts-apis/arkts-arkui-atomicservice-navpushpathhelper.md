# @ohos.atomicservice.NavPushPathHelper(Defines provides a push method for the target page in the routing table.)

## Child Components

Not supported

## Attributes

The [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Events

The [universal events](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Modules to Import

```TypeScript
import { NavPushPathHelper } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [NavPushPathHelper](arkts-arkui-atomicservice-navpushpathhelper-navpushpathhelper-c.md) | On the initial launch, the atomic service only downloads and installs the main package and its dependencies. Therefore, if the [NavDestination](../arkts-components/arkts-arkui-navdestination-comp.md#nav_destination) resides in a different HSP subpackage that is not a dependency of the main package, you'll need to use **NavPushPathHelper** to download and install the corresponding HSP subpackage first. After that, push the specified **NavDestination** page information onto the stack. This way, you enable [Navigation](../arkts-components/arkts-arkui-navigation-comp.md#navigation) to support dynamic loading of the HSP subpackage before the navigation occurs. |

## Examples

Main package:

```TypeScript
// Index.ets
import { NavPushPathHelper } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
@Entry
@Component
struct NavigationExample {
  pageInfo: NavPathStack = new NavPathStack();
  helper: NavPushPathHelper = new NavPushPathHelper(this.pageInfo);

  build() {
    Navigation(this.pageInfo) {
      Column() {
        Button('StartTest', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.helper.pushPath('hsptest1', { name: 'pageOne' }, false).then(() => {
              console.info(`[pushPath]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPath]failed, error code = ${error.code}, error.message = ${error.message}.`);
            }); // Push the NavDestination page specified by name to the navigation stack.
          })
      }
    }.title('NavIndex')
  }
}
```

Subpackage hsptest1:

```TypeScript
// PageOne.ets
import { NavPushPathHelper } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class NavParam {
  count: number = 10;
}

class ParamWithOp {
  operation: number = 1;
  count: number = 10;
}

@Builder
export function PageOneBuilder(name: string, param: Object) {
  PageOne();
}

@Component
export struct PageOne {
  pageInfo: NavPathStack = new NavPathStack();
  helper: NavPushPathHelper = new NavPushPathHelper(this.pageInfo);
  @State message: string = 'Hello World';

  build() {
    NavDestination() {
      Column() {
        Text(this.message)
          .width('80%')
          .height(50)
          .margin(10)

        Button('pushPath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.pushPath('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[pushPath]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}).then(() => {
              console.info(`[pushPath]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPath]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushPath with NavigationOptions', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.pushPath('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[pushPath with NavigationOptions]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}, {launchMode:0, animated:true}).then(() => {
              console.info(`[pushPath with NavigationOptions]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPath with NavigationOptions]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushPathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.pushPathByName('hsptest2', 'pageTwo', navParam, (popInfo) => {
              this.message = '[pushPathByName]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }).then(() => {
              console.info(`[pushPathByName]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPathByName]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushPathByNameWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.pushPathByName('hsptest2', 'pageTwo', navParam, true).then(() => {
              console.info(`[pushPathByNameWithoutOnPop]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushPathByNameWithoutOnPop]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushDestination', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.pushDestination('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[pushDestination]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}).then(() => {
              console.info(`[pushDestination]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushDestination]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushDestination with NavigationOptions', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.pushDestination('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[pushDestination with NavigationOptions]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}, {launchMode:0, animated:true}).then(() => {
              console.info(`[pushDestination with NavigationOptions]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushDestination with NavigationOptions]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushDestinationByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.pushDestinationByName('hsptest2', 'pageTwo', navParam, (popInfo) => {
              this.message = '[pushDestinationByName]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }).then(() => {
              console.info(`[pushDestinationByName]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[pushDestinationByName]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('pushDestinationByNameWithoutOnPop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.pushDestinationByName('hsptest2', 'pageTwo', navParam, true).then(() => {
              console.info(`[pushDestinationByNameWithoutOnPop]success.`);
            }).catch((error: BusinessError) => {
                console.error(`[pushDestinationByNameWithoutOnPop]failed, error code = ${error.code}, error.message = ${error.message}.`);
              });
          })

        Button('replacePath', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.replacePath('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[replacePath]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}).then(() => {
              console.info(`[replacePath]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[replacePath]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('replacePath with NavigationOptions', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            this.helper.replacePath('hsptest2', { name: 'pageTwo', param: new ParamWithOp(), onPop: (popInfo: PopInfo) => {
              this.message = '[replacePath with NavigationOptions]last page is: ' + popInfo.info.name + ', result: ' + JSON.stringify(popInfo.result);
            }}, {launchMode:0, animated:true}).then(() => {
              console.info(`[replacePath with NavigationOptions]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[replacePath with NavigationOptions]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

        Button('replacePathByName', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(35)
          .margin(10)
          .onClick(() => {
            let navParam = new NavParam();
            this.helper.replacePathByName('hsptest2', 'pageTwo', navParam).then(() => {
              console.info(`[replacePathByName]success.`);
            }).catch((error: BusinessError) => {
              console.error(`[replacePathByName]failed, error code = ${error.code}, error.message = ${error.message}.`);
            });
          })

      }.width('100%').height('100%')
    }.title('pageOne')
    .onBackPressed(() => {
      this.pageInfo.pop({ number: 1 }) // Pop the top element out of the navigation stack.
      return true;
    }).onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
      this.helper = new NavPushPathHelper(this.pageInfo);
    })
  }
}
```

Configure {"routerMap": "$profile:route_map"} in the project configuration file module.json5. The configuration in the route_map.json file is as follows:

```TypeScript
{
  "routerMap": [
    {
      "name": "pageOne",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

Subpackage hsptest2:

```TypeScript
// PageTwo.ets

class ResultClass {
  constructor(count: number) {
    this.count = count;
  }
  count: number = 10;
}

@Builder
export function PageTwoBuilder() {
  PageTwo();
}

@Component
export struct PageTwo {
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Button('pop', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pathStack.pop(new ResultClass(1)); // Return to the previous page and pass the processing result to the onPop callback of push.
          })
      }.width('100%').height('100%')
    }.title('pageTwo')
    .onBackPressed(() => {
      this.pathStack.pop(new ResultClass(0)); // Return to the previous page and pass the processing result to the onPop callback of push.
      return true;
    }).onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}
```

Configure {"routerMap": "$profile:route_map"} in the project configuration file module.json5. The configuration in the route_map.json file is as follows:

```TypeScript
{
  "routerMap": [
    {
      "name": "pageTwo",
      "pageSourceFile": "src/main/ets/pages/PageTwo.ets",
      "buildFunction": "PageTwoBuilder",
      "data": {
        "description": "this is pageTwo"
      }
    }
  ]
}
```
