# Starting a Local PageAbility

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @lidongrui-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=adac32ca89d9bd332aa4865feec176933267fbd9 translatedAt=2026-11-23T08:39:44.697Z pushedAt=2026-11-24T09:07:24.523Z nl=1 -->

The capabilities related to the PageAbility are provided through the **featureAbility** class. For example, **startAbility()** in **featureAbility** is used to start the PageAbility.


  **Table 1** featureAbility APIs

| API| Description|
| -------- | -------- |
| startAbility(parameter:&nbsp;StartAbilityParameter) | Starts an ability.|
| startAbilityForResult(parameter:&nbsp;StartAbilityParameter) | Starts an ability and returns the execution result when the ability is terminated.|


The following code snippet shows how to explicitly start a PageAbility through **startAbility()**. The parameters passed in for starting an ability include **want**. For details about the **want** parameter as well as implicit startup and explicit startup, see [Want](want-fa.md).

```ts
import featureAbility from '@ohos.ability.featureAbility';
import Want from '@ohos.app.ability.Want';
import hilog from '@ohos.hilog';

const TAG: string = 'PagePageAbilityFirst';
const domain: number = 0xFF00;
```
```ts
(async (): Promise<void> => {
  try {
    hilog.info(domain, TAG, 'Begin to start ability');
    let want: Want = {
      bundleName: 'com.samples.famodelabilitydevelop',
      moduleName: 'entry',
      abilityName: 'com.samples.famodelabilitydevelop.PageAbilitySingleton'
    };
    let code: number = await featureAbility.startAbility({ want: want });
    if (code === 0) {
      hilog.info(domain, TAG, `Start ability succeed`);
    } else {
      hilog.error(domain, TAG, `Start ability failed with code ${code}`);
    }
  }
  catch (error) {
    hilog.error(domain, TAG, 'Start ability failed with ' + error);
  }
})()
```
