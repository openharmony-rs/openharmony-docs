# API Switching Overview

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=79e2b0709a488b07e5881d61578e00850aa4f234 translatedAt=2026-09-17T08:19:08.536Z pushedAt=2026-09-21T11:20:26.700Z -->


Due to differences in the thread model and process model between the [FA model](ability-terminology.md#fa-model) and the [Stage model](ability-terminology.md#stage-model), some APIs can be used only in the FA model. These APIs are marked with FAModelOnly in the SDK to remind developers that they can be used only in the FA model. Therefore, when switching to the Stage model, you need to replace the FAModelOnly APIs used in your application with the corresponding APIs in the Stage model. The following is an example of switching the startAbility API. For the complete API list, see the subsequent sections:

Due to the differences in the thread model and process model, certain APIs can be used only in the [FA model](ability-terminology.md#fa-model). They are marked with **FAModelOnly** in the SDK. When switching an application from the FA model to the stage model, replace the APIs marked with **FAModelOnly** in the application with the APIs supported in the stage model. This topic uses the switching of **startAbility()** as an example.

![api-switch-overview](figures/api-switch-overview.png)

- Sample code in the FA model:

  ```ts
  import featureAbility from '@ohos.ability.featureAbility';
  import Want from '@ohos.app.ability.Want';
  import hilog from '@ohos.hilog';
  
  const TAG: string = 'PagePageAbilityFirst';
  const domain: number = 0xFF00;
  
  @Entry
  @Component
  struct PagePageAbilityFirst {
    build() {
      Column() {
        List({ initialIndex: 0 }) {
          ListItem() {
            Flex({ justifyContent: FlexAlign.SpaceBetween, alignContent: FlexAlign.Center }) {
              // ...
            }
            .onClick(() => {
              (async (): Promise<void> => {
                try {
                  hilog.info(domain, TAG, 'Begin to start ability');
                  let want: Want = {
                    bundleName: 'com.samples.famodelabilitydevelop',
                    moduleName: 'entry',
                    abilityName: 'com.samples.famodelabilitydevelop.PageAbilitySingleton'
                  };
                  await featureAbility.startAbility({ want: want });
                  hilog.info(domain, TAG, `Start ability succeed`);
                } catch (error) {
                  hilog.error(domain, TAG, 'Start ability failed with ' + error);
                }
              })()
            })
          }
        }
      }
    }
  }
  ```

- Sample code in the stage model

  ```ts
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { Want, common, Caller } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  const TAG: string = '[Page_UIAbilityComponentsInteractive]';
  const DOMAIN_NUMBER: number = 0xFF00;

  @Entry
  @Component
  struct Page_UIAbilityComponentsInteractive {
    private context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    caller: Caller | undefined = undefined;

    build() {
      Column() {
        List({ initialIndex: 0 }) {
          ListItem() {
            Row() {
            }
            .onClick(() => {
              // context is a member of the Ability object. To call it outside the Ability object, you need to
              // pass the Context object.
              let wantInfo: Want = {
                deviceId: '', // An empty deviceId indicates the local device.
                bundleName: 'com.samples.stagemodelabilitydevelop',
                moduleName: 'entry', // moduleName is optional.
                abilityName: 'FuncAbilityA',
                parameters: { // Custom information.
                  info: 'from the EntryAbility Page_UIAbilityComponentsInteractive page'
                },
              };
              // context is the UIAbilityContext of the calling UIAbility.
              this.context.startAbility(wantInfo).then(() => {
                hilog.info(DOMAIN_NUMBER, TAG, 'startAbility success.');
              }).catch((error: BusinessError) => {
                hilog.error(DOMAIN_NUMBER, TAG, 'startAbility failed.');
              });
            })
          }
        }
      }
    }
  }
  ```
