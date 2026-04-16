# Content Embed Kit术语
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @zhaotianyu-->
<!--Adviser: @jinqiuheng-->

## OE

对象编辑object editor缩写，代表OpenHarmony提供的对象编辑框架与技术，用来实现应用间文档嵌入与协同编辑。

## OE文档

通过OE技术实现的被嵌入文档，它在客户端界面中可能呈现为缩略图或者快照（Snapshot），也可能以标准格式序列化为一段二进制数据保存在内存或者某个文件中。

## OE格式文件

将遵循对象链接与嵌入标准格式的对象数据，经过序列化处理后封装为一段二进制数据流，并持久化存储在文件系统中的数据格式。

## OEID

**OE文档**的系统可识别标识符，包含在文档中。系统通过OEID定位并加载支持该OE文档的OE服务端应用，从而实现编辑功能。

## OE Extension

Content Embed Kit提供的ExtensionAbility组件，用于三方应用实现特定格式文档嵌入与编辑能力。

## OE SA

OE SA是运行于独立进程中的系统服务，作为OE能力的核心调度和管理模块，负责与系统底层能力交互，并对上层框架提供支撑，提供对应的OE ExtensionAbility的注册和管理能力。

## 客户端OE对象

客户端开发者用于封装OE文档的对象嵌入和编辑的程序对象，并且可与OE服务端进行交互。

## 服务端OE对象

服务端开发者用于封装OE文档的对象嵌入和编辑的程序对象，与客户端OE对象指向同一个OE文档，且可与客户端OE对象交互。

