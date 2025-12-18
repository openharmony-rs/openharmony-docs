| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|API widget permission change|Class name: global;<br>API declaration: declare namespace effectKit<br>Differences: NA|Class name: global;<br>API declaration: declare namespace effectKit<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: effectKit;<br>API declaration: interface Filter<br>Differences: NA|Class name: effectKit;<br>API declaration: interface Filter<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: Filter;<br>API declaration: blur(radius: number): Filter;<br>Differences: NA|Class name: Filter;<br>API declaration: blur(radius: number): Filter;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: Filter;<br>API declaration: brightness(bright: number): Filter;<br>Differences: NA|Class name: Filter;<br>API declaration: brightness(bright: number): Filter;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: Filter;<br>API declaration: grayscale(): Filter;<br>Differences: NA|Class name: Filter;<br>API declaration: grayscale(): Filter;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: Filter;<br>API declaration: getEffectPixelMap(): Promise\<image.PixelMap>;<br>Differences: NA|Class name: Filter;<br>API declaration: getEffectPixelMap(): Promise\<image.PixelMap>;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: effectKit;<br>API declaration: interface ColorPicker<br>Differences: NA|Class name: effectKit;<br>API declaration: interface ColorPicker<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: ColorPicker;<br>API declaration: getMainColor(): Promise\<Color>;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getMainColor(): Promise\<Color>;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: ColorPicker;<br>API declaration: getMainColorSync(): Color;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getMainColorSync(): Color;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: ColorPicker;<br>API declaration: getLargestProportionColor(): Color;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getLargestProportionColor(): Color;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: ColorPicker;<br>API declaration: getHighestSaturationColor(): Color;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getHighestSaturationColor(): Color;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: ColorPicker;<br>API declaration: getAverageColor(): Color;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getAverageColor(): Color;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: ColorPicker;<br>API declaration: isBlackOrWhiteOrGrayColor(color: number): boolean;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: isBlackOrWhiteOrGrayColor(color: number): boolean;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: effectKit;<br>API declaration: interface Color<br>Differences: NA|Class name: effectKit;<br>API declaration: interface Color<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: Color;<br>API declaration: red: number;<br>Differences: NA|Class name: Color;<br>API declaration: red: number;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: Color;<br>API declaration: green: number;<br>Differences: NA|Class name: Color;<br>API declaration: green: number;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: Color;<br>API declaration: blue: number;<br>Differences: NA|Class name: Color;<br>API declaration: blue: number;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: Color;<br>API declaration: alpha: number;<br>Differences: NA|Class name: Color;<br>API declaration: alpha: number;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: effectKit;<br>API declaration: function createEffect(source: image.PixelMap): Filter;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createEffect(source: image.PixelMap): Filter;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: form|api/@ohos.effectKit.d.ts|
|API widget permission change|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: form|api/@ohos.effectKit.d.ts|
|Function change|Class name: Canvas;<br>API declaration: drawImage(pixelmap: image.PixelMap, left: number, top: number): void;<br>Differences: NA|Class name: Canvas;<br>API declaration: drawImage(pixelmap: image.PixelMap, left: number, top: number, samplingOptions?: SamplingOptions): void;<br>Differences: samplingOptions?: SamplingOptions|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: common2D;<br>API declaration: interface Point<br>Differences: interface Point|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Point;<br>API declaration: x: number;<br>Differences: x: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Point;<br>API declaration: y: number;<br>Differences: y: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: common2D;<br>API declaration: interface Point3d<br>Differences: interface Point3d|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: Point3d;<br>API declaration: z: number;<br>Differences: z: number;|api/@ohos.graphics.common2D.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum PathDirection<br>Differences: enum PathDirection|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathDirection;<br>API declaration: CLOCKWISE = 0<br>Differences: CLOCKWISE = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathDirection;<br>API declaration: COUNTER_CLOCKWISE = 1<br>Differences: COUNTER_CLOCKWISE = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum PathFillType<br>Differences: enum PathFillType|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathFillType;<br>API declaration: WINDING = 0<br>Differences: WINDING = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathFillType;<br>API declaration: EVEN_ODD = 1<br>Differences: EVEN_ODD = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathFillType;<br>API declaration: INVERSE_WINDING = 2<br>Differences: INVERSE_WINDING = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathFillType;<br>API declaration: INVERSE_EVEN_ODD = 3<br>Differences: INVERSE_EVEN_ODD = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum PathMeasureMatrixFlags<br>Differences: enum PathMeasureMatrixFlags|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathMeasureMatrixFlags;<br>API declaration: GET_POSITION_MATRIX = 0<br>Differences: GET_POSITION_MATRIX = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathMeasureMatrixFlags;<br>API declaration: GET_TANGENT_MATRIX = 1<br>Differences: GET_TANGENT_MATRIX = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathMeasureMatrixFlags;<br>API declaration: GET_POSITION_AND_TANGENT_MATRIX = 2<br>Differences: GET_POSITION_AND_TANGENT_MATRIX = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class RoundRect<br>Differences: class RoundRect|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RoundRect;<br>API declaration: setCorner(pos: CornerPos, x: number, y: number): void;<br>Differences: setCorner(pos: CornerPos, x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RoundRect;<br>API declaration: getCorner(pos: CornerPos): common2D.Point;<br>Differences: getCorner(pos: CornerPos): common2D.Point;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RoundRect;<br>API declaration: offset(dx: number, dy: number): void;<br>Differences: offset(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum PathOp<br>Differences: enum PathOp|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathOp;<br>API declaration: DIFFERENCE = 0<br>Differences: DIFFERENCE = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathOp;<br>API declaration: INTERSECT = 1<br>Differences: INTERSECT = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathOp;<br>API declaration: UNION = 2<br>Differences: UNION = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathOp;<br>API declaration: XOR = 3<br>Differences: XOR = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathOp;<br>API declaration: REVERSE_DIFFERENCE = 4<br>Differences: REVERSE_DIFFERENCE = 4|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: conicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void;<br>Differences: conicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: rMoveTo(dx: number, dy: number): void;<br>Differences: rMoveTo(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: rLineTo(dx: number, dy: number): void;<br>Differences: rLineTo(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: rQuadTo(dx1: number, dy1: number, dx2: number, dy2: number): void;<br>Differences: rQuadTo(dx1: number, dy1: number, dx2: number, dy2: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: rConicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void;<br>Differences: rConicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: rCubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void;<br>Differences: rCubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: addPolygon(points: Array\<common2D.Point>, close: boolean): void;<br>Differences: addPolygon(points: Array\<common2D.Point>, close: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: op(path: Path, pathOp: PathOp): boolean;<br>Differences: op(path: Path, pathOp: PathOp): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: addArc(rect: common2D.Rect, startAngle: number, sweepAngle: number): void;<br>Differences: addArc(rect: common2D.Rect, startAngle: number, sweepAngle: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: addCircle(x: number, y: number, radius: number, pathDirection?: PathDirection): void;<br>Differences: addCircle(x: number, y: number, radius: number, pathDirection?: PathDirection): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: addOval(rect: common2D.Rect, start: number, pathDirection?: PathDirection): void;<br>Differences: addOval(rect: common2D.Rect, start: number, pathDirection?: PathDirection): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: addRect(rect: common2D.Rect, pathDirection?: PathDirection): void;<br>Differences: addRect(rect: common2D.Rect, pathDirection?: PathDirection): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: addRoundRect(roundRect: RoundRect, pathDirection?: PathDirection): void;<br>Differences: addRoundRect(roundRect: RoundRect, pathDirection?: PathDirection): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: addPath(path: Path, matrix?: Matrix \| null): void;<br>Differences: addPath(path: Path, matrix?: Matrix \| null): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: transform(matrix: Matrix): void;<br>Differences: transform(matrix: Matrix): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: contains(x: number, y: number): boolean;<br>Differences: contains(x: number, y: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: setFillType(pathFillType: PathFillType): void;<br>Differences: setFillType(pathFillType: PathFillType): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: getBounds(): common2D.Rect;<br>Differences: getBounds(): common2D.Rect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: offset(dx: number, dy: number): Path;<br>Differences: offset(dx: number, dy: number): Path;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: getLength(forceClosed: boolean): number;<br>Differences: getLength(forceClosed: boolean): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: getPositionAndTangent(forceClosed: boolean, distance: number, position: common2D.Point, tangent: common2D.Point): boolean;<br>Differences: getPositionAndTangent(forceClosed: boolean, distance: number, position: common2D.Point, tangent: common2D.Point): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: isClosed(): boolean;<br>Differences: isClosed(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: getMatrix(forceClosed: boolean, distance: number, matrix: Matrix, flags: PathMeasureMatrixFlags): boolean;<br>Differences: getMatrix(forceClosed: boolean, distance: number, matrix: Matrix, flags: PathMeasureMatrixFlags): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Path;<br>API declaration: buildFromSvgString(str: string): boolean;<br>Differences: buildFromSvgString(str: string): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum PointMode<br>Differences: enum PointMode|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PointMode;<br>API declaration: POINTS = 0<br>Differences: POINTS = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PointMode;<br>API declaration: LINES = 1<br>Differences: LINES = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PointMode;<br>API declaration: POLYGON = 2<br>Differences: POLYGON = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum FilterMode<br>Differences: enum FilterMode|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FilterMode;<br>API declaration: FILTER_MODE_NEAREST = 0<br>Differences: FILTER_MODE_NEAREST = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FilterMode;<br>API declaration: FILTER_MODE_LINEAR = 1<br>Differences: FILTER_MODE_LINEAR = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum ShadowFlag<br>Differences: enum ShadowFlag|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShadowFlag;<br>API declaration: NONE = 0<br>Differences: NONE = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShadowFlag;<br>API declaration: TRANSPARENT_OCCLUDER = 1<br>Differences: TRANSPARENT_OCCLUDER = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShadowFlag;<br>API declaration: GEOMETRIC_ONLY = 2<br>Differences: GEOMETRIC_ONLY = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShadowFlag;<br>API declaration: ALL = 3<br>Differences: ALL = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class SamplingOptions<br>Differences: class SamplingOptions|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawRoundRect(roundRect: RoundRect): void;<br>Differences: drawRoundRect(roundRect: RoundRect): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawNestedRoundRect(outer: RoundRect, inner: RoundRect): void;<br>Differences: drawNestedRoundRect(outer: RoundRect, inner: RoundRect): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawBackground(brush: Brush): void;<br>Differences: drawBackground(brush: Brush): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number, ambientColor: common2D.Color, spotColor: common2D.Color, flag: ShadowFlag): void;<br>Differences: drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number, ambientColor: common2D.Color, spotColor: common2D.Color, flag: ShadowFlag): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawImageRect(pixelmap: image.PixelMap, dstRect: common2D.Rect, samplingOptions?: SamplingOptions): void;<br>Differences: drawImageRect(pixelmap: image.PixelMap, dstRect: common2D.Rect, samplingOptions?: SamplingOptions): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawImageRectWithSrc(pixelmap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect, samplingOptions?: SamplingOptions, constraint?: SrcRectConstraint): void;<br>Differences: drawImageRectWithSrc(pixelmap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect, samplingOptions?: SamplingOptions, constraint?: SrcRectConstraint): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawOval(oval: common2D.Rect): void;<br>Differences: drawOval(oval: common2D.Rect): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawArc(arc: common2D.Rect, startAngle: number, sweepAngle: number): void;<br>Differences: drawArc(arc: common2D.Rect, startAngle: number, sweepAngle: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawPoints(points: Array\<common2D.Point>, mode?: PointMode): void;<br>Differences: drawPoints(points: Array\<common2D.Point>, mode?: PointMode): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawSingleCharacter(text: string, font: Font, x: number, y: number): void;<br>Differences: drawSingleCharacter(text: string, font: Font, x: number, y: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawPixelMapMesh(pixelmap: image.PixelMap, meshWidth: number, meshHeight: number, vertices: Array\<number>, vertOffset: number, colors: Array\<number>, colorOffset: number): void;<br>Differences: drawPixelMapMesh(pixelmap: image.PixelMap, meshWidth: number, meshHeight: number, vertices: Array\<number>, vertOffset: number, colors: Array\<number>, colorOffset: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: drawRegion(region: Region): void;<br>Differences: drawRegion(region: Region): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: save(): number;<br>Differences: save(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: saveLayer(rect?: common2D.Rect \| null, brush?: Brush \| null): number;<br>Differences: saveLayer(rect?: common2D.Rect \| null, brush?: Brush \| null): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: clear(color: common2D.Color): void;<br>Differences: clear(color: common2D.Color): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: restore(): void;<br>Differences: restore(): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: restoreToCount(count: number): void;<br>Differences: restoreToCount(count: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: getSaveCount(): number;<br>Differences: getSaveCount(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: getWidth(): number;<br>Differences: getWidth(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: getHeight(): number;<br>Differences: getHeight(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: getLocalClipBounds(): common2D.Rect;<br>Differences: getLocalClipBounds(): common2D.Rect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: getTotalMatrix(): Matrix;<br>Differences: getTotalMatrix(): Matrix;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: scale(sx: number, sy: number): void;<br>Differences: scale(sx: number, sy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: skew(sx: number, sy: number): void;<br>Differences: skew(sx: number, sy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: rotate(degrees: number, sx: number, sy: number): void;<br>Differences: rotate(degrees: number, sx: number, sy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: translate(dx: number, dy: number): void;<br>Differences: translate(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: clipPath(path: Path, clipOp?: ClipOp, doAntiAlias?: boolean): void;<br>Differences: clipPath(path: Path, clipOp?: ClipOp, doAntiAlias?: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: clipRect(rect: common2D.Rect, clipOp?: ClipOp, doAntiAlias?: boolean): void;<br>Differences: clipRect(rect: common2D.Rect, clipOp?: ClipOp, doAntiAlias?: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: concatMatrix(matrix: Matrix): void;<br>Differences: concatMatrix(matrix: Matrix): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: clipRegion(region: Region, clipOp?: ClipOp): void;<br>Differences: clipRegion(region: Region, clipOp?: ClipOp): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: clipRoundRect(roundRect: RoundRect, clipOp?: ClipOp, doAntiAlias?: boolean): void;<br>Differences: clipRoundRect(roundRect: RoundRect, clipOp?: ClipOp, doAntiAlias?: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: isClipEmpty(): boolean;<br>Differences: isClipEmpty(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: setMatrix(matrix: Matrix): void;<br>Differences: setMatrix(matrix: Matrix): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Canvas;<br>API declaration: resetMatrix(): void;<br>Differences: resetMatrix(): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum ClipOp<br>Differences: enum ClipOp|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ClipOp;<br>API declaration: DIFFERENCE = 0<br>Differences: DIFFERENCE = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ClipOp;<br>API declaration: INTERSECT = 1<br>Differences: INTERSECT = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextBlob;<br>API declaration: static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob;<br>Differences: static makeFromPosText(text: string, len: number, points: common2D.Point[], font: Font): TextBlob;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TextBlob;<br>API declaration: uniqueID(): number;<br>Differences: uniqueID(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Typeface;<br>API declaration: static makeFromFile(filePath: string): Typeface;<br>Differences: static makeFromFile(filePath: string): Typeface;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum FontEdging<br>Differences: enum FontEdging|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontEdging;<br>API declaration: ALIAS = 0<br>Differences: ALIAS = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontEdging;<br>API declaration: ANTI_ALIAS = 1<br>Differences: ANTI_ALIAS = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontEdging;<br>API declaration: SUBPIXEL_ANTI_ALIAS = 2<br>Differences: SUBPIXEL_ANTI_ALIAS = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum FontHinting<br>Differences: enum FontHinting|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontHinting;<br>API declaration: NONE = 0<br>Differences: NONE = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontHinting;<br>API declaration: SLIGHT = 1<br>Differences: SLIGHT = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontHinting;<br>API declaration: NORMAL = 2<br>Differences: NORMAL = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontHinting;<br>API declaration: FULL = 3<br>Differences: FULL = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: measureSingleCharacter(text: string): number;<br>Differences: measureSingleCharacter(text: string): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: setScaleX(scaleX: number): void;<br>Differences: setScaleX(scaleX: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: setSkewX(skewX: number): void;<br>Differences: setSkewX(skewX: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: setEdging(edging: FontEdging): void;<br>Differences: setEdging(edging: FontEdging): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: setHinting(hinting: FontHinting): void;<br>Differences: setHinting(hinting: FontHinting): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: countText(text: string): number;<br>Differences: countText(text: string): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: setBaselineSnap(isBaselineSnap: boolean): void;<br>Differences: setBaselineSnap(isBaselineSnap: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: isBaselineSnap(): boolean;<br>Differences: isBaselineSnap(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void;<br>Differences: setEmbeddedBitmaps(isEmbeddedBitmaps: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: isEmbeddedBitmaps(): boolean;<br>Differences: isEmbeddedBitmaps(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: setForceAutoHinting(isForceAutoHinting: boolean): void;<br>Differences: setForceAutoHinting(isForceAutoHinting: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: isForceAutoHinting(): boolean;<br>Differences: isForceAutoHinting(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: getWidths(glyphs: Array\<number>): Array\<number>;<br>Differences: getWidths(glyphs: Array\<number>): Array\<number>;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: textToGlyphs(text: string, glyphCount?: number): Array\<number>;<br>Differences: textToGlyphs(text: string, glyphCount?: number): Array\<number>;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: isSubpixel(): boolean;<br>Differences: isSubpixel(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: isLinearMetrics(): boolean;<br>Differences: isLinearMetrics(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: getSkewX(): number;<br>Differences: getSkewX(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: isEmbolden(): boolean;<br>Differences: isEmbolden(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: getScaleX(): number;<br>Differences: getScaleX(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: getHinting(): FontHinting;<br>Differences: getHinting(): FontHinting;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Font;<br>API declaration: getEdging(): FontEdging;<br>Differences: getEdging(): FontEdging;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum FontMetricsFlags<br>Differences: enum FontMetricsFlags|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetricsFlags;<br>API declaration: UNDERLINE_THICKNESS_VALID = 1 \<\< 0<br>Differences: UNDERLINE_THICKNESS_VALID = 1 \<\< 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetricsFlags;<br>API declaration: UNDERLINE_POSITION_VALID = 1 \<\< 1<br>Differences: UNDERLINE_POSITION_VALID = 1 \<\< 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetricsFlags;<br>API declaration: STRIKETHROUGH_THICKNESS_VALID = 1 \<\< 2<br>Differences: STRIKETHROUGH_THICKNESS_VALID = 1 \<\< 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetricsFlags;<br>API declaration: STRIKETHROUGH_POSITION_VALID = 1 \<\< 3<br>Differences: STRIKETHROUGH_POSITION_VALID = 1 \<\< 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetricsFlags;<br>API declaration: BOUNDS_INVALID = 1 \<\< 4<br>Differences: BOUNDS_INVALID = 1 \<\< 4|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: flags?: FontMetricsFlags;<br>Differences: flags?: FontMetricsFlags;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: avgCharWidth?: number;<br>Differences: avgCharWidth?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: maxCharWidth?: number;<br>Differences: maxCharWidth?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: xMin?: number;<br>Differences: xMin?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: xMax?: number;<br>Differences: xMax?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: xHeight?: number;<br>Differences: xHeight?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: capHeight?: number;<br>Differences: capHeight?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: underlineThickness?: number;<br>Differences: underlineThickness?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: underlinePosition?: number;<br>Differences: underlinePosition?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: strikethroughThickness?: number;<br>Differences: strikethroughThickness?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: FontMetrics;<br>API declaration: strikethroughPosition?: number;<br>Differences: strikethroughPosition?: number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class Lattice<br>Differences: class Lattice|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Lattice;<br>API declaration: static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<common2D.Color> \| null): Lattice;<br>Differences: static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<common2D.Color> \| null): Lattice;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum RectType<br>Differences: enum RectType|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RectType;<br>API declaration: DEFAULT = 0<br>Differences: DEFAULT = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RectType;<br>API declaration: TRANSPARENT = 1<br>Differences: TRANSPARENT = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RectType;<br>API declaration: FIXEDCOLOR = 2<br>Differences: FIXEDCOLOR = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class MaskFilter<br>Differences: class MaskFilter|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: MaskFilter;<br>API declaration: static createBlurMaskFilter(blurType: BlurType, sigma: number): MaskFilter;<br>Differences: static createBlurMaskFilter(blurType: BlurType, sigma: number): MaskFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class PathEffect<br>Differences: class PathEffect|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathEffect;<br>API declaration: static createDashPathEffect(intervals: Array\<number>, phase: number): PathEffect;<br>Differences: static createDashPathEffect(intervals: Array\<number>, phase: number): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: PathEffect;<br>API declaration: static createCornerPathEffect(radius: number): PathEffect;<br>Differences: static createCornerPathEffect(radius: number): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class ShaderEffect<br>Differences: class ShaderEffect|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShaderEffect;<br>API declaration: static createColorShader(color: number): ShaderEffect;<br>Differences: static createColorShader(color: number): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShaderEffect;<br>API declaration: static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;<br>Differences: static createLinearGradient(startPt: common2D.Point, endPt: common2D.Point, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShaderEffect;<br>API declaration: static createRadialGradient(centerPt: common2D.Point, radius: number, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;<br>Differences: static createRadialGradient(centerPt: common2D.Point, radius: number, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShaderEffect;<br>API declaration: static createSweepGradient(centerPt: common2D.Point, colors: Array\<number>, mode: TileMode, startAngle: number, endAngle: number, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;<br>Differences: static createSweepGradient(centerPt: common2D.Point, colors: Array\<number>, mode: TileMode, startAngle: number, endAngle: number, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShaderEffect;<br>API declaration: static createConicalGradient(startPt: common2D.Point, startRadius: number, endPt: common2D.Point, endRadius: number, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;<br>Differences: static createConicalGradient(startPt: common2D.Point, startRadius: number, endPt: common2D.Point, endRadius: number, colors: Array\<number>, mode: TileMode, pos?: Array\<number> \| null, matrix?: Matrix \| null): ShaderEffect;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum TileMode<br>Differences: enum TileMode|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TileMode;<br>API declaration: CLAMP = 0<br>Differences: CLAMP = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TileMode;<br>API declaration: REPEAT = 1<br>Differences: REPEAT = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TileMode;<br>API declaration: MIRROR = 2<br>Differences: MIRROR = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: TileMode;<br>API declaration: DECAL = 3<br>Differences: DECAL = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class ShadowLayer<br>Differences: class ShadowLayer|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ShadowLayer;<br>API declaration: static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer;<br>Differences: static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ColorFilter;<br>API declaration: static createMatrixColorFilter(matrix: Array\<number>): ColorFilter;<br>Differences: static createMatrixColorFilter(matrix: Array\<number>): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class ImageFilter<br>Differences: class ImageFilter|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ImageFilter;<br>API declaration: static createBlurImageFilter(sigmaX: number, sigmaY: number, tileMode: TileMode, imageFilter?: ImageFilter \| null): ImageFilter;<br>Differences: static createBlurImageFilter(sigmaX: number, sigmaY: number, tileMode: TileMode, imageFilter?: ImageFilter \| null): ImageFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ImageFilter;<br>API declaration: static createFromColorFilter(colorFilter: ColorFilter, imageFilter?: ImageFilter \| null): ImageFilter;<br>Differences: static createFromColorFilter(colorFilter: ColorFilter, imageFilter?: ImageFilter \| null): ImageFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum JoinStyle<br>Differences: enum JoinStyle|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: JoinStyle;<br>API declaration: MITER_JOIN = 0<br>Differences: MITER_JOIN = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: JoinStyle;<br>API declaration: ROUND_JOIN = 1<br>Differences: ROUND_JOIN = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: JoinStyle;<br>API declaration: BEVEL_JOIN = 2<br>Differences: BEVEL_JOIN = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum CapStyle<br>Differences: enum CapStyle|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: CapStyle;<br>API declaration: FLAT_CAP = 0<br>Differences: FLAT_CAP = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: CapStyle;<br>API declaration: SQUARE_CAP = 1<br>Differences: SQUARE_CAP = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: CapStyle;<br>API declaration: ROUND_CAP = 2<br>Differences: ROUND_CAP = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum BlurType<br>Differences: enum BlurType|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlurType;<br>API declaration: NORMAL = 0<br>Differences: NORMAL = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlurType;<br>API declaration: SOLID = 1<br>Differences: SOLID = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlurType;<br>API declaration: OUTER = 2<br>Differences: OUTER = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: BlurType;<br>API declaration: INNER = 3<br>Differences: INNER = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setMiterLimit(miter: number): void;<br>Differences: setMiterLimit(miter: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: getMiterLimit(): number;<br>Differences: getMiterLimit(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setShaderEffect(shaderEffect: ShaderEffect): void;<br>Differences: setShaderEffect(shaderEffect: ShaderEffect): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: getColor(): common2D.Color;<br>Differences: getColor(): common2D.Color;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: getWidth(): number;<br>Differences: getWidth(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: isAntiAlias(): boolean;<br>Differences: isAntiAlias(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: getAlpha(): number;<br>Differences: getAlpha(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: getColorFilter(): ColorFilter;<br>Differences: getColorFilter(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setImageFilter(filter: ImageFilter \| null): void;<br>Differences: setImageFilter(filter: ImageFilter \| null): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setMaskFilter(filter: MaskFilter): void;<br>Differences: setMaskFilter(filter: MaskFilter): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setPathEffect(effect: PathEffect): void;<br>Differences: setPathEffect(effect: PathEffect): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setShadowLayer(shadowLayer: ShadowLayer): void;<br>Differences: setShadowLayer(shadowLayer: ShadowLayer): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setJoinStyle(style: JoinStyle): void;<br>Differences: setJoinStyle(style: JoinStyle): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: getJoinStyle(): JoinStyle;<br>Differences: getJoinStyle(): JoinStyle;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: setCapStyle(style: CapStyle): void;<br>Differences: setCapStyle(style: CapStyle): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: getCapStyle(): CapStyle;<br>Differences: getCapStyle(): CapStyle;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: reset(): void;<br>Differences: reset(): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Pen;<br>API declaration: getFillPath(src: Path, dst: Path): boolean;<br>Differences: getFillPath(src: Path, dst: Path): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: getColor(): common2D.Color;<br>Differences: getColor(): common2D.Color;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: isAntiAlias(): boolean;<br>Differences: isAntiAlias(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: getAlpha(): number;<br>Differences: getAlpha(): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: getColorFilter(): ColorFilter;<br>Differences: getColorFilter(): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: setImageFilter(filter: ImageFilter \| null): void;<br>Differences: setImageFilter(filter: ImageFilter \| null): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: setMaskFilter(filter: MaskFilter): void;<br>Differences: setMaskFilter(filter: MaskFilter): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: setShadowLayer(shadowLayer: ShadowLayer): void;<br>Differences: setShadowLayer(shadowLayer: ShadowLayer): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: setShaderEffect(shaderEffect: ShaderEffect): void;<br>Differences: setShaderEffect(shaderEffect: ShaderEffect): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Brush;<br>API declaration: reset(): void;<br>Differences: reset(): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class Matrix<br>Differences: class Matrix|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: setRotation(degree: number, px: number, py: number): void;<br>Differences: setRotation(degree: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: setScale(sx: number, sy: number, px: number, py: number): void;<br>Differences: setScale(sx: number, sy: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: setTranslation(dx: number, dy: number): void;<br>Differences: setTranslation(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: setMatrix(values: Array\<number>): void;<br>Differences: setMatrix(values: Array\<number>): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: preConcat(matrix: Matrix): void;<br>Differences: preConcat(matrix: Matrix): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: isEqual(matrix: Matrix): Boolean;<br>Differences: isEqual(matrix: Matrix): Boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: invert(matrix: Matrix): Boolean;<br>Differences: invert(matrix: Matrix): Boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: isIdentity(): Boolean;<br>Differences: isIdentity(): Boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: getValue(index: number): number;<br>Differences: getValue(index: number): number;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: postRotate(degree: number, px: number, py: number): void;<br>Differences: postRotate(degree: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: postScale(sx: number, sy: number, px: number, py: number): void;<br>Differences: postScale(sx: number, sy: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: postTranslate(dx: number, dy: number): void;<br>Differences: postTranslate(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: preRotate(degree: number, px: number, py: number): void;<br>Differences: preRotate(degree: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: preScale(sx: number, sy: number, px: number, py: number): void;<br>Differences: preScale(sx: number, sy: number, px: number, py: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: preTranslate(dx: number, dy: number): void;<br>Differences: preTranslate(dx: number, dy: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: reset(): void;<br>Differences: reset(): void;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: mapPoints(src: Array\<common2D.Point>): Array\<common2D.Point>;<br>Differences: mapPoints(src: Array\<common2D.Point>): Array\<common2D.Point>;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: getAll(): Array\<number>;<br>Differences: getAll(): Array\<number>;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: mapRect(dst: common2D.Rect, src: common2D.Rect): boolean;<br>Differences: mapRect(dst: common2D.Rect, src: common2D.Rect): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: setRectToRect(src: common2D.Rect, dst: common2D.Rect, scaleToFit: ScaleToFit): boolean;<br>Differences: setRectToRect(src: common2D.Rect, dst: common2D.Rect, scaleToFit: ScaleToFit): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Matrix;<br>API declaration: setPolyToPoly(src: Array\<common2D.Point>, dst: Array\<common2D.Point>, count: number): boolean;<br>Differences: setPolyToPoly(src: Array\<common2D.Point>, dst: Array\<common2D.Point>, count: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum ScaleToFit<br>Differences: enum ScaleToFit|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ScaleToFit;<br>API declaration: FILL_SCALE_TO_FIT = 0<br>Differences: FILL_SCALE_TO_FIT = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ScaleToFit;<br>API declaration: START_SCALE_TO_FIT = 1<br>Differences: START_SCALE_TO_FIT = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ScaleToFit;<br>API declaration: CENTER_SCALE_TO_FIT = 2<br>Differences: CENTER_SCALE_TO_FIT = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: ScaleToFit;<br>API declaration: END_SCALE_TO_FIT = 3<br>Differences: END_SCALE_TO_FIT = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: class Region<br>Differences: class Region|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Region;<br>API declaration: isPointContained(x: number, y: number): boolean;<br>Differences: isPointContained(x: number, y: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Region;<br>API declaration: isRegionContained(other: Region): boolean;<br>Differences: isRegionContained(other: Region): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Region;<br>API declaration: op(region: Region, regionOp: RegionOp): boolean;<br>Differences: op(region: Region, regionOp: RegionOp): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Region;<br>API declaration: quickReject(left: number, top: number, right: number, bottom: number): boolean;<br>Differences: quickReject(left: number, top: number, right: number, bottom: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Region;<br>API declaration: setPath(path: Path, clip: Region): boolean;<br>Differences: setPath(path: Path, clip: Region): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: Region;<br>API declaration: setRect(left: number, top: number, right: number, bottom: number): boolean;<br>Differences: setRect(left: number, top: number, right: number, bottom: number): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum RegionOp<br>Differences: enum RegionOp|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RegionOp;<br>API declaration: DIFFERENCE = 0<br>Differences: DIFFERENCE = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RegionOp;<br>API declaration: INTERSECT = 1<br>Differences: INTERSECT = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RegionOp;<br>API declaration: UNION = 2<br>Differences: UNION = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RegionOp;<br>API declaration: XOR = 3<br>Differences: XOR = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RegionOp;<br>API declaration: REVERSE_DIFFERENCE = 4<br>Differences: REVERSE_DIFFERENCE = 4|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: RegionOp;<br>API declaration: REPLACE = 5<br>Differences: REPLACE = 5|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum CornerPos<br>Differences: enum CornerPos|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: CornerPos;<br>API declaration: TOP_LEFT_POS = 0<br>Differences: TOP_LEFT_POS = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: CornerPos;<br>API declaration: TOP_RIGHT_POS = 1<br>Differences: TOP_RIGHT_POS = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: CornerPos;<br>API declaration: BOTTOM_RIGHT_POS = 2<br>Differences: BOTTOM_RIGHT_POS = 2|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: CornerPos;<br>API declaration: BOTTOM_LEFT_POS = 3<br>Differences: BOTTOM_LEFT_POS = 3|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: drawing;<br>API declaration: enum SrcRectConstraint<br>Differences: enum SrcRectConstraint|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: SrcRectConstraint;<br>API declaration: STRICT = 0<br>Differences: STRICT = 0|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: SrcRectConstraint;<br>API declaration: FAST = 1<br>Differences: FAST = 1|api/@ohos.graphics.drawing.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace sendableColorSpaceManager<br>Differences: declare namespace sendableColorSpaceManager|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|New API|NA|Class name: sendableColorSpaceManager;<br>API declaration: type ISendable = lang.ISendable;<br>Differences: type ISendable = lang.ISendable;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|New API|NA|Class name: sendableColorSpaceManager;<br>API declaration: interface ColorSpaceManager<br>Differences: interface ColorSpaceManager|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|New API|NA|Class name: ColorSpaceManager;<br>API declaration: getColorSpaceName(): colorSpaceManager.ColorSpace;<br>Differences: getColorSpaceName(): colorSpaceManager.ColorSpace;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|New API|NA|Class name: ColorSpaceManager;<br>API declaration: getWhitePoint(): collections.Array\<number>;<br>Differences: getWhitePoint(): collections.Array\<number>;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|New API|NA|Class name: ColorSpaceManager;<br>API declaration: getGamma(): number;<br>Differences: getGamma(): number;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|New API|NA|Class name: sendableColorSpaceManager;<br>API declaration: function create(colorSpaceName: colorSpaceManager.ColorSpace): ColorSpaceManager;<br>Differences: function create(colorSpaceName: colorSpaceManager.ColorSpace): ColorSpaceManager;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|New API|NA|Class name: sendableColorSpaceManager;<br>API declaration: function create(primaries: colorSpaceManager.ColorSpacePrimaries, gamma: number): ColorSpaceManager;<br>Differences: function create(primaries: colorSpaceManager.ColorSpacePrimaries, gamma: number): ColorSpaceManager;|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|New API|NA|Class name: global;<br>API declaration: declare namespace text<br>Differences: declare namespace text|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum TextAlign<br>Differences: enum TextAlign|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextAlign;<br>API declaration: LEFT = 0<br>Differences: LEFT = 0|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextAlign;<br>API declaration: RIGHT = 1<br>Differences: RIGHT = 1|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextAlign;<br>API declaration: CENTER = 2<br>Differences: CENTER = 2|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextAlign;<br>API declaration: JUSTIFY = 3<br>Differences: JUSTIFY = 3|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextAlign;<br>API declaration: START = 4<br>Differences: START = 4|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextAlign;<br>API declaration: END = 5<br>Differences: END = 5|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum TextDirection<br>Differences: enum TextDirection|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDirection;<br>API declaration: RTL<br>Differences: RTL|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDirection;<br>API declaration: LTR<br>Differences: LTR|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum BreakStrategy<br>Differences: enum BreakStrategy|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: BreakStrategy;<br>API declaration: GREEDY<br>Differences: GREEDY|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: BreakStrategy;<br>API declaration: HIGH_QUALITY<br>Differences: HIGH_QUALITY|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: BreakStrategy;<br>API declaration: BALANCED<br>Differences: BALANCED|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum WordBreak<br>Differences: enum WordBreak|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: WordBreak;<br>API declaration: NORMAL<br>Differences: NORMAL|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: WordBreak;<br>API declaration: BREAK_ALL<br>Differences: BREAK_ALL|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: WordBreak;<br>API declaration: BREAK_WORD<br>Differences: BREAK_WORD|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface Decoration<br>Differences: interface Decoration|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Decoration;<br>API declaration: textDecoration?: TextDecorationType;<br>Differences: textDecoration?: TextDecorationType;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Decoration;<br>API declaration: color?: common2D.Color;<br>Differences: color?: common2D.Color;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Decoration;<br>API declaration: decorationStyle?: TextDecorationStyle;<br>Differences: decorationStyle?: TextDecorationStyle;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Decoration;<br>API declaration: decorationThicknessScale?: number;<br>Differences: decorationThicknessScale?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum TextDecorationType<br>Differences: enum TextDecorationType|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDecorationType;<br>API declaration: NONE<br>Differences: NONE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDecorationType;<br>API declaration: UNDERLINE<br>Differences: UNDERLINE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDecorationType;<br>API declaration: OVERLINE<br>Differences: OVERLINE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDecorationType;<br>API declaration: LINE_THROUGH<br>Differences: LINE_THROUGH|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum TextDecorationStyle<br>Differences: enum TextDecorationStyle|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDecorationStyle;<br>API declaration: SOLID<br>Differences: SOLID|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDecorationStyle;<br>API declaration: DOUBLE<br>Differences: DOUBLE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDecorationStyle;<br>API declaration: DOTTED<br>Differences: DOTTED|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDecorationStyle;<br>API declaration: DASHED<br>Differences: DASHED|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextDecorationStyle;<br>API declaration: WAVY<br>Differences: WAVY|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum FontWeight<br>Differences: enum FontWeight|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWeight;<br>API declaration: W100<br>Differences: W100|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWeight;<br>API declaration: W200<br>Differences: W200|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWeight;<br>API declaration: W300<br>Differences: W300|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWeight;<br>API declaration: W400<br>Differences: W400|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWeight;<br>API declaration: W500<br>Differences: W500|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWeight;<br>API declaration: W600<br>Differences: W600|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWeight;<br>API declaration: W700<br>Differences: W700|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWeight;<br>API declaration: W800<br>Differences: W800|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWeight;<br>API declaration: W900<br>Differences: W900|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum FontStyle<br>Differences: enum FontStyle|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontStyle;<br>API declaration: NORMAL<br>Differences: NORMAL|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontStyle;<br>API declaration: ITALIC<br>Differences: ITALIC|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontStyle;<br>API declaration: OBLIQUE<br>Differences: OBLIQUE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum FontWidth<br>Differences: enum FontWidth|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWidth;<br>API declaration: ULTRA_CONDENSED = 1<br>Differences: ULTRA_CONDENSED = 1|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWidth;<br>API declaration: EXTRA_CONDENSED = 2<br>Differences: EXTRA_CONDENSED = 2|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWidth;<br>API declaration: CONDENSED = 3<br>Differences: CONDENSED = 3|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWidth;<br>API declaration: SEMI_CONDENSED = 4<br>Differences: SEMI_CONDENSED = 4|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWidth;<br>API declaration: NORMAL = 5<br>Differences: NORMAL = 5|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWidth;<br>API declaration: SEMI_EXPANDED = 6<br>Differences: SEMI_EXPANDED = 6|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWidth;<br>API declaration: EXPANDED = 7<br>Differences: EXPANDED = 7|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWidth;<br>API declaration: EXTRA_EXPANDED = 8<br>Differences: EXTRA_EXPANDED = 8|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontWidth;<br>API declaration: ULTRA_EXPANDED = 9<br>Differences: ULTRA_EXPANDED = 9|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum TextHeightBehavior<br>Differences: enum TextHeightBehavior|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextHeightBehavior;<br>API declaration: ALL = 0x0<br>Differences: ALL = 0x0|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextHeightBehavior;<br>API declaration: DISABLE_FIRST_ASCENT = 0x1<br>Differences: DISABLE_FIRST_ASCENT = 0x1|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextHeightBehavior;<br>API declaration: DISABLE_LAST_ASCENT = 0x2<br>Differences: DISABLE_LAST_ASCENT = 0x2|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextHeightBehavior;<br>API declaration: DISABLE_ALL = 0x1 \| 0x2<br>Differences: DISABLE_ALL = 0x1 \| 0x2|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum TextBaseline<br>Differences: enum TextBaseline|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextBaseline;<br>API declaration: ALPHABETIC<br>Differences: ALPHABETIC|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextBaseline;<br>API declaration: IDEOGRAPHIC<br>Differences: IDEOGRAPHIC|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum EllipsisMode<br>Differences: enum EllipsisMode|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: EllipsisMode;<br>API declaration: START<br>Differences: START|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: EllipsisMode;<br>API declaration: MIDDLE<br>Differences: MIDDLE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: EllipsisMode;<br>API declaration: END<br>Differences: END|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface TextShadow<br>Differences: interface TextShadow|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextShadow;<br>API declaration: color?: common2D.Color;<br>Differences: color?: common2D.Color;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextShadow;<br>API declaration: point?: common2D.Point;<br>Differences: point?: common2D.Point;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextShadow;<br>API declaration: blurRadius?: number;<br>Differences: blurRadius?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface RectStyle<br>Differences: interface RectStyle|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectStyle;<br>API declaration: color: common2D.Color;<br>Differences: color: common2D.Color;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectStyle;<br>API declaration: leftTopRadius: number;<br>Differences: leftTopRadius: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectStyle;<br>API declaration: rightTopRadius: number;<br>Differences: rightTopRadius: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectStyle;<br>API declaration: rightBottomRadius: number;<br>Differences: rightBottomRadius: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectStyle;<br>API declaration: leftBottomRadius: number;<br>Differences: leftBottomRadius: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface FontFeature<br>Differences: interface FontFeature|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontFeature;<br>API declaration: name: string;<br>Differences: name: string;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontFeature;<br>API declaration: value: number;<br>Differences: value: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface FontVariation<br>Differences: interface FontVariation|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontVariation;<br>API declaration: axis: string;<br>Differences: axis: string;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontVariation;<br>API declaration: value: number;<br>Differences: value: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface TextStyle<br>Differences: interface TextStyle|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: decoration?: Decoration;<br>Differences: decoration?: Decoration;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: color?: common2D.Color;<br>Differences: color?: common2D.Color;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: fontWeight?: FontWeight;<br>Differences: fontWeight?: FontWeight;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: fontStyle?: FontStyle;<br>Differences: fontStyle?: FontStyle;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: baseline?: TextBaseline;<br>Differences: baseline?: TextBaseline;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: fontFamilies?: Array\<string>;<br>Differences: fontFamilies?: Array\<string>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: fontSize?: number;<br>Differences: fontSize?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: letterSpacing?: number;<br>Differences: letterSpacing?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: wordSpacing?: number;<br>Differences: wordSpacing?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: heightScale?: number;<br>Differences: heightScale?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: halfLeading?: boolean;<br>Differences: halfLeading?: boolean;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: heightOnly?: boolean;<br>Differences: heightOnly?: boolean;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: ellipsis?: string;<br>Differences: ellipsis?: string;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: ellipsisMode?: EllipsisMode;<br>Differences: ellipsisMode?: EllipsisMode;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: locale?: string;<br>Differences: locale?: string;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: baselineShift?: number;<br>Differences: baselineShift?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: fontFeatures?: Array\<FontFeature>;<br>Differences: fontFeatures?: Array\<FontFeature>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: textShadows?: Array\<TextShadow>;<br>Differences: textShadows?: Array\<TextShadow>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: backgroundRect?: RectStyle;<br>Differences: backgroundRect?: RectStyle;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextStyle;<br>API declaration: fontVariations?: Array\<FontVariation>;<br>Differences: fontVariations?: Array\<FontVariation>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: class FontCollection<br>Differences: class FontCollection|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontCollection;<br>API declaration: static getGlobalInstance(): FontCollection;<br>Differences: static getGlobalInstance(): FontCollection;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontCollection;<br>API declaration: loadFontSync(name: string, path: string \| Resource): void;<br>Differences: loadFontSync(name: string, path: string \| Resource): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: FontCollection;<br>API declaration: clearCaches(): void;<br>Differences: clearCaches(): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface StrutStyle<br>Differences: interface StrutStyle|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: fontFamilies?: Array\<string>;<br>Differences: fontFamilies?: Array\<string>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: fontStyle?: FontStyle;<br>Differences: fontStyle?: FontStyle;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: fontWidth?: FontWidth;<br>Differences: fontWidth?: FontWidth;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: fontWeight?: FontWeight;<br>Differences: fontWeight?: FontWeight;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: fontSize?: number;<br>Differences: fontSize?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: height?: number;<br>Differences: height?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: leading?: number;<br>Differences: leading?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: forceHeight?: boolean;<br>Differences: forceHeight?: boolean;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: enabled?: boolean;<br>Differences: enabled?: boolean;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: heightOverride?: boolean;<br>Differences: heightOverride?: boolean;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: StrutStyle;<br>API declaration: halfLeading?: boolean;<br>Differences: halfLeading?: boolean;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface ParagraphStyle<br>Differences: interface ParagraphStyle|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphStyle;<br>API declaration: textStyle?: TextStyle;<br>Differences: textStyle?: TextStyle;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphStyle;<br>API declaration: textDirection?: TextDirection;<br>Differences: textDirection?: TextDirection;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphStyle;<br>API declaration: align?: TextAlign;<br>Differences: align?: TextAlign;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphStyle;<br>API declaration: wordBreak?: WordBreak;<br>Differences: wordBreak?: WordBreak;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphStyle;<br>API declaration: maxLines?: number;<br>Differences: maxLines?: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphStyle;<br>API declaration: breakStrategy?: BreakStrategy;<br>Differences: breakStrategy?: BreakStrategy;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphStyle;<br>API declaration: strutStyle?: StrutStyle;<br>Differences: strutStyle?: StrutStyle;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphStyle;<br>API declaration: textHeightBehavior?: TextHeightBehavior;<br>Differences: textHeightBehavior?: TextHeightBehavior;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum PlaceholderAlignment<br>Differences: enum PlaceholderAlignment|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderAlignment;<br>API declaration: OFFSET_AT_BASELINE<br>Differences: OFFSET_AT_BASELINE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderAlignment;<br>API declaration: ABOVE_BASELINE<br>Differences: ABOVE_BASELINE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderAlignment;<br>API declaration: BELOW_BASELINE<br>Differences: BELOW_BASELINE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderAlignment;<br>API declaration: TOP_OF_ROW_BOX<br>Differences: TOP_OF_ROW_BOX|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderAlignment;<br>API declaration: BOTTOM_OF_ROW_BOX<br>Differences: BOTTOM_OF_ROW_BOX|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderAlignment;<br>API declaration: CENTER_OF_ROW_BOX<br>Differences: CENTER_OF_ROW_BOX|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface PlaceholderSpan<br>Differences: interface PlaceholderSpan|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderSpan;<br>API declaration: width: number;<br>Differences: width: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderSpan;<br>API declaration: height: number;<br>Differences: height: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderSpan;<br>API declaration: align: PlaceholderAlignment;<br>Differences: align: PlaceholderAlignment;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderSpan;<br>API declaration: baseline: TextBaseline;<br>Differences: baseline: TextBaseline;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PlaceholderSpan;<br>API declaration: baselineOffset: number;<br>Differences: baselineOffset: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface Range<br>Differences: interface Range|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Range;<br>API declaration: start: number;<br>Differences: start: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Range;<br>API declaration: end: number;<br>Differences: end: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: class Paragraph<br>Differences: class Paragraph|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: layoutSync(width: number): void;<br>Differences: layoutSync(width: number): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: paint(canvas: drawing.Canvas, x: number, y: number): void;<br>Differences: paint(canvas: drawing.Canvas, x: number, y: number): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: paintOnPath(canvas: drawing.Canvas, path: drawing.Path, hOffset: number, vOffset: number): void;<br>Differences: paintOnPath(canvas: drawing.Canvas, path: drawing.Path, hOffset: number, vOffset: number): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getMaxWidth(): number;<br>Differences: getMaxWidth(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getHeight(): number;<br>Differences: getHeight(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getLongestLine(): number;<br>Differences: getLongestLine(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getMinIntrinsicWidth(): number;<br>Differences: getMinIntrinsicWidth(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getMaxIntrinsicWidth(): number;<br>Differences: getMaxIntrinsicWidth(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getAlphabeticBaseline(): number;<br>Differences: getAlphabeticBaseline(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getIdeographicBaseline(): number;<br>Differences: getIdeographicBaseline(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getRectsForRange(range: Range, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array\<TextBox>;<br>Differences: getRectsForRange(range: Range, widthStyle: RectWidthStyle, heightStyle: RectHeightStyle): Array\<TextBox>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getRectsForPlaceholders(): Array\<TextBox>;<br>Differences: getRectsForPlaceholders(): Array\<TextBox>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity;<br>Differences: getGlyphPositionAtCoordinate(x: number, y: number): PositionWithAffinity;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getWordBoundary(offset: number): Range;<br>Differences: getWordBoundary(offset: number): Range;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getLineCount(): number;<br>Differences: getLineCount(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getLineHeight(line: number): number;<br>Differences: getLineHeight(line: number): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getLineWidth(line: number): number;<br>Differences: getLineWidth(line: number): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: didExceedMaxLines(): boolean;<br>Differences: didExceedMaxLines(): boolean;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getTextLines(): Array\<TextLine>;<br>Differences: getTextLines(): Array\<TextLine>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getActualTextRange(lineNumber: number, includeSpaces: boolean): Range;<br>Differences: getActualTextRange(lineNumber: number, includeSpaces: boolean): Range;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getLineMetrics(): Array\<LineMetrics>;<br>Differences: getLineMetrics(): Array\<LineMetrics>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Paragraph;<br>API declaration: getLineMetrics(lineNumber: number): LineMetrics \| undefined;<br>Differences: getLineMetrics(lineNumber: number): LineMetrics \| undefined;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface TextBox<br>Differences: interface TextBox|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextBox;<br>API declaration: rect: common2D.Rect;<br>Differences: rect: common2D.Rect;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextBox;<br>API declaration: direction: TextDirection;<br>Differences: direction: TextDirection;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface PositionWithAffinity<br>Differences: interface PositionWithAffinity|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PositionWithAffinity;<br>API declaration: position: number;<br>Differences: position: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: PositionWithAffinity;<br>API declaration: affinity: Affinity;<br>Differences: affinity: Affinity;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum RectWidthStyle<br>Differences: enum RectWidthStyle|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectWidthStyle;<br>API declaration: TIGHT<br>Differences: TIGHT|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectWidthStyle;<br>API declaration: MAX<br>Differences: MAX|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum RectHeightStyle<br>Differences: enum RectHeightStyle|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectHeightStyle;<br>API declaration: TIGHT<br>Differences: TIGHT|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectHeightStyle;<br>API declaration: MAX<br>Differences: MAX|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectHeightStyle;<br>API declaration: INCLUDE_LINE_SPACE_MIDDLE<br>Differences: INCLUDE_LINE_SPACE_MIDDLE|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectHeightStyle;<br>API declaration: INCLUDE_LINE_SPACE_TOP<br>Differences: INCLUDE_LINE_SPACE_TOP|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectHeightStyle;<br>API declaration: INCLUDE_LINE_SPACE_BOTTOM<br>Differences: INCLUDE_LINE_SPACE_BOTTOM|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RectHeightStyle;<br>API declaration: STRUT<br>Differences: STRUT|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: enum Affinity<br>Differences: enum Affinity|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Affinity;<br>API declaration: UPSTREAM<br>Differences: UPSTREAM|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Affinity;<br>API declaration: DOWNSTREAM<br>Differences: DOWNSTREAM|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: class ParagraphBuilder<br>Differences: class ParagraphBuilder|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphBuilder;<br>API declaration: pushStyle(textStyle: TextStyle): void;<br>Differences: pushStyle(textStyle: TextStyle): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphBuilder;<br>API declaration: popStyle(): void;<br>Differences: popStyle(): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphBuilder;<br>API declaration: addText(text: string): void;<br>Differences: addText(text: string): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphBuilder;<br>API declaration: addPlaceholder(placeholderSpan: PlaceholderSpan): void;<br>Differences: addPlaceholder(placeholderSpan: PlaceholderSpan): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphBuilder;<br>API declaration: build(): Paragraph;<br>Differences: build(): Paragraph;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: ParagraphBuilder;<br>API declaration: addSymbol(symbolId: number): void;<br>Differences: addSymbol(symbolId: number): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: class TextLine<br>Differences: class TextLine|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextLine;<br>API declaration: getGlyphCount(): number;<br>Differences: getGlyphCount(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextLine;<br>API declaration: getTextRange(): Range;<br>Differences: getTextRange(): Range;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextLine;<br>API declaration: getGlyphRuns(): Array\<Run>;<br>Differences: getGlyphRuns(): Array\<Run>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: TextLine;<br>API declaration: paint(canvas: drawing.Canvas, x: number, y: number): void;<br>Differences: paint(canvas: drawing.Canvas, x: number, y: number): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: class Run<br>Differences: class Run|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Run;<br>API declaration: getGlyphCount(): number;<br>Differences: getGlyphCount(): number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Run;<br>API declaration: getGlyphs(): Array\<number>;<br>Differences: getGlyphs(): Array\<number>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Run;<br>API declaration: getPositions(): Array\<common2D.Point>;<br>Differences: getPositions(): Array\<common2D.Point>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Run;<br>API declaration: getOffsets(): Array\<common2D.Point>;<br>Differences: getOffsets(): Array\<common2D.Point>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Run;<br>API declaration: getFont(): drawing.Font;<br>Differences: getFont(): drawing.Font;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: Run;<br>API declaration: paint(canvas: drawing.Canvas, x: number, y: number): void;<br>Differences: paint(canvas: drawing.Canvas, x: number, y: number): void;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface RunMetrics<br>Differences: interface RunMetrics|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RunMetrics;<br>API declaration: textStyle: TextStyle;<br>Differences: textStyle: TextStyle;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: RunMetrics;<br>API declaration: fontMetrics: drawing.FontMetrics;<br>Differences: fontMetrics: drawing.FontMetrics;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: text;<br>API declaration: interface LineMetrics<br>Differences: interface LineMetrics|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: startIndex: number;<br>Differences: startIndex: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: endIndex: number;<br>Differences: endIndex: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: ascent: number;<br>Differences: ascent: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: descent: number;<br>Differences: descent: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: height: number;<br>Differences: height: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: width: number;<br>Differences: width: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: left: number;<br>Differences: left: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: baseline: number;<br>Differences: baseline: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: lineNumber: number;<br>Differences: lineNumber: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: topHeight: number;<br>Differences: topHeight: number;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: LineMetrics;<br>API declaration: runMetrics: Map\<number, RunMetrics>;<br>Differences: runMetrics: Map\<number, RunMetrics>;|api/@ohos.graphics.text.d.ts|
|New API|NA|Class name: global;<br>API declaration: declare namespace uiEffect<br>Differences: declare namespace uiEffect|api/@ohos.graphics.uiEffect.d.ts|
|New API|NA|Class name: uiEffect;<br>API declaration: interface Filter<br>Differences: interface Filter|api/@ohos.graphics.uiEffect.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: blur(blurRadius: number): Filter;<br>Differences: blur(blurRadius: number): Filter;|api/@ohos.graphics.uiEffect.d.ts|
|New API|NA|Class name: uiEffect;<br>API declaration: interface VisualEffect<br>Differences: interface VisualEffect|api/@ohos.graphics.uiEffect.d.ts|
|New API|NA|Class name: uiEffect;<br>API declaration: function createFilter(): Filter;<br>Differences: function createFilter(): Filter;|api/@ohos.graphics.uiEffect.d.ts|
|New API|NA|Class name: uiEffect;<br>API declaration: function createEffect(): VisualEffect;<br>Differences: function createEffect(): VisualEffect;|api/@ohos.graphics.uiEffect.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: invert(): Filter;<br>Differences: invert(): Filter;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: Filter;<br>API declaration: setColorMatrix(colorMatrix: Array\<number>): Filter;<br>Differences: setColorMatrix(colorMatrix: Array\<number>): Filter;|api/@ohos.effectKit.d.ts|
|New API|NA|Class name: ColorPicker;<br>API declaration: getTopProportionColors(colorCount: number): Array\<Color \| null>;<br>Differences: getTopProportionColors(colorCount: number): Array\<Color \| null>;|api/@ohos.effectKit.d.ts|
|Kit change|ArkGraphics 2D|ArkGraphics2D|api/@ohos.graphics.common2D.d.ts|
|Kit change|ArkGraphics 2D|ArkGraphics2D|api/@ohos.graphics.drawing.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.graphics.sendableColorSpaceManager.d.ets<br>Differences: ArkGraphics2D|api/@ohos.graphics.sendableColorSpaceManager.d.ets|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.graphics.text.d.ts<br>Differences: ArkGraphics2D|api/@ohos.graphics.text.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.graphics.uiEffect.d.ts<br>Differences: ArkGraphics2D|api/@ohos.graphics.uiEffect.d.ts|
|New support for atomic services|Class name: global;<br>API declaration: declare namespace effectKit<br>Differences: NA|Class name: global;<br>API declaration: declare namespace effectKit<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: effectKit;<br>API declaration: interface Filter<br>Differences: NA|Class name: effectKit;<br>API declaration: interface Filter<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: Filter;<br>API declaration: blur(radius: number): Filter;<br>Differences: NA|Class name: Filter;<br>API declaration: blur(radius: number): Filter;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: Filter;<br>API declaration: brightness(bright: number): Filter;<br>Differences: NA|Class name: Filter;<br>API declaration: brightness(bright: number): Filter;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: Filter;<br>API declaration: grayscale(): Filter;<br>Differences: NA|Class name: Filter;<br>API declaration: grayscale(): Filter;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: Filter;<br>API declaration: getEffectPixelMap(): Promise\<image.PixelMap>;<br>Differences: NA|Class name: Filter;<br>API declaration: getEffectPixelMap(): Promise\<image.PixelMap>;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: effectKit;<br>API declaration: interface ColorPicker<br>Differences: NA|Class name: effectKit;<br>API declaration: interface ColorPicker<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: ColorPicker;<br>API declaration: getMainColor(): Promise\<Color>;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getMainColor(): Promise\<Color>;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: ColorPicker;<br>API declaration: getMainColorSync(): Color;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getMainColorSync(): Color;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: ColorPicker;<br>API declaration: getLargestProportionColor(): Color;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getLargestProportionColor(): Color;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: ColorPicker;<br>API declaration: getHighestSaturationColor(): Color;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getHighestSaturationColor(): Color;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: ColorPicker;<br>API declaration: getAverageColor(): Color;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: getAverageColor(): Color;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: ColorPicker;<br>API declaration: isBlackOrWhiteOrGrayColor(color: number): boolean;<br>Differences: NA|Class name: ColorPicker;<br>API declaration: isBlackOrWhiteOrGrayColor(color: number): boolean;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: effectKit;<br>API declaration: interface Color<br>Differences: NA|Class name: effectKit;<br>API declaration: interface Color<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: Color;<br>API declaration: red: number;<br>Differences: NA|Class name: Color;<br>API declaration: red: number;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: Color;<br>API declaration: green: number;<br>Differences: NA|Class name: Color;<br>API declaration: green: number;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: Color;<br>API declaration: blue: number;<br>Differences: NA|Class name: Color;<br>API declaration: blue: number;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: Color;<br>API declaration: alpha: number;<br>Differences: NA|Class name: Color;<br>API declaration: alpha: number;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: effectKit;<br>API declaration: function createEffect(source: image.PixelMap): Filter;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createEffect(source: image.PixelMap): Filter;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap): Promise\<ColorPicker>;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>): Promise\<ColorPicker>;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: NA|Class name: effectKit;<br>API declaration: function createColorPicker(source: image.PixelMap, region: Array\<number>, callback: AsyncCallback\<ColorPicker>): void;<br>Differences: atomicservice|api/@ohos.effectKit.d.ts|
|New support for atomic services|Class name: global;<br>API declaration: declare namespace colorSpaceManager<br>Differences: NA|Class name: global;<br>API declaration: declare namespace colorSpaceManager<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: colorSpaceManager;<br>API declaration: enum ColorSpace<br>Differences: NA|Class name: colorSpaceManager;<br>API declaration: enum ColorSpace<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: UNKNOWN = 0<br>Differences: NA|Class name: ColorSpace;<br>API declaration: UNKNOWN = 0<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: ADOBE_RGB_1998 = 1<br>Differences: NA|Class name: ColorSpace;<br>API declaration: ADOBE_RGB_1998 = 1<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: DCI_P3 = 2<br>Differences: NA|Class name: ColorSpace;<br>API declaration: DCI_P3 = 2<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: DISPLAY_P3 = 3<br>Differences: NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3 = 3<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: SRGB = 4<br>Differences: NA|Class name: ColorSpace;<br>API declaration: SRGB = 4<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT709 = 6<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT709 = 6<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT601_EBU = 7<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT601_EBU = 7<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT601_SMPTE_C = 8<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT601_SMPTE_C = 8<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT2020_HLG = 9<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT2020_HLG = 9<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT2020_PQ = 10<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT2020_PQ = 10<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: P3_HLG = 11<br>Differences: NA|Class name: ColorSpace;<br>API declaration: P3_HLG = 11<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: P3_PQ = 12<br>Differences: NA|Class name: ColorSpace;<br>API declaration: P3_PQ = 12<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: ADOBE_RGB_1998_LIMIT = 13<br>Differences: NA|Class name: ColorSpace;<br>API declaration: ADOBE_RGB_1998_LIMIT = 13<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_LIMIT = 14<br>Differences: NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_LIMIT = 14<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: SRGB_LIMIT = 15<br>Differences: NA|Class name: ColorSpace;<br>API declaration: SRGB_LIMIT = 15<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT709_LIMIT = 16<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT709_LIMIT = 16<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT601_EBU_LIMIT = 17<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT601_EBU_LIMIT = 17<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT601_SMPTE_C_LIMIT = 18<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT601_SMPTE_C_LIMIT = 18<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT2020_HLG_LIMIT = 19<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT2020_HLG_LIMIT = 19<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: BT2020_PQ_LIMIT = 20<br>Differences: NA|Class name: ColorSpace;<br>API declaration: BT2020_PQ_LIMIT = 20<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: P3_HLG_LIMIT = 21<br>Differences: NA|Class name: ColorSpace;<br>API declaration: P3_HLG_LIMIT = 21<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: P3_PQ_LIMIT = 22<br>Differences: NA|Class name: ColorSpace;<br>API declaration: P3_PQ_LIMIT = 22<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: LINEAR_P3 = 23<br>Differences: NA|Class name: ColorSpace;<br>API declaration: LINEAR_P3 = 23<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: LINEAR_SRGB = 24<br>Differences: NA|Class name: ColorSpace;<br>API declaration: LINEAR_SRGB = 24<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: LINEAR_BT709 = LINEAR_SRGB<br>Differences: NA|Class name: ColorSpace;<br>API declaration: LINEAR_BT709 = LINEAR_SRGB<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: LINEAR_BT2020 = 25<br>Differences: NA|Class name: ColorSpace;<br>API declaration: LINEAR_BT2020 = 25<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: DISPLAY_SRGB = SRGB<br>Differences: NA|Class name: ColorSpace;<br>API declaration: DISPLAY_SRGB = SRGB<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_SRGB = DISPLAY_P3<br>Differences: NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_SRGB = DISPLAY_P3<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_HLG = P3_HLG<br>Differences: NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_HLG = P3_HLG<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_PQ = P3_PQ<br>Differences: NA|Class name: ColorSpace;<br>API declaration: DISPLAY_P3_PQ = P3_PQ<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: ColorSpace;<br>API declaration: CUSTOM = 5<br>Differences: NA|Class name: ColorSpace;<br>API declaration: CUSTOM = 5<br>Differences: atomicservice|api/@ohos.graphics.colorSpaceManager.d.ts|
|New support for atomic services|Class name: global;<br>API declaration: declare namespace hdrCapability<br>Differences: NA|Class name: global;<br>API declaration: declare namespace hdrCapability<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|New support for atomic services|Class name: hdrCapability;<br>API declaration: enum HDRFormat<br>Differences: NA|Class name: hdrCapability;<br>API declaration: enum HDRFormat<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|New support for atomic services|Class name: HDRFormat;<br>API declaration: NONE = 0<br>Differences: NA|Class name: HDRFormat;<br>API declaration: NONE = 0<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|New support for atomic services|Class name: HDRFormat;<br>API declaration: VIDEO_HLG = 1<br>Differences: NA|Class name: HDRFormat;<br>API declaration: VIDEO_HLG = 1<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|New support for atomic services|Class name: HDRFormat;<br>API declaration: VIDEO_HDR10 = 2<br>Differences: NA|Class name: HDRFormat;<br>API declaration: VIDEO_HDR10 = 2<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|New support for atomic services|Class name: HDRFormat;<br>API declaration: VIDEO_HDR_VIVID = 3<br>Differences: NA|Class name: HDRFormat;<br>API declaration: VIDEO_HDR_VIVID = 3<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|New support for atomic services|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_VIVID_DUAL = 4<br>Differences: NA|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_VIVID_DUAL = 4<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|New support for atomic services|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_VIVID_SINGLE = 5<br>Differences: NA|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_VIVID_SINGLE = 5<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|New support for atomic services|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_ISO_DUAL = 6<br>Differences: NA|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_ISO_DUAL = 6<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
|New support for atomic services|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_ISO_SINGLE = 7<br>Differences: NA|Class name: HDRFormat;<br>API declaration: IMAGE_HDR_ISO_SINGLE = 7<br>Differences: atomicservice|api/@ohos.graphics.hdrCapability.d.ts|
