# 划词服务术语

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @no86-->
<!--Designer: @mmwwbb-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->

## S

- ### Selected Application；被划词应用

    用户选中文本时所处的源应用。划词服务通过系统复制机制从中提取选中文本，无需该应用额外适配；不支持系统级复制的应用（如受控WebView、沙箱环境应用）则无法配合该功能。

- ### Selection Application；划词应用

    实现了划词扩展能力的应用。该类应用被划词服务拉起后，可监听划词完成事件以获取用户选中文本，进而执行翻译、摘要、扩写等后续业务逻辑。

- ### Selection ExtensionAbility；划词扩展能力

    一种ExtensionAbility组件类型。它允许应用在用户选词后获取选中文本，并管理划词面板的生命周期，从而方便实现翻译、摘要、扩写等业务逻辑。