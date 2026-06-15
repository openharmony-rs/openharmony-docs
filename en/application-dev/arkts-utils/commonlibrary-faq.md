# Common Library FAQs

<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @Malzahar-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=7322f9d523f66911f71514248bc2b0cdc9af44ee translatedAt=2026-05-28T07:54:59.813Z pushedAt=2026-05-29T06:32:27.765Z -->

## Out of Memory When Parsing Large XML Files

Since the XML parsing APIs provided by ArkTS do not yet support streaming parsing mode, it is recommended to implement this by calling third-party C/C++ libraries through a Native project. The **libxml2** library is recommended. It is mature, stable, and offers superior performance, supporting streaming parsing methods such as SAX to effectively reduce memory usage.

The specific implementation steps are as follows:

1. **Create a Native project**: Create a C++ module in your OpenHarmony project.

2. **Integrate libxml2**: Download and configure the libxml2 library source code or precompiled library, and reference it in `CMakeLists.txt`.

3. **Write parsing code**: Use the APIs provided by libxml2 to implement streaming parsing logic.

4. **XML object processing**: When the XML file size exceeds 100 MB, it is recommended to handle it on the native side.

For details on how to reference a compiled third-party .so library on the ArkTS side, see [How do I import a third-party library in ArkTS?](https://developer.huawei.com/consumer/en/doc/harmonyos-faqs/faqs-ndk-21).

The main callback functions supported by the libxml2 library are as follows:

| Callback Function Pointer | Trigger Timing | Purpose |
| :--- | :--- | :--- |
| `startDocument` | At the start of the document | Initializes the environment and allocates resources. |
| `endDocument` | At the end of the document | Releases resources and prints statistical information. |
| `startElement` | When a start tag (e.g., `<tag>`) is read | Obtains the tag name and its attributes. |
| `endElement` | When an end tag (e.g., `</tag>`) is read | Handles the tag end logic, such as popping from the stack. |
| `characters` | When text content between tags is read | Processes text data (note that it may be called multiple times). |

Code example:

```c
// User-defined data
ParseContext context;

// Initialize the SAX Handler structure
xmlSAXHandler SAXHandler = { 0 };

// Bind callback functions for processing XML data during parsing
SAXHandler.startDocument = startDocument;
SAXHandler.endDocument = endDocument;
SAXHandler.startElement = startElement;
SAXHandler.endElement = endElement;
SAXHandler.characters = characters;

// Parse a file
// User-defined data pointer
int ret = xmlSAXUserParseFile(&SAXHandler, &context, xmlFileName);

if (ret != 0) {
    printf("Failed to parse XML file.\n");
    return 1;
}

// Clean up libxml2 global state
xmlCleanupParser();
```

## Timer Deleted by Mistake

Because timer IDs are shared within a process and start from 0, developer misoperations can easily cause a timer to be deleted.

For example, the following scenario:

```ts
export class testClass {
    // The initial value is set to 0.
    private timeoutId: number = 0;
    private intervalId: number = 0;

    // In some cases, the clearAnimation function is called to delete the timer without first calling setTimeout to set a timer, which causes the timer with timeoutId 0 to be deleted.
    clearAnimation(): void {
        clearInterval(this.intervalId);
        clearTimeout(this.timeoutId);
    }
}
```

You can quickly locate the issue using the following method:

Override the globalThis.clearTimeout function to print the call stack when the clearTimeout function is called, so you can quickly locate where the timer was deleted.

The calling sequence is to first call the test() function in the clearTimeout.ts file, and then call the clearAnimation() function of the testClass class in the TimerTest.ets file.

Sample code:

```ts
// Custom TS file clearTimeout.ts

// The test function needs to be called before the program calls the clearTimeout function.
export function test() {
    // Fully compatible with the original clearTimeout type
    const origClear = globalThis.clearTimeout;
    globalThis.clearTimeout = (...args: any[]) => {
        const timeoutId = args[0];

        // Check all possible cases where timerId = 0
        if (timeoutId === 0 || timeoutId === "0") {
            console.info("Clear timerId = 0!", new Error().stack);
            // Trigger breakpoint
            debugger;
        }

        // Use apply to ensure all parameters are passed correctly
        return origClear.apply(this, args);
    }
}
```

```ts
// Custom ets file TimerTest.ets

export class testClass {
    // Set the initial value to 0.
    private timeoutId: number = 0;
    private intervalId: number = 0;

    // In some cases, if the clearAnimation function is called to delete a timer without having called setTimeout to set the timer first, the timer with a timeoutId of 0 will be deleted.
    clearAnimation(): void {
        clearInterval(this.intervalId);
        clearTimeout(this.timeoutId);
    }
}
```

```ts
import { test } from './clearTimeout';
import { testClass } from './TimerTest';

@Entry
@Component
struct Index {
    @State message: string = 'Hello World';

    build() {
      Row() {
        Column() {
          Text(this.message)
            .fontSize(50)
            .fontWeight(FontWeight.Bold)
            .onClick(() => {
                test();
                let testCase = new testClass();
                testCase.clearAnimation();
                this.message = 'success';
            })
        }
        .width('100%')
      }
      .height('100%')
    }
}
```