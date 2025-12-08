| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：Canvas；<br>API声明：drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number, ambientColor: common2D.Color \| number, spotColor: common2D.Color \| number, flag: ShadowFlag): void;<br>差异内容：drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number, ambientColor: common2D.Color \| number, spotColor: common2D.Color \| number, flag: ShadowFlag): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawColor(color: number, blendMode?: BlendMode): void;<br>差异内容：drawColor(color: number, blendMode?: BlendMode): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：clear(color: common2D.Color \| number): void;<br>差异内容：clear(color: common2D.Color \| number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Lattice；<br>API声明：static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<number> \| null): Lattice;<br>差异内容：static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<number> \| null): Lattice;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ShadowLayer；<br>API声明：static create(blurRadius: number, x: number, y: number, color: common2D.Color \| number): ShadowLayer;<br>差异内容：static create(blurRadius: number, x: number, y: number, color: common2D.Color \| number): ShadowLayer;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：ColorFilter；<br>API声明：static createBlendModeColorFilter(color: common2D.Color \| number, mode: BlendMode): ColorFilter;<br>差异内容：static createBlendModeColorFilter(color: common2D.Color \| number, mode: BlendMode): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：setColor(color: number): void;<br>差异内容：setColor(color: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：setColor(color: number): void;<br>差异内容：setColor(color: number): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum PathIteratorVerb<br>差异内容：enum PathIteratorVerb|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIteratorVerb；<br>API声明：MOVE = 0<br>差异内容：MOVE = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIteratorVerb；<br>API声明：LINE = 1<br>差异内容：LINE = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIteratorVerb；<br>API声明：QUAD = 2<br>差异内容：QUAD = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIteratorVerb；<br>API声明：CONIC = 3<br>差异内容：CONIC = 3|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIteratorVerb；<br>API声明：CUBIC = 4<br>差异内容：CUBIC = 4|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIteratorVerb；<br>API声明：CLOSE = 5<br>差异内容：CLOSE = 5|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIteratorVerb；<br>API声明：DONE = CLOSE + 1<br>差异内容：DONE = CLOSE + 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：class PathIterator<br>差异内容：class PathIterator|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIterator；<br>API声明：next(points: Array\<common2D.Point>, offset?: number): PathIteratorVerb;<br>差异内容：next(points: Array\<common2D.Point>, offset?: number): PathIteratorVerb;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIterator；<br>API声明：peek(): PathIteratorVerb;<br>差异内容：peek(): PathIteratorVerb;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathIterator；<br>API声明：hasNext(): boolean;<br>差异内容：hasNext(): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：getSegment(forceClosed: boolean, start: number, stop: number, startWithMoveTo: boolean, dst: Path): boolean;<br>差异内容：getSegment(forceClosed: boolean, start: number, stop: number, startWithMoveTo: boolean, dst: Path): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Path；<br>API声明：getPathIterator(): PathIterator;<br>差异内容：getPathIterator(): PathIterator;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawImageLattice(pixelmap: image.PixelMap, lattice: Lattice, dstRect: common2D.Rect, filterMode: FilterMode): void;<br>差异内容：drawImageLattice(pixelmap: image.PixelMap, lattice: Lattice, dstRect: common2D.Rect, filterMode: FilterMode): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawImageNine(pixelmap: image.PixelMap, center: common2D.Rect, dstRect: common2D.Rect, filterMode: FilterMode): void;<br>差异内容：drawImageNine(pixelmap: image.PixelMap, center: common2D.Rect, dstRect: common2D.Rect, filterMode: FilterMode): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：drawArcWithCenter(arc: common2D.Rect, startAngle: number, sweepAngle: number, useCenter: boolean): void;<br>差异内容：drawArcWithCenter(arc: common2D.Rect, startAngle: number, sweepAngle: number, useCenter: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：quickRejectPath(path: Path): boolean;<br>差异内容：quickRejectPath(path: Path): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Canvas；<br>API声明：quickRejectRect(rect: common2D.Rect): boolean;<br>差异内容：quickRejectRect(rect: common2D.Rect): boolean;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Typeface；<br>API声明：static makeFromRawFile(rawfile: Resource): Typeface;<br>差异内容：static makeFromRawFile(rawfile: Resource): Typeface;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：createPathForGlyph(index: number): Path;<br>差异内容：createPathForGlyph(index: number): Path;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getBounds(glyphs: Array\<number>): Array\<common2D.Rect>;<br>差异内容：getBounds(glyphs: Array\<number>): Array\<common2D.Rect>;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Font；<br>API声明：getTextPath(text: string, byteLength: number, x: number, y: number): Path;<br>差异内容：getTextPath(text: string, byteLength: number, x: number, y: number): Path;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：drawing；<br>API声明：enum PathDashStyle<br>差异内容：enum PathDashStyle|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathDashStyle；<br>API声明：TRANSLATE = 0<br>差异内容：TRANSLATE = 0|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathDashStyle；<br>API声明：ROTATE = 1<br>差异内容：ROTATE = 1|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathDashStyle；<br>API声明：MORPH = 2<br>差异内容：MORPH = 2|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathEffect；<br>API声明：static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect;<br>差异内容：static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathEffect；<br>API声明：static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect;<br>差异内容：static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathEffect；<br>API声明：static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect;<br>差异内容：static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：PathEffect；<br>API声明：static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect;<br>差异内容：static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Pen；<br>API声明：getHexColor(): number;<br>差异内容：getHexColor(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Brush；<br>API声明：getHexColor(): number;<br>差异内容：getHexColor(): number;|api/@ohos.graphics.drawing.d.ts|
|新增API|NA|类名：Run；<br>API声明：getGlyphs(range: Range): Array\<number>;<br>差异内容：getGlyphs(range: Range): Array\<number>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getPositions(range: Range): Array\<common2D.Point>;<br>差异内容：getPositions(range: Range): Array\<common2D.Point>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：WordBreak；<br>API声明：BREAK_HYPHEN<br>差异内容：BREAK_HYPHEN|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：FontCollection；<br>API声明：loadFont(name: string, path: string \| Resource): Promise\<void>;<br>差异内容：loadFont(name: string, path: string \| Resource): Promise\<void>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphStyle；<br>API声明：tab?: TextTab;<br>差异内容：tab?: TextTab;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：SystemFontType；<br>API声明：CUSTOMIZED = 1 \<\< 4<br>差异内容：CUSTOMIZED = 1 \<\< 4|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Paragraph；<br>API声明：layout(width: number): Promise\<void>;<br>差异内容：layout(width: number): Promise\<void>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：class LineTypeset<br>差异内容：class LineTypeset|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineTypeset；<br>API声明：getLineBreak(startIndex: number, width: number): number;<br>差异内容：getLineBreak(startIndex: number, width: number): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：LineTypeset；<br>API声明：createLine(startIndex: number, count: number): TextLine;<br>差异内容：createLine(startIndex: number, count: number): TextLine;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ParagraphBuilder；<br>API声明：buildLineTypeset(): LineTypeset;<br>差异内容：buildLineTypeset(): LineTypeset;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface TypographicBounds<br>差异内容：interface TypographicBounds|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TypographicBounds；<br>API声明：ascent: number;<br>差异内容：ascent: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TypographicBounds；<br>API声明：descent: number;<br>差异内容：descent: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TypographicBounds；<br>API声明：leading: number;<br>差异内容：leading: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TypographicBounds；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：type CaretOffsetsCallback = (offset: number, index: number, leadingEdge: boolean) => boolean;<br>差异内容：type CaretOffsetsCallback = (offset: number, index: number, leadingEdge: boolean) => boolean;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：createTruncatedLine(width: number, ellipsisMode: EllipsisMode, ellipsis: string): TextLine;<br>差异内容：createTruncatedLine(width: number, ellipsisMode: EllipsisMode, ellipsis: string): TextLine;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：getTypographicBounds(): TypographicBounds;<br>差异内容：getTypographicBounds(): TypographicBounds;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：getImageBounds(): common2D.Rect;<br>差异内容：getImageBounds(): common2D.Rect;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：getTrailingSpaceWidth(): number;<br>差异内容：getTrailingSpaceWidth(): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：getStringIndexForPosition(point: common2D.Point): number;<br>差异内容：getStringIndexForPosition(point: common2D.Point): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：getOffsetForStringIndex(index: number): number;<br>差异内容：getOffsetForStringIndex(index: number): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：enumerateCaretOffsets(callback: CaretOffsetsCallback): void;<br>差异内容：enumerateCaretOffsets(callback: CaretOffsetsCallback): void;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextLine；<br>API声明：getAlignmentOffset(alignmentFactor: number, alignmentWidth: number): number;<br>差异内容：getAlignmentOffset(alignmentFactor: number, alignmentWidth: number): number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getStringIndices(range?: Range): Array\<number>;<br>差异内容：getStringIndices(range?: Range): Array\<number>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getStringRange(): Range;<br>差异内容：getStringRange(): Range;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getTypographicBounds(): TypographicBounds;<br>差异内容：getTypographicBounds(): TypographicBounds;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：Run；<br>API声明：getImageBounds(): common2D.Rect;<br>差异内容：getImageBounds(): common2D.Rect;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：function matchFontDescriptors(desc: FontDescriptor): Promise\<Array\<FontDescriptor>>;<br>差异内容：function matchFontDescriptors(desc: FontDescriptor): Promise\<Array\<FontDescriptor>>;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：text；<br>API声明：interface TextTab<br>差异内容：interface TextTab|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextTab；<br>API声明：alignment: TextAlign;<br>差异内容：alignment: TextAlign;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：TextTab；<br>API声明：location: number;<br>差异内容：location: number;|api/@ohos.graphics.text.d.ts|
|新增API|NA|类名：ColorSpace；<br>API声明：H_LOG = 26<br>差异内容：H_LOG = 26|api/@ohos.graphics.colorSpaceManager.d.ts|
