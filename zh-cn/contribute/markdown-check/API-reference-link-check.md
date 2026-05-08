# API参考链接跳转锚点准确

## 链接检测范围

application-dev中，检测所有链接到reference（API参考）中的链接

## 检查总体逻辑

`[链接名称](链接地址)`

### 检测通过匹配链接名称是否在对应链接对应的标题中

```markdown
[BuilderNode内的BuilderProxyNode导致树结构发生变化](../../ui/arkts-user-defined-arktsNode-builderNode.md#buildernode内的builderproxynode导致树结构发生变化)

## BuilderNode内的BuilderProxyNode导致树结构发生变化
​
```

```markdown
[getUniqueId](../reference/apis-arkui/js-apis-arkui-frameNode.md#getuniqueid12)


### getUniqueId<sup>12+</sup>
​
```

### 如果链接名称不在链接地址中，则反向匹配链接地址对应的标题是否在链接名称中

```markdown
当id是string时，对应[通用属性id](arkui-ts/ts-universal-attributes-component-id.md#id)所指定的组件
​
```

### 如果链接名称与链接地址对应标题正反向匹配都不满足，则检查链接下表格中是否存在链接名称

> **说明：**
> 
> 匹配名称列与 typedef 关键字列

```markdown
Context支持获取当前应用的进程名[processName](js-apis-inner-application-context.md#属性)

### 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称   | 类型     | 只读   | 可选   | 说明   |
|---------------------| ------ | ---- | ---- |----------|
| processName<sup>18+</sup> | string | 否   | 否 | 当前应用的进程名。<br/>**原子化服务API**：从API version 18开始，该接口支持在原子化服务中使用。 |
​
```

### 获取标题下第一行中内容，与链接名称匹配

```markdown
[startBackgroundRunning(context: Context, bgModes: string[], wantAgent: WantAgent): Promise&lt;ContinuousTaskNotification&gt;](#backgroundtaskmanagerstartbackgroundrunning12)

## backgroundTaskManager.startBackgroundRunning<sup>12+</sup>

startBackgroundRunning(context: Context, bgModes: string[], wantAgent: WantAgent): Promise&lt;ContinuousTaskNotification&gt;

​
```

### 如果链接地址为文档，则匹配文档的一级标题

通过

```markdown
[Context](../../reference/apis-ability-kit/js-apis-inner-application-context.md)

# Context (Stage模型的上下文基类)
​
```

## 链接名称及锚点标题预处理规则

### 链接名称中存在`.` 的时候，取最后一个`.`后的内容

```markdown
[fileIo.Stat.isBlockDevice](js-apis-file-fs.md#isblockdevice)

### isBlockDevice
​
```

### 去除所有的删除替换标题

```markdown
[<!--DelEnd-->卡片组件<!--Del-->](../reference/apis-arkui/arkui-ts/ts-basic-components-formcomponent-sys.md)
​
```

### 存在`()` 或者 `#` 则删除

```markdown
AbilityStage拥有[onCreate()](../reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#oncreate)

### onCreate
​
```

### 存在上标，则去除上标

```markdown
[Query<sup>8+</sup>](#query8)

## Query<sup>8+</sup>
​
```

### 存在转义符或者源码，则统一转换为实际显示样式

`当前仅适配 空格  &nbsp;   左右尖括号 &lt;  &gt;`

```
[getTopWindow(callback:&nbsp;AsyncCallback&lt;Window&gt;):&nbsp;void;](../reference/apis-arkui/arkts-apis-window-f.md#windowgettopwindowdeprecated)

[getUnifiedData(): Promise\<unifiedDataChannel.UnifiedData\>](../../reference/apis-basic-services-kit/js-apis-pasteboard.md#getunifieddata12)
​
```

## 大文件拆分情况

### 如果链接的是大文件的第一个文档，判断文件名称是否是 `模块描述`或`组件描述`，则在Readme中检查模块名称

```markdown
[相机管理](../apis-camera-kit/arkts-apis-camera.md)

arkts-apis-camera.md
# 模块描述

Readme

- @ohos.multimedia.camera (相机管理)<!--js-apis-camera-->
  - [模块描述](arkts-apis-camera.md)
  - [Functions](arkts-apis-camera-f.md)
  - [Interface (AutoDeviceSwitch)](arkts-apis-camera-AutoDeviceSwitch.md)
​
```

## 白名单机制

### 机制原理

docs仓中存放白名单文件。

读取文档相对路径以及链接信息，在白名单中则跳过不检测

### 白名单路径

zh-cn/contribute/allowed-link.md

<!--no_check-->