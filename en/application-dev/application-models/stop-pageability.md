# Stopping a PageAbility

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @lidongrui-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=79e2b0709a488b07e5881d61578e00850aa4f234 translatedAt=2026-11-23T08:41:01.742Z pushedAt=2026-11-24T09:07:52.945Z nl=1 -->

The **terminateSelf()** method in the **featureAbility** class is used to stop a PageAbility.


  **Table 1** featureAbility APIs

| API| Description|
| -------- | -------- |
| terminateSelf() | Terminates this ability.|
| terminateSelfWithResult(parameter:&nbsp;AbilityResult) | Terminates this ability and returns the execution result.|


The following code snippet shows how to stop an ability.

```ts
import featureAbility from '@ohos.ability.featureAbility';
import hilog from '@ohos.hilog';

const TAG: string = 'PagePageAbilityFirst';
const domain: number = 0xFF00;
```
```ts
// ...
(async (): Promise<void> => {
  try {
    hilog.info(domain, TAG, 'Begin to terminateSelf');
    await featureAbility.terminateSelf();
    hilog.info(domain, TAG, 'terminateSelf succeed');
  } catch (error) {
    hilog.error(domain, TAG, 'terminateSelf failed with ' + error);
  }
})()
// ...
```
