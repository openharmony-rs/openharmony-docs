# ArkTS卡片页面交互概述
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->

ArkTS卡片提供页面交互能力，包括卡片与卡片提供方（例如：应用）的页面跳转、卡片拉起卡片提供方进程、卡片与卡片提供方的消息传递。其中动态卡片可以使用postCardAction接口、静态卡片使用FormLink实现页面交互功能。并且postCardAction和FormLink，均支持router、message和call三种类型的事件，具体使用场景如下：

- router事件：可以使用router事件跳转到指定UIAbility，以完成点击卡片跳转至应用内页面的功能。对于非系统应用仅支持跳转到自己应用内的UIAbility。
- call事件：可以使用call事件拉起指定UIAbility到后台，再通过UIAbility申请对应后台长时任务完成音乐播放等功能。
- message事件：可以使用message拉起FormExtensionAbility，通过onFormEvent接口回调通知，以完成点击卡片控件后传递消息给应用的功能。
