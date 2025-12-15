# Component Startup Rules (Stage Model)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

Component startup refers to the behavior of starting or connecting to an application component.


- Start the [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md), ServiceExtensionAbility, and DataShareExtensionAbility components. For example, you can use [startAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability), **startServiceExtensionAbility()**, [startAbilityByCall()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall), and [openLink()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12).

- Connect to the ServiceExtensionAbility and DataShareExtensionAbility components. For example, you can use [connectServiceExtensionAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#connectserviceextensionability) and **createDataShareHelper()**.

## General Component Startup Rules

To deliver a better user experience, the system restricts the following behavior:


- A background application randomly displays a dialog box, such as an ads pop-up.

- Background applications wake up each other. This type of behavior occupies system resources and increases power consumption, or even causes system frozen.

- A foreground application randomly redirects to another application, for example, redirecting to the payment page of another application. This type of behavior poses security risks.


In view of this, the system formulates a set of component startup rules, as follows:

- Before starting a component of another application, check whether the component can be called by others.

  If the **exported** field of the component is set to **true**, the component can be called by other applications. If the field is set to **false**, the component cannot be called by other applications. If this is the case, you must also verify the permission **ohos.permission.START_INVISIBLE_ABILITY**, which is available only for system applications. For details about the **exported** fields, see [abilities](../quick-start/module-configuration-file.md#abilities).

- Before starting a UIAbility component of a background application, verify the permission **ohos.permission.START_ABILITIES_FROM_BACKGROUND**, which is available only for system applications.

  > **NOTE**
  > 
  > - An application is considered as a foreground application only when the application process gains focus or its UIAbility component is running in the foreground.
  > - For 2-in-1 devices and tablets:
  >   - Starting from API version 18, if an application has a floating window in the foreground, it can start other abilities without checking the BACKGROUND permission after the application moves to the background.
  >   - Starting from API version 21 onwards, if an application is already in the status bar, it can start its own UIAbility without checking the BACKGROUND permission after the application moves to the background.
 
- Before using **startAbilityByCall()** to start a component running on another device, verify the permission **ohos.permission.DISTRIBUTED_DATASYNC**.

The component startup rules described above apply from API version 9 onwards. The specific version when new rules come into effect is noted separately within the rules. Familiarity with these rules helps you prevent service exceptions.  



## Intra-Device Component Startup Rules

  The rules for starting components on the same device vary in the following scenarios:

- Starting the UIAbility component

- Starting the ServiceExtensionAbility and DataShareExtensionAbility components

- Using [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) to start the UIAbility component

> **NOTE**
> 
> The BACKGROUND and CALL permissions in the following figure refer to ohos.permission.START_ABILITIES_FROM_BACKGROUND and ohos.permission.ABILITY_BACKGROUND_COMMUNICATION, respectively.

![startup-rule](figures/component-startup-inner-stage.png)


## Inter-Device Component Startup Rules

  The rules for starting components on a different device vary in the following scenarios:

- Starting the UIAbility component

- Starting the ServiceExtensionAbility and DataShareExtensionAbility components

- Using [startAbilityByCall](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startabilitybycall) to start the UIAbility component

> **NOTE**
> 
> The BACKGROUND and DATASYNC permissions in the following figure refer to ohos.permission.START_ABILITIES_FROM_BACKGROUND and ohos.permission.DISTRIBUTED_DATASYNC, respectively.

![component-startup-rules](figures/component-startup-inter-stage.png)
