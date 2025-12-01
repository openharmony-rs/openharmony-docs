# 系统服务管理子系统划词框架模块Changelog

## cl.selectionfwk.1 划词通知接口返回的SelectionInfo中，删除text属性

**访问级别**

系统接口

**变更原因**

划词服务在判断到用户选择文本时，返回的[SelectionInfo](../../../application-dev/reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager-sys.md#selectioninfo)中不再包含text属性；同时新增[getSelectionContent](../../../application-dev/reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager-sys.md#getselectioncontent)方法，用于获取当前选中的文本内容，从而实现划词通知与获取文本内容的解耦。

**变更影响**

该变更涉及应用适配。

划词通知与获取文本内容的解耦将使得开发者在使用划词服务时，能够更加灵活地处理监听到划词事件后的行为。同时，由于不再返回text属性，可能会影响到依赖该属性的现有代码逻辑，开发者需要根据新的接口规范进行相应的调整。

**起始 API Level**

22

**变更发生版本**

从OpenHarmony SDK 6.0.0.51版本开始。

**变更的接口/组件**
| 类名           | 删除属性                                                 |
| -------------- | ------------------------------------------------------------ |
| SelectionInfo | text: string |

**适配指导**

开发者需要根据新的接口规范，调整现有代码逻辑，在监听到划词事件后，通过新增的[getSelectionContent](../../../application-dev/reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager-sys.md#getselectioncontent)方法获取当前选中的文本内容。

```ts
selectionManager.on('selectionCompleted', async (info: selectionManagerSelectionInfo) => {
  try {
    let content = await selectionManager.getSelectionContent();
  } catch (err) {
    console.error(`Failed to get selection content: ${JSON.stringify(err)}`);
  }
});
```
