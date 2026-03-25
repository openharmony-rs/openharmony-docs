# Content Embed Kit术语
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @zhaotianyu-->
<!--Adviser: @jinqiuheng-->

## OE

对象编辑object editor缩写，代表OpenHarmony提供的对象编辑框架与技术，用来实现应用间文档嵌入与协同编辑。

## OE对象

开发者用于实现对象嵌入和编辑的程序对象，通常表示某个**OE Extension**在客户端的代理实例，用于与服务端交互。

## OE文档

通过OE技术实现的被嵌入文档，它在客户端界面中可能呈现为缩略图或者快照（Snapshot），也可能以标准格式序列化为一段二进制数据保存在内存或者某个文件中。

## OEID

**OE文档**的系统可识别标识符，包含在文档中。系统通过OEID定位并加载支持该OE文档的OE服务端应用，从而实现编辑功能。

## OE Extension

Content Embed Kit提供的ExtensionAbility组件，用于三方应用实现特定格式文档嵌入与编辑能力。

## OE SA

OE SA是运行于独立进程中的系统服务，作为OE能力的核心调度和管理模块，负责与系统底层能力交互，并对上层框架提供支撑。

