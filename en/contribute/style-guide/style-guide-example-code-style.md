# Sample Code Style

<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @ge-yafang-->
<!--Designer: @lingminghw-->
<!--Tester: @RayShih-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=880254a662ee51954fb21f2681e88bb383ac8c29 translatedAt=2026-11-17T02:46:33.905Z nl=1 -->

This specification applies to sample code snippets in documentation written in ArkTS, JavaScript, C/C++, and other programming languages. It aims to improve readability, maintainability, and style consistency in OpenHarmony sample code.

## Coding Conventions

### [Rule] Follow Basic Coding Conventions

[Description]

Sample code must follow the basic conventions in the [OpenHarmony Application ArkTS Coding Style Guide](../../application-dev/quick-start/arkts-coding-style-guide.md), [JavaScript Coding Style Guide](../OpenHarmony-JavaScript-coding-style-guide.md), [C Coding Style Guide](../OpenHarmony-c-coding-style-guide.md), and [C++ Coding Style Guide](../OpenHarmony-cpp-coding-style-guide.md), including naming, formatting, and coding conventions.

### [Rule] Provide Sample Code for Each API

[Description]

In API references, provide sample code for every API, including methods and components. If multiple APIs are related, demonstrate them together in a scenario-based example.

### [Rule] Include Exception Handling in Development Guide Samples

[Description]

Development guides provide comprehensive code examples that help readers use APIs correctly in real applications. Include exception handling to ensure that the sample code is robust and reliable. This helps readers understand how to handle errors in different situations and improve code quality.

Exception handling in development guide samples helps readers understand how to write robust code and apply these practices in actual development.

[Correct]

```ts
import { BusinessError } from '@kit.BasicServicesKit';

declare function doSthAsync1(): Promise<void>;

declare function doSthAsync2(): Promise<void>;

declare function doSthAsync3(): Promise<void>;

declare function doSthSync1(): void;

declare function doSthSync2(): void;

// Correct example 1: For an asynchronous Promise API, add a .catch() branch.
doSthAsync1()
  .then(() => {
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to do something. Code is ${err.code}, message is ${err.message}`);
  });

// Correct example 2: For asynchronous APIs used with async/await, add try...catch.
async () => {
  try {
    await doSthAsync1();
    await doSthAsync2();
    await doSthAsync3();
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    // Handle invalid argument exceptions.
    console.error(`Failed to do something. Code is ${err.code}, message is ${err.message}`);
  }
}

// Correct example 3: For synchronous APIs, add try...catch.
try {
  doSthSync1();
  doSthSync2();
} catch (error) {
  const err: BusinessError = error as BusinessError;
  // Handle invalid argument exceptions.
  console.error(`Failed to do something. Code is ${err.code}, message is ${err.message}`);
}

// Correct example 4: Add try...catch for synchronous APIs and check error codes as needed.
try {
  doSthSync1();
  doSthSync2();
} catch (err) {
  switch (err.code) {
    case 401:
      // Handle parameters exceptions
      break;
    case 12300001:
      // Handle 12300001 exceptions
      break;
    case 12300002:
    case 12300003:
    case 12300004:
      console.error(`Failed to do something. Code is ${err.code}, message is ${err.message}`);
      break;
  }
}
```

[Incorrect]

```ts
declare function doSthAsync1(): Promise<void>;

declare function doSthAsync2(): Promise<void>;

declare function doSthAsync3(): Promise<void>;

declare function doSthSync1(): void;

declare function doSthSync2(): void;

// Incorrect example 1: The asynchronous API has no .catch() exception handler.
doSthAsync1()
  .then(() => {
  })

// Incorrect example 2: Asynchronous APIs used with async/await have no try...catch handler.
async () => {
  await doSthAsync1();
  await doSthAsync2();
  await doSthAsync3();
}

// Incorrect example 3: The synchronous APIs have no try...catch handler.
doSthSync1();
doSthSync2();
```

### [Rule] Clarify Variable Definitions and Usage

[Description]

For variables in sample code, provide definitions, usage instructions, links to their sources, or explanations so readers understand how to use them. For example, if a sample uses an application file path, provide a link or instructions for obtaining that path.

[Correct]

For details about obtaining `context` in this example, see [Obtaining the Context of UIAbility](../../application-dev/application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
import { common, Want } from '@kit.AbilityKit';

const context: common.UIAbilityContext = this.context; // UIAbilityContext
let want: Want = {
  deviceId: '', // An empty deviceId indicates the local device.
  bundleName: 'com.example.myapplication',
  abilityName: 'FuncAbility',
  moduleName: 'func', // moduleName is optional.
  parameters: {
    // Custom information.
    info: 'From the EntryAbility Index page',
  },
}
// context is the UIAbilityContext of the calling UIAbility.
context.startAbilityForResult(want)
  .then((data) => {
    // ...
  })
```

