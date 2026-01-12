| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: Canvas;<br>API declaration: drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number, ambientColor: common2D.Color \| number, spotColor: common2D.Color \| number, flag: ShadowFlag): void;<br>DIfferences: drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number, ambientColor: common2D.Color \| number, spotColor: common2D.Color \| number, flag: ShadowFlag): void;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Canvas;<br>API declaration: drawColor(color: number, blendMode?: BlendMode): void;<br>DIfferences: drawColor(color: number, blendMode?: BlendMode): void;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Canvas;<br>API declaration: clear(color: common2D.Color \| number): void;<br>DIfferences: clear(color: common2D.Color \| number): void;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Lattice;<br>API declaration: static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<number> \| null): Lattice;<br>DIfferences: static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<number> \| null): Lattice;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: ShadowLayer;<br>API declaration: static create(blurRadius: number, x: number, y: number, color: common2D.Color \| number): ShadowLayer;<br>DIfferences: static create(blurRadius: number, x: number, y: number, color: common2D.Color \| number): ShadowLayer;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: ColorFilter;<br>API declaration: static createBlendModeColorFilter(color: common2D.Color \| number, mode: BlendMode): ColorFilter;<br>DIfferences: static createBlendModeColorFilter(color: common2D.Color \| number, mode: BlendMode): ColorFilter;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Pen;<br>API declaration: setColor(color: number): void;<br>DIfferences: setColor(color: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Brush;<br>API declaration: setColor(color: number): void;<br>DIfferences: setColor(color: number): void;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: drawing;<br>API declaration: enum PathIteratorVerb<br>DIfferences: enum PathIteratorVerb|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIteratorVerb;<br>API declaration: MOVE = 0<br>DIfferences: MOVE = 0|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIteratorVerb;<br>API declaration: LINE = 1<br>DIfferences: LINE = 1|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIteratorVerb;<br>API declaration: QUAD = 2<br>DIfferences: QUAD = 2|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIteratorVerb;<br>API declaration: CONIC = 3<br>DIfferences: CONIC = 3|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIteratorVerb;<br>API declaration: CUBIC = 4<br>DIfferences: CUBIC = 4|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIteratorVerb;<br>API declaration: CLOSE = 5<br>DIfferences: CLOSE = 5|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIteratorVerb;<br>API declaration: DONE = CLOSE + 1<br>DIfferences: DONE = CLOSE + 1|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: drawing;<br>API declaration: class PathIterator<br>DIfferences: class PathIterator|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIterator;<br>API declaration: next(points: Array\<common2D.Point>, offset?: number): PathIteratorVerb;<br>DIfferences: next(points: Array\<common2D.Point>, offset?: number): PathIteratorVerb;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIterator;<br>API declaration: peek(): PathIteratorVerb;<br>DIfferences: peek(): PathIteratorVerb;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathIterator;<br>API declaration: hasNext(): boolean;<br>DIfferences: hasNext(): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Path;<br>API declaration: getSegment(forceClosed: boolean, start: number, stop: number, startWithMoveTo: boolean, dst: Path): boolean;<br>DIfferences: getSegment(forceClosed: boolean, start: number, stop: number, startWithMoveTo: boolean, dst: Path): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Path;<br>API declaration: getPathIterator(): PathIterator;<br>DIfferences: getPathIterator(): PathIterator;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Canvas;<br>API declaration: drawImageLattice(pixelmap: image.PixelMap, lattice: Lattice, dstRect: common2D.Rect, filterMode: FilterMode): void;<br>DIfferences: drawImageLattice(pixelmap: image.PixelMap, lattice: Lattice, dstRect: common2D.Rect, filterMode: FilterMode): void;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Canvas;<br>API declaration: drawImageNine(pixelmap: image.PixelMap, center: common2D.Rect, dstRect: common2D.Rect, filterMode: FilterMode): void;<br>DIfferences: drawImageNine(pixelmap: image.PixelMap, center: common2D.Rect, dstRect: common2D.Rect, filterMode: FilterMode): void;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Canvas;<br>API declaration: drawArcWithCenter(arc: common2D.Rect, startAngle: number, sweepAngle: number, useCenter: boolean): void;<br>DIfferences: drawArcWithCenter(arc: common2D.Rect, startAngle: number, sweepAngle: number, useCenter: boolean): void;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Canvas;<br>API declaration: quickRejectPath(path: Path): boolean;<br>DIfferences: quickRejectPath(path: Path): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Canvas;<br>API declaration: quickRejectRect(rect: common2D.Rect): boolean;<br>DIfferences: quickRejectRect(rect: common2D.Rect): boolean;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Typeface;<br>API declaration: static makeFromRawFile(rawfile: Resource): Typeface;<br>DIfferences: static makeFromRawFile(rawfile: Resource): Typeface;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Font;<br>API declaration: createPathForGlyph(index: number): Path;<br>DIfferences: createPathForGlyph(index: number): Path;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Font;<br>API declaration: getBounds(glyphs: Array\<number>): Array\<common2D.Rect>;<br>DIfferences: getBounds(glyphs: Array\<number>): Array\<common2D.Rect>;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Font;<br>API declaration: getTextPath(text: string, byteLength: number, x: number, y: number): Path;<br>DIfferences: getTextPath(text: string, byteLength: number, x: number, y: number): Path;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: drawing;<br>API declaration: enum PathDashStyle<br>DIfferences: enum PathDashStyle|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathDashStyle;<br>API declaration: TRANSLATE = 0<br>DIfferences: TRANSLATE = 0|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathDashStyle;<br>API declaration: ROTATE = 1<br>DIfferences: ROTATE = 1|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathDashStyle;<br>API declaration: MORPH = 2<br>DIfferences: MORPH = 2|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathEffect;<br>API declaration: static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect;<br>DIfferences: static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathEffect;<br>API declaration: static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect;<br>DIfferences: static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathEffect;<br>API declaration: static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect;<br>DIfferences: static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: PathEffect;<br>API declaration: static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect;<br>DIfferences: static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Pen;<br>API declaration: getHexColor(): number;<br>DIfferences: getHexColor(): number;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Brush;<br>API declaration: getHexColor(): number;<br>DIfferences: getHexColor(): number;|api/@ohos.graphics.drawing.d.ts|
|New API |NA|Class name: Run;<br>API declaration: getGlyphs(range: Range): Array\<number>;<br>DIfferences: getGlyphs(range: Range): Array\<number>;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: Run;<br>API declaration: getPositions(range: Range): Array\<common2D.Point>;<br>DIfferences: getPositions(range: Range): Array\<common2D.Point>;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: WordBreak;<br>API declaration: BREAK_HYPHEN<br>DIfferences: BREAK_HYPHEN|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: FontCollection;<br>API declaration: loadFont(name: string, path: string \| Resource): Promise\<void>;<br>DIfferences: loadFont(name: string, path: string \| Resource): Promise\<void>;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: ParagraphStyle;<br>API declaration: tab?: TextTab;<br>DIfferences: tab?: TextTab;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: SystemFontType;<br>API declaration: CUSTOMIZED = 1 \<\< 4<br>DIfferences: CUSTOMIZED = 1 \<\< 4|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: Paragraph;<br>API declaration: layout(width: number): Promise\<void>;<br>DIfferences: layout(width: number): Promise\<void>;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: text;<br>API declaration: class LineTypeset<br>DIfferences: class LineTypeset|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: LineTypeset;<br>API declaration: getLineBreak(startIndex: number, width: number): number;<br>DIfferences: getLineBreak(startIndex: number, width: number): number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: LineTypeset;<br>API declaration: createLine(startIndex: number, count: number): TextLine;<br>DIfferences: createLine(startIndex: number, count: number): TextLine;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: ParagraphBuilder;<br>API declaration: buildLineTypeset(): LineTypeset;<br>DIfferences: buildLineTypeset(): LineTypeset;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: text;<br>API declaration: interface TypographicBounds<br>DIfferences: interface TypographicBounds|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TypographicBounds;<br>API declaration: ascent: number;<br>DIfferences: ascent: number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TypographicBounds;<br>API declaration: descent: number;<br>DIfferences: descent: number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TypographicBounds;<br>API declaration: leading: number;<br>DIfferences: leading: number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TypographicBounds;<br>API declaration: width: number;<br>DIfferences: width: number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: text;<br>API declaration: type CaretOffsetsCallback = (offset: number, index: number, leadingEdge: boolean) => boolean;<br>DIfferences: type CaretOffsetsCallback = (offset: number, index: number, leadingEdge: boolean) => boolean;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextLine;<br>API declaration: createTruncatedLine(width: number, ellipsisMode: EllipsisMode, ellipsis: string): TextLine;<br>DIfferences: createTruncatedLine(width: number, ellipsisMode: EllipsisMode, ellipsis: string): TextLine;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextLine;<br>API declaration: getTypographicBounds(): TypographicBounds;<br>DIfferences: getTypographicBounds(): TypographicBounds;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextLine;<br>API declaration: getImageBounds(): common2D.Rect;<br>DIfferences: getImageBounds(): common2D.Rect;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextLine;<br>API declaration: getTrailingSpaceWidth(): number;<br>DIfferences: getTrailingSpaceWidth(): number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextLine;<br>API declaration: getStringIndexForPosition(point: common2D.Point): number;<br>DIfferences: getStringIndexForPosition(point: common2D.Point): number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextLine;<br>API declaration: getOffsetForStringIndex(index: number): number;<br>DIfferences: getOffsetForStringIndex(index: number): number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextLine;<br>API declaration: enumerateCaretOffsets(callback: CaretOffsetsCallback): void;<br>DIfferences: enumerateCaretOffsets(callback: CaretOffsetsCallback): void;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextLine;<br>API declaration: getAlignmentOffset(alignmentFactor: number, alignmentWidth: number): number;<br>DIfferences: getAlignmentOffset(alignmentFactor: number, alignmentWidth: number): number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: Run;<br>API declaration: getStringIndices(range?: Range): Array\<number>;<br>DIfferences: getStringIndices(range?: Range): Array\<number>;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: Run;<br>API declaration: getStringRange(): Range;<br>DIfferences: getStringRange(): Range;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: Run;<br>API declaration: getTypographicBounds(): TypographicBounds;<br>DIfferences: getTypographicBounds(): TypographicBounds;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: Run;<br>API declaration: getImageBounds(): common2D.Rect;<br>DIfferences: getImageBounds(): common2D.Rect;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: text;<br>API declaration: function matchFontDescriptors(desc: FontDescriptor): Promise\<Array\<FontDescriptor>>;<br>DIfferences: function matchFontDescriptors(desc: FontDescriptor): Promise\<Array\<FontDescriptor>>;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: text;<br>API declaration: interface TextTab<br>DIfferences: interface TextTab|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextTab;<br>API declaration: alignment: TextAlign;<br>DIfferences: alignment: TextAlign;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: TextTab;<br>API declaration: location: number;<br>DIfferences: location: number;|api/@ohos.graphics.text.d.ts|
|New API |NA|Class name: ColorSpace;<br>API declaration: H_LOG = 26<br>DIfferences: H_LOG = 26|api/@ohos.graphics.colorSpaceManager.d.ts|
