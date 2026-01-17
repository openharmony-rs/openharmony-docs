# ArkTS运行时常见问题
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @DaiHuina1997-->
<!--Designer: @yao_dashuai-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @foryourself-->

## 正则运算与预期输出结果不一致场景

如果使用正则运算时结果与期望不符，请检查以下场景。

### 正则运算对于\b处理与预期不一致

<!-- @[test_wordBoundaryInArkRegex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

规避方案：暂无。
> **说明：**
> 
> 正则匹配\b（单词边界）遇到某些ASCII编码之外的字符时，会将其当成ASCII字符来处理，从而将不是单词边界匹配识别成单词边界。

### 正则运算对于先行断言((?=pattern)或(?!pattern)) 嵌套在后行断言((?<=pattern)或(?<!pattern))内部的场景与预期不一致

<!-- @[test_lookbehindWithNestedLookahead](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

规避方案：使用/(?<=abcd)ef/代替/(?<=ab(?=c)cd)ef/。

### 正则运算对于大小写的处理与预期不一致

<!-- @[test_regexIgnoreCaseCaseFolding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

规避方案：暂无。

### 正则运算/()/ug匹配时lastIndex与预期不一致

<!-- @[test_regexLastIndexWithEmptyGroupInGlobalUnicodeMode](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

规避方案：暂无。

### 正则运算[]内部使用'-'与预期不一致

<!-- @[test_beforeRegexHyphenInCharacterClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

规避方案：使用转义后的"-"。

<!-- @[test_afterRegexHyphenInCharacterClass](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

### 正则运算具名捕获组获取与预期不一致

<!-- @[test_namedCaptureGroupAccess](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

规避方案：计算具名捕获组位置获取具名捕获组匹配的内容。

<!-- @[test_getNamedGroupMatchByIndexFallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

### 正则匹配使用'|'与预期不一致

在使用正则匹配时，如果'|'前是一个空匹配，会导致'|'后的匹配不成功。

<!-- @[test_beforeRegexAlternationOperator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

规避方案：使用reg2或reg3替换reg1。

<!-- @[test_afterRegexAlternationOperator](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

### 字符串 `replace` 接口对于第一个参数为空字符串的场景与预期不一致

在使用字符串replace接口时，如果第一个参数是空字符串，则直接返回原始字符串。

<!-- @[test_beforeStringReplaceWithEmptySearchValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

规避方案：使用正则表达式 `/^/` 表示字符串起始符，作为第一个参数。

<!-- @[test_afterStringReplaceWithEmptySearchValue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

## Async函数内部异常的处理机制

**场景**

如果在Async函数内部产生了异常，且没有使用catch捕获该异常，在ArkTS中不会导致进程退出。其本质是Async函数返回了一个rejected状态的Promise对象，没有被处理，使得Promise的rejected状态没有被捕获。Async函数内部的异常会变成 unhandledRejection，表现为异常未抛出。

**Async函数内部异常的捕获方式**

1. 使用[errorManager.on()](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md#errormanageronerror)捕获到Async函数产生的unhandledrejection事件，再通过编写errorManager.on()注册的回调函数，来进行异常处理操作。

<!-- @[test_safeAsyncCall](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

2. 在Async函数内部，针对可能发生异常的代码块添加try-catch逻辑，直接捕获可能出现的异常。

> **注意：**
> 
> 注意必须在Async函数内部，外部无法捕获Async函数内部的异常，外部只能通过errorManager.on()监听。


**查看Async函数内部是否有异常的方式**

若开发者仅需要查看Async函数内部是否产生异常，首先需要在DevEco Studio终端执行以下hilog命令开启debug级别日志打印：

```shell
   hilog -b D
```

然后点击DevEco Studio下方HiLog选项卡，输入过滤条件“Throw error:”，即可查看到Async函数内产生的异常信息。

![alt text](figures/arkts-runtime-faq.png)

## Array.flatMap()接口常见问题

Array.flatMap()接口在处理包含Proxy的Array时，未正确展平嵌套的Proxy Array，导致返回结果与预期不一致。

### ArkTS使用场景

<!-- @[test_arrayFlatMapCompliance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->

### ArkUI使用场景

ArkUI状态管理框架会为使用状态变量装饰器（如@State、@Trace、@Local）装饰的Array添加一层代理，用于观测API调用产生的变化。如果状态修饰器与Array组合，并且调用Array.flatMap，会出现如下问题。

以状态管理V2为例：

<!-- @[test_componentV2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Local.ets) -->

### Array.flatMap规避方案

避免使用Array.flatMap()接口，改为调用Array.map()接口后再调用深度为1的Array.flat()接口。以上文ArkTS使用场景为例：

<!-- @[test_afterArrayFlatMapCompliance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTSRuntime/ArktsRuntimeFag/entry/src/main/ets/pages/Scene.ets) -->
