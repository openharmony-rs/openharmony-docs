---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "讲解ArkTS分支、循环、跳转等控制语句的语法与用法，涵盖循环控制与提前退出等常用技巧。"
keywords: [ArkTS, 控制语句, 分支语句, 循环语句, switch, 跳转语句, 提前退出]
doctype: guide
status: active
---

# 控制语句
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

控制语句用于控制程序的执行流程。ArkTS提供分支语句、循环语句和跳转语句，实现复杂的逻辑控制。

## 分支语句

分支语句根据条件选择不同的执行路径。

### if语句

`if`语句在条件为`true`时执行对应代码块，可搭配`else if`和`else`处理多分支场景。对于只需满足条件即执行、无需处理其他分支的简单场景，可省略`else`部分：

<!-- @[simple_condition_check](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let value: number = 10;

// 只检查条件，无需else
if (value > 0) {
  console.info('正数');
}

// else分支为空时可直接省略
if (value < 0) {
  console.info('负数');
}

// 简洁写法
if (value !== 0) {
  console.info('非零');
}
```

当需要处理多个互斥条件时，可以使用`else if`串联多个判断分支：

<!-- @[if_else_if_chain](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let chainScore: number = 85;

if (chainScore >= 90) {
  console.info('优秀');
} else if (chainScore >= 80) {
  console.info('良好');
} else if (chainScore >= 60) {
  console.info('及格');
} else {
  console.info('不及格');
}

// 多条件组合
let role: string = 'admin';
let hasPermission: boolean = true;

if (role === 'admin') {
  console.info('管理员权限');
} else if (role === 'user' && hasPermission) {
  console.info('用户权限');
} else {
  console.info('无权限');
}
```

### switch语句

`switch`语句根据表达式的值匹配多个`case`分支，适合离散值的多分支选择。

``` TypeScript
switch (expression) {
  case value1:
    // 执行代码
    break;
  case value2:
    // 执行代码
    break;
  default:
    // 默认执行代码
    break;
}
```

下面通过日期和状态匹配的具体示例展示`switch`的基本用法：

<!-- @[switch_basic_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let day: number = 3;

switch (day) {
  case 1:
    console.info('星期一');
    break;
  case 2:
    console.info('星期二');
    break;
  case 3:
    console.info('星期三');
    break;
  case 4:
    console.info('星期四');
    break;
  case 5:
    console.info('星期五');
    break;
  case 6:
    console.info('星期六');
    break;
  case 7:
    console.info('星期日');
    break;
  default:
    console.info('无效日期');
}

let status: string = 'active';

switch (status) {
  case 'active':
    console.info('激活状态');
    break;
  case 'inactive':
    console.info('未激活状态');
    break;
  case 'pending':
    console.info('待处理状态');
    break;
  default:
    console.info('未知状态');
}
```

`break`语句用来控制`switch`不继续向下执行，遗漏`break`导致执行了非预期的逻辑是很常见的编程错误。

`default`分支用于捕获所有未匹配的情况，适合处理未知命令等场景。

省略`break`通常用于合并多个`case`标签，复用同一段执行逻辑，实现值的分组匹配：

<!-- @[switch_case_fallthrough](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let fallValue: number = 5;

switch (fallValue) {
  case 1:
  case 2:
  case 3:
    console.info('小数值');
    break;
  case 4:
  case 5:
  case 6:
    console.info('中等数值');
    break;
  default:
    console.info('大数值');
}
```

`switch`和`if...else if`各有适用场景：前者适合明确、离散的值判断，后者适合复杂条件、区间范围的判断。以下示例对比两种写法：

<!-- @[switch_vs_if_range](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
let rangeScore: number = 85;

// 使用if实现范围匹配
if (rangeScore >= 90 && rangeScore <= 100) {
  console.info('A级');
} else if (rangeScore >= 80 && rangeScore < 90) {
  console.info('B级');
} else if (rangeScore >= 70 && rangeScore < 80) {
  console.info('C级');
} else if (rangeScore >= 60 && rangeScore < 70) {
  console.info('D级');
} else {
  console.info('F级');
}

// 使用switch映射
let grade: number = Math.floor(rangeScore / 10);

switch (grade) {
  case 10:
  case 9:
    console.info('A级');
    break;
  case 8:
    console.info('B级');
    break;
  case 7:
    console.info('C级');
    break;
  case 6:
    console.info('D级');
    break;
  default:
    console.info('F级');
}
```

## 循环语句

循环语句在条件满足时重复执行代码块，ArkTS提供`for`、`for...of`、`while`、`do...while`等多种循环形式。

### for循环（传统计数式）

传统`for`循环使用计数器控制循环，由初始化、条件判断和迭代三部分组成。

执行流程为：先执行初始化表达式（仅一次），再判断条件表达式（为`true`则继续、为`false`则退出），然后执行循环体，执行迭代表达式后回到条件判断循环。

<!-- @[traditional_for_loop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// 基本结构
// 初始化：let i = 0
// 条件：i < 5
// 增量：i++
for (let i = 0; i < 5; i++) {
  console.info(`${i}`);
}

// 倒序循环
for (let i = 5; i >= 0; i--) {
  console.info(`${i}`);
}

// 步长为2
for (let i = 0; i < 10; i += 2) {
  console.info(`${i}`);
}

// 遍历数组索引
let arr: number[] = [10, 20, 30, 40, 50];
for (let i = 0; i < arr.length; i++) {
  console.info(`索引 ${i}: ${arr[i] ?? 0}`);
}

// 多变量循环
for (let i = 0, j = 10; i < j; i++, j--) {
  console.info(`i=${i}, j=${j}`);
}
```

### for...of循环

`for...of`遍历可迭代对象的元素，语法简洁、通用性强、类型安全。

<!-- @[for_of_iteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// 遍历数组
let numbers: number[] = [1, 2, 3, 4, 5];
for (let num of numbers) {
  console.info(`${num}`);
}

// 遍历字符串
let text: string = 'Hello';
for (let char of text) {
  console.info(`${char}`);
}
```

`for...of`常用于集合类型的遍历，更多示例见[集合类型](./arkts-language-guide-collection-types.md)章节。

### while循环

`while`循环先判断条件，再执行循环体，是基于条件控制的循环语句。

``` TypeScript
while (condition) {
  // 循环体代码
  // 注意：需要在循环体内更新条件变量
}
```

`while`适合循环次数在编译时无法确定、基于特定条件（如队列非空）、等待条件满足（如轮询）或需动态调整循环条件的场景。

<!-- @[while_loop_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// 基本结构
let count: number = 0;
while (count < 5) {
  console.info(`${count.toString()}`);
  count++;
}

// 条件为false时跳过循环体
let loopValue: number = 10;
while (loopValue < 5) {
  console.info(`${loopValue.toString()}`);  // 不执行
  loopValue++;
}

// 处理数据直到条件满足
let data: string | null = 'data';
while (data !== null) {
  console.info(`${data}`);
  data = getNextData();
}

function getNextData(): string | null {
  // 返回数据或null
  return null;
}

// 累加直到满足条件
let sum: number = 0;
let i: number = 1;
while (sum < 100) {
  sum += i;
  i++;
}
console.info(`累加到 ${sum}`);
```

### do...while循环

`do...while`循环先执行循环体，再判断条件，适用于用户输入验证（至少询问一次）、资源获取（至少尝试一次）、状态检查等需要先执行再判断的场景。执行流程为：先执行循环体，再判断条件表达式，条件为`true`则继续执行，为`false`则退出循环。

<!-- @[do_while_loop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// 基本结构：至少执行一次
let loopCount: number = 0;
do {
  console.info(`${loopCount.toString()}`);
  loopCount++;
} while (loopCount < 5);

// 即使条件初始为false也执行一次
let loopValue2: number = 10;
do {
  console.info(`${loopValue2.toString()}`);  // 执行一次，输出10
  loopValue2++;
} while (loopValue2 < 5);

// 用户输入验证
let input: string = '';
do {
  input = getInput();
} while (input.length === 0);

function getInput(): string {
  return 'valid input';
}

// 重试逻辑
let success: boolean = false;
let attempts: number = 0;
do {
  success = tryConnect();
  attempts++;
} while (!success && attempts < 3);

function tryConnect(): boolean {
  return true;
}
```

## 跳转语句

跳转语句用于改变循环的执行流程。

### break语句

`break`用于跳出循环或`switch`，立即终止当前循环或分支的执行。

`break`常用于查找元素后终止、条件满足时退出、遇到错误时跳出以及提前结束无意义循环以优化性能。

<!-- @[break_statement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// 跳出for循环
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    break;  // 跳出循环
  }
  console.info(`${i.toString()}`);
}
// 输出：0, 1, 2, 3, 4

// 跳出while循环
let breakCount: number = 0;
while (breakCount < 10) {
  if (breakCount === 5) {
    break;
  }
  console.info(`${breakCount.toString()}`);
  breakCount++;
}

// 查找元素后跳出
let breakNumbers: number[] = [1, 2, 3, 4, 5];
for (let num of breakNumbers) {
  if (num === 3) {
    console.info('找到 3');
    break;
  }
}
```

嵌套循环中，带标签的`break`可以直接跳出外层循环：

<!-- @[nested_loop_break](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// 带标签的break：跳出外层循环
outerLoop: for (let i = 0; i < 10; i++) {
  for (let j = 0; j < 10; j++) {
    if (i + j === 15) {
      console.info(`找到: i=${i}, j=${j}`);
      break outerLoop;
    }
  }
}
```

### continue语句

`continue`用于跳过当前循环，继续下一次循环。`continue`常用于过滤无效数据、满足条件时跳过、避免执行不必要代码以优化性能，以及替代复杂`if-else`嵌套以简化逻辑。

<!-- @[continue_statement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// 跳过偶数
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) {
    continue;  // 跳过偶数
  }
  console.info(`${i.toString()}`);
}
// 输出：1, 3, 5, 7, 9

// 跳过特定值
let continueNumbers: number[] = [1, 2, 3, 4, 5];
for (let num of continueNumbers) {
  if (num === 3) {
    continue;  // 跳过3
  }
  console.info(`${num.toString()}`);
}
// 输出：1, 2, 4, 5

// 过滤无效数据
let continueData: (string | null)[] = ['valid', '', 'valid', null, 'valid'];
for (let item of continueData) {
  if (item === '' || item === null) {
    continue;  // 跳过空值
  }
  processItem(item);
}

function processItem(item: string): void {
  console.info(`处理: ${item}`);
}
```

类似地，`continue`也支持标签语法，用于跳过外层循环的当前迭代：

<!-- @[nested_loop_continue](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Control.ets) -->

``` TypeScript
// 带标签的continue：跳过外层循环当前迭代
outerLoop: for (let i = 0; i < 5; i++) {
  for (let j = 0; j < 5; j++) {
    if (j === 2) {
      continue outerLoop;
    }
    console.info(`i=${i}, j=${j}`);
  }
}
```

### 其他控制语句（return和throw）

ArkTS还支持其他控制语句，如[return](./arkts-language-guide-functions.md)和[throw](./arkts-language-guide-error-handling.md)，详见相关章节介绍。
