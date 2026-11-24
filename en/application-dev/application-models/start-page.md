# Starting a Specified Page

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @lidongrui-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=44da4106816f0fa51f767760459fa4941200eb6f translatedAt=2026-11-23T08:40:06.355Z pushedAt=2026-11-24T09:07:30.501Z nl=1 -->

<!--deprecated_code_no_check-->

When the launch mode of a PageAbility is set to singleton (for specific setting methods and typical scenario examples, see [PageAbility launch mode](pageability-launch-type.md); the default is the singleton instance mode), if the PageAbility has already been launched, starting the PageAbility again triggers the onNewWant callback (that is, it is not launched for the first time). The developer can pass startup parameters through Want. For example, if the developer wants to start the PageAbility from a specified page, the pages information can be passed through the parameters parameter in Want. The example code is as follows:


In the app.ets or page of the caller PageAbility, use startAbility to launch the PageAbility again, and pass the page information through the uri parameter in Want:

```ts
import featureAbility from '@ohos.ability.featureAbility';
import Want from '@ohos.app.ability.Want';
import hilog from '@ohos.hilog';

const TAG: string = 'PagePageAbilityFirst';
const domain: number = 0xFF00;
```
```ts
(async (): Promise<void> => {
  let wantInfo: Want = {
    bundleName: 'com.samples.famodelabilitydevelop',
    abilityName: 'com.samples.famodelabilitydevelop.PageAbilitySingleton',
    parameters: { page: 'pages/second' }
  };
  featureAbility.startAbility({ want: wantInfo }).then((data) => {
    hilog.info(domain, TAG, `restartAbility success : ${data}`);
  });
})()
```


Obtain the **want** parameter that contains the page information from the **onNewWant()** callback of the target PageAbility.

```ts
// Construct a singleton object in GlobalContext.ts.
export class GlobalContext {
  private constructor() {
  }

  private static instance: GlobalContext;
  private _objects = new Map<string, Object>();

  public static getContext(): GlobalContext {
    if (!GlobalContext.instance) {
      GlobalContext.instance = new GlobalContext();
    }
    return GlobalContext.instance;
  }

  getObject(value: string): Object | undefined {
    return this._objects.get(value);
  }

  setObject(key: string, objectClass: Object): void {
    this._objects.set(key, objectClass);
  }
}
```

```ts
import Want from '@ohos.app.ability.Want';
import featureAbility from '@ohos.ability.featureAbility';
import { GlobalContext } from '../utils/GlobalContext';

class PageAbilitySingleton {
  onNewWant(want: Want) {
    featureAbility.getWant().then((want) => {
      GlobalContext.getContext().setObject('newWant', want);
    })
  }
}

export default new PageAbilitySingleton();
```


Obtain the **want** parameter that contains the page information from the custom component of the target PageAbility and process the route based on the URI.

```ts
import Want from '@ohos.app.ability.Want';
import router from '@ohos.router';
import { GlobalContext } from '../../utils/GlobalContext';

@Entry
@Component
struct First {
  onPageShow() {
    let newWant = GlobalContext.getContext().getObject('newWant') as Want;
    if (newWant) {
      if (newWant.parameters) {
        if (newWant.parameters.page) {
          router.pushUrl({ url: newWant.parameters.page as string});
          GlobalContext.getContext().setObject("newWant", undefined)
        }
      }
    }
  }

  build() {
    Column() {
      Row() {
        Text('singleton_first_title')
          .fontSize(24)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Start)
          .margin({ top: 12, bottom: 11, right: 24, left: 24 })
      }
      .width('100%')
      .height(56)
      .justifyContent(FlexAlign.Start)

      Image('pic_empty')
        .width(120)
        .height(120)
        .margin({ top: 224 })

      Text('no_content')
        .fontSize(14)
        .margin({ top: 8, bottom: 317, right: 152, left: 152 })
        .fontColor('text_color')
        .opacity(0.4)
    }
    .width('100%')
    .height('100%')
    .backgroundColor('backGrounding')
  }
}
```


When the launch mode of a PageAbility is set to multi-instance mode, or when a singleton-mode PageAbility is started for the first time (for specific setting methods and typical scenario examples, see [PageAbility launch mode](pageability-launch-type.md)), in the caller PageAbility, the pages information of the specified page to be started is passed through the parameters parameter in Want, and the startAbility() method is called to start the PageAbility. The called end can use the getWant method of featureAbility in onCreate to obtain the Want, and then call router.pushUrl to start the specified page.


In the page of the caller, a button click is implemented to trigger the startAbility method to start the target-end PageAbility. The Want input parameter of the startAbility method carries the specified page information. The example code is as follows:

```ts
import featureAbility from '@ohos.ability.featureAbility';
import Want from '@ohos.app.ability.Want';
import { BusinessError } from '@ohos.base';
import fs from '@ohos.file.fs';
import promptAction from '@ohos.promptAction';
import worker from '@ohos.worker';
import hilog from '@ohos.hilog';

const TAG: string = 'PagePageAbilityFirst';
const domain: number = 0xFF00;

@Entry
@Component
struct PagePageAbilityFirst {
  build() {
    Column() {
      // ...
      List({ initialIndex: 0 }) {
        // ...
        ListItem() {
          Flex({ justifyContent: FlexAlign.SpaceBetween, alignContent: FlexAlign.Center }) {
          // ...
          }
          .onClick(() => {
            let want: Want = {
              bundleName: 'com.samples.famodelabilitydevelop',
              abilityName: 'com.samples.famodelabilitydevelop.PageAbilityStandard',
              parameters: { page: 'pages/first' }
            };
            featureAbility.startAbility({ want: want }).then((data) => {
              hilog.info(domain, TAG, `startAbility finish:${data}`);
            }).catch((err: BusinessError) => {
              hilog.error(domain, TAG, `startAbility failed errcode:${err.code}`);
            })
          })
        }
        // ...
        ListItem() {
          Flex({ justifyContent: FlexAlign.SpaceBetween, alignContent: FlexAlign.Center }) {
          // ...
          }
          .onClick(() => {
            let want: Want = {
              bundleName: 'com.samples.famodelabilitydevelop',
              abilityName: 'com.samples.famodelabilitydevelop.PageAbilityStandard',
              parameters: { page: 'pages/second' }
            };
            featureAbility.startAbility({ want: want }).then((data) => {
              hilog.info(domain, TAG, `startAbility finish:${data}`);
            }).catch((err: BusinessError) => {
              hilog.error(domain, TAG, `startAbility failed errcode:${err.code}`);
            })
          })
        }
        // ...
      }
      // ...
    }
    // ...
  }
}
```


In the onCreate lifecycle callback of the target-end PageAbility, the getWant method of featureAbility is used to obtain the Want, and the parameters are parsed to launch the specified page:

```ts
import featureAbility from '@ohos.ability.featureAbility';
import router from '@ohos.router';

class PageAbilityStandard {
  onCreate() {
    featureAbility.getWant().then((want) => {
      if (want.parameters) {
        if (want.parameters.page) {
          router.pushUrl({ url: want.parameters.page as string });
        }
      }
    })
  }
}

export default new PageAbilityStandard();
```
