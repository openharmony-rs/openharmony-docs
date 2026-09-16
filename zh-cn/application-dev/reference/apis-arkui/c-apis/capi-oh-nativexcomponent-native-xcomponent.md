# OH_NativeXComponent Native XComponent

## 概述

OH_NativeXComponent提供ArkUI XComponent持有的Surface和触摸事件能力。支持将EGL/OpenGLES渲染输出、媒体数据等自绘内容上屏显示，并实现Native层与ArkUI之间的触摸等事件交互。适用于游戏/图形渲染、视频播放、相机预览等需要在Native侧进行高性能绘制并与ArkUI联动交互的场景，具体使用请参考Native XComponent。

**起始版本：** 8

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md) | 声明用于访问Native XComponent的API。Native XComponent提供Surface生命周期管理、触摸事件、鼠标事件、按键事件、帧率控制、图像AI分析及无障碍接入等能力，适用于需要在ArkUI中嵌入自渲染内容（如游戏渲染、媒体播放等）的场景。 |
| [native_xcomponent_key_event.h](capi-native-xcomponent-key-event-h.md) | 声明用于访问Native XComponent按键事件所使用到的枚举类型。 |
