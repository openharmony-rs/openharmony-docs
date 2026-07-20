# EnhancedPanelRect

增强的输入法面板位置、大小信息，包含自定义避让区域、自定义热区。

**起始版本：** 15

<!--Device-inputMethodEngine-export interface EnhancedPanelRect--><!--Device-inputMethodEngine-export interface EnhancedPanelRect-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## fullScreenMode

```TypeScript
fullScreenMode?: boolean
```

是否开启全屏模式。默认值为false。

- 值为true，landscapeRect和portraitRect可不填写。  
- 值为false，landscapeRect和portraitRect为必选属性。

**类型：** boolean

**默认值：** false

**起始版本：** 15

<!--Device-EnhancedPanelRect-fullScreenMode?: boolean--><!--Device-EnhancedPanelRect-fullScreenMode?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## landscapeAvoidY

```TypeScript
landscapeAvoidY?: number
```

横屏状态时，面板中的避让线距离面板顶部的距离，单位px。默认值为0。

- 应用内其他系统组件会对避让线以下的输入法面板区域进行避让。  
- 面板为固定态时，避让线到屏幕底部的高度不能超过屏幕高度的70%。当面板高度大于屏幕高度70%时，取默认值0将无法通过此校验，需要开发者手动设置，使得避让线到屏幕底部的高度不超过屏幕高度的70%。

**类型：** number

**默认值：** 0

**起始版本：** 15

<!--Device-EnhancedPanelRect-landscapeAvoidY?: int--><!--Device-EnhancedPanelRect-landscapeAvoidY?: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## landscapeInputRegion

```TypeScript
landscapeInputRegion?: Array<window.Rect>
```

横屏状态时，面板接收输入事件的区域。

- 数组大小限制为[1, 4]。默认值为横屏时的面板大小。  
- 传入的热区位置是相对于输入法面板窗口左顶点的位置。

**类型：** Array&lt;window.Rect&gt;

**起始版本：** 15

<!--Device-EnhancedPanelRect-landscapeInputRegion?: Array<window.Rect>--><!--Device-EnhancedPanelRect-landscapeInputRegion?: Array<window.Rect>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## landscapeRect

```TypeScript
landscapeRect?: window.Rect
```

横屏状态时输入法面板窗口的位置大小。

- 当fullScreenMode不填写或值为false时，此属性为必选。

**类型：** window.Rect

**起始版本：** 15

<!--Device-EnhancedPanelRect-landscapeRect?: window.Rect--><!--Device-EnhancedPanelRect-landscapeRect?: window.Rect-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## portraitAvoidY

```TypeScript
portraitAvoidY?: number
```

竖屏状态时，面板中的避让线距离面板顶部的距离，单位px。默认值为0。

- 应用内其他系统组件会对避让线以下的输入法面板区域进行避让。  
- 面板为固定态时，避让线到屏幕底部的高度不能超过屏幕高度的70%。当面板高度大于屏幕高度70%时，取默认值0将无法通过此校验，需要开发者手动设置，使得避让线到屏幕底部的高度不超过屏幕高度的70%。

**类型：** number

**默认值：** 0

**起始版本：** 15

<!--Device-EnhancedPanelRect-portraitAvoidY?: int--><!--Device-EnhancedPanelRect-portraitAvoidY?: int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## portraitInputRegion

```TypeScript
portraitInputRegion?: Array<window.Rect>
```

竖屏状态时，面板接收输入事件的区域。

- 数组大小限制为[1, 4]。默认值为竖屏时的面板大小。  
- 传入的热区位置是相对于输入法面板窗口左顶点的位置。

**类型：** Array&lt;window.Rect&gt;

**起始版本：** 15

<!--Device-EnhancedPanelRect-portraitInputRegion?: Array<window.Rect>--><!--Device-EnhancedPanelRect-portraitInputRegion?: Array<window.Rect>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## portraitRect

```TypeScript
portraitRect?: window.Rect
```

竖屏状态时，输入法面板窗口的位置大小。

- 当fullScreenMode不填写或值为false时，此属性为必选。

**类型：** window.Rect

**起始版本：** 15

<!--Device-EnhancedPanelRect-portraitRect?: window.Rect--><!--Device-EnhancedPanelRect-portraitRect?: window.Rect-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

