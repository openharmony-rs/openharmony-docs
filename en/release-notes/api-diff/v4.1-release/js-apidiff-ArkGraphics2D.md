| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace effectKit<br>Differences: declare namespace effectKit|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: effectKit;<br>API declaration: interface Filter<br>Differences: interface Filter|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: blur(radius: number): Filter;<br>Differences: blur(radius: number): Filter;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: brightness(bright: number): Filter;<br>Differences: brightness(bright: number): Filter;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: grayscale(): Filter;<br>Differences: grayscale(): Filter;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: getPixelMap(): image.PixelMap;<br>Differences: getPixelMap(): image.PixelMap;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: getEffectPixelMap(): Promise\<image.PixelMap>;<br>Differences: getEffectPixelMap(): Promise\<image.PixelMap>;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: effectKit;<br>API declaration: interface ColorPicker<br>Differences: interface ColorPicker|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: ColorPicker;<br>API declaration: getMainColor(): Promise\<Color>;<br>Differences: getMainColor(): Promise\<Color>;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: ColorPicker;<br>API declaration: getMainColorSync(): Color;<br>Differences: getMainColorSync(): Color;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: ColorPicker;<br>API declaration: getLargestProportionColor(): Color;<br>Differences: getLargestProportionColor(): Color;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: ColorPicker;<br>API declaration: getHighestSaturationColor(): Color;<br>Differences: getHighestSaturationColor(): Color;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: ColorPicker;<br>API declaration: getAverageColor(): Color;<br>Differences: getAverageColor(): Color;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: ColorPicker;<br>API declaration: isBlackOrWhiteOrGrayColor(color: number): boolean;<br>Differences: isBlackOrWhiteOrGrayColor(color: number): boolean;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: effectKit;<br>API declaration: interface Color<br>Differences: interface Color|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Color;<br>API declaration: red: number;<br>Differences: red: number;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Color;<br>API declaration: green: number;<br>Differences: green: number;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Color;<br>API declaration: blue: number;<br>Differences: blue: number;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Color;<br>API declaration: alpha: number;<br>Differences: alpha: number;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: effectKit;<br>API declaration: function createEffect(source: image.PixelMap): Filter;<br>Differences: function createEffect(source: image.PixelMap): Filter;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>Differences: function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>Differences: function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace colorSpaceManager<br>Differences: declare namespace colorSpaceManager|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: colorSpaceManager;<br>API declaration: enum ColorSpace<br>Differences: enum ColorSpace|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: UNKNOWN = 0<br>Differences: UNKNOWN = 0|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: ADOBE_RGB_1998 = 1<br>Differences: ADOBE_RGB_1998 = 1|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: DCI_P3 = 2<br>Differences: DCI_P3 = 2|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3 = 3<br>Differences: DISPLAY_P3 = 3|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: SRGB = 4<br>Differences: SRGB = 4|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT709 = 6<br>Differences: BT709 = 6|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT601_EBU = 7<br>Differences: BT601_EBU = 7|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT601_SMPTE_C = 8<br>Differences: BT601_SMPTE_C = 8|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT2020_HLG = 9<br>Differences: BT2020_HLG = 9|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT2020_PQ = 10<br>Differences: BT2020_PQ = 10|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: P3_HLG = 11<br>Differences: P3_HLG = 11|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: P3_PQ = 12<br>Differences: P3_PQ = 12|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: ADOBE_RGB_1998_LIMIT = 13<br>Differences: ADOBE_RGB_1998_LIMIT = 13|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_LIMIT = 14<br>Differences: DISPLAY_P3_LIMIT = 14|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: SRGB_LIMIT = 15<br>Differences: SRGB_LIMIT = 15|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT709_LIMIT = 16<br>Differences: BT709_LIMIT = 16|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT601_EBU_LIMIT = 17<br>Differences: BT601_EBU_LIMIT = 17|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT601_SMPTE_C_LIMIT = 18<br>Differences: BT601_SMPTE_C_LIMIT = 18|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT2020_HLG_LIMIT = 19<br>Differences: BT2020_HLG_LIMIT = 19|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: BT2020_PQ_LIMIT = 20<br>Differences: BT2020_PQ_LIMIT = 20|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: P3_HLG_LIMIT = 21<br>Differences: P3_HLG_LIMIT = 21|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: P3_PQ_LIMIT = 22<br>Differences: P3_PQ_LIMIT = 22|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: LINEAR_P3 = 23<br>Differences: LINEAR_P3 = 23|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: LINEAR_SRGB = 24<br>Differences: LINEAR_SRGB = 24|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: LINEAR_BT709 = LINEAR_SRGB<br>Differences: LINEAR_BT709 = LINEAR_SRGB|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: LINEAR_BT2020 = 25<br>Differences: LINEAR_BT2020 = 25|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: DISPLAY_SRGB = SRGB<br>Differences: DISPLAY_SRGB = SRGB|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_SRGB = DISPLAY_P3<br>Differences: DISPLAY_P3_SRGB = DISPLAY_P3|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_HLG = P3_HLG<br>Differences: DISPLAY_P3_HLG = P3_HLG|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_PQ = P3_PQ<br>Differences: DISPLAY_P3_PQ = P3_PQ|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpace;<br>API declaration: CUSTOM = 5<br>Differences: CUSTOM = 5|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: colorSpaceManager;<br>API declaration: interface ColorSpacePrimaries<br>Differences: interface ColorSpacePrimaries|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpacePrimaries;<br>API declaration: redX: number;<br>Differences: redX: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpacePrimaries;<br>API declaration: redY: number;<br>Differences: redY: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpacePrimaries;<br>API declaration: greenX: number;<br>Differences: greenX: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpacePrimaries;<br>API declaration: greenY: number;<br>Differences: greenY: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpacePrimaries;<br>API declaration: blueX: number;<br>Differences: blueX: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpacePrimaries;<br>API declaration: blueY: number;<br>Differences: blueY: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpacePrimaries;<br>API declaration: whitePointX: number;<br>Differences: whitePointX: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpacePrimaries;<br>API declaration: whitePointY: number;<br>Differences: whitePointY: number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: colorSpaceManager;<br>API declaration: interface ColorSpaceManager<br>Differences: interface ColorSpaceManager|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpaceManager;<br>API declaration: getColorSpaceName(): ColorSpace;<br>Differences: getColorSpaceName(): ColorSpace;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpaceManager;<br>API declaration: getWhitePoint(): Array\<number>;<br>Differences: getWhitePoint(): Array\<number>;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: ColorSpaceManager;<br>API declaration: getGamma(): number;<br>Differences: getGamma(): number;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: colorSpaceManager;<br>API declaration: function create(colorSpaceName: ColorSpace): ColorSpaceManager;<br>Differences: function create(colorSpaceName: ColorSpace): ColorSpaceManager;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: colorSpaceManager;<br>API declaration: function create(primaries: ColorSpacePrimaries, gamma: number): ColorSpaceManager;<br>Differences: function create(primaries: ColorSpacePrimaries, gamma: number): ColorSpaceManager;|api/@ohos.graphics.colorSpaceManager.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace displaySync<br>Differences: declare namespace displaySync|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: displaySync;<br>API declaration: interface IntervalInfo<br>Differences: interface IntervalInfo|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: IntervalInfo;<br>API declaration: timestamp: number;<br>Differences: timestamp: number;|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: IntervalInfo;<br>API declaration: targetTimestamp: number;<br>Differences: targetTimestamp: number;|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: displaySync;<br>API declaration: interface DisplaySync<br>Differences: interface DisplaySync|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: DisplaySync;<br>API declaration: setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void;<br>Differences: setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange): void;|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: DisplaySync;<br>API declaration: on(type: 'frame', callback: Callback\<IntervalInfo>): void;<br>Differences: on(type: 'frame', callback: Callback\<IntervalInfo>): void;|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: DisplaySync;<br>API declaration: off(type: 'frame', callback?: Callback\<IntervalInfo>): void;<br>Differences: off(type: 'frame', callback?: Callback\<IntervalInfo>): void;|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: DisplaySync;<br>API declaration: start(): void;<br>Differences: start(): void;|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: DisplaySync;<br>API declaration: stop(): void;<br>Differences: stop(): void;|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: displaySync;<br>API declaration: function create(): DisplaySync;<br>Differences: function create(): DisplaySync;|api/@ohos.graphics.displaySync.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace hdrCapability<br>Differences: declare namespace hdrCapability|api/@ohos.graphics.hdrCapability.d.ts|
|New API|NA|Class name: hdrCapability;<br>API declaration: enum HDRFormat<br>Differences: enum HDRFormat|api/@ohos.graphics.hdrCapability.d.ts|
|New API|NA|Class name: HDRFormat;<br>API declaration: NONE = 0<br>Differences: NONE = 0|api/@ohos.graphics.hdrCapability.d.ts|
|New API|NA|Class name: HDRFormat;<br>API declaration: VIDEO_HLG = 1<br>Differences: VIDEO_HLG = 1|api/@ohos.graphics.hdrCapability.d.ts|
|New API|NA|Class name: HDRFormat;<br>API declaration: VIDEO_HDR10 = 2<br>Differences: VIDEO_HDR10 = 2|api/@ohos.graphics.hdrCapability.d.ts|
|New API|NA|Class name: HDRFormat;<br>API declaration: VIDEO_HDR_VIVID = 3<br>Differences: VIDEO_HDR_VIVID = 3|api/@ohos.graphics.hdrCapability.d.ts|
|New API|NA|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_VIVID_DUAL = 4<br>Differences: IMAGE_HDR_VIVID_DUAL = 4|api/@ohos.graphics.hdrCapability.d.ts|
|New API|NA|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_VIVID_SINGLE = 5<br>Differences: IMAGE_HDR_VIVID_SINGLE = 5|api/@ohos.graphics.hdrCapability.d.ts|
|New API|NA|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_ISO_DUAL = 6<br>Differences: IMAGE_HDR_ISO_DUAL = 6|api/@ohos.graphics.hdrCapability.d.ts|
|New API|NA|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_ISO_SINGLE = 7<br>Differences: IMAGE_HDR_ISO_SINGLE = 7|api/@ohos.graphics.hdrCapability.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.effectKit.d.ts<br>Differences: ArkGraphics2D|api/@ohos.effectKit.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.graphics.colorSpaceManager.d.ts<br>Differences: ArkGraphics2D|api/@ohos.graphics.colorSpaceManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.graphics.displaySync.d.ts<br>Differences: ArkGraphics2D|api/@ohos.graphics.displaySync.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.graphics.hdrCapability.d.ts<br>Differences: ArkGraphics2D|api/@ohos.graphics.hdrCapability.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.ArkGraphics2D.d.ts<br>Differences: ArkGraphics2D|kits/@kit.ArkGraphics2D.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace common2D<br>Differences: declare namespace common2D|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: common2D;<br>API declaration: interface Color<br>Differences: interface Color|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Color;<br>API declaration: alpha: number;<br>Differences: alpha: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Color;<br>API declaration: red: number;<br>Differences: red: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Color;<br>API declaration: green: number;<br>Differences: green: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Color;<br>API declaration: blue: number;<br>Differences: blue: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: common2D;<br>API declaration: interface Rect<br>Differences: interface Rect|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: left: number;<br>Differences: left: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: top: number;<br>Differences: top: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: right: number;<br>Differences: right: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: bottom: number;<br>Differences: bottom: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace drawing<br>Differences: declare namespace drawing|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum BlendMode<br>Differences: enum BlendMode|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: CLEAR = 0<br>Differences: CLEAR = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: SRC = 1<br>Differences: SRC = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: DST = 2<br>Differences: DST = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: SRC_OVER = 3<br>Differences: SRC_OVER = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: DST_OVER = 4<br>Differences: DST_OVER = 4|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: SRC_IN = 5<br>Differences: SRC_IN = 5|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: DST_IN = 6<br>Differences: DST_IN = 6|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: SRC_OUT = 7<br>Differences: SRC_OUT = 7|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: DST_OUT = 8<br>Differences: DST_OUT = 8|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: SRC_ATOP = 9<br>Differences: SRC_ATOP = 9|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: DST_ATOP = 10<br>Differences: DST_ATOP = 10|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: XOR = 11<br>Differences: XOR = 11|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: PLUS = 12<br>Differences: PLUS = 12|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: MODULATE = 13<br>Differences: MODULATE = 13|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: SCREEN = 14<br>Differences: SCREEN = 14|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: OVERLAY = 15<br>Differences: OVERLAY = 15|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: DARKEN = 16<br>Differences: DARKEN = 16|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: LIGHTEN = 17<br>Differences: LIGHTEN = 17|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: COLOR_DODGE = 18<br>Differences: COLOR_DODGE = 18|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: COLOR_BURN = 19<br>Differences: COLOR_BURN = 19|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: HARD_LIGHT = 20<br>Differences: HARD_LIGHT = 20|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: SOFT_LIGHT = 21<br>Differences: SOFT_LIGHT = 21|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: DIFFERENCE = 22<br>Differences: DIFFERENCE = 22|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: EXCLUSION = 23<br>Differences: EXCLUSION = 23|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: MULTIPLY = 24<br>Differences: MULTIPLY = 24|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: HUE = 25<br>Differences: HUE = 25|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: SATURATION = 26<br>Differences: SATURATION = 26|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: COLOR = 27<br>Differences: COLOR = 27|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlendMode;<br>API declaration: LUMINOSITY = 28<br>Differences: LUMINOSITY = 28|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class Path<br>Differences: class Path|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: moveTo(x: number, y: number): void;<br>Differences: moveTo(x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: lineTo(x: number, y: number): void;<br>Differences: lineTo(x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: arcTo(x1: number, y1: number, x2: number, y2: number, startDeg: number, sweepDeg: number): void;<br>Differences: arcTo(x1: number, y1: number, x2: number, y2: number, startDeg: number, sweepDeg: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: quadTo(ctrlX: number, ctrlY: number, endX: number, endY: number): void;<br>Differences: quadTo(ctrlX: number, ctrlY: number, endX: number, endY: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: cubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void;<br>Differences: cubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: close(): void;<br>Differences: close(): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: reset(): void;<br>Differences: reset(): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class Canvas<br>Differences: class Canvas|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawRect(rect: common2D.Rect): void;<br>Differences: drawRect(rect: common2D.Rect): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawCircle(x: number, y: number, radius: number): void;<br>Differences: drawCircle(x: number, y: number, radius: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawImage(pixelmap: image.PixelMap, left: number, top: number): void;<br>Differences: drawImage(pixelmap: image.PixelMap, left: number, top: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawColor(color: common2D.Color, blendMode?: BlendMode): void;<br>Differences: drawColor(color: common2D.Color, blendMode?: BlendMode): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawPoint(x: number, y: number): void;<br>Differences: drawPoint(x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawPath(path: Path): void;<br>Differences: drawPath(path: Path): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawLine(x0: number, y0: number, x1: number, y1: number): void;<br>Differences: drawLine(x0: number, y0: number, x1: number, y1: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawTextBlob(blob: TextBlob, x: number, y: number): void;<br>Differences: drawTextBlob(blob: TextBlob, x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: attachPen(pen: Pen): void;<br>Differences: attachPen(pen: Pen): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: attachBrush(brush: Brush): void;<br>Differences: attachBrush(brush: Brush): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: detachPen(): void;<br>Differences: detachPen(): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: detachBrush(): void;<br>Differences: detachBrush(): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: interface TextBlobRunBuffer<br>Differences: interface TextBlobRunBuffer|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextBlobRunBuffer;<br>API declaration: glyph: number;<br>Differences: glyph: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextBlobRunBuffer;<br>API declaration: positionX: number;<br>Differences: positionX: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextBlobRunBuffer;<br>API declaration: positionY: number;<br>Differences: positionY: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum TextEncoding<br>Differences: enum TextEncoding|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextEncoding;<br>API declaration: TEXT_ENCODING_UTF8 = 0<br>Differences: TEXT_ENCODING_UTF8 = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextEncoding;<br>API declaration: TEXT_ENCODING_UTF16 = 1<br>Differences: TEXT_ENCODING_UTF16 = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextEncoding;<br>API declaration: TEXT_ENCODING_UTF32 = 2<br>Differences: TEXT_ENCODING_UTF32 = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextEncoding;<br>API declaration: TEXT_ENCODING_GLYPH_ID = 3<br>Differences: TEXT_ENCODING_GLYPH_ID = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class TextBlob<br>Differences: class TextBlob|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextBlob;<br>API declaration: static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob;<br>Differences: static makeFromString(text: string, font: Font, encoding?: TextEncoding): TextBlob;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextBlob;<br>API declaration: static makeFromRunBuffer(pos: Array\<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob;<br>Differences: static makeFromRunBuffer(pos: Array\<TextBlobRunBuffer>, font: Font, bounds?: common2D.Rect): TextBlob;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextBlob;<br>API declaration: bounds(): common2D.Rect;<br>Differences: bounds(): common2D.Rect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class Typeface<br>Differences: class Typeface|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Typeface;<br>API declaration: getFamilyName(): string;<br>Differences: getFamilyName(): string;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class Font<br>Differences: class Font|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: enableSubpixel(isSubpixel: boolean): void;<br>Differences: enableSubpixel(isSubpixel: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: enableEmbolden(isEmbolden: boolean): void;<br>Differences: enableEmbolden(isEmbolden: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: enableLinearMetrics(isLinearMetrics: boolean): void;<br>Differences: enableLinearMetrics(isLinearMetrics: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: setSize(textSize: number): void;<br>Differences: setSize(textSize: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: getSize(): number;<br>Differences: getSize(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: setTypeface(typeface: Typeface): void;<br>Differences: setTypeface(typeface: Typeface): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: getTypeface(): Typeface;<br>Differences: getTypeface(): Typeface;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: getMetrics(): FontMetrics;<br>Differences: getMetrics(): FontMetrics;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: measureText(text: string, encoding: TextEncoding): number;<br>Differences: measureText(text: string, encoding: TextEncoding): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: interface FontMetrics<br>Differences: interface FontMetrics|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: top: number;<br>Differences: top: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: ascent: number;<br>Differences: ascent: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: descent: number;<br>Differences: descent: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: bottom: number;<br>Differences: bottom: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: leading: number;<br>Differences: leading: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class ColorFilter<br>Differences: class ColorFilter|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ColorFilter;<br>API declaration: static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter;<br>Differences: static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ColorFilter;<br>API declaration: static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter;<br>Differences: static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ColorFilter;<br>API declaration: static createLinearToSRGBGamma(): ColorFilter;<br>Differences: static createLinearToSRGBGamma(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ColorFilter;<br>API declaration: static createSRGBGammaToLinear(): ColorFilter;<br>Differences: static createSRGBGammaToLinear(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ColorFilter;<br>API declaration: static createLumaColorFilter(): ColorFilter;<br>Differences: static createLumaColorFilter(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class Pen<br>Differences: class Pen|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setColor(color: common2D.Color): void;<br>Differences: setColor(color: common2D.Color): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setStrokeWidth(width: number): void;<br>Differences: setStrokeWidth(width: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setAntiAlias(aa: boolean): void;<br>Differences: setAntiAlias(aa: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setAlpha(alpha: number): void;<br>Differences: setAlpha(alpha: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setColorFilter(filter: ColorFilter): void;<br>Differences: setColorFilter(filter: ColorFilter): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setBlendMode(mode: BlendMode): void;<br>Differences: setBlendMode(mode: BlendMode): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setDither(dither: boolean): void;<br>Differences: setDither(dither: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class Brush<br>Differences: class Brush|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: setColor(color: common2D.Color): void;<br>Differences: setColor(color: common2D.Color): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: setAntiAlias(aa: boolean): void;<br>Differences: setAntiAlias(aa: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: setAlpha(alpha: number): void;<br>Differences: setAlpha(alpha: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: setColorFilter(filter: ColorFilter): void;<br>Differences: setColorFilter(filter: ColorFilter): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: setBlendMode(mode: BlendMode): void;<br>Differences: setBlendMode(mode: BlendMode): void;|api/@ohos.graphics.drawing.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.graphics.common2D.d.ts<br>Differences: ArkGraphics 2D|api/@ohos.graphics.common2D.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.graphics.drawing.d.ts<br>Differences: ArkGraphics 2D|api/@ohos.graphics.drawing.d.ts|
