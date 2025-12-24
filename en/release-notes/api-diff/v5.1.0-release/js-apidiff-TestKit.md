| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
| Deleted API|Class name: global;<br>API declaration: declare enum PerfMetric<br>DIfferences: declare enum PerfMetric|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMetric;<br>API declaration: DURATION = 0<br>DIfferences: DURATION = 0|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMetric;<br>API declaration: CPU_LOAD = 1<br>DIfferences: CPU_LOAD = 1|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMetric;<br>API declaration: CPU_USAGE = 2<br>DIfferences: CPU_USAGE = 2|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMetric;<br>API declaration: MEMORY_RSS = 3<br>DIfferences: MEMORY_RSS = 3|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMetric;<br>API declaration: MEMORY_PSS = 4<br>DIfferences: MEMORY_PSS = 4|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMetric;<br>API declaration: APP_START_RESPONSE_TIME = 5<br>DIfferences: APP_START_RESPONSE_TIME = 5|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMetric;<br>API declaration: APP_START_COMPLETE_TIME = 6<br>DIfferences: APP_START_COMPLETE_TIME = 6|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMetric;<br>API declaration: PAGE_SWITCH_COMPLETE_TIME = 7<br>DIfferences: PAGE_SWITCH_COMPLETE_TIME = 7|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMetric;<br>API declaration: LIST_SWIPE_FPS = 8<br>DIfferences: LIST_SWIPE_FPS = 8|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare interface PerfTestStrategy<br>DIfferences: declare interface PerfTestStrategy|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTestStrategy;<br>API declaration: metrics: Array\<PerfMetric>;<br>DIfferences: metrics: Array\<PerfMetric>;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTestStrategy;<br>API declaration: actionCode: Callback\<Callback\<boolean>>;<br>DIfferences: actionCode: Callback\<Callback\<boolean>>;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTestStrategy;<br>API declaration: resetCode?: Callback\<Callback\<boolean>>;<br>DIfferences: resetCode?: Callback\<Callback\<boolean>>;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTestStrategy;<br>API declaration: bundleName?: string;<br>DIfferences: bundleName?: string;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTestStrategy;<br>API declaration: iterations?: number;<br>DIfferences: iterations?: number;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTestStrategy;<br>API declaration: timeout?: number;<br>DIfferences: timeout?: number;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare interface PerfMeasureResult<br>DIfferences: declare interface PerfMeasureResult|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMeasureResult;<br>API declaration: readonly metric: PerfMetric;<br>DIfferences: readonly metric: PerfMetric;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMeasureResult;<br>API declaration: readonly roundValues: Array\<number>;<br>DIfferences: readonly roundValues: Array\<number>;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMeasureResult;<br>API declaration: readonly maximum: number;<br>DIfferences: readonly maximum: number;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMeasureResult;<br>API declaration: readonly minimum: number;<br>DIfferences: readonly minimum: number;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfMeasureResult;<br>API declaration: readonly average: number;<br>DIfferences: readonly average: number;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare class PerfTest<br>DIfferences: declare class PerfTest|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTest;<br>API declaration: static create(strategy: PerfTestStrategy): PerfTest;<br>DIfferences: static create(strategy: PerfTestStrategy): PerfTest;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTest;<br>API declaration: run(): Promise\<void>;<br>DIfferences: run(): Promise\<void>;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTest;<br>API declaration: getMeasureResult(metric: PerfMetric): PerfMeasureResult;<br>DIfferences: getMeasureResult(metric: PerfMetric): PerfMeasureResult;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: PerfTest;<br>API declaration: destroy(): void;<br>DIfferences: destroy(): void;|NA|api/@ohos.test.PerfTest.d.ts|
| Deleted API|Class name: MatchPattern;<br>API declaration: REG_EXP = 4<br>DIfferences: REG_EXP = 4|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: MatchPattern;<br>API declaration: REG_EXP_ICASE = 5<br>DIfferences: REG_EXP_ICASE = 5|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Point;<br>API declaration: displayId?: number;<br>DIfferences: displayId?: number;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Rect;<br>API declaration: displayId?: number;<br>DIfferences: displayId?: number;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: WindowFilter;<br>API declaration: displayId?: number;<br>DIfferences: displayId?: number;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare interface TouchPadSwipeOptions<br>DIfferences: declare interface TouchPadSwipeOptions|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: TouchPadSwipeOptions;<br>API declaration: stay?: boolean;<br>DIfferences: stay?: boolean;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: TouchPadSwipeOptions;<br>API declaration: speed?: number;<br>DIfferences: speed?: number;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: global;<br>API declaration: declare interface InputTextMode<br>DIfferences: declare interface InputTextMode|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: InputTextMode;<br>API declaration: paste?: boolean;<br>DIfferences: paste?: boolean;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: InputTextMode;<br>API declaration: addition?: boolean;<br>DIfferences: addition?: boolean;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: On;<br>API declaration: id(id: string, pattern: MatchPattern): On;<br>DIfferences: id(id: string, pattern: MatchPattern): On;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: On;<br>API declaration: type(tp: string, pattern: MatchPattern): On;<br>DIfferences: type(tp: string, pattern: MatchPattern): On;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: On;<br>API declaration: belongingDisplay(displayId: number): On;<br>DIfferences: belongingDisplay(displayId: number): On;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: On;<br>API declaration: hint(val: string, pattern?: MatchPattern): On;<br>DIfferences: hint(val: string, pattern?: MatchPattern): On;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: On;<br>API declaration: originalText(text: string, pattern?: MatchPattern): On;<br>DIfferences: originalText(text: string, pattern?: MatchPattern): On;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Component;<br>API declaration: getDisplayId(): Promise\<number>;<br>DIfferences: getDisplayId(): Promise\<number>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Component;<br>API declaration: inputText(text: string, mode: InputTextMode): Promise\<void>;<br>DIfferences: inputText(text: string, mode: InputTextMode): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Component;<br>API declaration: scrollSearch(on: On, vertical?: boolean, offset?: number): Promise\<Component>;<br>DIfferences: scrollSearch(on: On, vertical?: boolean, offset?: number): Promise\<Component>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Component;<br>API declaration: getHint(): Promise\<string>;<br>DIfferences: getHint(): Promise\<string>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Component;<br>API declaration: getOriginalText(): Promise\<string>;<br>DIfferences: getOriginalText(): Promise\<string>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: pressBack(displayId: number): Promise\<void>;<br>DIfferences: pressBack(displayId: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: triggerKey(keyCode: number, displayId: number): Promise\<void>;<br>DIfferences: triggerKey(keyCode: number, displayId: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: triggerCombineKeys(key0: number, key1: number, key2?: number, displayId?: number): Promise\<void>;<br>DIfferences: triggerCombineKeys(key0: number, key1: number, key2?: number, displayId?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: clickAt(point: Point): Promise\<void>;<br>DIfferences: clickAt(point: Point): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: doubleClickAt(point: Point): Promise\<void>;<br>DIfferences: doubleClickAt(point: Point): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: longClickAt(point: Point, duration?: number): Promise\<void>;<br>DIfferences: longClickAt(point: Point, duration?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: swipeBetween(from: Point, to: Point, speed?: number): Promise\<void>;<br>DIfferences: swipeBetween(from: Point, to: Point, speed?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: dragBetween(from: Point, to: Point, speed?: number, duration?: number): Promise\<void>;<br>DIfferences: dragBetween(from: Point, to: Point, speed?: number, duration?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: screenCap(savePath: string, displayId: number): Promise\<boolean>;<br>DIfferences: screenCap(savePath: string, displayId: number): Promise\<boolean>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: getDisplayRotation(displayId: number): Promise\<DisplayRotation>;<br>DIfferences: getDisplayRotation(displayId: number): Promise\<DisplayRotation>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: getDisplaySize(displayId: number): Promise\<Point>;<br>DIfferences: getDisplaySize(displayId: number): Promise\<Point>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: getDisplayDensity(displayId: number): Promise\<Point>;<br>DIfferences: getDisplayDensity(displayId: number): Promise\<Point>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: pressHome(displayId: number): Promise\<void>;<br>DIfferences: pressHome(displayId: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: fling(direction: UiDirection, speed: number, displayId: number): Promise\<void>;<br>DIfferences: fling(direction: UiDirection, speed: number, displayId: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: mouseLongClick(p: Point, btnId: MouseButton, key1?: number, key2?: number, duration?: number): Promise\<void>;<br>DIfferences: mouseLongClick(p: Point, btnId: MouseButton, key1?: number, key2?: number, duration?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: mouseDrag(from: Point, to: Point, speed?: number, duration?: number): Promise\<void>;<br>DIfferences: mouseDrag(from: Point, to: Point, speed?: number, duration?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: inputText(p: Point, text: string, mode: InputTextMode): Promise\<void>;<br>DIfferences: inputText(p: Point, text: string, mode: InputTextMode): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: touchPadMultiFingerSwipe(fingers: number, direction: UiDirection, options?: TouchPadSwipeOptions): Promise\<void>;<br>DIfferences: touchPadMultiFingerSwipe(fingers: number, direction: UiDirection, options?: TouchPadSwipeOptions): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: penClick(point: Point): Promise\<void>;<br>DIfferences: penClick(point: Point): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: penLongClick(point: Point, pressure?: number): Promise\<void>;<br>DIfferences: penLongClick(point: Point, pressure?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: penDoubleClick(point: Point): Promise\<void>;<br>DIfferences: penDoubleClick(point: Point): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: penSwipe(startPoint: Point, endPoint: Point, speed?: number, pressure?: number): Promise\<void>;<br>DIfferences: penSwipe(startPoint: Point, endPoint: Point, speed?: number, pressure?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: injectPenPointerAction(pointers: PointerMatrix, speed?: number, pressure?: number): Promise\<void>;<br>DIfferences: injectPenPointerAction(pointers: PointerMatrix, speed?: number, pressure?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: Driver;<br>API declaration: crownRotate(d: number, speed?: number): Promise\<void>;<br>DIfferences: crownRotate(d: number, speed?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
| Deleted API|Class name: UiWindow;<br>API declaration: getDisplayId(): Promise\<number>;<br>DIfferences: getDisplayId(): Promise\<number>;|NA|api/@ohos.UiTest.d.ts|
|Deleted kit|Class name: global;<br>API declaration: api\@ohos.test.PerfTest.d.ts<br>DIfferences: TestKit|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.test.PerfTest.d.ts|
|Compatible for ArkTS version evolution|Class name: global;<br>API declaration: interface TestRunner<br>DIfferences: NA|Class name: global;<br>API declaration: export interface TestRunner<br>DIfferences: NA|api/@ohos.application.testRunner.d.ts|
