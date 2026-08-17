# global

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [canIUse](arkts-arkui-global-caniuse-f.md#caniuse) | 查询系统是否具备某个系统能力。 |
| [clearInterval](arkts-arkui-global-clearinterval-f.md#clearinterval) | 取消通过setInterval()设置的重复定时任务。 定时器对象保存在创建它的线程内，删除定时器时需要在该线程中进行。 |
| [clearTimeout](arkts-arkui-global-cleartimeout-f.md#cleartimeout) | 取消通过调用setTimeout()建立的定时器。 定时器对象保存在创建它的线程内，删除定时器时需要在该线程中进行。 |
| [getInspectorByKey](arkts-arkui-global-getinspectorbykey-f.md#getinspectorbykey) | 根据id获取组件的所有属性。 |
| [getInspectorTree](arkts-arkui-global-getinspectortree-f.md#getinspectortree) | 获取当前组件树。 |
| [loadNativeModule](arkts-arkui-global-loadnativemodule-f.md#loadnativemodule) | 同步动态加载native模块，目的是按需加载所需要的模块。 使用该接口会增加so文件的加载时间，使用前需评估其对应用性能和功能的影响。 |
| [sendEventByKey](arkts-arkui-global-sendeventbykey-f.md#sendeventbykey) | Sends an event to the component with the specified ID. |
| [sendKeyEvent](arkts-arkui-global-sendkeyevent-f.md#sendkeyevent) | Send key event. |
| [sendMouseEvent](arkts-arkui-global-sendmouseevent-f.md#sendmouseevent) | Send mouse event. |
| [sendTouchEvent](arkts-arkui-global-sendtouchevent-f.md#sendtouchevent) | Send touch event. |
| [setInterval](arkts-arkui-global-setinterval-f.md#setinterval) | 重复调用一个函数，在每次调用之间具有固定的时间延迟。 删除该定时器需手动调用clearInterval()接口。 |
| [setTimeout](arkts-arkui-global-settimeout-f.md#settimeout) | 设置一个定时器，该定时器在定时器到期后执行一个函数。 该定时器在回调被执行后自动删除，或使用clearTimeout()接口手动删除。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [markModuleCollectable](arkts-arkui-global-markmodulecollectable-f-sys.md#markmodulecollectable) | Mark moduleNamespace which loaded by dynamic-import is collectable. |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [console](arkts-arkui-global-console-c.md) | 提供一个简单的调试控制台，类似于浏览器提供的JavaScript控制台机制。 |

