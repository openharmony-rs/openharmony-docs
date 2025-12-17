| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：global；<br>API声明：declare namespace effectKit<br>差异内容：NA|类名：global；<br>API声明：declare namespace effectKit<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：effectKit；<br>API声明：interface Filter<br>差异内容：NA|类名：effectKit；<br>API声明：interface Filter<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Filter；<br>API声明：blur(radius: number): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：blur(radius: number): Filter;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Filter；<br>API声明：brightness(bright: number): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：brightness(bright: number): Filter;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Filter；<br>API声明：grayscale(): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：grayscale(): Filter;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Filter；<br>API声明：invert(): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：invert(): Filter;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Filter；<br>API声明：setColorMatrix(colorMatrix: Array\<number>): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：setColorMatrix(colorMatrix: Array\<number>): Filter;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Filter；<br>API声明：getEffectPixelMap(): Promise\<image.PixelMap>;<br>差异内容：NA|类名：Filter；<br>API声明：getEffectPixelMap(): Promise\<image.PixelMap>;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：effectKit；<br>API声明：interface ColorPicker<br>差异内容：NA|类名：effectKit；<br>API声明：interface ColorPicker<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：ColorPicker；<br>API声明：getMainColor(): Promise\<Color>;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getMainColor(): Promise\<Color>;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：ColorPicker；<br>API声明：getMainColorSync(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getMainColorSync(): Color;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：ColorPicker；<br>API声明：getLargestProportionColor(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getLargestProportionColor(): Color;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：ColorPicker；<br>API声明：getTopProportionColors(colorCount: number): Array\<Color \| null>;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getTopProportionColors(colorCount: number): Array\<Color \| null>;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：ColorPicker；<br>API声明：getHighestSaturationColor(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getHighestSaturationColor(): Color;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：ColorPicker；<br>API声明：getAverageColor(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getAverageColor(): Color;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：ColorPicker；<br>API声明：isBlackOrWhiteOrGrayColor(color: number): boolean;<br>差异内容：NA|类名：ColorPicker；<br>API声明：isBlackOrWhiteOrGrayColor(color: number): boolean;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：effectKit；<br>API声明：interface Color<br>差异内容：NA|类名：effectKit；<br>API声明：interface Color<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Color；<br>API声明：red: number;<br>差异内容：NA|类名：Color；<br>API声明：red: number;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Color；<br>API声明：green: number;<br>差异内容：NA|类名：Color；<br>API声明：green: number;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Color；<br>API声明：blue: number;<br>差异内容：NA|类名：Color；<br>API声明：blue: number;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：Color；<br>API声明：alpha: number;<br>差异内容：NA|类名：Color；<br>API声明：alpha: number;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：effectKit；<br>API声明：function createEffect(source: image.PixelMap): Filter;<br>差异内容：NA|类名：effectKit；<br>API声明：function createEffect(source: image.PixelMap): Filter;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|API跨平台权限变更|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：crossplatform|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：effectKit；<br>API声明：enum TileMode<br>差异内容：enum TileMode|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：TileMode；<br>API声明：CLAMP = 0<br>差异内容：CLAMP = 0|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：TileMode；<br>API声明：REPEAT = 1<br>差异内容：REPEAT = 1|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：TileMode；<br>API声明：MIRROR = 2<br>差异内容：MIRROR = 2|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：TileMode；<br>API声明：DECAL = 3<br>差异内容：DECAL = 3|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：text；<br>API声明：enum SystemFontType<br>差异内容：enum SystemFontType|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：SystemFontType；<br>API声明：ALL = 1 \<\< 0<br>差异内容：ALL = 1 \<\< 0|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：SystemFontType；<br>API声明：GENERIC = 1 \<\< 1<br>差异内容：GENERIC = 1 \<\< 1|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：SystemFontType；<br>API声明：STYLISH = 1 \<\< 2<br>差异内容：STYLISH = 1 \<\< 2|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：SystemFontType；<br>API声明：INSTALLED = 1 \<\< 3<br>差异内容：INSTALLED = 1 \<\< 3|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface FontDescriptor<br>差异内容：interface FontDescriptor|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：path?: string;<br>差异内容：path?: string;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：postScriptName?: string;<br>差异内容：postScriptName?: string;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：fullName?: string;<br>差异内容：fullName?: string;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：fontFamily?: string;<br>差异内容：fontFamily?: string;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：fontSubfamily?: string;<br>差异内容：fontSubfamily?: string;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：weight?: FontWeight;<br>差异内容：weight?: FontWeight;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：width?: number;<br>差异内容：width?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：italic?: number;<br>差异内容：italic?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：monoSpace?: boolean;<br>差异内容：monoSpace?: boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontDescriptor；<br>API声明：symbolic?: boolean;<br>差异内容：symbolic?: boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：function getSystemFontFullNamesByType(fontType: SystemFontType): Promise\<Array\<string>>;<br>差异内容：function getSystemFontFullNamesByType(fontType: SystemFontType): Promise\<Array\<string>>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：function getFontDescriptorByFullName(fullName: string, fontType: SystemFontType): Promise\<FontDescriptor>;<br>差异内容：function getFontDescriptorByFullName(fullName: string, fontType: SystemFontType): Promise\<FontDescriptor>;|api/@ohos.graphics.text.d.ts|