[Incorrect]

```ts
// Incorrect example: The context and want variables are not defined.
// context is the UIAbilityContext of the calling UIAbility.
context.startAbilityForResult(want)
  .then((data) => {
    // ...
  })
```

### [Recommendation] Use Consistent Names for Imported Packages

[Description]

Keep imported package names consistent with their namespaces to make the code easier to maintain and understand.

Consistent naming also helps the IDE suggest imports, improving coding efficiency.

[Correct]

```ts
import { promptAction } from '@kit.ArkUI';
```

[Incorrect]

```ts
// The package name differs from its namespace, making the code harder to maintain and understand.
import { promptAction as prompt } from '@kit.ArkUI';
```

### [Rule] Use Kit-Based Imports Consistently

[Description]

To use an exposed capability, you can import its API module directly or import it through the corresponding kit.

For modules that support both methods, kit-based imports are recommended.

[Correct]

```ts
// Import the kit to use its capabilities.
import { UIAbility } from '@kit.AbilityKit';
```

[Incorrect]

```ts
// Import the API module directly to use its capabilities.
import UIAbility from '@ohos.app.ability.UIAbility';
```

### [Rule] Omit Units from UI Component Width and Height Properties

[Description]

For consistency and simplicity, avoid adding explicit units (such as `vp`/`fp`/`px`) when using the default units for component width, height, and similar properties. Width and height use `vp` (virtual pixels) by default. Omitting units also makes the code easier to read and maintain.

[Correct]

```ts
Text('Hello World')
  .width(100)
  .height(100)

Text('Hello World')
  .fontSize(50)
```

[Incorrect]

```ts
Text('Hello World')
  .width('100vp')
  .height('100vp')

Text('Hello World')
  .width('300px')
  .height('400px')

Text('Hello World')
  .fontSize('50fp')
```

## Code Presentation

### [Rule] Use Backticks for Inline Code

[Description]

Enclose code elements in body text, such as method names, parameter names, and code file names, in backticks (`).

[Correct]

Implement page navigation in the `Index.ets` file.

[Incorrect]

Implement page navigation in the Index.ets file.

### [Rule] Use Code Blocks for Syntax Highlighting

[Description]

Use code formatting for sample code and command lines. In Markdown, use \`\`\` and specify the language.

Syntax highlighting uses different colors to distinguish syntax elements in an editor. For example, different colors for keywords, variable names, and comments make code easier to read and understand.

### [Rule] Format Code

[Description]

Before adding sample code to a guide, format it with the code formatting feature in DevEco Studio to ensure consistency and readability.

Formatting includes indentation, spacing, and line breaks. These improve readability, maintainability, and extensibility.

[Correct]

```ts
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', (err: BusinessError, data) => {
    });
  }
}
```

[Incorrect]

```ts
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
  // The code is not formatted and lacks indentation.
  windowStage.loadContent('pages/Index', (err: BusinessError, data) => {
  });
  }
}
```

### [Rule] Use a Consistent Placeholder for Omitted Code

[Description]

When omitting content in documentation or code, use a consistent placeholder. Keep it clear and concise rather than lengthy or confusing.

[Correct]

```ts
// Correct example 1
// ...

// Correct example 2
// To do something.
```

[Incorrect]

```ts
// Incorrect example 1
...

// Incorrect example 2
....

// Incorrect example 3
......
```

### [Rule] Add Clear Code Comments

[Description]

Add comments to explain key content and logic in sample code so readers understand what the code does.

Add comments where needed, especially for explanations, development recommendations, or precautions. Appropriate comments improve readability and help readers understand the development process quickly.

Use comment delimiters that match the code language; do not invent delimiters. Add one space between the delimiter and the comment text. For example, write ArkTS comments as "// Comment text".

If a comment is too long for one line, split it at a suitable sentence or clause boundary and continue on the next line.

Comments should be clear, concise, and useful, helping others understand the code. Place comments above or to the right of the code.

[Correct]

```ts
// Correct example 1
// Define the lifecycle callback object.
let abilityLifecycleCallback = {};

// Correct example 2
let abilityLifecycleCallback = {}; // Define the lifecycle callback object.
```

[Incorrect]

```ts
// Incorrect example 1: No space between the comment delimiter and comment text.
//Define the lifecycle callback object.
let abilityLifecycleCallback = {};

// Incorrect example 2: No space between the comment delimiter and comment text.
let abilityLifecycleCallback = {}; //Define the lifecycle callback object.

