| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：On；<br>API声明：id(id: string, pattern: MatchPattern): On;<br>差异内容：id(id: string, pattern: MatchPattern): On;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：On；<br>API声明：type(tp: string, pattern: MatchPattern): On;<br>差异内容：type(tp: string, pattern: MatchPattern): On;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：Component；<br>API声明：scrollSearch(on: On, vertical?: boolean, offset?: number): Promise\<Component>;<br>差异内容：scrollSearch(on: On, vertical?: boolean, offset?: number): Promise\<Component>;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：MatchPattern；<br>API声明：REG_EXP = 4<br>差异内容：REG_EXP = 4|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：MatchPattern；<br>API声明：REG_EXP_ICASE = 5<br>差异内容：REG_EXP_ICASE = 5|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface TouchPadSwipeOptions<br>差异内容：declare interface TouchPadSwipeOptions|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：TouchPadSwipeOptions；<br>API声明：stay?: boolean;<br>差异内容：stay?: boolean;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：TouchPadSwipeOptions；<br>API声明：speed?: number;<br>差异内容：speed?: number;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：On；<br>API声明：hint(val: string, pattern?: MatchPattern): On;<br>差异内容：hint(val: string, pattern?: MatchPattern): On;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：Component；<br>API声明：getHint(): Promise\<string>;<br>差异内容：getHint(): Promise\<string>;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：Driver；<br>API声明：touchPadMultiFingerSwipe(fingers: number, direction: UiDirection, options?: TouchPadSwipeOptions): Promise\<void>;<br>差异内容：touchPadMultiFingerSwipe(fingers: number, direction: UiDirection, options?: TouchPadSwipeOptions): Promise\<void>;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：Driver；<br>API声明：penClick(point: Point): Promise\<void>;<br>差异内容：penClick(point: Point): Promise\<void>;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：Driver；<br>API声明：penLongClick(point: Point, pressure?: number): Promise\<void>;<br>差异内容：penLongClick(point: Point, pressure?: number): Promise\<void>;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：Driver；<br>API声明：penDoubleClick(point: Point): Promise\<void>;<br>差异内容：penDoubleClick(point: Point): Promise\<void>;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：Driver；<br>API声明：penSwipe(startPoint: Point, endPoint: Point, speed?: number, pressure?: number): Promise\<void>;<br>差异内容：penSwipe(startPoint: Point, endPoint: Point, speed?: number, pressure?: number): Promise\<void>;|api/@ohos.UiTest.d.ts|
|新增API|NA|类名：Driver；<br>API声明：injectPenPointerAction(pointers: PointerMatrix, speed?: number, pressure?: number): Promise\<void>;<br>差异内容：injectPenPointerAction(pointers: PointerMatrix, speed?: number, pressure?: number): Promise\<void>;|api/@ohos.UiTest.d.ts|
