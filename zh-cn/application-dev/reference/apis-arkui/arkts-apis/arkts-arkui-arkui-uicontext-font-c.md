# Font

Font用于管理自定义字体和系统字体信息，支持注册自定义字体、获取系统字体列表、查询字体详细信息等功能，适用于需要在应用中使用自定义字体或查询系统字体资源的场景。 > **说明：**> > - 以下API需先使用UIContext中的[getFont()](arkts-arkui-arkui-uicontext-uicontext-c.md#getFont)方法获取到Font对象，再通过该对象调用对应方法。 > > - 推荐使用字体引擎的[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadFontSync)接口注册自定义字体。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-export class Font--><!--Device-unnamed-export class Font-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getFontByName

```TypeScript
getFontByName(fontName: string): font.FontInfo
```

根据传入的系统字体名称获取系统字体的相关信息。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getFontByName(fontName: string): font.FontInfo--><!--Device-Font-getFontByName(fontName: string): font.FontInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontName | string | 是 | 系统的字体名，可通过[getSystemFontList()](#getSystemFontList)方法获取支持的字体名称列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| font.FontInfo | 字体的详细信息。&lt;br&gt;如果查询不到字体，返回undefined。 |

## getSystemFontList

```TypeScript
getSystemFontList(): Array<string>
```

获取系统支持的字体列表。 该接口仅在PC/2in1设备上生效，在其他设备上返回空数组。 > **说明：**> 推荐使用[getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md#getSystemFontFullNamesByType)接口获取系统最新支持的字体列表数据。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Font-getSystemFontList(): Array<string>--><!--Device-Font-getSystemFontList(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 系统支持的字体名称列表，返回的名称可用于getFontByName方法查询对应字体的详细信息。 |

## registerFont

```TypeScript
registerFont(options: font.FontOptions): void
```

在字体管理中注册自定义字体。 推荐使用字体引擎的[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadFontSync)接口注册自定义字体。 该接口为异步接口，字体注册为异步过程，不支持并发调用。由于注册是异步完成的，建议在页面初始化阶段（如aboutToAppear）提前调用，以确保字体在使用前已注册完成。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Font-registerFont(options: font.FontOptions): void--><!--Device-Font-registerFont(options: font.FontOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | font.FontOptions | 是 | 注册的自定义字体信息。 &lt;br&gt;**说明：**&lt;br&gt;设置注册字体文件的路径，读取系统沙箱路径内的资源时，建议使用file://路径前缀的字符串，需要确保沙箱目录路径下的文件存在并且有可读权限。 |

