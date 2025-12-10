| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API卡片权限变更|类名：global；<br>API声明：declare namespace effectKit<br>差异内容：NA|类名：global；<br>API声明：declare namespace effectKit<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：effectKit；<br>API声明：interface Filter<br>差异内容：NA|类名：effectKit；<br>API声明：interface Filter<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：Filter；<br>API声明：blur(radius: number): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：blur(radius: number): Filter;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：Filter；<br>API声明：brightness(bright: number): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：brightness(bright: number): Filter;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：Filter；<br>API声明：grayscale(): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：grayscale(): Filter;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：Filter；<br>API声明：getEffectPixelMap(): Promise\<image.PixelMap>;<br>差异内容：NA|类名：Filter；<br>API声明：getEffectPixelMap(): Promise\<image.PixelMap>;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：effectKit；<br>API声明：interface ColorPicker<br>差异内容：NA|类名：effectKit；<br>API声明：interface ColorPicker<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：ColorPicker；<br>API声明：getMainColor(): Promise\<Color>;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getMainColor(): Promise\<Color>;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：ColorPicker；<br>API声明：getMainColorSync(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getMainColorSync(): Color;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：ColorPicker；<br>API声明：getLargestProportionColor(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getLargestProportionColor(): Color;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：ColorPicker；<br>API声明：getHighestSaturationColor(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getHighestSaturationColor(): Color;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：ColorPicker；<br>API声明：getAverageColor(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getAverageColor(): Color;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：ColorPicker；<br>API声明：isBlackOrWhiteOrGrayColor(color: number): boolean;<br>差异内容：NA|类名：ColorPicker；<br>API声明：isBlackOrWhiteOrGrayColor(color: number): boolean;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：effectKit；<br>API声明：interface Color<br>差异内容：NA|类名：effectKit；<br>API声明：interface Color<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：Color；<br>API声明：red: number;<br>差异内容：NA|类名：Color；<br>API声明：red: number;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：Color；<br>API声明：green: number;<br>差异内容：NA|类名：Color；<br>API声明：green: number;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：Color；<br>API声明：blue: number;<br>差异内容：NA|类名：Color；<br>API声明：blue: number;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：Color；<br>API声明：alpha: number;<br>差异内容：NA|类名：Color；<br>API声明：alpha: number;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：effectKit；<br>API声明：function createEffect(source: image.PixelMap): Filter;<br>差异内容：NA|类名：effectKit；<br>API声明：function createEffect(source: image.PixelMap): Filter;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|API卡片权限变更|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：form|api/@ohos.effectKit.d.ts|
|函数变更|类名：Canvas；<br>API声明：drawImage(pixelmap: image.PixelMap, left: number, top: number): void;<br>差异内容：NA|类名：Canvas；<br>API声明：drawImage(pixelmap: image.PixelMap, left: number, top: number, samplingOptions?: SamplingOptions): void;<br>差异内容：samplingOptions?: SamplingOptions|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：common2D；<br>API声明：interface Point<br>差异内容：interface Point|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Point；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Point；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：common2D；<br>API声明：interface Point3d<br>差异内容：interface Point3d|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：Point3d；<br>API声明：z: number;<br>差异内容：z: number;|api/@ohos.graphics.common2D.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum PathDirection<br>差异内容：enum PathDirection|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathDirection；<br>API声明：CLOCKWISE = 0<br>差异内容：CLOCKWISE = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathDirection；<br>API声明：COUNTER_CLOCKWISE = 1<br>差异内容：COUNTER_CLOCKWISE = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum PathFillType<br>差异内容：enum PathFillType|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathFillType；<br>API声明：WINDING = 0<br>差异内容：WINDING = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathFillType；<br>API声明：EVEN_ODD = 1<br>差异内容：EVEN_ODD = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathFillType；<br>API声明：INVERSE_WINDING = 2<br>差异内容：INVERSE_WINDING = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathFillType；<br>API声明：INVERSE_EVEN_ODD = 3<br>差异内容：INVERSE_EVEN_ODD = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum PathMeasureMatrixFlags<br>差异内容：enum PathMeasureMatrixFlags|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathMeasureMatrixFlags；<br>API声明：GET_POSITION_MATRIX = 0<br>差异内容：GET_POSITION_MATRIX = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathMeasureMatrixFlags；<br>API声明：GET_TANGENT_MATRIX = 1<br>差异内容：GET_TANGENT_MATRIX = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathMeasureMatrixFlags；<br>API声明：GET_POSITION_AND_TANGENT_MATRIX = 2<br>差异内容：GET_POSITION_AND_TANGENT_MATRIX = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class RoundRect<br>差异内容：class RoundRect|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RoundRect；<br>API声明：setCorner(pos: CornerPos, x: number, y: number): void;<br>差异内容：setCorner(pos: CornerPos, x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RoundRect；<br>API声明：getCorner(pos: CornerPos): common2D.Point;<br>差异内容：getCorner(pos: CornerPos): common2D.Point;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RoundRect；<br>API声明：offset(dx: number, dy: number): void;<br>差异内容：offset(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum PathOp<br>差异内容：enum PathOp|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathOp；<br>API声明：DIFFERENCE = 0<br>差异内容：DIFFERENCE = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathOp；<br>API声明：INTERSECT = 1<br>差异内容：INTERSECT = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathOp；<br>API声明：UNION = 2<br>差异内容：UNION = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathOp；<br>API声明：XOR = 3<br>差异内容：XOR = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathOp；<br>API声明：REVERSE_DIFFERENCE = 4<br>差异内容：REVERSE_DIFFERENCE = 4|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：conicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void;<br>差异内容：conicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：rMoveTo(dx: number, dy: number): void;<br>差异内容：rMoveTo(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：rLineTo(dx: number, dy: number): void;<br>差异内容：rLineTo(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：rQuadTo(dx1: number, dy1: number, dx2: number, dy2: number): void;<br>差异内容：rQuadTo(dx1: number, dy1: number, dx2: number, dy2: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：rConicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void;<br>差异内容：rConicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：rCubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void;<br>差异内容：rCubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：addPolygon(points: Array\<common2D.Point>, close: boolean): void;<br>差异内容：addPolygon(points: Array\<common2D.Point>, close: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：op(path: Path, pathOp: PathOp): boolean;<br>差异内容：op(path: Path, pathOp: PathOp): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：addArc(rect: common2D.Rect, startAngle: number, sweepAngle: number): void;<br>差异内容：addArc(rect: common2D.Rect, startAngle: number, sweepAngle: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：addCircle(x: number, y: number, radius: number, pathDirection?: PathDirection): void;<br>差异内容：addCircle(x: number, y: number, radius: number, pathDirection?: PathDirection): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：addOval(rect: common2D.Rect, start: number, pathDirection?: PathDirection): void;<br>差异内容：addOval(rect: common2D.Rect, start: number, pathDirection?: PathDirection): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：addRect(rect: common2D.Rect, pathDirection?: PathDirection): void;<br>差异内容：addRect(rect: common2D.Rect, pathDirection?: PathDirection): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：addRoundRect(roundRect: RoundRect, pathDirection?: PathDirection): void;<br>差异内容：addRoundRect(roundRect: RoundRect, pathDirection?: PathDirection): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：addPath(path: Path, matrix?: Matrix \| null): void;<br>差异内容：addPath(path: Path, matrix?: Matrix \| null): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：transform(matrix: Matrix): void;<br>差异内容：transform(matrix: Matrix): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：contains(x: number, y: number): boolean;<br>差异内容：contains(x: number, y: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：setFillType(pathFillType: PathFillType): void;<br>差异内容：setFillType(pathFillType: PathFillType): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：getBounds(): common2D.Rect;<br>差异内容：getBounds(): common2D.Rect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：offset(dx: number, dy: number): Path;<br>差异内容：offset(dx: number, dy: number): Path;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：getLength(forceClosed: boolean): number;<br>差异内容：getLength(forceClosed: boolean): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：getPositionAndTangent(forceClosed: boolean, distance: number, position: common2D.Point, tangent: common2D.Point): boolean;<br>差异内容：getPositionAndTangent(forceClosed: boolean, distance: number, position: common2D.Point, tangent: common2D.Point): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：isClosed(): boolean;<br>差异内容：isClosed(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：getMatrix(forceClosed: boolean, distance: number, matrix: Matrix, flags: PathMeasureMatrixFlags): boolean;<br>差异内容：getMatrix(forceClosed: boolean, distance: number, matrix: Matrix, flags: PathMeasureMatrixFlags): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：buildFromSvgString(str: string): boolean;<br>差异内容：buildFromSvgString(str: string): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum PointMode<br>差异内容：enum PointMode|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PointMode；<br>API声明：POINTS = 0<br>差异内容：POINTS = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PointMode；<br>API声明：LINES = 1<br>差异内容：LINES = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PointMode；<br>API声明：POLYGON = 2<br>差异内容：POLYGON = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum FilterMode<br>差异内容：enum FilterMode|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FilterMode；<br>API声明：FILTER_MODE_NEAREST = 0<br>差异内容：FILTER_MODE_NEAREST = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FilterMode；<br>API声明：FILTER_MODE_LINEAR = 1<br>差异内容：FILTER_MODE_LINEAR = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum ShadowFlag<br>差异内容：enum ShadowFlag|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShadowFlag；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShadowFlag；<br>API声明：TRANSPARENT_OCCLUDER = 1<br>差异内容：TRANSPARENT_OCCLUDER = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShadowFlag；<br>API声明：GEOMETRIC_ONLY = 2<br>差异内容：GEOMETRIC_ONLY = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShadowFlag；<br>API声明：ALL = 3<br>差异内容：ALL = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class SamplingOptions<br>差异内容：class SamplingOptions|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawRoundRect(roundRect: RoundRect): void;<br>差异内容：drawRoundRect(roundRect: RoundRect): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawNestedRoundRect(outer: RoundRect, inner: RoundRect): void;<br>差异内容：drawNestedRoundRect(outer: RoundRect, inner: RoundRect): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawBackground(brush: Brush): void;<br>差异内容：drawBackground(brush: Brush): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number, ambientColor: common2D.Color, spotColor: common2D.Color, flag: ShadowFlag): void;<br>差异内容：drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number, ambientColor: common2D.Color, spotColor: common2D.Color, flag: ShadowFlag): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawImageRect(pixelmap: image.PixelMap, dstRect: common2D.Rect, samplingOptions?: SamplingOptions): void;<br>差异内容：drawImageRect(pixelmap: image.PixelMap, dstRect: common2D.Rect, samplingOptions?: SamplingOptions): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawImageRectWithSrc(pixelmap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect, samplingOptions?: SamplingOptions, constraint?: SrcRectConstraint): void;<br>差异内容：drawImageRectWithSrc(pixelmap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect, samplingOptions?: SamplingOptions, constraint?: SrcRectConstraint): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawOval(oval: common2D.Rect): void;<br>差异内容：drawOval(oval: common2D.Rect): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawArc(arc: common2D.Rect, startAngle: number, sweepAngle: number): void;<br>差异内容：drawArc(arc: common2D.Rect, startAngle: number, sweepAngle: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawPoints(points: Array\<common2D.Point>, mode?: PointMode): void;<br>差异内容：drawPoints(points: Array\<common2D.Point>, mode?: PointMode): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawSingleCharacter(text: string, font: Font, x: number, y: number): void;<br>差异内容：drawSingleCharacter(text: string, font: Font, x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawPixelMapMesh(pixelmap: image.PixelMap, meshWidth: number, meshHeight: number, vertices: Array\<number>, vertOffset: number, colors: Array\<number>, colorOffset: number): void;<br>差异内容：drawPixelMapMesh(pixelmap: image.PixelMap, meshWidth: number, meshHeight: number, vertices: Array\<number>, vertOffset: number, colors: Array\<number>, colorOffset: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawRegion(region: Region): void;<br>差异内容：drawRegion(region: Region): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：save(): number;<br>差异内容：save(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：saveLayer(rect?: common2D.Rect \| null, brush?: Brush \| null): number;<br>差异内容：saveLayer(rect?: common2D.Rect \| null, brush?: Brush \| null): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：clear(color: common2D.Color): void;<br>差异内容：clear(color: common2D.Color): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：restore(): void;<br>差异内容：restore(): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：restoreToCount(count: number): void;<br>差异内容：restoreToCount(count: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：getSaveCount(): number;<br>差异内容：getSaveCount(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：getWidth(): number;<br>差异内容：getWidth(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：getHeight(): number;<br>差异内容：getHeight(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：getLocalClipBounds(): common2D.Rect;<br>差异内容：getLocalClipBounds(): common2D.Rect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：getTotalMatrix(): Matrix;<br>差异内容：getTotalMatrix(): Matrix;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：scale(sx: number, sy: number): void;<br>差异内容：scale(sx: number, sy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：skew(sx: number, sy: number): void;<br>差异内容：skew(sx: number, sy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：rotate(degrees: number, sx: number, sy: number): void;<br>差异内容：rotate(degrees: number, sx: number, sy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：translate(dx: number, dy: number): void;<br>差异内容：translate(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：clipPath(path: Path, clipOp?: ClipOp, doAntiAlias?: boolean): void;<br>差异内容：clipPath(path: Path, clipOp?: ClipOp, doAntiAlias?: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：clipRect(rect: common2D.Rect, clipOp?: ClipOp, doAntiAlias?: boolean): void;<br>差异内容：clipRect(rect: common2D.Rect, clipOp?: ClipOp, doAntiAlias?: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：concatMatrix(matrix: Matrix): void;<br>差异内容：concatMatrix(matrix: Matrix): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：clipRegion(region: Region, clipOp?: ClipOp): void;<br>差异内容：clipRegion(region: Region, clipOp?: ClipOp): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：clipRoundRect(roundRect: RoundRect, clipOp?: ClipOp, doAntiAlias?: boolean): void;<br>差异内容：clipRoundRect(roundRect: RoundRect, clipOp?: ClipOp, doAntiAlias?: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：isClipEmpty(): boolean;<br>差异内容：isClipEmpty(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：setMatrix(matrix: Matrix): void;<br>差异内容：setMatrix(matrix: Matrix): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：resetMatrix(): void;<br>差异内容：resetMatrix(): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum ClipOp<br>差异内容：enum ClipOp|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ClipOp；<br>API声明：DIFFERENCE = 0<br>差异内容：DIFFERENCE = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ClipOp；<br>API声明：INTERSECT = 1<br>差异内容：INTERSECT = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextBlob；<br>API声明：static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob;<br>差异内容：static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TextBlob；<br>API声明：uniqueID(): number;<br>差异内容：uniqueID(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Typeface；<br>API声明：static makeFromFile(filePath: string): Typeface;<br>差异内容：static makeFromFile(filePath: string): Typeface;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum FontEdging<br>差异内容：enum FontEdging|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontEdging；<br>API声明：ALIAS = 0<br>差异内容：ALIAS = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontEdging；<br>API声明：ANTI_ALIAS = 1<br>差异内容：ANTI_ALIAS = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontEdging；<br>API声明：SUBPIXEL_ANTI_ALIAS = 2<br>差异内容：SUBPIXEL_ANTI_ALIAS = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum FontHinting<br>差异内容：enum FontHinting|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontHinting；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontHinting；<br>API声明：SLIGHT = 1<br>差异内容：SLIGHT = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontHinting；<br>API声明：NORMAL = 2<br>差异内容：NORMAL = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontHinting；<br>API声明：FULL = 3<br>差异内容：FULL = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：measureSingleCharacter(text: string): number;<br>差异内容：measureSingleCharacter(text: string): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：setScaleX(scaleX: number): void;<br>差异内容：setScaleX(scaleX: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：setSkewX(skewX: number): void;<br>差异内容：setSkewX(skewX: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：setEdging(edging: FontEdging): void;<br>差异内容：setEdging(edging: FontEdging): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：setHinting(hinting: FontHinting): void;<br>差异内容：setHinting(hinting: FontHinting): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：countText(text: string): number;<br>差异内容：countText(text: string): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：setBaselineSnap(isBaselineSnap: boolean): void;<br>差异内容：setBaselineSnap(isBaselineSnap: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：isBaselineSnap(): boolean;<br>差异内容：isBaselineSnap(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void;<br>差异内容：setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：isEmbeddedBitmaps(): boolean;<br>差异内容：isEmbeddedBitmaps(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：setForceAutoHinting(isForceAutoHinting: boolean): void;<br>差异内容：setForceAutoHinting(isForceAutoHinting: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：isForceAutoHinting(): boolean;<br>差异内容：isForceAutoHinting(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getWidths(glyphs: Array\<number>): Array\<number>;<br>差异内容：getWidths(glyphs: Array\<number>): Array\<number>;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：textToGlyphs(text: string, glyphCount?: number): Array\<number>;<br>差异内容：textToGlyphs(text: string, glyphCount?: number): Array\<number>;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：isSubpixel(): boolean;<br>差异内容：isSubpixel(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：isLinearMetrics(): boolean;<br>差异内容：isLinearMetrics(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getSkewX(): number;<br>差异内容：getSkewX(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：isEmbolden(): boolean;<br>差异内容：isEmbolden(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getScaleX(): number;<br>差异内容：getScaleX(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getHinting(): FontHinting;<br>差异内容：getHinting(): FontHinting;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getEdging(): FontEdging;<br>差异内容：getEdging(): FontEdging;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum FontMetricsFlags<br>差异内容：enum FontMetricsFlags|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetricsFlags；<br>API声明：UNDERLINE_THICKNESS_VALID = 1 \<\< 0<br>差异内容：UNDERLINE_THICKNESS_VALID = 1 \<\< 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetricsFlags；<br>API声明：UNDERLINE_POSITION_VALID = 1 \<\< 1<br>差异内容：UNDERLINE_POSITION_VALID = 1 \<\< 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetricsFlags；<br>API声明：STRIKETHROUGH_THICKNESS_VALID = 1 \<\< 2<br>差异内容：STRIKETHROUGH_THICKNESS_VALID = 1 \<\< 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetricsFlags；<br>API声明：STRIKETHROUGH_POSITION_VALID = 1 \<\< 3<br>差异内容：STRIKETHROUGH_POSITION_VALID = 1 \<\< 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetricsFlags；<br>API声明：BOUNDS_INVALID = 1 \<\< 4<br>差异内容：BOUNDS_INVALID = 1 \<\< 4|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：flags?: FontMetricsFlags;<br>差异内容：flags?: FontMetricsFlags;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：avgCharWidth?: number;<br>差异内容：avgCharWidth?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：maxCharWidth?: number;<br>差异内容：maxCharWidth?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：xMin?: number;<br>差异内容：xMin?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：xMax?: number;<br>差异内容：xMax?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：xHeight?: number;<br>差异内容：xHeight?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：capHeight?: number;<br>差异内容：capHeight?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：underlineThickness?: number;<br>差异内容：underlineThickness?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：underlinePosition?: number;<br>差异内容：underlinePosition?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：strikethroughThickness?: number;<br>差异内容：strikethroughThickness?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：FontMetrics；<br>API声明：strikethroughPosition?: number;<br>差异内容：strikethroughPosition?: number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class Lattice<br>差异内容：class Lattice|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Lattice；<br>API声明：static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<common2D.Color> \| null): Lattice;<br>差异内容：static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<common2D.Color> \| null): Lattice;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum RectType<br>差异内容：enum RectType|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RectType；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RectType；<br>API声明：TRANSPARENT = 1<br>差异内容：TRANSPARENT = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RectType；<br>API声明：FIXEDCOLOR = 2<br>差异内容：FIXEDCOLOR = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class MaskFilter<br>差异内容：class MaskFilter|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：MaskFilter；<br>API声明：static createBlurMaskFilter(blurType: BlurType, sigma: number): MaskFilter;<br>差异内容：static createBlurMaskFilter(blurType: BlurType, sigma: number): MaskFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class PathEffect<br>差异内容：class PathEffect|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathEffect；<br>API声明：static createDashPathEffect(intervals: Array\<number>, phase: number): PathEffect;<br>差异内容：static createDashPathEffect(intervals: Array\<number>, phase: number): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathEffect；<br>API声明：static createCornerPathEffect(radius: number): PathEffect;<br>差异内容：static createCornerPathEffect(radius: number): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class ShaderEffect<br>差异内容：class ShaderEffect|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShaderEffect；<br>API声明：static createColorShader(color: number): ShaderEffect;<br>差异内容：static createColorShader(color: number): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShaderEffect；<br>API声明：static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;<br>差异内容：static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShaderEffect；<br>API声明：static createRadialGradient(centerPt: common2D.Point, radius: number, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;<br>差异内容：static createRadialGradient(centerPt: common2D.Point, radius: number, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShaderEffect；<br>API声明：static createSweepGradient(centerPt: common2D.Point, colors: Array\<number>, mode: TileMode, startAngle: number, endAngle: number, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;<br>差异内容：static createSweepGradient(centerPt: common2D.Point, colors: Array\<number>, mode: TileMode, startAngle: number, endAngle: number, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShaderEffect；<br>API声明：static createConicalGradient(startPt: common2D.Point, startRadius: number, endPt: common2D.Point, endRadius: number, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;<br>差异内容：static createConicalGradient(startPt: common2D.Point, startRadius: number, endPt: common2D.Point, endRadius: number, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum TileMode<br>差异内容：enum TileMode|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TileMode；<br>API声明：CLAMP = 0<br>差异内容：CLAMP = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TileMode；<br>API声明：REPEAT = 1<br>差异内容：REPEAT = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TileMode；<br>API声明：MIRROR = 2<br>差异内容：MIRROR = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：TileMode；<br>API声明：DECAL = 3<br>差异内容：DECAL = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class ShadowLayer<br>差异内容：class ShadowLayer|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShadowLayer；<br>API声明：static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer;<br>差异内容：static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ColorFilter；<br>API声明：static createMatrixColorFilter(matrix: Array\<number>): ColorFilter;<br>差异内容：static createMatrixColorFilter(matrix: Array\<number>): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class ImageFilter<br>差异内容：class ImageFilter|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ImageFilter；<br>API声明：static createBlurImageFilter(sigmaX: number, sigmaY: number, tileMode: TileMode, imageFilter?: ImageFilter \| null): ImageFilter;<br>差异内容：static createBlurImageFilter(sigmaX: number, sigmaY: number, tileMode: TileMode, imageFilter?: ImageFilter \| null): ImageFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ImageFilter；<br>API声明：static createFromColorFilter(colorFilter: ColorFilter, imageFilter?: ImageFilter \| null): ImageFilter;<br>差异内容：static createFromColorFilter(colorFilter: ColorFilter, imageFilter?: ImageFilter \| null): ImageFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum JoinStyle<br>差异内容：enum JoinStyle|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：JoinStyle；<br>API声明：MITER_JOIN = 0<br>差异内容：MITER_JOIN = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：JoinStyle；<br>API声明：ROUND_JOIN = 1<br>差异内容：ROUND_JOIN = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：JoinStyle；<br>API声明：BEVEL_JOIN = 2<br>差异内容：BEVEL_JOIN = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum CapStyle<br>差异内容：enum CapStyle|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：CapStyle；<br>API声明：FLAT_CAP = 0<br>差异内容：FLAT_CAP = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：CapStyle；<br>API声明：SQUARE_CAP = 1<br>差异内容：SQUARE_CAP = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：CapStyle；<br>API声明：ROUND_CAP = 2<br>差异内容：ROUND_CAP = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum BlurType<br>差异内容：enum BlurType|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlurType；<br>API声明：NORMAL = 0<br>差异内容：NORMAL = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlurType；<br>API声明：SOLID = 1<br>差异内容：SOLID = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlurType；<br>API声明：OUTER = 2<br>差异内容：OUTER = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：BlurType；<br>API声明：INNER = 3<br>差异内容：INNER = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setMiterLimit(miter: number): void;<br>差异内容：setMiterLimit(miter: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：getMiterLimit(): number;<br>差异内容：getMiterLimit(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setShaderEffect(shaderEffect: ShaderEffect): void;<br>差异内容：setShaderEffect(shaderEffect: ShaderEffect): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：getColor(): common2D.Color;<br>差异内容：getColor(): common2D.Color;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：getWidth(): number;<br>差异内容：getWidth(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：isAntiAlias(): boolean;<br>差异内容：isAntiAlias(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：getAlpha(): number;<br>差异内容：getAlpha(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：getColorFilter(): ColorFilter;<br>差异内容：getColorFilter(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setImageFilter(filter: ImageFilter \| null): void;<br>差异内容：setImageFilter(filter: ImageFilter \| null): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setMaskFilter(filter: MaskFilter): void;<br>差异内容：setMaskFilter(filter: MaskFilter): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setPathEffect(effect: PathEffect): void;<br>差异内容：setPathEffect(effect: PathEffect): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setShadowLayer(shadowLayer: ShadowLayer): void;<br>差异内容：setShadowLayer(shadowLayer: ShadowLayer): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setJoinStyle(style: JoinStyle): void;<br>差异内容：setJoinStyle(style: JoinStyle): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：getJoinStyle(): JoinStyle;<br>差异内容：getJoinStyle(): JoinStyle;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setCapStyle(style: CapStyle): void;<br>差异内容：setCapStyle(style: CapStyle): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：getCapStyle(): CapStyle;<br>差异内容：getCapStyle(): CapStyle;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：reset(): void;<br>差异内容：reset(): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：getFillPath(src: Path, dst: Path): boolean;<br>差异内容：getFillPath(src: Path, dst: Path): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：getColor(): common2D.Color;<br>差异内容：getColor(): common2D.Color;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：isAntiAlias(): boolean;<br>差异内容：isAntiAlias(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：getAlpha(): number;<br>差异内容：getAlpha(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：getColorFilter(): ColorFilter;<br>差异内容：getColorFilter(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setImageFilter(filter: ImageFilter \| null): void;<br>差异内容：setImageFilter(filter: ImageFilter \| null): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setMaskFilter(filter: MaskFilter): void;<br>差异内容：setMaskFilter(filter: MaskFilter): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setShadowLayer(shadowLayer: ShadowLayer): void;<br>差异内容：setShadowLayer(shadowLayer: ShadowLayer): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setShaderEffect(shaderEffect: ShaderEffect): void;<br>差异内容：setShaderEffect(shaderEffect: ShaderEffect): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：reset(): void;<br>差异内容：reset(): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class Matrix<br>差异内容：class Matrix|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：setRotation(degree: number, px: number, py: number): void;<br>差异内容：setRotation(degree: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：setScale(sx: number, sy: number, px: number, py: number): void;<br>差异内容：setScale(sx: number, sy: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：setTranslation(dx: number, dy: number): void;<br>差异内容：setTranslation(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：setMatrix(values: Array\<number>): void;<br>差异内容：setMatrix(values: Array\<number>): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：preConcat(matrix: Matrix): void;<br>差异内容：preConcat(matrix: Matrix): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：isEqual(matrix: Matrix): Boolean;<br>差异内容：isEqual(matrix: Matrix): Boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：invert(matrix: Matrix): Boolean;<br>差异内容：invert(matrix: Matrix): Boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：isIdentity(): Boolean;<br>差异内容：isIdentity(): Boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：getValue(index: number): number;<br>差异内容：getValue(index: number): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：postRotate(degree: number, px: number, py: number): void;<br>差异内容：postRotate(degree: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：postScale(sx: number, sy: number, px: number, py: number): void;<br>差异内容：postScale(sx: number, sy: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：postTranslate(dx: number, dy: number): void;<br>差异内容：postTranslate(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：preRotate(degree: number, px: number, py: number): void;<br>差异内容：preRotate(degree: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：preScale(sx: number, sy: number, px: number, py: number): void;<br>差异内容：preScale(sx: number, sy: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：preTranslate(dx: number, dy: number): void;<br>差异内容：preTranslate(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：reset(): void;<br>差异内容：reset(): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：mapPoints(src: Array\<common2D.Point>): Array\<common2D.Point>;<br>差异内容：mapPoints(src: Array\<common2D.Point>): Array\<common2D.Point>;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：getAll(): Array\<number>;<br>差异内容：getAll(): Array\<number>;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：mapRect(dst: common2D.Rect, src: common2D.Rect): boolean;<br>差异内容：mapRect(dst: common2D.Rect, src: common2D.Rect): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：setRectToRect(src: common2D.Rect, dst: common2D.Rect, scaleToFit: ScaleToFit): boolean;<br>差异内容：setRectToRect(src: common2D.Rect, dst: common2D.Rect, scaleToFit: ScaleToFit): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Matrix；<br>API声明：setPolyToPoly(src: Array\<common2D.Point>, dst: Array\<common2D.Point>, count: number): boolean;<br>差异内容：setPolyToPoly(src: Array\<common2D.Point>, dst: Array\<common2D.Point>, count: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum ScaleToFit<br>差异内容：enum ScaleToFit|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ScaleToFit；<br>API声明：FILL_SCALE_TO_FIT = 0<br>差异内容：FILL_SCALE_TO_FIT = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ScaleToFit；<br>API声明：START_SCALE_TO_FIT = 1<br>差异内容：START_SCALE_TO_FIT = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ScaleToFit；<br>API声明：CENTER_SCALE_TO_FIT = 2<br>差异内容：CENTER_SCALE_TO_FIT = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ScaleToFit；<br>API声明：END_SCALE_TO_FIT = 3<br>差异内容：END_SCALE_TO_FIT = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class Region<br>差异内容：class Region|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Region；<br>API声明：isPointContained(x: number, y: number): boolean;<br>差异内容：isPointContained(x: number, y: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Region；<br>API声明：isRegionContained(other: Region): boolean;<br>差异内容：isRegionContained(other: Region): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Region；<br>API声明：op(region: Region, regionOp: RegionOp): boolean;<br>差异内容：op(region: Region, regionOp: RegionOp): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Region；<br>API声明：quickReject(left: number, top: number, right: number, bottom: number): boolean;<br>差异内容：quickReject(left: number, top: number, right: number, bottom: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Region；<br>API声明：setPath(path: Path, clip: Region): boolean;<br>差异内容：setPath(path: Path, clip: Region): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Region；<br>API声明：setRect(left: number, top: number, right: number, bottom: number): boolean;<br>差异内容：setRect(left: number, top: number, right: number, bottom: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum RegionOp<br>差异内容：enum RegionOp|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RegionOp；<br>API声明：DIFFERENCE = 0<br>差异内容：DIFFERENCE = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RegionOp；<br>API声明：INTERSECT = 1<br>差异内容：INTERSECT = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RegionOp；<br>API声明：UNION = 2<br>差异内容：UNION = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RegionOp；<br>API声明：XOR = 3<br>差异内容：XOR = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RegionOp；<br>API声明：REVERSE_DIFFERENCE = 4<br>差异内容：REVERSE_DIFFERENCE = 4|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：RegionOp；<br>API声明：REPLACE = 5<br>差异内容：REPLACE = 5|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum CornerPos<br>差异内容：enum CornerPos|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：CornerPos；<br>API声明：TOP_LEFT_POS = 0<br>差异内容：TOP_LEFT_POS = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：CornerPos；<br>API声明：TOP_RIGHT_POS = 1<br>差异内容：TOP_RIGHT_POS = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：CornerPos；<br>API声明：BOTTOM_RIGHT_POS = 2<br>差异内容：BOTTOM_RIGHT_POS = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：CornerPos；<br>API声明：BOTTOM_LEFT_POS = 3<br>差异内容：BOTTOM_LEFT_POS = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum SrcRectConstraint<br>差异内容：enum SrcRectConstraint|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：SrcRectConstraint；<br>API声明：STRICT = 0<br>差异内容：STRICT = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：SrcRectConstraint；<br>API声明：FAST = 1<br>差异内容：FAST = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace sendableColorSpaceManager<br>差异内容：declare namespace sendableColorSpaceManager|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|新增API|NA|类名：sendableColorSpaceManager；<br>API声明：type ISendable = lang.ISendable;<br>差异内容：type ISendable = lang.ISendable;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|新增API|NA|类名：sendableColorSpaceManager；<br>API声明：interface ColorSpaceManager<br>差异内容：interface ColorSpaceManager|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|新增API|NA|类名：ColorSpaceManager；<br>API声明：getColorSpaceName(): colorSpaceManager.ColorSpace;<br>差异内容：getColorSpaceName(): colorSpaceManager.ColorSpace;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|新增API|NA|类名：ColorSpaceManager；<br>API声明：getWhitePoint(): collections.Array\<number>;<br>差异内容：getWhitePoint(): collections.Array\<number>;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|新增API|NA|类名：ColorSpaceManager；<br>API声明：getGamma(): number;<br>差异内容：getGamma(): number;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|新增API|NA|类名：sendableColorSpaceManager；<br>API声明：function create(colorSpaceName: colorSpaceManager.ColorSpace): ColorSpaceManager;<br>差异内容：function create(colorSpaceName: colorSpaceManager.ColorSpace): ColorSpaceManager;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|新增API|NA|类名：sendableColorSpaceManager；<br>API声明：function create(primaries: colorSpaceManager.ColorSpacePrimaries, gamma: number): ColorSpaceManager;<br>差异内容：function create(primaries: colorSpaceManager.ColorSpacePrimaries, gamma: number): ColorSpaceManager;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|新增API|NA|类名：global；<br>API声明：declare namespace text<br>差异内容：declare namespace text|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum TextAlign<br>差异内容：enum TextAlign|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextAlign；<br>API声明：LEFT = 0<br>差异内容：LEFT = 0|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextAlign；<br>API声明：RIGHT = 1<br>差异内容：RIGHT = 1|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextAlign；<br>API声明：CENTER = 2<br>差异内容：CENTER = 2|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextAlign；<br>API声明：JUSTIFY = 3<br>差异内容：JUSTIFY = 3|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextAlign；<br>API声明：START = 4<br>差异内容：START = 4|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextAlign；<br>API声明：END = 5<br>差异内容：END = 5|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum TextDirection<br>差异内容：enum TextDirection|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDirection；<br>API声明：RTL<br>差异内容：RTL|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDirection；<br>API声明：LTR<br>差异内容：LTR|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum BreakStrategy<br>差异内容：enum BreakStrategy|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：BreakStrategy；<br>API声明：GREEDY<br>差异内容：GREEDY|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：BreakStrategy；<br>API声明：HIGH_QUALITY<br>差异内容：HIGH_QUALITY|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：BreakStrategy；<br>API声明：BALANCED<br>差异内容：BALANCED|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum WordBreak<br>差异内容：enum WordBreak|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：WordBreak；<br>API声明：NORMAL<br>差异内容：NORMAL|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：WordBreak；<br>API声明：BREAK_ALL<br>差异内容：BREAK_ALL|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：WordBreak；<br>API声明：BREAK_WORD<br>差异内容：BREAK_WORD|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface Decoration<br>差异内容：interface Decoration|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Decoration；<br>API声明：textDecoration?: TextDecorationType;<br>差异内容：textDecoration?: TextDecorationType;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Decoration；<br>API声明：color?: common2D.Color;<br>差异内容：color?: common2D.Color;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Decoration；<br>API声明：decorationStyle?: TextDecorationStyle;<br>差异内容：decorationStyle?: TextDecorationStyle;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Decoration；<br>API声明：decorationThicknessScale?: number;<br>差异内容：decorationThicknessScale?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum TextDecorationType<br>差异内容：enum TextDecorationType|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDecorationType；<br>API声明：NONE<br>差异内容：NONE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDecorationType；<br>API声明：UNDERLINE<br>差异内容：UNDERLINE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDecorationType；<br>API声明：OVERLINE<br>差异内容：OVERLINE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDecorationType；<br>API声明：LINE_THROUGH<br>差异内容：LINE_THROUGH|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum TextDecorationStyle<br>差异内容：enum TextDecorationStyle|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：SOLID<br>差异内容：SOLID|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：DOUBLE<br>差异内容：DOUBLE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：DOTTED<br>差异内容：DOTTED|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：DASHED<br>差异内容：DASHED|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextDecorationStyle；<br>API声明：WAVY<br>差异内容：WAVY|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum FontWeight<br>差异内容：enum FontWeight|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWeight；<br>API声明：W100<br>差异内容：W100|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWeight；<br>API声明：W200<br>差异内容：W200|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWeight；<br>API声明：W300<br>差异内容：W300|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWeight；<br>API声明：W400<br>差异内容：W400|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWeight；<br>API声明：W500<br>差异内容：W500|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWeight；<br>API声明：W600<br>差异内容：W600|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWeight；<br>API声明：W700<br>差异内容：W700|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWeight；<br>API声明：W800<br>差异内容：W800|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWeight；<br>API声明：W900<br>差异内容：W900|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum FontStyle<br>差异内容：enum FontStyle|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontStyle；<br>API声明：NORMAL<br>差异内容：NORMAL|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontStyle；<br>API声明：ITALIC<br>差异内容：ITALIC|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontStyle；<br>API声明：OBLIQUE<br>差异内容：OBLIQUE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum FontWidth<br>差异内容：enum FontWidth|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWidth；<br>API声明：ULTRA_CONDENSED = 1<br>差异内容：ULTRA_CONDENSED = 1|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWidth；<br>API声明：EXTRA_CONDENSED = 2<br>差异内容：EXTRA_CONDENSED = 2|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWidth；<br>API声明：CONDENSED = 3<br>差异内容：CONDENSED = 3|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWidth；<br>API声明：SEMI_CONDENSED = 4<br>差异内容：SEMI_CONDENSED = 4|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWidth；<br>API声明：NORMAL = 5<br>差异内容：NORMAL = 5|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWidth；<br>API声明：SEMI_EXPANDED = 6<br>差异内容：SEMI_EXPANDED = 6|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWidth；<br>API声明：EXPANDED = 7<br>差异内容：EXPANDED = 7|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWidth；<br>API声明：EXTRA_EXPANDED = 8<br>差异内容：EXTRA_EXPANDED = 8|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontWidth；<br>API声明：ULTRA_EXPANDED = 9<br>差异内容：ULTRA_EXPANDED = 9|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum TextHeightBehavior<br>差异内容：enum TextHeightBehavior|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextHeightBehavior；<br>API声明：ALL = 0x0<br>差异内容：ALL = 0x0|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextHeightBehavior；<br>API声明：DISABLE_FIRST_ASCENT = 0x1<br>差异内容：DISABLE_FIRST_ASCENT = 0x1|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextHeightBehavior；<br>API声明：DISABLE_LAST_ASCENT = 0x2<br>差异内容：DISABLE_LAST_ASCENT = 0x2|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextHeightBehavior；<br>API声明：DISABLE_ALL = 0x1 \| 0x2<br>差异内容：DISABLE_ALL = 0x1 \| 0x2|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum TextBaseline<br>差异内容：enum TextBaseline|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextBaseline；<br>API声明：ALPHABETIC<br>差异内容：ALPHABETIC|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextBaseline；<br>API声明：IDEOGRAPHIC<br>差异内容：IDEOGRAPHIC|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum EllipsisMode<br>差异内容：enum EllipsisMode|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：EllipsisMode；<br>API声明：START<br>差异内容：START|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：EllipsisMode；<br>API声明：MIDDLE<br>差异内容：MIDDLE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：EllipsisMode；<br>API声明：END<br>差异内容：END|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface TextShadow<br>差异内容：interface TextShadow|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextShadow；<br>API声明：color?: common2D.Color;<br>差异内容：color?: common2D.Color;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextShadow；<br>API声明：point?: common2D.Point;<br>差异内容：point?: common2D.Point;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextShadow；<br>API声明：blurRadius?: number;<br>差异内容：blurRadius?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface RectStyle<br>差异内容：interface RectStyle|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectStyle；<br>API声明：color: common2D.Color;<br>差异内容：color: common2D.Color;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectStyle；<br>API声明：leftTopRadius: number;<br>差异内容：leftTopRadius: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectStyle；<br>API声明：rightTopRadius: number;<br>差异内容：rightTopRadius: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectStyle；<br>API声明：rightBottomRadius: number;<br>差异内容：rightBottomRadius: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectStyle；<br>API声明：leftBottomRadius: number;<br>差异内容：leftBottomRadius: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface FontFeature<br>差异内容：interface FontFeature|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontFeature；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontFeature；<br>API声明：value: number;<br>差异内容：value: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface FontVariation<br>差异内容：interface FontVariation|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontVariation；<br>API声明：axis: string;<br>差异内容：axis: string;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontVariation；<br>API声明：value: number;<br>差异内容：value: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface TextStyle<br>差异内容：interface TextStyle|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：decoration?: Decoration;<br>差异内容：decoration?: Decoration;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：color?: common2D.Color;<br>差异内容：color?: common2D.Color;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：fontWeight?: FontWeight;<br>差异内容：fontWeight?: FontWeight;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：fontStyle?: FontStyle;<br>差异内容：fontStyle?: FontStyle;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：baseline?: TextBaseline;<br>差异内容：baseline?: TextBaseline;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：fontFamilies?: Array\<string>;<br>差异内容：fontFamilies?: Array\<string>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：fontSize?: number;<br>差异内容：fontSize?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：letterSpacing?: number;<br>差异内容：letterSpacing?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：wordSpacing?: number;<br>差异内容：wordSpacing?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：heightScale?: number;<br>差异内容：heightScale?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：halfLeading?: boolean;<br>差异内容：halfLeading?: boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：heightOnly?: boolean;<br>差异内容：heightOnly?: boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：ellipsis?: string;<br>差异内容：ellipsis?: string;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：ellipsisMode?: EllipsisMode;<br>差异内容：ellipsisMode?: EllipsisMode;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：locale?: string;<br>差异内容：locale?: string;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：baselineShift?: number;<br>差异内容：baselineShift?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：fontFeatures?: Array\<FontFeature>;<br>差异内容：fontFeatures?: Array\<FontFeature>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：textShadows?: Array\<TextShadow>;<br>差异内容：textShadows?: Array\<TextShadow>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：backgroundRect?: RectStyle;<br>差异内容：backgroundRect?: RectStyle;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextStyle；<br>API声明：fontVariations?: Array\<FontVariation>;<br>差异内容：fontVariations?: Array\<FontVariation>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：class FontCollection<br>差异内容：class FontCollection|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontCollection；<br>API声明：static getGlobalInstance(): FontCollection;<br>差异内容：static getGlobalInstance(): FontCollection;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontCollection；<br>API声明：loadFontSync(name: string, path: string \| Resource): void;<br>差异内容：loadFontSync(name: string, path: string \| Resource): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontCollection；<br>API声明：clearCaches(): void;<br>差异内容：clearCaches(): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface StrutStyle<br>差异内容：interface StrutStyle|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：fontFamilies?: Array\<string>;<br>差异内容：fontFamilies?: Array\<string>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：fontStyle?: FontStyle;<br>差异内容：fontStyle?: FontStyle;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：fontWidth?: FontWidth;<br>差异内容：fontWidth?: FontWidth;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：fontWeight?: FontWeight;<br>差异内容：fontWeight?: FontWeight;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：fontSize?: number;<br>差异内容：fontSize?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：height?: number;<br>差异内容：height?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：leading?: number;<br>差异内容：leading?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：forceHeight?: boolean;<br>差异内容：forceHeight?: boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：enabled?: boolean;<br>差异内容：enabled?: boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：heightOverride?: boolean;<br>差异内容：heightOverride?: boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：StrutStyle；<br>API声明：halfLeading?: boolean;<br>差异内容：halfLeading?: boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface ParagraphStyle<br>差异内容：interface ParagraphStyle|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：textStyle?: TextStyle;<br>差异内容：textStyle?: TextStyle;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：textDirection?: TextDirection;<br>差异内容：textDirection?: TextDirection;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：align?: TextAlign;<br>差异内容：align?: TextAlign;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：wordBreak?: WordBreak;<br>差异内容：wordBreak?: WordBreak;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：maxLines?: number;<br>差异内容：maxLines?: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：breakStrategy?: BreakStrategy;<br>差异内容：breakStrategy?: BreakStrategy;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：strutStyle?: StrutStyle;<br>差异内容：strutStyle?: StrutStyle;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：textHeightBehavior?: TextHeightBehavior;<br>差异内容：textHeightBehavior?: TextHeightBehavior;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum PlaceholderAlignment<br>差异内容：enum PlaceholderAlignment|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderAlignment；<br>API声明：OFFSET_AT_BASELINE<br>差异内容：OFFSET_AT_BASELINE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderAlignment；<br>API声明：ABOVE_BASELINE<br>差异内容：ABOVE_BASELINE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderAlignment；<br>API声明：BELOW_BASELINE<br>差异内容：BELOW_BASELINE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderAlignment；<br>API声明：TOP_OF_ROW_BOX<br>差异内容：TOP_OF_ROW_BOX|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderAlignment；<br>API声明：BOTTOM_OF_ROW_BOX<br>差异内容：BOTTOM_OF_ROW_BOX|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderAlignment；<br>API声明：CENTER_OF_ROW_BOX<br>差异内容：CENTER_OF_ROW_BOX|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface PlaceholderSpan<br>差异内容：interface PlaceholderSpan|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderSpan；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderSpan；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderSpan；<br>API声明：align: PlaceholderAlignment;<br>差异内容：align: PlaceholderAlignment;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderSpan；<br>API声明：baseline: TextBaseline;<br>差异内容：baseline: TextBaseline;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PlaceholderSpan；<br>API声明：baselineOffset: number;<br>差异内容：baselineOffset: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface Range<br>差异内容：interface Range|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Range；<br>API声明：start: number;<br>差异内容：start: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Range；<br>API声明：end: number;<br>差异内容：end: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：class Paragraph<br>差异内容：class Paragraph|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：layoutSync(width: number): void;<br>差异内容：layoutSync(width: number): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：paint(canvas: drawing.Canvas, x: number, y: number): void;<br>差异内容：paint(canvas: drawing.Canvas, x: number, y: number): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：paintOnPath(canvas: drawing.Canvas, path: drawing.Path, hOffset: number, vOffset: number): void;<br>差异内容：paintOnPath(canvas: drawing.Canvas, path: drawing.Path, hOffset: number, vOffset: number): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getMaxWidth(): number;<br>差异内容：getMaxWidth(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getHeight(): number;<br>差异内容：getHeight(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getLongestLine(): number;<br>差异内容：getLongestLine(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getMinIntrinsicWidth(): number;<br>差异内容：getMinIntrinsicWidth(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getMaxIntrinsicWidth(): number;<br>差异内容：getMaxIntrinsicWidth(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getAlphabeticBaseline(): number;<br>差异内容：getAlphabeticBaseline(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getIdeographicBaseline(): number;<br>差异内容：getIdeographicBaseline(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getRectsForRange(range: Range, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array\<TextBox>;<br>差异内容：getRectsForRange(range: Range, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array\<TextBox>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getRectsForPlaceholders(): Array\<TextBox>;<br>差异内容：getRectsForPlaceholders(): Array\<TextBox>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity;<br>差异内容：getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getWordBoundary(offset: number): Range;<br>差异内容：getWordBoundary(offset: number): Range;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getLineCount(): number;<br>差异内容：getLineCount(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getLineHeight(line: number): number;<br>差异内容：getLineHeight(line: number): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getLineWidth(line: number): number;<br>差异内容：getLineWidth(line: number): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：didExceedMaxLines(): boolean;<br>差异内容：didExceedMaxLines(): boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getTextLines(): Array\<TextLine>;<br>差异内容：getTextLines(): Array\<TextLine>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getActualTextRange(lineNumber: number, includeSpaces: boolean): Range;<br>差异内容：getActualTextRange(lineNumber: number, includeSpaces: boolean): Range;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getLineMetrics(): Array\<LineMetrics>;<br>差异内容：getLineMetrics(): Array\<LineMetrics>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：getLineMetrics(lineNumber: number): LineMetrics \| undefined;<br>差异内容：getLineMetrics(lineNumber: number): LineMetrics \| undefined;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface TextBox<br>差异内容：interface TextBox|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextBox；<br>API声明：rect: common2D.Rect;<br>差异内容：rect: common2D.Rect;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextBox；<br>API声明：direction: TextDirection;<br>差异内容：direction: TextDirection;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface PositionWithAffinity<br>差异内容：interface PositionWithAffinity|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PositionWithAffinity；<br>API声明：position: number;<br>差异内容：position: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：PositionWithAffinity；<br>API声明：affinity: Affinity;<br>差异内容：affinity: Affinity;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum RectWidthStyle<br>差异内容：enum RectWidthStyle|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectWidthStyle；<br>API声明：TIGHT<br>差异内容：TIGHT|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectWidthStyle；<br>API声明：MAX<br>差异内容：MAX|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum RectHeightStyle<br>差异内容：enum RectHeightStyle|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectHeightStyle；<br>API声明：TIGHT<br>差异内容：TIGHT|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectHeightStyle；<br>API声明：MAX<br>差异内容：MAX|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectHeightStyle；<br>API声明：INCLUDE_LINE_SPACE_MIDDLE<br>差异内容：INCLUDE_LINE_SPACE_MIDDLE|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectHeightStyle；<br>API声明：INCLUDE_LINE_SPACE_TOP<br>差异内容：INCLUDE_LINE_SPACE_TOP|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectHeightStyle；<br>API声明：INCLUDE_LINE_SPACE_BOTTOM<br>差异内容：INCLUDE_LINE_SPACE_BOTTOM|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RectHeightStyle；<br>API声明：STRUT<br>差异内容：STRUT|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：enum Affinity<br>差异内容：enum Affinity|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Affinity；<br>API声明：UPSTREAM<br>差异内容：UPSTREAM|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Affinity；<br>API声明：DOWNSTREAM<br>差异内容：DOWNSTREAM|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：class ParagraphBuilder<br>差异内容：class ParagraphBuilder|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphBuilder；<br>API声明：pushStyle(textStyle: TextStyle): void;<br>差异内容：pushStyle(textStyle: TextStyle): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphBuilder；<br>API声明：popStyle(): void;<br>差异内容：popStyle(): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphBuilder；<br>API声明：addText(text: string): void;<br>差异内容：addText(text: string): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphBuilder；<br>API声明：addPlaceholder(placeholderSpan: PlaceholderSpan): void;<br>差异内容：addPlaceholder(placeholderSpan: PlaceholderSpan): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphBuilder；<br>API声明：build(): Paragraph;<br>差异内容：build(): Paragraph;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphBuilder；<br>API声明：addSymbol(symbolId: number): void;<br>差异内容：addSymbol(symbolId: number): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：class TextLine<br>差异内容：class TextLine|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：getGlyphCount(): number;<br>差异内容：getGlyphCount(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：getTextRange(): Range;<br>差异内容：getTextRange(): Range;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：getGlyphRuns(): Array\<Run>;<br>差异内容：getGlyphRuns(): Array\<Run>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：paint(canvas: drawing.Canvas, x: number, y: number): void;<br>差异内容：paint(canvas: drawing.Canvas, x: number, y: number): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：class Run<br>差异内容：class Run|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getGlyphCount(): number;<br>差异内容：getGlyphCount(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getGlyphs(): Array\<number>;<br>差异内容：getGlyphs(): Array\<number>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getPositions(): Array\<common2D.Point>;<br>差异内容：getPositions(): Array\<common2D.Point>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getOffsets(): Array\<common2D.Point>;<br>差异内容：getOffsets(): Array\<common2D.Point>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getFont(): drawing.Font;<br>差异内容：getFont(): drawing.Font;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：paint(canvas: drawing.Canvas, x: number, y: number): void;<br>差异内容：paint(canvas: drawing.Canvas, x: number, y: number): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface RunMetrics<br>差异内容：interface RunMetrics|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RunMetrics；<br>API声明：textStyle: TextStyle;<br>差异内容：textStyle: TextStyle;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：RunMetrics；<br>API声明：fontMetrics: drawing.FontMetrics;<br>差异内容：fontMetrics: drawing.FontMetrics;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface LineMetrics<br>差异内容：interface LineMetrics|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：startIndex: number;<br>差异内容：startIndex: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：endIndex: number;<br>差异内容：endIndex: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：ascent: number;<br>差异内容：ascent: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：descent: number;<br>差异内容：descent: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：left: number;<br>差异内容：left: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：baseline: number;<br>差异内容：baseline: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：lineNumber: number;<br>差异内容：lineNumber: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：topHeight: number;<br>差异内容：topHeight: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineMetrics；<br>API声明：runMetrics: Map\<number, RunMetrics>;<br>差异内容：runMetrics: Map\<number, RunMetrics>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace uiEffect<br>差异内容：declare namespace uiEffect|api/@ohos.graphics.uiEffect.d.ts|
|新增API|NA|类名：uiEffect；<br>API声明：interface Filter<br>差异内容：interface Filter|api/@ohos.graphics.uiEffect.d.ts|
|新增API|NA|类名：Filter；<br>API声明：blur(blurRadius: number): Filter;<br>差异内容：blur(blurRadius: number): Filter;|api/@ohos.graphics.uiEffect.d.ts|
|新增API|NA|类名：uiEffect；<br>API声明：interface VisualEffect<br>差异内容：interface VisualEffect|api/@ohos.graphics.uiEffect.d.ts|
|新增API|NA|类名：uiEffect；<br>API声明：function createFilter(): Filter;<br>差异内容：function createFilter(): Filter;|api/@ohos.graphics.uiEffect.d.ts|
|新增API|NA|类名：uiEffect；<br>API声明：function createEffect(): VisualEffect;<br>差异内容：function createEffect(): VisualEffect;|api/@ohos.graphics.uiEffect.d.ts|
|新增API|NA|类名：Filter；<br>API声明：invert(): Filter;<br>差异内容：invert(): Filter;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：Filter；<br>API声明：setColorMatrix(colorMatrix: Array\<number>): Filter;<br>差异内容：setColorMatrix(colorMatrix: Array\<number>): Filter;|api/@ohos.effectKit.d.ts|
|新增API|NA|类名：ColorPicker；<br>API声明：getTopProportionColors(colorCount: number): Array\<Color \| null>;<br>差异内容：getTopProportionColors(colorCount: number): Array\<Color \| null>;|api/@ohos.effectKit.d.ts|
|kit变更|ArkGraphics 2D|ArkGraphics2D|api/@ohos.graphics.common2D.d.ts|
|kit变更|ArkGraphics 2D|ArkGraphics2D|api/@ohos.graphics.drawing.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.graphics.sendableColorSpaceManager.d.ets<br>差异内容：ArkGraphics2D|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.graphics.text.d.ts<br>差异内容：ArkGraphics2D|api/@ohos.graphics.text.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.graphics.uiEffect.d.ts<br>差异内容：ArkGraphics2D|api/@ohos.graphics.uiEffect.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace effectKit<br>差异内容：NA|类名：global；<br>API声明：declare namespace effectKit<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：effectKit；<br>API声明：interface Filter<br>差异内容：NA|类名：effectKit；<br>API声明：interface Filter<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：Filter；<br>API声明：blur(radius: number): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：blur(radius: number): Filter;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：Filter；<br>API声明：brightness(bright: number): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：brightness(bright: number): Filter;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：Filter；<br>API声明：grayscale(): Filter;<br>差异内容：NA|类名：Filter；<br>API声明：grayscale(): Filter;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：Filter；<br>API声明：getEffectPixelMap(): Promise\<image.PixelMap>;<br>差异内容：NA|类名：Filter；<br>API声明：getEffectPixelMap(): Promise\<image.PixelMap>;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：effectKit；<br>API声明：interface ColorPicker<br>差异内容：NA|类名：effectKit；<br>API声明：interface ColorPicker<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：ColorPicker；<br>API声明：getMainColor(): Promise\<Color>;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getMainColor(): Promise\<Color>;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：ColorPicker；<br>API声明：getMainColorSync(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getMainColorSync(): Color;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：ColorPicker；<br>API声明：getLargestProportionColor(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getLargestProportionColor(): Color;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：ColorPicker；<br>API声明：getHighestSaturationColor(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getHighestSaturationColor(): Color;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：ColorPicker；<br>API声明：getAverageColor(): Color;<br>差异内容：NA|类名：ColorPicker；<br>API声明：getAverageColor(): Color;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：ColorPicker；<br>API声明：isBlackOrWhiteOrGrayColor(color: number): boolean;<br>差异内容：NA|类名：ColorPicker；<br>API声明：isBlackOrWhiteOrGrayColor(color: number): boolean;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：effectKit；<br>API声明：interface Color<br>差异内容：NA|类名：effectKit；<br>API声明：interface Color<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：Color；<br>API声明：red: number;<br>差异内容：NA|类名：Color；<br>API声明：red: number;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：Color；<br>API声明：green: number;<br>差异内容：NA|类名：Color；<br>API声明：green: number;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：Color；<br>API声明：blue: number;<br>差异内容：NA|类名：Color；<br>API声明：blue: number;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：Color；<br>API声明：alpha: number;<br>差异内容：NA|类名：Color；<br>API声明：alpha: number;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：effectKit；<br>API声明：function createEffect(source: image.PixelMap): Filter;<br>差异内容：NA|类名：effectKit；<br>API声明：function createEffect(source: image.PixelMap): Filter;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：NA|类名：effectKit；<br>API声明：function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>差异内容：atomicservice|api/@ohos.effectKit.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace colorSpaceManager<br>差异内容：NA|类名：global；<br>API声明：declare namespace colorSpaceManager<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：colorSpaceManager；<br>API声明：enum ColorSpace<br>差异内容：NA|类名：colorSpaceManager；<br>API声明：enum ColorSpace<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：UNKNOWN = 0<br>差异内容：NA|类名：ColorSpace；<br>API声明：UNKNOWN = 0<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：ADOBE_RGB_1998 = 1<br>差异内容：NA|类名：ColorSpace；<br>API声明：ADOBE_RGB_1998 = 1<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：DCI_P3 = 2<br>差异内容：NA|类名：ColorSpace；<br>API声明：DCI_P3 = 2<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：DISPLAY_P3 = 3<br>差异内容：NA|类名：ColorSpace；<br>API声明：DISPLAY_P3 = 3<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：SRGB = 4<br>差异内容：NA|类名：ColorSpace；<br>API声明：SRGB = 4<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT709 = 6<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT709 = 6<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT601_EBU = 7<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT601_EBU = 7<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT601_SMPTE_C = 8<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT601_SMPTE_C = 8<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT2020_HLG = 9<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT2020_HLG = 9<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT2020_PQ = 10<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT2020_PQ = 10<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：P3_HLG = 11<br>差异内容：NA|类名：ColorSpace；<br>API声明：P3_HLG = 11<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：P3_PQ = 12<br>差异内容：NA|类名：ColorSpace；<br>API声明：P3_PQ = 12<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：ADOBE_RGB_1998_LIMIT = 13<br>差异内容：NA|类名：ColorSpace；<br>API声明：ADOBE_RGB_1998_LIMIT = 13<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：DISPLAY_P3_LIMIT = 14<br>差异内容：NA|类名：ColorSpace；<br>API声明：DISPLAY_P3_LIMIT = 14<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：SRGB_LIMIT = 15<br>差异内容：NA|类名：ColorSpace；<br>API声明：SRGB_LIMIT = 15<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT709_LIMIT = 16<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT709_LIMIT = 16<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT601_EBU_LIMIT = 17<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT601_EBU_LIMIT = 17<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT601_SMPTE_C_LIMIT = 18<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT601_SMPTE_C_LIMIT = 18<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT2020_HLG_LIMIT = 19<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT2020_HLG_LIMIT = 19<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：BT2020_PQ_LIMIT = 20<br>差异内容：NA|类名：ColorSpace；<br>API声明：BT2020_PQ_LIMIT = 20<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：P3_HLG_LIMIT = 21<br>差异内容：NA|类名：ColorSpace；<br>API声明：P3_HLG_LIMIT = 21<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：P3_PQ_LIMIT = 22<br>差异内容：NA|类名：ColorSpace；<br>API声明：P3_PQ_LIMIT = 22<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：LINEAR_P3 = 23<br>差异内容：NA|类名：ColorSpace；<br>API声明：LINEAR_P3 = 23<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：LINEAR_SRGB = 24<br>差异内容：NA|类名：ColorSpace；<br>API声明：LINEAR_SRGB = 24<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：LINEAR_BT709 = LINEAR_SRGB<br>差异内容：NA|类名：ColorSpace；<br>API声明：LINEAR_BT709 = LINEAR_SRGB<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：LINEAR_BT2020 = 25<br>差异内容：NA|类名：ColorSpace；<br>API声明：LINEAR_BT2020 = 25<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：DISPLAY_SRGB = SRGB<br>差异内容：NA|类名：ColorSpace；<br>API声明：DISPLAY_SRGB = SRGB<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：DISPLAY_P3_SRGB = DISPLAY_P3<br>差异内容：NA|类名：ColorSpace；<br>API声明：DISPLAY_P3_SRGB = DISPLAY_P3<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：DISPLAY_P3_HLG = P3_HLG<br>差异内容：NA|类名：ColorSpace；<br>API声明：DISPLAY_P3_HLG = P3_HLG<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：DISPLAY_P3_PQ = P3_PQ<br>差异内容：NA|类名：ColorSpace；<br>API声明：DISPLAY_P3_PQ = P3_PQ<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：ColorSpace；<br>API声明：CUSTOM = 5<br>差异内容：NA|类名：ColorSpace；<br>API声明：CUSTOM = 5<br>差异内容：atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace hdrCapability<br>差异内容：NA|类名：global；<br>API声明：declare namespace hdrCapability<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|API从不支持元服务到支持元服务|类名：hdrCapability；<br>API声明：enum HDRFormat<br>差异内容：NA|类名：hdrCapability；<br>API声明：enum HDRFormat<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|API从不支持元服务到支持元服务|类名：HDRFormat；<br>API声明：NONE = 0<br>差异内容：NA|类名：HDRFormat；<br>API声明：NONE = 0<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|API从不支持元服务到支持元服务|类名：HDRFormat；<br>API声明：VIDEO_HLG = 1<br>差异内容：NA|类名：HDRFormat；<br>API声明：VIDEO_HLG = 1<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|API从不支持元服务到支持元服务|类名：HDRFormat；<br>API声明：VIDEO_HDR10 = 2<br>差异内容：NA|类名：HDRFormat；<br>API声明：VIDEO_HDR10 = 2<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|API从不支持元服务到支持元服务|类名：HDRFormat；<br>API声明：VIDEO_HDR_VIVID = 3<br>差异内容：NA|类名：HDRFormat；<br>API声明：VIDEO_HDR_VIVID = 3<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|API从不支持元服务到支持元服务|类名：HDRFormat；<br>API声明：IMAGE_HDR_VIVID_DUAL = 4<br>差异内容：NA|类名：HDRFormat；<br>API声明：IMAGE_HDR_VIVID_DUAL = 4<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|API从不支持元服务到支持元服务|类名：HDRFormat；<br>API声明：IMAGE_HDR_VIVID_SINGLE = 5<br>差异内容：NA|类名：HDRFormat；<br>API声明：IMAGE_HDR_VIVID_SINGLE = 5<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|API从不支持元服务到支持元服务|类名：HDRFormat；<br>API声明：IMAGE_HDR_ISO_DUAL = 6<br>差异内容：NA|类名：HDRFormat；<br>API声明：IMAGE_HDR_ISO_DUAL = 6<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|API从不支持元服务到支持元服务|类名：HDRFormat；<br>API声明：IMAGE_HDR_ISO_SINGLE = 7<br>差异内容：NA|类名：HDRFormat；<br>API声明：IMAGE_HDR_ISO_SINGLE = 7<br>差异内容：atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
