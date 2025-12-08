| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除API|类名：global；<br>API声明：declare enum PerfMetric<br>差异内容：declare enum PerfMetric|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMetric；<br>API声明：DURATION = 0<br>差异内容：DURATION = 0|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMetric；<br>API声明：CPU_LOAD = 1<br>差异内容：CPU_LOAD = 1|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMetric；<br>API声明：CPU_USAGE = 2<br>差异内容：CPU_USAGE = 2|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMetric；<br>API声明：MEMORY_RSS = 3<br>差异内容：MEMORY_RSS = 3|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMetric；<br>API声明：MEMORY_PSS = 4<br>差异内容：MEMORY_PSS = 4|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMetric；<br>API声明：APP_START_RESPONSE_TIME = 5<br>差异内容：APP_START_RESPONSE_TIME = 5|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMetric；<br>API声明：APP_START_COMPLETE_TIME = 6<br>差异内容：APP_START_COMPLETE_TIME = 6|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMetric；<br>API声明：PAGE_SWITCH_COMPLETE_TIME = 7<br>差异内容：PAGE_SWITCH_COMPLETE_TIME = 7|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMetric；<br>API声明：LIST_SWIPE_FPS = 8<br>差异内容：LIST_SWIPE_FPS = 8|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：global；<br>API声明：declare interface PerfTestStrategy<br>差异内容：declare interface PerfTestStrategy|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTestStrategy；<br>API声明：metrics: Array\<PerfMetric>;<br>差异内容：metrics: Array\<PerfMetric>;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTestStrategy；<br>API声明：actionCode: Callback\<Callback\<boolean>>;<br>差异内容：actionCode: Callback\<Callback\<boolean>>;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTestStrategy；<br>API声明：resetCode?: Callback\<Callback\<boolean>>;<br>差异内容：resetCode?: Callback\<Callback\<boolean>>;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTestStrategy；<br>API声明：bundleName?: string;<br>差异内容：bundleName?: string;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTestStrategy；<br>API声明：iterations?: number;<br>差异内容：iterations?: number;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTestStrategy；<br>API声明：timeout?: number;<br>差异内容：timeout?: number;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：global；<br>API声明：declare interface PerfMeasureResult<br>差异内容：declare interface PerfMeasureResult|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMeasureResult；<br>API声明：readonly metric: PerfMetric;<br>差异内容：readonly metric: PerfMetric;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMeasureResult；<br>API声明：readonly roundValues: Array\<number>;<br>差异内容：readonly roundValues: Array\<number>;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMeasureResult；<br>API声明：readonly maximum: number;<br>差异内容：readonly maximum: number;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMeasureResult；<br>API声明：readonly minimum: number;<br>差异内容：readonly minimum: number;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfMeasureResult；<br>API声明：readonly average: number;<br>差异内容：readonly average: number;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：global；<br>API声明：declare class PerfTest<br>差异内容：declare class PerfTest|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTest；<br>API声明：static create(strategy: PerfTestStrategy): PerfTest;<br>差异内容：static create(strategy: PerfTestStrategy): PerfTest;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTest；<br>API声明：run(): Promise\<void>;<br>差异内容：run(): Promise\<void>;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTest；<br>API声明：getMeasureResult(metric: PerfMetric): PerfMeasureResult;<br>差异内容：getMeasureResult(metric: PerfMetric): PerfMeasureResult;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：PerfTest；<br>API声明：destroy(): void;<br>差异内容：destroy(): void;|NA|api/@ohos.test.PerfTest.d.ts|
|删除API|类名：MatchPattern；<br>API声明：REG_EXP = 4<br>差异内容：REG_EXP = 4|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：MatchPattern；<br>API声明：REG_EXP_ICASE = 5<br>差异内容：REG_EXP_ICASE = 5|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Point；<br>API声明：displayId?: number;<br>差异内容：displayId?: number;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Rect；<br>API声明：displayId?: number;<br>差异内容：displayId?: number;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：WindowFilter；<br>API声明：displayId?: number;<br>差异内容：displayId?: number;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：global；<br>API声明：declare interface TouchPadSwipeOptions<br>差异内容：declare interface TouchPadSwipeOptions|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：TouchPadSwipeOptions；<br>API声明：stay?: boolean;<br>差异内容：stay?: boolean;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：TouchPadSwipeOptions；<br>API声明：speed?: number;<br>差异内容：speed?: number;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：global；<br>API声明：declare interface InputTextMode<br>差异内容：declare interface InputTextMode|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：InputTextMode；<br>API声明：paste?: boolean;<br>差异内容：paste?: boolean;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：InputTextMode；<br>API声明：addition?: boolean;<br>差异内容：addition?: boolean;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：On；<br>API声明：id(id: string, pattern: MatchPattern): On;<br>差异内容：id(id: string, pattern: MatchPattern): On;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：On；<br>API声明：type(tp: string, pattern: MatchPattern): On;<br>差异内容：type(tp: string, pattern: MatchPattern): On;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：On；<br>API声明：belongingDisplay(displayId: number): On;<br>差异内容：belongingDisplay(displayId: number): On;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：On；<br>API声明：hint(val: string, pattern?: MatchPattern): On;<br>差异内容：hint(val: string, pattern?: MatchPattern): On;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：On；<br>API声明：originalText(text: string, pattern?: MatchPattern): On;<br>差异内容：originalText(text: string, pattern?: MatchPattern): On;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Component；<br>API声明：getDisplayId(): Promise\<number>;<br>差异内容：getDisplayId(): Promise\<number>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Component；<br>API声明：inputText(text: string, mode: InputTextMode): Promise\<void>;<br>差异内容：inputText(text: string, mode: InputTextMode): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Component；<br>API声明：scrollSearch(on: On, vertical?: boolean, offset?: number): Promise\<Component>;<br>差异内容：scrollSearch(on: On, vertical?: boolean, offset?: number): Promise\<Component>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Component；<br>API声明：getHint(): Promise\<string>;<br>差异内容：getHint(): Promise\<string>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Component；<br>API声明：getOriginalText(): Promise\<string>;<br>差异内容：getOriginalText(): Promise\<string>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：pressBack(displayId: number): Promise\<void>;<br>差异内容：pressBack(displayId: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：triggerKey(keyCode: number, displayId: number): Promise\<void>;<br>差异内容：triggerKey(keyCode: number, displayId: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：triggerCombineKeys(key0: number, key1: number, key2?: number, displayId?: number): Promise\<void>;<br>差异内容：triggerCombineKeys(key0: number, key1: number, key2?: number, displayId?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：clickAt(point: Point): Promise\<void>;<br>差异内容：clickAt(point: Point): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：doubleClickAt(point: Point): Promise\<void>;<br>差异内容：doubleClickAt(point: Point): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：longClickAt(point: Point, duration?: number): Promise\<void>;<br>差异内容：longClickAt(point: Point, duration?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：swipeBetween(from: Point, to: Point, speed?: number): Promise\<void>;<br>差异内容：swipeBetween(from: Point, to: Point, speed?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：dragBetween(from: Point, to: Point, speed?: number, duration?: number): Promise\<void>;<br>差异内容：dragBetween(from: Point, to: Point, speed?: number, duration?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：screenCap(savePath: string, displayId: number): Promise\<boolean>;<br>差异内容：screenCap(savePath: string, displayId: number): Promise\<boolean>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：getDisplayRotation(displayId: number): Promise\<DisplayRotation>;<br>差异内容：getDisplayRotation(displayId: number): Promise\<DisplayRotation>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：getDisplaySize(displayId: number): Promise\<Point>;<br>差异内容：getDisplaySize(displayId: number): Promise\<Point>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：getDisplayDensity(displayId: number): Promise\<Point>;<br>差异内容：getDisplayDensity(displayId: number): Promise\<Point>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：pressHome(displayId: number): Promise\<void>;<br>差异内容：pressHome(displayId: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：fling(direction: UiDirection, speed: number, displayId: number): Promise\<void>;<br>差异内容：fling(direction: UiDirection, speed: number, displayId: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：mouseLongClick(p: Point, btnId: MouseButton, key1?: number, key2?: number, duration?: number): Promise\<void>;<br>差异内容：mouseLongClick(p: Point, btnId: MouseButton, key1?: number, key2?: number, duration?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：mouseDrag(from: Point, to: Point, speed?: number, duration?: number): Promise\<void>;<br>差异内容：mouseDrag(from: Point, to: Point, speed?: number, duration?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：inputText(p: Point, text: string, mode: InputTextMode): Promise\<void>;<br>差异内容：inputText(p: Point, text: string, mode: InputTextMode): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：touchPadMultiFingerSwipe(fingers: number, direction: UiDirection, options?: TouchPadSwipeOptions): Promise\<void>;<br>差异内容：touchPadMultiFingerSwipe(fingers: number, direction: UiDirection, options?: TouchPadSwipeOptions): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：penClick(point: Point): Promise\<void>;<br>差异内容：penClick(point: Point): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：penLongClick(point: Point, pressure?: number): Promise\<void>;<br>差异内容：penLongClick(point: Point, pressure?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：penDoubleClick(point: Point): Promise\<void>;<br>差异内容：penDoubleClick(point: Point): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：penSwipe(startPoint: Point, endPoint: Point, speed?: number, pressure?: number): Promise\<void>;<br>差异内容：penSwipe(startPoint: Point, endPoint: Point, speed?: number, pressure?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：injectPenPointerAction(pointers: PointerMatrix, speed?: number, pressure?: number): Promise\<void>;<br>差异内容：injectPenPointerAction(pointers: PointerMatrix, speed?: number, pressure?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：Driver；<br>API声明：crownRotate(d: number, speed?: number): Promise\<void>;<br>差异内容：crownRotate(d: number, speed?: number): Promise\<void>;|NA|api/@ohos.UiTest.d.ts|
|删除API|类名：UiWindow；<br>API声明：getDisplayId(): Promise\<number>;<br>差异内容：getDisplayId(): Promise\<number>;|NA|api/@ohos.UiTest.d.ts|
|删除kit|类名：global；<br>API声明：api\@ohos.test.PerfTest.d.ts<br>差异内容：TestKit|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.test.PerfTest.d.ts|
|arkts演进版本整改兼容变化|类名：global；<br>API声明：interface TestRunner<br>差异内容：NA|类名：global；<br>API声明：export interface TestRunner<br>差异内容：NA|api/@ohos.application.testRunner.d.ts|
