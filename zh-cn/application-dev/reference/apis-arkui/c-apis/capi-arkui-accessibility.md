# ArkUI_Accessibility

## 概述

本模块描述ArkUI Accessibility对外支持的Native能力，支持查询无障碍节点、上报无障碍事件等。适用于第三方平台需要将自身UI组件接入ArkUI无障碍体系、与系统无障碍能力进行交互的场景，便于开发者构建无障碍辅助能力，提升应用的无障碍体验。

**起始版本：** 13

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_interface_accessibility.h](capi-native-interface-accessibility-h.md) | 声明用于访问Native Accessibility的API，提供无障碍相关能力。支持第三方平台将自身UI组件接入ArkUI无障碍服务体系，包括注册无障碍回调、设置和查询无障碍节点信息、主动上报无障碍事件以及适配多实例场景等，使系统无障碍服务能够识别并操作第三方平台的UI组件，适用于第三方UI框架需要与系统无障碍能力进行交互的场景。 |
