# IsolatedComponent属性/事件

```TypeScript
declare class IsolatedComponentAttribute extends CommonMethod<IsolatedComponentAttribute>
```

仅支持[width](arkts-arkui-common-comp-commonmethod-c.md#width)、[height](arkts-arkui-common-comp-commonmethod-c.md#height)和[backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor)通用属性。

不支持通用事件。

事件经过坐标转换后异步传递给受限Worker线程处理。不支持线程之间的事件冒泡，线程之间的UI交互存在事件冲突现象。

**继承/实现关系：** IsolatedComponentAttribute extends CommonMethod&lt;IsolatedComponentAttribute&gt;

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
