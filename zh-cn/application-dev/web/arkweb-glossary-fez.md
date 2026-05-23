# ArkWeb术语解释

## A

### about:blank

空白页面，用于在离线Web组件不再被使用时加载，为下次复用做准备。

### aboutToResize

当布局大小发生变化时进行回调。

### Active

活跃状态，开启渲染引擎的状态。

## B

### Blank page

空白页面，用于在离线Web组件不再被使用时加载，为下次复用做准备。

## C

### createNWeb

创建离线Web组件接口，用于初始化自定义Web组件。

## D

### dispose

释放/销毁方法，用于销毁BuilderNode节点。

### 动态组件

Dynamic Component，通过NodeController和BuilderNode创建的可动态挂载和移除的组件。

## F

### force

强制参数，用于强制回收所有离线Web组件，包括已绑定和未绑定的组件。

## G

### getNWeb

获取离线Web组件接口，返回指定URL对应的NodeController。

## H

### Hidden

隐藏状态，离线Web组件创建后的初始状态，不会立即对用户呈现。

### 后台渲染

Background Rendering，在后台预先渲染Web页面内容的过程。

## I

### Inactive

不活跃状态，停止渲染引擎的状态。

### isBound

是否绑定方法，用于检查离线Web组件是否被NodeContainer绑定。

## L

### loadUrl

加载URL方法，用于加载指定的Web页面。

## M

### Memory overhead

内存开销，每个Web组件大约占用200MB内存和计算资源。

## N

### NavDestination

导航目标组件，用于页面导航。

### nodeMap

节点映射表，用于保存所需要的NodeController。

### 内存占用

Memory Usage，Web组件占用的内存资源，每个组件大约200MB。

## O

### Offline Web Component；离线Web组件

Offline Web Component，创建后不会立即挂载到组件树中的Web组件，状态为Hidden和Inactive。

### onActive

开启渲染方法，用于开启渲染引擎进行渲染。

### onBackground

应用退到后台回调，在此回调中可释放离线Web组件。

### onBind

绑定回调，用于跟踪离线Web组件的绑定状态。

### onForeground

应用回到前台回调，在此回调中可恢复离线Web组件。

### onInactive

停止渲染方法，用于在预渲染完成后停止渲染。

### onUnbind

解绑回调，用于跟踪离线Web组件的解绑状态。

### onWillHide

将要隐藏回调，在NavDestination中用于让当前Web组件加载空白页并取消与当前UI的关联。

## P

### Pre-render Web page；预渲染Web页面

在Web页面启动或跳转的场景下，预先在后台创建Web组件，加载数据并完成渲染，从而实现快速显示。

### Pre-start render process；预启动渲染进程

在未进入Web页面时，提前创建空Web组件，启动Web的渲染进程，为后续使用做好准备。

## R

### recycledNWebs

已释放的离线组件集合，用于保存已释放的离线组件URL信息。

### recycleNWeb

回收离线Web组件接口，用于释放不再需要的离线Web组件。

### recycleNWebs

回收所有离线Web组件接口，用于释放所有离线Web组件。

### restoreNWebs

恢复离线Web组件接口，用于恢复之前释放的离线Web组件。

## S

### Single Render Process Mode

单渲染进程模式，全局共享一个Web渲染进程的模式。

### Size

尺寸对象，用于表示布局的宽度和高度。

## V

### ViewTree

视图树，组件挂载的目标组件树。

## W

### Web Render Process

Web渲染进程，用于渲染Web内容的进程。

## X

### 性能优化

Performance Optimization，通过预启动渲染进程和预渲染Web页面提升Web组件加载速度的技术手段。

### 渲染进程

Render Process，用于渲染Web内容的专用进程。

## Y

### 预渲染

Pre-rendering，在后台预先渲染Web页面内容的技术。

## Z

### 组件树

Component Tree，UI组件的层级结构树，Web组件可动态挂载或移除。
