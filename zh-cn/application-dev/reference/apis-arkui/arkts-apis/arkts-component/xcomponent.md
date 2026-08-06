# component/xcomponent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [XComponent](xcomponent-xcomponent-f.md#xcomponent) | 定义XComponent组件。要求在组件属性设置开始时调用setXComponentOptions， 并在组件属性设置结束时调用applyAttributeFinish。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [XComponentController](xcomponent-xcomponentcontroller-c.md) | XComponent组件的控制器，可以将此对象绑定至XComponent组件，然后通过控制器来调用组件方法。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [NativeXComponentParameters](xcomponent-nativexcomponentparameters-i.md) | 定义XComponent的具体配置参数。通过这种构造参数创建的XComponent，可以将其对应的FrameNode对象传递至Native侧， 使用NDK接口进行Surface生命周期的相关设置和添加事件监听。 |
| [SurfaceConfig](xcomponent-surfaceconfig-i.md) | 用于描述XComponent持有的Surface在渲染时是否需要被视为不透明。 |
| [SurfaceRect](xcomponent-surfacerect-i.md) | 用于描述XComponent持有Surface的显示区域。 |
| [SurfaceRotationOptions](xcomponent-surfacerotationoptions-i.md) | 用于描述XComponent持有Surface在屏幕旋转时是否锁定方向的设置。 |
| [XComponentAttribute](xcomponent-xcomponentattribute-i.md) | 定义XComponent属性。 |
| [XComponentOptions](xcomponent-xcomponentoptions-i.md) | 定义XComponent的具体配置参数。 |
| [XComponentParameters](xcomponent-xcomponentparameters-i.md) | 定义XComponent的具体配置参数，支持Native侧触发XComponent生命周期回调。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [XComponentAttribute](xcomponent-xcomponentattribute-i-sys.md) | 定义XComponent属性。 |
| [XComponentOptions](xcomponent-xcomponentoptions-i-sys.md) | 定义XComponent的具体配置参数。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HdrType](xcomponent-hdrtype-e.md) | HDR视频的高动态范围渲染类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [NativeXComponentPointer](arkts-arkui-nativexcomponentpointer-t.md) | 表示NativeXComponent指针类型。 |

