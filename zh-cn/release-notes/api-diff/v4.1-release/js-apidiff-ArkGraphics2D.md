| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace effectKit<br>差异内容：declare namespace effectKit|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：effectKit；<br>API声明：interface Filter<br>差异内容：interface Filter|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Filter；<br>API声明：blur(radius: number): Filter;<br>差异内容：blur(radius: number): Filter;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Filter；<br>API声明：brightness(bright: number): Filter;<br>差异内容：brightness(bright: number): Filter;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Filter；<br>API声明：grayscale(): Filter;<br>差异内容：grayscale(): Filter;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Filter；<br>API声明：getPixelMap(): image.PixelMap;<br>差异内容：getPixelMap(): image.PixelMap;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Filter；<br>API声明：getEffectPixelMap(): Promise\<image.PixelMap>;<br>差异内容：getEffectPixelMap(): Promise\<image.PixelMap>;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：effectKit；<br>API声明：interface ColorPicker<br>差异内容：interface ColorPicker|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：ColorPicker；<br>API声明：getMainColor(): Promise\<Color>;<br>差异内容：getMainColor(): Promise\<Color>;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：ColorPicker；<br>API声明：getMainColorSync(): Color;<br>差异内容：getMainColorSync(): Color;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：ColorPicker；<br>API声明：getLargestProportionColor(): Color;<br>差异内容：getLargestProportionColor(): Color;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：ColorPicker；<br>API声明：getHighestSaturationColor(): Color;<br>差异内容：getHighestSaturationColor(): Color;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：ColorPicker；<br>API声明：getAverageColor(): Color;<br>差异内容：getAverageColor(): Color;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：ColorPicker；<br>API声明：isBlackOrWhiteOrGrayColor(color: number): boolean;<br>差异内容：isBlackOrWhiteOrGrayColor(color: number): boolean;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：effectKit；<br>API声明：interface Color<br>差异内容：interface Color|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Color；<br>API声明：red: number;<br>差异内容：red: number;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Color；<br>API声明：green: number;<br>差异内容：green: number;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Color；<br>API声明：blue: number;<br>差异内容：blue: number;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Color；<br>API声明：alpha: number;<br>差异内容：alpha: number;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：effectKit；<br>API声明：function createEffect(source: image.PixelMap): Filter;<br>差异内容：function createEffect(source: image.PixelMap): Filter;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>差异内容：function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>差异内容：function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace colorSpaceManager<br>差异内容：declare namespace colorSpaceManager|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：colorSpaceManager；<br>API声明：enum ColorSpace<br>差异内容：enum ColorSpace|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：UNKNOWN = 0<br>差异内容：UNKNOWN = 0|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：ADOBE_RGB_1998 = 1<br>差异内容：ADOBE_RGB_1998 = 1|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：DCI_P3 = 2<br>差异内容：DCI_P3 = 2|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：DISPLAY_P3 = 3<br>差异内容：DISPLAY_P3 = 3|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：SRGB = 4<br>差异内容：SRGB = 4|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT709 = 6<br>差异内容：BT709 = 6|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT601_EBU = 7<br>差异内容：BT601_EBU = 7|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT601_SMPTE_C = 8<br>差异内容：BT601_SMPTE_C = 8|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT2020_HLG = 9<br>差异内容：BT2020_HLG = 9|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT2020_PQ = 10<br>差异内容：BT2020_PQ = 10|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：P3_HLG = 11<br>差异内容：P3_HLG = 11|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：P3_PQ = 12<br>差异内容：P3_PQ = 12|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：ADOBE_RGB_1998_LIMIT = 13<br>差异内容：ADOBE_RGB_1998_LIMIT = 13|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：DISPLAY_P3_LIMIT = 14<br>差异内容：DISPLAY_P3_LIMIT = 14|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：SRGB_LIMIT = 15<br>差异内容：SRGB_LIMIT = 15|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT709_LIMIT = 16<br>差异内容：BT709_LIMIT = 16|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT601_EBU_LIMIT = 17<br>差异内容：BT601_EBU_LIMIT = 17|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT601_SMPTE_C_LIMIT = 18<br>差异内容：BT601_SMPTE_C_LIMIT = 18|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT2020_HLG_LIMIT = 19<br>差异内容：BT2020_HLG_LIMIT = 19|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：BT2020_PQ_LIMIT = 20<br>差异内容：BT2020_PQ_LIMIT = 20|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：P3_HLG_LIMIT = 21<br>差异内容：P3_HLG_LIMIT = 21|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：P3_PQ_LIMIT = 22<br>差异内容：P3_PQ_LIMIT = 22|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：LINEAR_P3 = 23<br>差异内容：LINEAR_P3 = 23|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：LINEAR_SRGB = 24<br>差异内容：LINEAR_SRGB = 24|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：LINEAR_BT709 = LINEAR_SRGB<br>差异内容：LINEAR_BT709 = LINEAR_SRGB|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：LINEAR_BT2020 = 25<br>差异内容：LINEAR_BT2020 = 25|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：DISPLAY_SRGB = SRGB<br>差异内容：DISPLAY_SRGB = SRGB|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：DISPLAY_P3_SRGB = DISPLAY_P3<br>差异内容：DISPLAY_P3_SRGB = DISPLAY_P3|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：DISPLAY_P3_HLG = P3_HLG<br>差异内容：DISPLAY_P3_HLG = P3_HLG|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：DISPLAY_P3_PQ = P3_PQ<br>差异内容：DISPLAY_P3_PQ = P3_PQ|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：CUSTOM = 5<br>差异内容：CUSTOM = 5|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：colorSpaceManager；<br>API声明：interface ColorSpacePrimaries<br>差异内容：interface ColorSpacePrimaries|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpacePrimaries；<br>API声明：redX: number;<br>差异内容：redX: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpacePrimaries；<br>API声明：redY: number;<br>差异内容：redY: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpacePrimaries；<br>API声明：greenX: number;<br>差异内容：greenX: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpacePrimaries；<br>API声明：greenY: number;<br>差异内容：greenY: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpacePrimaries；<br>API声明：blueX: number;<br>差异内容：blueX: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpacePrimaries；<br>API声明：blueY: number;<br>差异内容：blueY: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpacePrimaries；<br>API声明：whitePointX: number;<br>差异内容：whitePointX: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpacePrimaries；<br>API声明：whitePointY: number;<br>差异内容：whitePointY: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：colorSpaceManager；<br>API声明：interface ColorSpaceManager<br>差异内容：interface ColorSpaceManager|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpaceManager；<br>API声明：getColorSpaceName(): ColorSpace;<br>差异内容：getColorSpaceName(): ColorSpace;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpaceManager；<br>API声明：getWhitePoint(): Array\<number>;<br>差异内容：getWhitePoint(): Array\<number>;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：ColorSpaceManager；<br>API声明：getGamma(): number;<br>差异内容：getGamma(): number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：colorSpaceManager；<br>API声明：function create(colorSpaceName: ColorSpace): ColorSpaceManager;<br>差异内容：function create(colorSpaceName: ColorSpace): ColorSpaceManager;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：colorSpaceManager；<br>API声明：function create(primaries: ColorSpacePrimaries, gamma: number): ColorSpaceManager;<br>差异内容：function create(primaries: ColorSpacePrimaries, gamma: number): ColorSpaceManager;|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace displaySync<br>差异内容：declare namespace displaySync|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：displaySync；<br>API声明：interface IntervalInfo<br>差异内容：interface IntervalInfo|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：IntervalInfo；<br>API声明：timestamp: number;<br>差异内容：timestamp: number;|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：IntervalInfo；<br>API声明：targetTimestamp: number;<br>差异内容：targetTimestamp: number;|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：displaySync；<br>API声明：interface DisplaySync<br>差异内容：interface DisplaySync|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：DisplaySync；<br>API声明：setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void;<br>差异内容：setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void;|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：DisplaySync；<br>API声明：on(type: 'frame', callback: Callback\<IntervalInfo>): void;<br>差异内容：on(type: 'frame', callback: Callback\<IntervalInfo>): void;|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：DisplaySync；<br>API声明：off(type: 'frame', callback?: Callback\<IntervalInfo>): void;<br>差异内容：off(type: 'frame', callback?: Callback\<IntervalInfo>): void;|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：DisplaySync；<br>API声明：start(): void;<br>差异内容：start(): void;|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：DisplaySync；<br>API声明：stop(): void;<br>差异内容：stop(): void;|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：displaySync；<br>API声明：function create(): DisplaySync;<br>差异内容：function create(): DisplaySync;|api/@ohos.graphics.displaySync.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace hdrCapability<br>差异内容：declare namespace hdrCapability|api/@ohos.graphics.hdrCapability.d.ts|
|新增API|NA|类名：hdrCapability；<br>API声明：enum HDRFormat<br>差异内容：enum HDRFormat|api/@ohos.graphics.hdrCapability.d.ts|
|新增API|NA|类名：HDRFormat；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.graphics.hdrCapability.d.ts|
|新增API|NA|类名：HDRFormat；<br>API声明：VIDEO_HLG = 1<br>差异内容：VIDEO_HLG = 1|api/@ohos.graphics.hdrCapability.d.ts|
|新增API|NA|类名：HDRFormat；<br>API声明：VIDEO_HDR10 = 2<br>差异内容：VIDEO_HDR10 = 2|api/@ohos.graphics.hdrCapability.d.ts|
|新增API|NA|类名：HDRFormat；<br>API声明：VIDEO_HDR_VIVID = 3<br>差异内容：VIDEO_HDR_VIVID = 3|api/@ohos.graphics.hdrCapability.d.ts|
|新增API|NA|类名：HDRFormat；<br>API声明：IMAGE_HDR_VIVID_DUAL = 4<br>差异内容：IMAGE_HDR_VIVID_DUAL = 4|api/@ohos.graphics.hdrCapability.d.ts|
|新增API|NA|类名：HDRFormat；<br>API声明：IMAGE_HDR_VIVID_SINGLE = 5<br>差异内容：IMAGE_HDR_VIVID_SINGLE = 5|api/@ohos.graphics.hdrCapability.d.ts|
|新增API|NA|类名：HDRFormat；<br>API声明：IMAGE_HDR_ISO_DUAL = 6<br>差异内容：IMAGE_HDR_ISO_DUAL = 6|api/@ohos.graphics.hdrCapability.d.ts|
|新增API|NA|类名：HDRFormat；<br>API声明：IMAGE_HDR_ISO_SINGLE = 7<br>差异内容：IMAGE_HDR_ISO_SINGLE = 7|api/@ohos.graphics.hdrCapability.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.effectKit.d.ts<br>差异内容：ArkGraphics2D|api/@ohos.effectKit.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.graphics.colorSpaceManager.d.ts<br>差异内容：ArkGraphics2D|api/@ohos.graphics.colorSpaceManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.graphics.displaySync.d.ts<br>差异内容：ArkGraphics2D|api/@ohos.graphics.displaySync.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.graphics.hdrCapability.d.ts<br>差异内容：ArkGraphics2D|api/@ohos.graphics.hdrCapability.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.ArkGraphics2D.d.ts<br>差异内容：ArkGraphics2D|kits/@kit.ArkGraphics2D.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace common2D<br>差异内容：declare namespace common2D|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：common2D；<br>API声明：interface Color<br>差异内容：interface Color|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Color；<br>API声明：alpha: number;<br>差异内容：alpha: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Color；<br>API声明：red: number;<br>差异内容：red: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Color；<br>API声明：green: number;<br>差异内容：green: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Color；<br>API声明：blue: number;<br>差异内容：blue: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：common2D；<br>API声明：interface Rect<br>差异内容：interface Rect|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Rect；<br>API声明：left: number;<br>差异内容：left: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Rect；<br>API声明：top: number;<br>差异内容：top: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Rect；<br>API声明：right: number;<br>差异内容：right: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Rect；<br>API声明：bottom: number;<br>差异内容：bottom: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace drawing<br>差异内容：declare namespace drawing|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum BlendMode<br>差异内容：enum BlendMode|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：CLEAR = 0<br>差异内容：CLEAR = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：SRC = 1<br>差异内容：SRC = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：DST = 2<br>差异内容：DST = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：SRC_OVER = 3<br>差异内容：SRC_OVER = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：DST_OVER = 4<br>差异内容：DST_OVER = 4|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：SRC_IN = 5<br>差异内容：SRC_IN = 5|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：DST_IN = 6<br>差异内容：DST_IN = 6|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：SRC_OUT = 7<br>差异内容：SRC_OUT = 7|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：DST_OUT = 8<br>差异内容：DST_OUT = 8|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：SRC_ATOP = 9<br>差异内容：SRC_ATOP = 9|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：DST_ATOP = 10<br>差异内容：DST_ATOP = 10|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：XOR = 11<br>差异内容：XOR = 11|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：PLUS = 12<br>差异内容：PLUS = 12|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：MODULATE = 13<br>差异内容：MODULATE = 13|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：SCREEN = 14<br>差异内容：SCREEN = 14|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：OVERLAY = 15<br>差异内容：OVERLAY = 15|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：DARKEN = 16<br>差异内容：DARKEN = 16|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：LIGHTEN = 17<br>差异内容：LIGHTEN = 17|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：COLOR_DODGE = 18<br>差异内容：COLOR_DODGE = 18|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：COLOR_BURN = 19<br>差异内容：COLOR_BURN = 19|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：HARD_LIGHT = 20<br>差异内容：HARD_LIGHT = 20|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：SOFT_LIGHT = 21<br>差异内容：SOFT_LIGHT = 21|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：DIFFERENCE = 22<br>差异内容：DIFFERENCE = 22|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：EXCLUSION = 23<br>差异内容：EXCLUSION = 23|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：MULTIPLY = 24<br>差异内容：MULTIPLY = 24|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：HUE = 25<br>差异内容：HUE = 25|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：SATURATION = 26<br>差异内容：SATURATION = 26|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：COLOR = 27<br>差异内容：COLOR = 27|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlendMode；<br>API声明：LUMINOSITY = 28<br>差异内容：LUMINOSITY = 28|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class Path<br>差异内容：class Path|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：moveTo(x: number, y: number): void;<br>差异内容：moveTo(x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：lineTo(x: number, y: number): void;<br>差异内容：lineTo(x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：arcTo(x1: number, y1: number, x2: number, y2: number, startDeg: number, sweepDeg: number): void;<br>差异内容：arcTo(x1: number, y1: number, x2: number, y2: number, startDeg: number, sweepDeg: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：quadTo(ctrlX: number, ctrlY: number, endX: number, endY: number): void;<br>差异内容：quadTo(ctrlX: number, ctrlY: number, endX: number, endY: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：cubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void;<br>差异内容：cubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：reset(): void;<br>差异内容：reset(): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class Canvas<br>差异内容：class Canvas|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawRect(rect: common2D.Rect): void;<br>差异内容：drawRect(rect: common2D.Rect): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawCircle(x: number, y: number, radius: number): void;<br>差异内容：drawCircle(x: number, y: number, radius: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawImage(pixelmap: image.PixelMap, left: number, top: number): void;<br>差异内容：drawImage(pixelmap: image.PixelMap, left: number, top: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawColor(color: common2D.Color, blendMode?: BlendMode): void;<br>差异内容：drawColor(color: common2D.Color, blendMode?: BlendMode): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawPoint(x: number, y: number): void;<br>差异内容：drawPoint(x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawPath(path: Path): void;<br>差异内容：drawPath(path: Path): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawLine(x0: number, y0: number, x1: number, y1: number): void;<br>差异内容：drawLine(x0: number, y0: number, x1: number, y1: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawTextBlob(blob: TextBlob, x: number, y: number): void;<br>差异内容：drawTextBlob(blob: TextBlob, x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：attachPen(pen: Pen): void;<br>差异内容：attachPen(pen: Pen): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：attachBrush(brush: Brush): void;<br>差异内容：attachBrush(brush: Brush): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：detachPen(): void;<br>差异内容：detachPen(): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：detachBrush(): void;<br>差异内容：detachBrush(): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：interface TextBlobRunBuffer<br>差异内容：interface TextBlobRunBuffer|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextBlobRunBuffer；<br>API声明：glyph: number;<br>差异内容：glyph: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextBlobRunBuffer；<br>API声明：positionX: number;<br>差异内容：positionX: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextBlobRunBuffer；<br>API声明：positionY: number;<br>差异内容：positionY: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum TextEncoding<br>差异内容：enum TextEncoding|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextEncoding；<br>API声明：TEXT_ENCODING_UTF8 = 0<br>差异内容：TEXT_ENCODING_UTF8 = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextEncoding；<br>API声明：TEXT_ENCODING_UTF16 = 1<br>差异内容：TEXT_ENCODING_UTF16 = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextEncoding；<br>API声明：TEXT_ENCODING_UTF32 = 2<br>差异内容：TEXT_ENCODING_UTF32 = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextEncoding；<br>API声明：TEXT_ENCODING_GLYPH_ID = 3<br>差异内容：TEXT_ENCODING_GLYPH_ID = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class TextBlob<br>差异内容：class TextBlob|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextBlob；<br>API声明：static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob;<br>差异内容：static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextBlob；<br>API声明：static makeFromRunBuffer(pos: Array\<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob;<br>差异内容：static makeFromRunBuffer(pos: Array\<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextBlob；<br>API声明：bounds(): common2D.Rect;<br>差异内容：bounds(): common2D.Rect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class Typeface<br>差异内容：class Typeface|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Typeface；<br>API声明：getFamilyName(): string;<br>差异内容：getFamilyName(): string;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class Font<br>差异内容：class Font|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：enableSubpixel(isSubpixel: boolean): void;<br>差异内容：enableSubpixel(isSubpixel: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：enableEmbolden(isEmbolden: boolean): void;<br>差异内容：enableEmbolden(isEmbolden: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：enableLinearMetrics(isLinearMetrics: boolean): void;<br>差异内容：enableLinearMetrics(isLinearMetrics: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：setSize(textSize: number): void;<br>差异内容：setSize(textSize: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getSize(): number;<br>差异内容：getSize(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：setTypeface(typeface: Typeface): void;<br>差异内容：setTypeface(typeface: Typeface): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getTypeface(): Typeface;<br>差异内容：getTypeface(): Typeface;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getMetrics(): FontMetrics;<br>差异内容：getMetrics(): FontMetrics;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：measureText(text: string, encoding: TextEncoding): number;<br>差异内容：measureText(text: string, encoding: TextEncoding): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：interface FontMetrics<br>差异内容：interface FontMetrics|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：top: number;<br>差异内容：top: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：ascent: number;<br>差异内容：ascent: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：descent: number;<br>差异内容：descent: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：bottom: number;<br>差异内容：bottom: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：leading: number;<br>差异内容：leading: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class ColorFilter<br>差异内容：class ColorFilter|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ColorFilter；<br>API声明：static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter;<br>差异内容：static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ColorFilter；<br>API声明：static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter;<br>差异内容：static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ColorFilter；<br>API声明：static createLinearToSRGBGamma(): ColorFilter;<br>差异内容：static createLinearToSRGBGamma(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ColorFilter；<br>API声明：static createSRGBGammaToLinear(): ColorFilter;<br>差异内容：static createSRGBGammaToLinear(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ColorFilter；<br>API声明：static createLumaColorFilter(): ColorFilter;<br>差异内容：static createLumaColorFilter(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class Pen<br>差异内容：class Pen|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setColor(color: common2D.Color): void;<br>差异内容：setColor(color: common2D.Color): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setStrokeWidth(width: number): void;<br>差异内容：setStrokeWidth(width: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setAntiAlias(aa: boolean): void;<br>差异内容：setAntiAlias(aa: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setAlpha(alpha: number): void;<br>差异内容：setAlpha(alpha: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setColorFilter(filter: ColorFilter): void;<br>差异内容：setColorFilter(filter: ColorFilter): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setBlendMode(mode: BlendMode): void;<br>差异内容：setBlendMode(mode: BlendMode): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setDither(dither: boolean): void;<br>差异内容：setDither(dither: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class Brush<br>差异内容：class Brush|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setColor(color: common2D.Color): void;<br>差异内容：setColor(color: common2D.Color): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setAntiAlias(aa: boolean): void;<br>差异内容：setAntiAlias(aa: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setAlpha(alpha: number): void;<br>差异内容：setAlpha(alpha: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setColorFilter(filter: ColorFilter): void;<br>差异内容：setColorFilter(filter: ColorFilter): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setBlendMode(mode: BlendMode): void;<br>差异内容：setBlendMode(mode: BlendMode): void;|api/@ohos.graphics.drawing.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.graphics.common2D.d.ts<br>差异内容：ArkGraphics 2D|api/@ohos.graphics.common2D.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.graphics.drawing.d.ts<br>差异内容：ArkGraphics 2D|api/@ohos.graphics.drawing.d.ts|
