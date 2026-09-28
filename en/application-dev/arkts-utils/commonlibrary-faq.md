# Basic Library FAQ

<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @Malzahar-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-31T12:36:29.706Z pushedAt=2026-08-31T14:46:10.673Z -->

## Out of Memory When Parsing Large XML Files

Because the XML parsing APIs provided on the ArkTS side do not yet support streaming parsing, it is recommended that you call a third-party C/C++ library through a Native project. The **libxml2** library is recommended. It is mature, stable, and high-performance, and it supports streaming parsing methods such as SAX, effectively reducing memory usage.

The specific implementation steps are as follows:

1. **Create a Native project**: Create a C++ module in the OpenHarmony project.

2. **Integrate libxml2**: Download and configure the libxml2 source code or a precompiled library, and reference it in `CMakeLists.txt`.

3. **Write parsing code**: Use the APIs provided by libxml2 to implement the streaming parsing logic.

4. **XML object processing**: When the XML file size exceeds 100 MB, it is recommended to process it on the Native side.

For details about how to reference a compiled third-party .so library on the ArkTS side, see [How to Reference a Third-Party .so Library on the ArkTS Side](https://developer.huawei.com/consumer/en/doc/harmonyos-faqs/faqs-ndk-21).

The main callback functions supported by the libxml2 library are as follows:

| Callback Function Pointer | Trigger Timing | Purpose |
| :--- | :--- | :--- |
| `startDocument` | When the document starts | Initialize the environment and allocate resources. |
| `endDocument` | When the document ends | Release resources and print statistics. |
| `startElement` | When a start tag (such as `<tag>`) is read | Obtain the tag name and its attributes. |
| `endElement` | When an end tag (such as `</tag>`) is read | Process the tag end logic, such as popping the stack. |
| `characters` | When the text content between tags is read | Process text data (note that it may be called multiple times). |

Code example:

```c
// User-defined data
ParseContext context;

// Initialize the SAX Handler structure.
xmlSAXHandler SAXHandler = { 0 };

// Bind callback functions to process XML data during parsing.
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

// Clean up the libxml2 global state.
xmlCleanupParser();
```

## Timer Deleted by Mistake

Because timer IDs are shared across processes and start from 0, misoperation by developers can easily cause a timer to be deleted.

For example, consider the following scenario:

```ts
export class testClass {
    // Set the initial value to 0.
    private timeoutId: number = 0;
    private intervalId: number = 0;

    // In some cases, the clearAnimation function is called to delete a timer without first calling setTimeout to set the timer, which causes the timer with timeoutId 0 to be deleted.
    clearAnimation(): void {
        clearInterval(this.intervalId);
        clearTimeout(this.timeoutId);
    }
}
```

You can quickly locate the issue using the following method:

Override the globalThis.clearTimeout function to print the call stack when clearTimeout is called, so as to quickly locate where the timer is deleted.

The call sequence is to first call the test() function in the clearTimeout.ts file, and then call the clearAnimation() function of the testClass class in the TimerTest.ets file.

Sample code:

```ts
// Custom TS file clearTimeout.ts

// The test function must be called before the program calls the clearTimeout function.
export function test() {
    // Fully compatible with the original clearTimeout type.
    const origClear = globalThis.clearTimeout;
    globalThis.clearTimeout = (...args: any[]) => {
        const timeoutId = args[0];

        // Check all possible cases where timerId = 0.
        if (timeoutId === 0 || timeoutId === "0") {
            console.info("Clear timerId = 0!", new Error().stack);
            // Trigger a breakpoint.
            debugger;
        }

        // Use apply to ensure all parameters are passed correctly.
        return origClear.apply(this, args);
    }
}
```

```ts
// Custom ets file TimerTest.ets.

export class testClass {
    // Set the initial value to 0.
    private timeoutId: number = 0;
    private intervalId: number = 0;

    // In some cases, the clearAnimation function is called to delete the timer without calling setTimeout to set the timer first, which causes the timer with timeoutId = 0 to be deleted.
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

## Base64 Encoding Rules

Base64 encoding uses a specific set of 64 characters to represent binary data. These 64 characters include uppercase letters A-Z, lowercase letters a-z, digits 0-9, and the symbols "+" and "/". In some cases, "=" is also used as a padding character. Base64 encoding groups the raw data into 3-byte blocks, and each 3-byte block is converted into 4 Base64 characters.

The Base64 encoding table is as follows:

| Index | Character | Index | Character | Index | Character | Index | Character |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | A | 16 | Q | 32 | g | 48 | w |
| 1 | B | 17 | R | 33 | h | 49 | x |
| 2 | C | 18 | S | 34 | i | 50 | y |
| 3 | D | 19 | T | 35 | j | 51 | z |
| 4 | E | 20 | U | 36 | k | 52 | 0 |
| 5 | F | 21 | V | 37 | l | 53 | 1 |
| 6 | G | 22 | W | 38 | m | 54 | 2 |
| 7 | H | 23 | X | 39 | n | 55 | 3 |
| 8 | I | 24 | Y | 40 | o | 56 | 4 |
| 9 | J | 25 | Z | 41 | p | 57 | 5 |
| 10 | K | 26 | a | 42 | q | 58 | 6 |
| 11 | L | 27 | b | 43 | r | 59 | 7 |
| 12 | M | 28 | c | 44 | s | 60 | 8 |
| 13 | N | 29 | d | 45 | t | 61 | 9 |
| 14 | O | 30 | e | 46 | u | 62 | + |
| 15 | P | 31 | f | 47 | v | 63 | / |

It can be seen that Base64 is an encoding and decoding method that represents binary data based on 64 printable characters. It converts binary data into a string (ASCII code) to facilitate data transmission and encryption/decryption protection.

Its encoding implementation principle is as follows:

Convert the string to be encoded into a binary sequence, then divide it into groups of 6 binary bits each. If the last group has fewer than 6 bits, pad the low-order bits with 0. Each 6-bit group forms a new byte with the high-order bits padded with 00, constituting a new binary sequence. Finally, find the corresponding character according to the value in the Base64 index table.

For example, for the string "ABC", after Base64 encoding, the final result is QUJD:

| Raw character | A |  B  |  C  | - |
| :--- | :--- | :--- | :--- | :--- |
| ASCII encoding | 65 | 66 | 67 |   -   |
| Binary bit | 01000001 | 01000010 | 01000011 | -  |
| Encoding conversion | 010000 | 010100 | 001001 | 000011 |
| Base64 index value | 16 | 20 | 9 | 3 |
| Base64 character | Q | U | J | D |

If the length of the raw string is not a multiple of 3, the encoded result is padded with "=" at the end so that the final length of the Base64 string is a multiple of 4, satisfying the Base64 length requirement after conversion.

For example, the string "AB" is converted to "QUI". To make up 4 bytes, "=" needs to be appended at the end:

| Raw character | A |  B  | -  | - |
| :--- | :--- | :--- | :--- | :--- |
| ASCII encoding | 65 | 66 | - |   -   |
| Binary bit | 01000001 | 01000010 | - | -  |
| Encoding conversion (pad with 0 if fewer than 6 bits) | 010000 | 010100 | 001000 | - |
| Base64 index value | 16 | 20 | 8 | - |
| Base64 character | Q | U | I | = |