// Incorrect example 3: Multiple spaces between the code and the comment delimiter.
let abilityLifecycleCallback = {};       // Define the lifecycle callback object.
```

### [Rule] Include Code from Only One File in Each Code Block

[Description]

When presenting sample code, include code from only one file in each code block. This improves readability, makes the code easier to understand, and reflects the actual development environment. Mixing code from multiple files can obscure file boundaries and context. Keeping files separate makes examples clear, organized, and easy to copy and use.

[Correct]

Place code from different files in separate code blocks. This clearly presents each file and helps readers understand the file structure and relationships between components. For example:

1. Develop the `MyComponent` custom component.

   ```ts
   // MyComponent.ets
   @Component
   export struct MyComponent {
     @State message: string = 'Hello, World!';
   
     build() {
       Row() {
         Text(this.message)
           .fontSize(50)
           .fontWeight(FontWeight.Bold)
       }
       .height('100%')
     }
   }
   ```

2. Reference the custom component in `Index.ets`.

   ```ts
   // pages/Index.ets
   import { MyComponent } from '../common/components/MyComponent';
   
   @Entry
   @Component
   struct Index {
     build() {
       Column() {
         MyComponent()
       }
       .width('100%')
       .height('100%')
     }
   }
   ```

[Incorrect]

Mixing code from multiple files in one block can make file boundaries unclear, increase the effort required to understand the code, and make copying and using it more difficult. For example:

Develop the `MyComponent` custom component. Reference it in `Index.ets`.

```ts
// MyComponent.ets
@Component
export struct MyComponent {
  @State message: string = 'Hello, World!';

