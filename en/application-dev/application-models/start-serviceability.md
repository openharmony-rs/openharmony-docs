# Starting a ServiceAbility
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!--deprecated_code_no_check-->
<!-- md-trans-meta sourceCommit=79e2b0709a488b07e5881d61578e00850aa4f234 translatedAt=2026-10-13T07:26:09.363Z pushedAt=2026-10-14T06:17:54.717Z -->

Starting a ServiceAbility is no different from starting other abilities. An application developer can start a ServiceAbility in a PageAbility through the **startAbility** API of **featureAbility**, and start a ServiceAbility in a ServiceAbility through the **startAbility** API of **particleAbility**. For details about the ServiceAbility startup rules, see [FA Model Component Startup Rules](component-startup-rules-fa.md).


The following example shows how to use **startAbility()** to start the ServiceAbility whose **bundleName** is **com.example.myapplication** and **abilityName** is **ServiceAbility** in a PageAbility. When starting the ServiceAbility of the [FA model](ability-terminology.md#fa-model), concatenate the **bundleName** string before **abilityName**.

```ts
import featureAbility from '@ohos.ability.featureAbility';
import Want from '@ohos.app.ability.Want';
import promptAction from '@ohos.promptAction';
import hilog from '@ohos.hilog';

const TAG: string = 'PageServiceAbility';
const domain: number = 0xFF00;

@Entry
@Component
struct PageServiceAbility {
  async startServiceAbility(): Promise<void> {
    try {
      hilog.info(domain, TAG, 'Begin to start ability');
      let want: Want = {
        bundleName: 'com.samples.famodelabilitydevelop',
        abilityName: 'com.samples.famodelabilitydevelop.ServiceAbility'
      };
      await featureAbility.startAbility({ want });
      promptAction.showToast({
        message: 'start_service_success_toast'
      });
      hilog.info(domain, TAG, `Start ability succeed`);
    } catch (error) {
      hilog.error(domain, TAG, 'Start ability failed with ' + error);
    }
  }
  build() {
    // ...
  }
}
```


After the preceding code is executed, the ability starts the ServiceAbility through the [`startAbility()`](../reference/apis-ability-kit/js-apis-ability-featureAbility.md#featureabilitystartability) method.


- If the ServiceAbility is not running, the system calls **onStart()** to initialize the ServiceAbility, and then calls **onCommand()** on the ServiceAbility.

- If the ServiceAbility is running, the system directly calls **onCommand()** on the ServiceAbility.
