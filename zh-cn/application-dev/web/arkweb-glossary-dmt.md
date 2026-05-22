# ArkWeb术语解释

## A

### AVPlayer

音视频播放器，用于播放音频和视频媒体的组件。

### AVPlayerDemo

AVPlayer演示类，用于演示AVPlayer播放器功能的示例类。

### AVPlayerListener

AVPlayer监听接口，用于监听AVPlayer播放器状态变化的回调接口。

## B

### BuilderNode

构建节点，用于动态构建UI组件的节点对象。

## C

### 沉浸式全屏

一种视频全屏播放模式，视频扩展至整个系统屏幕显示，提供沉浸式的观看体验。

## E

### enableNativeMediaPlayer

开启接管网页媒体播放接口，用于开启应用接管网页中媒体播放的功能。

### enterpictureinpicture

进入画中画事件，当HTMLVideoElement成功进入画中画模式时触发的事件。

### exitPictureInPicture

退出画中画方法，用于退出画中画模式，视频将重新在原始标签页中显示。

## H

### HTMLVideoElement

HTML视频元素，HTML中用于嵌入视频内容的元素接口。

## L

### leavepictureinpicture

退出画中画事件，当HTMLVideoElement成功退出画中画模式时触发的事件。

## M

### MediaInfo

媒体信息，包含媒体资源相关信息的对象，用于在托管网页媒体播放时传递媒体信息。

### MediaStreamConstraints

媒体流约束对象，用于说明请求的媒体类型，包含video和audio两个成员。

## N

### NativeMediaPlayer

本地媒体播放器，应用提供的用于接管网页媒体播放的本地播放器实例。

### NativeMediaPlayerBridge

本地媒体播放器桥接接口，本地播放器需要实现的接口，以便ArkWeb内核对本地播放器进行播控操作。

### NativeMediaPlayerHandler

本地媒体播放器处理器，由ArkWeb内核传递给应用的对象，用于将本地播放器的状态信息通知给ArkWeb内核。

### navigator.mediaDevices.getUserMedia

获取用户媒体设备接口，W3C标准协议接口，用于打开摄像头和麦克风。

## O

### onCreateNativeMediaPlayer

创建本地播放器回调，当网页中有媒体需要播放时触发的回调函数。

### onFullScreenEnter

进入全屏事件回调，当Web组件进入全屏模式时触发的回调函数。

### onFullScreenExit

退出全屏事件回调，当Web组件退出全屏模式时触发的回调函数。

## P

### Peer-to-Peer；点对点

一种网络连接方式，允许在无需中间媒介的情况下建立浏览器之间的直接连接。

### Picture-in-Picture；画中画

一种在浮动窗口中播放视频的功能，使用户在浏览其他网页或与其他应用交互时可继续观看视频。

### pictureInPictureElement

画中画元素，返回当前处于画中画模式的HTMLVideoElement元素，如果没有则返回null。

### pictureInPictureEnabled

画中画功能是否启用，用于检查浏览器是否支持画中画功能。

## R

### requestPictureInPicture

请求进入画中画方法，HTMLVideoElement接口提供的方法，用于请求进入画中画模式。

## S

### Surface

绘制表面，用于渲染媒体画面的绘制表面。

### SurfaceId

绘制表面ID，用于标识Surface的唯一标识符。

## V

### VideoController

视频控制器，用于控制视频播放的控制器对象。

### visibility

可见性，ArkUI提供的组件通用属性，用于控制组件的显隐状态。

## W

### WebMediaPlayer

Web媒体播放器，ArkWeb内核创建的用于播放网页中媒体资源的播放器。

### WebRTC；Web实时通信

Web Real-Time Communications，一项实时通讯技术，允许网络应用在无需中间媒介的情况下建立浏览器之间的点对点连接，实现视频流、音频流或其他数据的传输。

## X

### 显示与隐藏

组件的可见性控制，通过设置组件属性visibility的不同值，控制组件的显隐状态。