  build() {
    Row() {
      Text(this.message)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
    .height('100%')
  }
}


// pages/Index.ets
import { MyComponent } from '../common/components/MyComponent';
@Entry
@Component
struct Index {
  build() {
    Column() {
      MyComponent()
    }
    .width('100%')
    .height('100%')
  }
}
```

## Exception Handling

### [Rule] Catch Exceptions Where They May Occur

[Description]

Add exception handling to code that may throw exceptions and branch by exception type. Use a consistent branching pattern for each exception type.

[Correct]

```ts
// Correct example 1: Case 1, where err can be undefined.
if (err) {
  // ...
}

// Correct example 2: Case 2, where a nonzero err.code indicates an error.
if (err.code) {
  // ...
}
```

[Incorrect]

```ts
// Incorrect example 1
if (err == null) {
  // ...
}

// Incorrect example 2
if (err != null) {
  // ...
}

// Incorrect example 3
if (err == undefined) {
  // ...
}

// Incorrect example 4
if (err === undefined) {
  // ...
}

// Incorrect example 5
if (err !== undefined) {
  // ...
}
```

### [Rule] Use console.error to Log Detailed Exception Information

[Description]

If an exception occurs, use `console.error(...)` to log it to the console so that issues can be found quickly during debugging.

Log detailed exception information in exception handlers to aid debugging.

Use template literals for exception messages and include the `code` and `message` parameters.

[Correct]

```ts
// Template
console.error(`Failed to do something. Code: ${err.code}, message: ${err.message}`);

// Correct example 1
notificationManager.publish(notificationRequest, (err: BusinessError) => {
  if (err) {
    // Log the exception.
    console.error(`Failed to publish notification. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  // ...
});

// Correct example 2
notificationManager.publish(notificationRequest)
  .then(() => {
    // ...
  })
  .catch((err: BusinessError) => {
    // Log the exception.
    console.error(`Failed to publish notification. Code: ${err.code}, message: ${err.message}`);
  })

// Correct example 3
let pathDir: string = '<pathDir>'; // Application file path.
let filePath: string = pathDir + '/test.txt';
try {
  let str: string = fs.readTextSync(filePath, { offset: 1, length: 3 });
  console.info(`Succeeded in reading text, str is ${str}`);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to read text. Code is ${err.code}, message is ${err.message}`);
}
```

[Incorrect]

```ts
// Incorrect example 1: console.log is used for errors, making issues harder to find during debugging.
notificationManager.publish(notificationRequest, (err: BusinessError) => {
  if (err) {
    // Log the exception.
    console.log(`Failed to publish notification. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  // ...
});

// Incorrect example 2: console.info is used instead of console.error, making log levels and issues harder to identify.
notificationManager.publish(notificationRequest, (err: BusinessError) => {
  if (err) {
    // Log the exception.
    console.info(`Failed to publish notification. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  // ...
});

// Incorrect example 3: The exception message lacks specific code and message parameters, making troubleshooting harder.
console.error(`Failed to publish notification, err: ${err}`);

// Incorrect example 4: Single quotes prevent interpolation; use a template literal instead.
console.error('Failed to publish notification, err: ${err}');

// Incorrect example 5: Concatenation and JSON serialization make the message less clear and concise, increase log volume, and hinder troubleshooting.
console.error('Failed to publish notification, err: ' + JSON.stringify(err));
```

## Logging

### [Rule] Use console.info for Normal Console Logs

[Description]

Use logging to record program execution so that exceptions can be located and investigated.

Under normal conditions, use `console.info(...)` for normal log messages.

[Correct]

```ts
// Template
console.info('Succeeded in doing something.');

// Correct example
declare function doSthAsync1(): Promise<void>;

doSthAsync1()
  .then(() => {
    console.info('Succeeded in publishing notification.');
  })
```

[Incorrect]

```ts
declare function doSthAsync1(): Promise<void>;

// Incorrect example 1: console.log(...) may leave readers unsure whether this is a normal log or an error log.
doSthAsync1()
  .then(() => {
    console.log('Succeeded in publishing notification.');
  })

// Incorrect example 2: console.error(...) is used instead of console.info(...) for a normal log. console.error is intended for errors.
doSthAsync1()
  .then(() => {
    console.error('Succeeded in publishing notification.');
  })
```

### [Rule] Follow English Grammar in Log Messages

[Description]

Follow English grammar when writing log messages. Log messages must not contain grammatical errors.

For example, use `Succeeded in doing something` or `do something successfully` for success messages.

For example, use `Failed to do something` for error messages.

[Correct]

```ts
// Template
console.info('Succeeded in doing something.');

// Correct example
declare function doSthAsync1(): Promise<void>;

doSthAsync1()
  .then(() => {
    console.info('Succeeded in doing something.');
  })
```

[Incorrect]

```ts
declare function doSthAsync1(): Promise<void>;

// Incorrect example 1
doSthAsync1()
  .then(() => {
    console.info('Invoke do something success.');
  })

// Incorrect example 2
doSthAsync1()
  .then(() => {
    console.info('Invoke do something successful.');
  })

// Incorrect example 3
doSthAsync1()
  .then(() => {
    console.info('Invoke do something successfully.');
  })
```

## Code Logic

### [Rule] Use Arrow Functions for Callbacks

[Description]

When implementing callbacks, prefer arrow functions to regular functions. A key benefit is avoiding issues with `this`: an arrow function captures `this` from its enclosing context rather than from the call site. This avoids the need to bind `this` with `bind()` or `call()` as may be required with regular functions, simplifying code and improving readability.

[Correct]

```ts
notificationManager.publish(notificationRequest, (err: BusinessError) => {
  if (err) {
    // ...
    return;
  }
  console.info('Succeeded in publishing notification.');
});
```

[Incorrect]

```ts
notificationManager.publish(notificationRequest, function (err: BusinessError) {
  if (err) {
    // ...
    return;
  }
  console.info('Succeeded in publishing notification.');
});
```

### [Rule] Do Not Use Deprecated APIs

[Description]

Do not use deprecated APIs, because they may be removed or changed in future versions. Use up-to-date APIs to keep code stable and maintainable.

Deprecated APIs may cause instability, build errors, or runtime errors as APIs are phased out in later versions.

When APIs are removed in a later version, update all sample code that depends on them.

[Correct]

```ts
import { common } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';

/**
 * Obtain the application file path.
 **/
const context: common.UIAbilityContext = this.context; // UIAbilityContext
let filesDir: string = context.filesDir;

// Create and open a file.
let file: fileIo.File = fileIo.openSync(filesDir + '/test.txt', fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
// Write content to the file.
let writeLen: number = fileIo.writeSync(file.fd, 'Try to write str.');
// Read content from the file.
let buf: ArrayBuffer = new ArrayBuffer(1024);
let readLen: number = fileIo.readSync(file.fd, buf, {
  offset: 0
});
// Close the file.
fileIo.closeSync(file);
```

[Incorrect]

```ts
// The deprecated fileio API is used instead of the recommended fileIo API.
import fileio from '@ohos.fileio';
import common from '@ohos.app.ability.common';

// Obtain the application file path.
const context: common.UIAbilityContext = this.context; // UIAbilityContext
let filesDir: string = context.filesDir;

// Create and open a file.
let fileFD: number = fileio.openSync(filesDir + '/test.txt', 0o102, 0o640);
// Write content to the file.
let writeLen: number = fileio.writeSync(fileFD, 'Try to write str.');
// Read content from the file.
let buf: ArrayBuffer = new ArrayBuffer(1024);
let readLen: number = fileio.readSync(fileFD, buf, { offset: 0 });
// Close the file.
fileio.closeSync(fileFD);
```