# video
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zjsxstar-->
<!--SE: @sunbees-->
<!--TSE: @liuli0427-->


>  **说明：**
>
>  - 从API version 4开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>

视频播放组件。


## 子组件

不支持。


## 属性

除支持[通用属性](js-components-common-attributes.md)外，还支持如下属性：

| 名称       | 类型      | 默认值   | 必填   | 描述                                       |
| -------- | ------- | ----- | ---- | ---------------------------------------- |
| muted    | boolean | false | 否    | 视频是否静音播放。<br/>true：开启静音；<br/>false：关闭静音。                           |
| src      | string  | -     | 否    | 播放视频内容的路径。                               |
| autoplay | boolean | false | 否    | 视频是否自动播放。<br/>true：开启自动播放；<br/>false：关闭自动播放。                                |
| controls | boolean | true  | 否    | 控制视频播放的控制栏是否显示，如果设置为false，则不显示控制栏。默认为true，由系统决定显示或隐藏控制栏。 |


## 样式

除支持[通用样式](js-components-common-styles.md)外，还支持如下样式：

| 名称         | 类型     | 默认值     | 必填   | 描述                                       |
| ---------- | ------ | ------- | ---- | ---------------------------------------- |
| object-fit | string | contain | 否    | 视频源的缩放类型，如果poster设置了值，那么此配置还会影响视频海报的缩放类型，可选值参考表 object-fit 类型说明。 |

**表1** object-fit 类型说明

| 类型   | 描述                        |
| ---- | ------------------------- |
| fill | 不保持宽高比进行放大缩小，使得图片填充满显示边界。 |


## 事件

除支持[通用事件](js-components-common-events.md)外，还支持如下事件：

| 名称         | 参数                                       | 描述                                    |
| ---------- | ---------------------------------------- | ------------------------------------- |
| prepared   | {&nbsp;duration:&nbsp;value&nbsp;}<sup>5+</sup> | 视频准备完成时触发该事件，通过duration可以获取视频时长，单位为s。 |
| start      | -                                        | 播放时触发该事件。                             |
| pause      | -                                        | 暂停时触发该事件。                             |
| finish     | -                                        | 播放结束时触发该事件。                           |
| error      | -                                        | 播放失败时触发该事件。                           |
| seeking    | {&nbsp;currenttime:&nbsp;value&nbsp;}    | 操作进度条过程时上报时间信息，单位为s。                  |
| seeked     | {&nbsp;currenttime:&nbsp;value&nbsp;}    | 操作进度条完成后，上报播放时间信息，单位为s。               |
| timeupdate | {&nbsp;currenttime:&nbsp;value&nbsp;}    | 播放进度变化时触发该事件，单位为s，更新时间间隔为250ms。       |


## 方法

除支持[通用方法](js-components-common-methods.md)外，还支持如下方法：

| 名称             | 参数                                    | 描述                |
| -------------- | ------------------------------------- | ----------------- |
| start          | -                                     | 请求播放视频。           |
| pause          | -                                     | 请求暂停播放视频。         |
| setCurrentTime | {&nbsp;currenttime:&nbsp;value&nbsp;} | 指定视频播放的进度位置，单位为s。 |

>  **说明：**
>  在attached组件生命周期回调后，可以调用上述组件方法。

## 示例

```html
<!-- xxx.hml -->
<div class="container">
  <video id='videoId' src='/common/myDream.mp4' muted='false' autoplay='false'
         controls='true' onprepared='preparedCallback' onstart='startCallback'
         onpause='pauseCallback' onfinish='finishCallback' onerror='errorCallback'
         onseeking='seekingCallback' onseeked='seekedCallback' 
         ontimeupdate='timeupdateCallback'
         style="object-fit:fill; width:80%; height:400px;"
         onclick="change_start_pause">
   </video>
</div>
```

```css
/* xxx.css */
.container {
  justify-content: center;
  align-items: center;
}
```

```js
// xxx.js
export default {
  data: {
    event:'',
    seekingtime:'',
    timeupdatetime:'',
    seekedtime:'',
    isStart: true,
    duration: '',
  },
  preparedCallback:function(e){ this.event = '视频连接成功'; this.duration = e.duration;},
  startCallback:function(){ this.event = '视频开始播放';},
  pauseCallback:function(){ this.event = '视频暂停播放'; },
  finishCallback:function(){ this.event = '视频播放结束';},
  errorCallback:function(){ this.event = '视频播放错误';},
  seekingCallback:function(e){ this.seekingtime = e.currenttime; },
  timeupdateCallback:function(e){ this.timeupdatetime = e.currenttime;},
  change_start_pause: function() {
    if(this.isStart) {
      this.$element('videoId').pause();
      this.isStart = false;
    } else {
      this.$element('videoId').start();
      this.isStart = true; 
    }
  },
}
```

