# 设置预上屏文本样式
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

预上屏文本是输入法正在编辑、尚未确认的内容。例如输入拼音时，输入法可以先在编辑框中显示正在组合的拼音，并用下划线标出可继续修改的范围。结束预上屏时，编辑框保留文字并清除下划线。

从API版本26.1.0开始，输入法可以在设置预上屏文本时指定无下划线、实线、波浪线或虚线，并选择下划线颜色。系统编辑框由对应组件处理样式，自绘编辑框需要接收样式信息并自行绘制。

自绘编辑框接收样式的开发步骤，参见[在自绘编辑框中接收预上屏样式（ArkTS）](preview-text-style-guide-arkts.md)或[在自绘编辑框中接收预上屏样式（C/C++）](preview-text-style-guide-ndk.md)。

## 约束与限制

- 当前编辑框须支持预上屏。输入法可调用`getEditorAttribute()`获取[EditorAttribute](../reference/apis-ime-kit/js-apis-inputmethodengine.md#editorattribute)，通过`isTextPreviewSupported`判断。`true`表示支持，`false`表示不支持。
- 设置预上屏文本及样式时，当前编辑框须已获焦并与输入法绑定。
- 以系统编辑组件TextInput为例，[enablePreviewText](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md#enablepreviewtext12)默认开启预上屏。若已关闭，可将该属性设为true。

## 输入法发送预上屏文本

发送前，先启用输入法，并确认当前编辑框已获焦并与输入法绑定。

1. 在DevEco Studio打开下方示例代码所在的PreviewTextStyleJS工程并安装到设备。首次运行前，需启用并切换到本示例的输入法。在设备已开启开发者模式并连接HDC后，依次执行以下命令。

   ```shell
   # 启用本示例的输入法
   hdc shell ime -e com.samples.previewstylejs -f
   # 将当前输入法切换为本示例的输入法
   hdc shell ime -s com.samples.previewstylejs
   # 查询当前输入法，确认包名为com.samples.previewstylejs
   hdc shell ime -g
   ```

   `-f`用于完整体验模式，运行设备需支持该模式。确认当前输入法为com.samples.previewstylejs后，继续以下步骤。

2. 返回默认的编辑框页面，点击“绑定编辑器”。输入法通过[on('inputStart')](../reference/apis-ime-kit/js-apis-inputmethodengine.md#oninputstart9)监听绑定成功事件，并取得当前[InputClient](../reference/apis-ime-kit/js-apis-inputmethodengine.md#inputclient9)。输入法扩展从`app.string.preview_text`读取示例文本，交由`PreviewSender`保存。previewSender为同工程PreviewSender模块导出的实例。

   <!-- @[preview_style_js_input_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/ets/keyboard/PreviewInputMethod.ets) -->
   
   ``` TypeScript
   onCreate(): void {
     previewSender.setPreviewText(this.context.resourceManager.getStringSync($r('app.string.preview_text').id));
     this.active = true;
     this.ability.on('inputStart', (_keyboard: inputMethodEngine.KeyboardController,
       client: inputMethodEngine.InputClient): void => {
       previewSender.setClient(client);
     });
     this.ability.on('inputStop', this.inputStopCallback);
     this.createKeyboard();
   }
   ```

3. 点击“发送预上屏”，调用[setPreviewTextWithStyle](../reference/apis-ime-kit/js-apis-inputmethodengine.md#setpreviewtextwithstyle)，在当前预上屏范围显示红色波浪线。

   [PreviewTextStyle](../reference/apis-ime-kit/js-apis-inputmethodengine.md#previewtextstyle)的`underlineStyle`指定下划线样式。`underlineColor`为可选颜色值，颜色格式为0xRRGGBB。透明度通道无效，由编辑框忽略。省略时默认跟随光标颜色，显式传入0表示黑色。

   方法先检查输入连接和发送状态，再构造范围与样式并异步发送。发送期间busy用于阻止重复操作，finally中恢复该状态；调用失败时显示错误码。

   <!-- @[preview_style_js_send](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/ets/keyboard/PreviewSender.ets) -->

   ```typescript
   async send(): Promise<void> {
     const client = this.client;
     if (client === undefined || this.busy) {
       this.status(this.busy ? $r('app.string.operation_busy') : $r('app.string.bind_editor_first'));
       return;
     }
     this.busy = true;
     const range: inputMethodEngine.Range = { start: -1, end: -1 };
     const style: inputMethodEngine.PreviewTextStyle = {
       underlineStyle: inputMethodEngine.UnderlineStyle.WAVY,
       underlineColor: 0x00FF0000
     };
     // 省略underlineColor使用编辑框主题色；显式传入0表示黑色。
     try {
       await client.setPreviewTextWithStyle(this.previewText, range, style);
       this.status($r('app.string.preview_displayed'));
     } catch (error) {
       const detail = error as BusinessError;
       this.status($r('app.string.preview_send_failed', detail.code));
     } finally {
       this.busy = false;
     }
   }
   ```

4. 需要同步发送时，调用[setPreviewTextWithStyleSync](../reference/apis-ime-kit/js-apis-inputmethodengine.md#setpreviewtextwithstylesync)设置预上屏文本和样式。

   同步方法使用相同的范围和样式，通过try/catch处理调用失败。此方法用于说明同步接口的调用方式，示例页面仍使用前面的异步方法。

   <!-- @[preview_style_js_send_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/ets/keyboard/PreviewSender.ets) -->

   ```typescript
   // 同步调用的等价写法。页面使用上面的异步方法。
   sendSync(): void {
     const client = this.client;
     if (client === undefined || this.busy) {
       this.status(this.busy ? $r('app.string.operation_busy') : $r('app.string.bind_editor_first'));
       return;
     }
     const range: inputMethodEngine.Range = { start: -1, end: -1 };
     const style: inputMethodEngine.PreviewTextStyle = {
       underlineStyle: inputMethodEngine.UnderlineStyle.WAVY,
       underlineColor: 0x00FF0000
     };
     try {
       client.setPreviewTextWithStyleSync(this.previewText, range, style);
       this.status($r('app.string.preview_displayed'));
     } catch (error) {
       const detail = error as BusinessError;
       this.status($r('app.string.preview_send_failed', detail.code));
     }
   }
   ```

5. 点击“结束预上屏”，调用[finishTextPreview](../reference/apis-ime-kit/js-apis-inputmethodengine.md#finishtextpreview12)。编辑框保留正文并清除下划线。

   方法先检查输入连接和操作状态，再结束预上屏；成功或失败时分别更新提示，finally中恢复busy状态。

   <!-- @[preview_style_js_finish](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/InputMethod/PreviewTextStyleJS/entry/src/main/ets/keyboard/PreviewSender.ets) -->

   ```typescript
   async finish(): Promise<void> {
     const client = this.client;
     if (client === undefined || this.busy) {
       this.status(this.busy ? $r('app.string.operation_busy') : $r('app.string.bind_editor_first'));
       return;
     }
     this.busy = true;
     try {
       await client.finishTextPreview();
       this.status($r('app.string.preview_finished'));
     } catch (error) {
       const detail = error as BusinessError;
       this.status($r('app.string.preview_finish_failed', detail.code));
     } finally {
       this.busy = false;
     }
   }
   ```
