# Common Library FAQs
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->


## Out of Memory Occurs When a Large XML File Is Parsed

The XML parsing API provided by ArkTS does not support streaming parsing. You are advised to call a third-party C/C++ library through a native project. The **libxml2** library is recommended because it is mature, stable, and high-performance, and supports streaming parsing modes such as SAX, effectively reducing memory usage.

The procedure is as follows:
1. **Create a native project**: Create a C++ module in the OpenHarmony project.
2. **Integrate libxml2**: Download and configure the libxml2 library source code or precompiled library, and reference it in `CMakeLists.txt`.
3. **Compile the parsing code**: Use the APIs provided by libxml2 to implement the streaming parsing logic.
4. **XML object processing**: If the size of an XML file exceeds 100 MB, you are advised to process the file on the Native side.

For details about how to reference the compiled third-party SO library on the ArkTS side, see [How do I import a third-party library in ArkTS?](https://developer.huawei.com/consumer/en/doc/harmonyos-faqs/faqs-ndk-21).

The following table lists the callback functions supported by the libxml2 library.
| Callback Function Pointer| Triggered When| Description|
| :--- | :--- | :--- |
| `startDocument` | At document start| Initialize the environment and allocate resources.|
| `endDocument` | At document end| Release resources and print statistics.|
| `startElement` | When a start tag is encountered (for example, `<tag>`)| Obtain the tag name and its attributes.|
| `endElement` | When an end tag is encountered (for example, `</tag>`)| Process the end logic of the tag, for example, pop from the stack.|
| `characters` | When the text content between tags is read| Process the text data. (possible multiple calls)|

Code example:

```c
// User-defined data
ParseContext context;

// Initialize the SAX Handler structure.
xmlSAXHandler SAXHandler = { 0 };

// Bind the callback function to process XML data during parsing.
SAXHandler.startDocument = startDocument;
SAXHandler.endDocument = endDocument;
SAXHandler.startElement = startElement;
SAXHandler.endElement = endElement;
SAXHandler.characters = characters;

// Parse the file.
// User-defined data pointer
int ret = xmlSAXUserParseFile(&SAXHandler, &context, xmlFileName);

if (ret != 0) {
    printf("Failed to parse XML file.\n");
    return 1;
}

// Clear the libxml2 global status.
xmlCleanupParser();
```

## Timer Deleted by Mistake

Timer IDs are shared by processes and start from 0. Misoperations may cause timers to be deleted.

For example:

```ts
export class testClass {
    // Set the initial value to 0.
    private timeoutId: number = 0;
    private interbalId: number = 0;

    // In some cases, the clearAnimation function is called to delete the timer without calling the setTimeout function to set the timer. As a result, the timer whose timeoutId is 0 is deleted.
    clearAnimation(): void {
        clearInterval(this.interbalId);
        clearTimeout(this.timeoutId);
    }
}
```

You can use the following method to quickly locate the fault:

Rewrite the globalThis.clearTimeout function to print the call stack when the clearTimeout function is called to quickly locate where the timer is deleted.

The test() function in the clearTimeout.ts file is called before the timerTestCase() function in the TimerTest.ets file.

Sample code:

```ts
// Customize the clearTimeout.ts file.

// The test function needs to be called before the clearTimeout function is called.
export function test() {
    // Fully compatible with the original clearTimeout type.
    const origClear = globalThis.clearTimeout;
    globalThis.clearTimeout = (...args: any[]) => {
        const timeoutId = args[0];

        // Check all possible cases where timerId = 0.
        if (timeoutId === 0 || timeoutId === "0") {
            console.info ("Clear timerId = 0 !", new Error().stack);
            // Trigger the breakpoint.
            debugger;
        }

        // Use apply to ensure that all parameters are correctly passed.
        return origClear.apply(this, args);
    }
}
```

```ts
// Customize the TimerTest.ets file.

let timeoutId: number = 0;

export function timerTestCase() {
    test1();
    clearTime();
}

function test1() {
    timeoutId = setTimeout(() => {
        console.info("begin");
    }, 1);
    console.info("timeoutId = " + timeoutId);
}

function clearTime() {
    clearTimeout(timeoutId);
    console.info("clearTimeout Id = " + timeoutId);
}
```
