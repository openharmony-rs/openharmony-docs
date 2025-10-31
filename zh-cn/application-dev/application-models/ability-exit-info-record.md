# 获取应用异常退出原因

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

当应用异常退出后再次启动时，开发者往往需要获取上次异常退出的具体原因和当时的应用状态信息，比如应用内存占用的rss、pss值、上次应用退出的时间等等。通过UIAbility和UIExtensionAbility的OnCreate生命周期函数中的launchParam参数，开发者可以获取到相关信息，并将其应用于应用体验的分析改进，从而调整业务逻辑、提高应用的存活率。

## 约束限制

仅[UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md)和[UIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-uiExtensionAbility.md)支持获取上次的退出原因。

## 接口说明

接口详情参见[API参考](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam)。

| **接口名**  | **描述** |
| -------- | -------- |
| [LaunchParam](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam)       | 启动参数。此接口的lastExitReason、lastExitMessage、lastExitDetailInfo成员记录Ability上次异常退出的信息。  |
| [LastExitDetailInfo](../reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#lastexitdetailinfo18)       | 从API version 18开始，支持通过该接口获取应用上次异常退出时的进程状态和详细原因。 |

## 开发步骤

1. 获取UIAbility上次退出的原因。

    在UIAbility类的OnCreate成员函数的launchParam参数中读取Ability上次退出的信息。

    <!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UnexpExit/entry/src/main/ets/exitability/ExitAbility1.ets) -->


2. 根据上次退出的信息做相应的业务处理。

    - 对于不同的退出原因，开发者可以增加不同的处理逻辑，例如：

    <!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UnexpExit/entry/src/main/ets/exitability/ExitAbility2.ets) -->

    - 根据进程信息感知应用内存占用异常，例如：

    <!-- @[quick_start1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UnexpExit/entry/src/main/ets/exitability/ExitAbility2.ets) -->


    - 根据异常退出时刻的时间戳，明确异常发生的时刻，便于问题定位。
    
    <!-- @[quick_start2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/UnexpExit/entry/src/main/ets/exitability/ExitAbility2.ets) -->
