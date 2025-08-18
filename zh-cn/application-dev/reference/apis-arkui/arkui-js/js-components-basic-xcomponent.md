# xcomponent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zjsxstar-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @HelloCrease-->

  > **说明：**
  > 该组件从API Version 8 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

  用于显示写入了EGL/OpenGLES或媒体数据的组件。

## 权限列表

  无

## 子组件

  不支持。

## 属性

除支持[通用属性](js-components-common-attributes.md)外，还支持如下属性：

| 名称          | 参数类型   | 必填   | 描述                                       |
| ----------- | ------ | ---- | ---------------------------------------- |
| id          | string | 是    | 组件的唯一标识，支持最大的字符串长度128。                   |
| type        | string | 是    | 用于指定xcomponent组件类型，可选值为：<br/>- surface：组件内容单独送显，直接合成到屏幕。<br/>- component：组件内容与其他组件合成后统一送显。<br/> |
| libraryname | string | 否    | 应用Native层编译输出动态库名称。                      |

## 样式

支持[通用样式](js-components-common-styles.md)。

## 事件

除支持[通用事件](js-components-common-events.md)外，还支持如下事件：

| 名称                               | 功能描述                                     |
| -------------------------------- | ---------------------------------------- |
| onLoad(context?: object) => void | 插件加载完成时回调事件。<br/>context：开发者扩展的xcomponent方法的实例对象，context对象的接口由开发者自定义。 |
| onDestroy() => void              | 插件卸载完成时回调事件。                             |

## 方法

除支持[通用方法](js-components-common-methods.md)外，还支持如下方法：

| 名称                       | 参数                                       | 返回值类型  | 描述                                       |
| ------------------------ | ---------------------------------------- | ------ | ---------------------------------------- |
| getXComponentSurfaceId   | -                                        | string | 获取xcomponent对应Surface的ID，供@ohos接口使用，比如camera相关接口。 |
| setXComponentSurfaceSize | {<br/>surfaceWidth: number,<br/>surfaceHeight: number  <br/>} | -      | 设置xcomponent持有Surface的宽度和高度。             |
| getXComponentContext     | -                                        | object | 获取开发者扩展的xcomponent方法的实例对象。               |

## 示例

提供surface类型xcomponent，支持相机预览等能力。

   ```html
<!-- xxx.hml -->
<div style="height: 500px; width: 500px; flex-direction: column; justify-content: center; align-items: center;">
	<text id = 'camera' class = 'title'>camera_display</text>
	<xcomponent id = 'xcomponent' type = 'surface' onload = 'onload' ondestroy = 'ondestroy'></xcomponent>
</div>
   ```

   ```js
// xxx.js
import camera from '@ohos.multimedia.camera';
export default {
    onload() {
        var surfaceId = this.$element('xcomponent').getXComponentSurfaceId();
        camera.createPreviewOutput(surfaceId).then((previewOutput) => {
            console.log('Promise returned with the PreviewOutput instance');
        })
    }
}
   ```