# Content Elements

<!-- md-trans-meta sourceCommit=da575bb3bb7e4ff8c44a4790b5825bcbd0bbae89 translatedAt=2026-11-17T02:46:33.905Z nl=1 -->

## Lists

[Rule] For unordered lists, use a hyphen (-) followed by one space. For ordered lists, use a number followed by a period and one space.

| **Correct**                                                     | **Incorrect**                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| \-&nbsp;Unordered list item 1<br/>\-&nbsp;Unordered list item 2<br/>\-&nbsp;Unordered list item 3<br/>1.&nbsp;Ordered list item 1<br/>2.&nbsp;Ordered list item 2<br/>3.&nbsp;Ordered list item 3 | \-&nbsp;Unordered list item 1<br/>\*&nbsp;Unordered list item 2<br/>\+&nbsp;Unordered list item 3<br/>1)&nbsp;Ordered list item 1<br/>2)&nbsp;Ordered list item 2<br/>3)&nbsp;Ordered list item 3 |

| **Correct**                                                     | **Incorrect**                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| \-&nbsp;Unordered item 1<br/>&nbsp;&nbsp;&nbsp;\-&nbsp;Unordered item 1.1<br/>&nbsp;&nbsp;&nbsp;\-&nbsp;Unordered item 1.2<br/>&nbsp;&nbsp;&nbsp;\-&nbsp;Unordered item 1.3<br/>1.&nbsp;Ordered item 1<br/>&nbsp;&nbsp;&nbsp;1.&nbsp;Ordered item 1.1<br/>&nbsp;&nbsp;&nbsp;2.&nbsp;Ordered item 1.2<br/>&nbsp;&nbsp;&nbsp;2.&nbsp;Ordered item 1.3<br/>2.&nbsp;Ordered item 2<br/>3.&nbsp;Ordered item 3 | None |

[Rule] Use parallel structures and consistent sentence patterns for list items. For example, use either phrases or sentences throughout a list.

| **Correct**                                                     | **Incorrect**                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Playback event callback type. Supported events include&nbsp;`'play'\|'stop'\|'dataLoad'`&nbsp;:<br/>-&nbsp;`play`: Triggered when the play() call completes and audio playback starts.<br/>-&nbsp;`stop`: Triggered when the stop() call completes and audio playback stops.<br/>-&nbsp;`dataLoad`: Triggered when audio data loading completes, that is, after the src property is set. | Playback event callback type. Supported events include&nbsp;`'play'\|'stop'\|'dataLoad'`&nbsp;:<br/>-&nbsp;`play`: Triggered when audio starts playing.<br/>-&nbsp;`stop`: Audio stop event.<br/>-&nbsp;`dataLoad`: Triggered after audio data is loaded, that is, after the src property is set. |

[Rule] Omit end punctuation when list items are terms or phrases. End every item with a period when the items are sentences.

| Correct | Incorrect |
| -------- | -------- |
| Supported formats include:<br/>-&nbsp;video/h263<br/>-&nbsp;audio/mp4a-latm | None |

[Recommendation] Use 2 to 9 items in a list.

[Recommendation] If a list has only one item, combine it with the surrounding body text.

[Recommendation] Use no more than two list levels, including combinations of ordered and unordered lists.


## Tables

[Rule] A table must contain at least two rows and two columns.

[Rule] Tables must have no more than nine rows and four columns; two or three columns are recommended. Split tables with more than four columns or combine column content to reduce the number of columns. Alternatively, rewrite the content as a list. Keep the content in each cell within five lines.

[Rule] If a Markdown table does not preview well, improve readability by reducing the number of columns, shortening individual English strings in cells, or rewriting the table as a list.

[Rule] Use consistent noun-phrase column headers for equivalent tables. For example, use Description consistently in parameter tables instead of alternating labels.

[Rule] Use consistent wording and end punctuation within each column.

- If a column contains only phrases, omit periods.

- If a column contains sentences, or a mixture of sentences and phrases, end all entries with periods.

[Rule] Do not leave cells empty. Distinguish between "None" and "Not applicable". If repeated "Not applicable" entries obscure important information, use a dash (-) instead.

[Rule] Markdown does not support merged cells. Split the table or combine row content when merged cells would otherwise be needed.

[Rule] Left-align table content by default.

[Recommendation] If a table has many columns but few rows, consider transposing it.

[Recommendation] Use consistent table title styles for similar tables within a documentation set, such as a kit.


## Images


### General Image Requirements

[Rule] Do not use images without the required copyright rights. If you cannot confirm that you hold permanent rights to an image, do not use it. Create a drawing or take a photograph instead.

[Rule] Images must clearly show the intended information. Avoid artificially composited or low-resolution images.

[Rule] Images must not exceed one screen at 100% page zoom.

[Rule] Do not reference images by URL. Store and reference them locally.

[Rule] Image naming conventions:

- Use letters, digits, and hyphens (-).

- Use meaningful names that reflect the key nouns or verbs in the image. Base names on the caption, context, content, or purpose. In principle, use no more than four English words, for example, typical-service-view.png.

- Image names must be unique within a folder.

[Recommendation] To avoid images that are too large or too small, use widths of 600 pt (about 800 px) for large images, 360 pt (about 480 px) for medium images, and 200 pt (about 260 px) for small images. Image height must not exceed the usable page height.

[Recommendation] Use consistent caption styles for similar figures within a documentation set, such as a kit. Figures in descriptive modules, such as working principle diagrams and flowcharts, convey relatively complete information and need captions. Figures within steps usually illustrate or supplement the instructions, do not convey complete information on their own, and do not need captions.


### Drawings

[Rule] For English text in drawings, capitalize terms, abbreviations, and proper nouns (such as development board and device names) consistently according to [Terms and Abbreviations](#terms-and-abbreviations). Use sentence case for other text: capitalize the first word.

[Recommendation] Use 10.5 pt (14 px) as the normal font size for both Chinese and English text. The minimum size is 9 pt (12 px) for Chinese and 8 pt (11 px) for English.

[Recommendation] Prefer gray and blue color schemes. Use no more than three color schemes in one figure.


### Screenshots

[Rule] Screenshot edges must be complete and clear. If the boundary is not obvious, add a light gray outer border (RGB: 217/217/217).

[Rule] Exclude unnecessary information, such as unrelated desktop icons or toolbars.

[Rule] Do not include sensitive information, such as personal email addresses or public IP addresses.

[Recommendation] Highlight key information with a 1 px blue outline (RGB: 37/79/247). Center the information within the outline and place the outline as close as possible to its edges.


## Notices and Notes

[Rule] To emphasize important notices or supplementary information that differs from the body text, use the following labels.

| Label | Purpose or Meaning | Typical Scenarios |
| -------- | -------- | -------- |
| Note | Provides helpful tips or useful reference information. | -&nbsp;Information that supports development decisions, such as parameter selection principles or supplementary explanations of system mechanisms<br/>-&nbsp;Information that improves development efficiency<br/>-&nbsp;Version differences<br/>-&nbsp;Dependencies<br/>-&nbsp;Related references |
| Caution | Failure to follow the instructions may interrupt a task or cause unexpected results, but recovery is possible. | -&nbsp;Functional errors<br/>-&nbsp;Test failures<br/>-&nbsp;Effects on system overhead or performance<br/>-&nbsp;Feature constraints or version requirements<br/>-&nbsp;Effects on successful application installation<br/>-&nbsp;Attacks on processes<br/>-&nbsp;Memory access errors or corruption<br/>-&nbsp;Security issues, such as data or device security<br/>-&nbsp;Stability issues<br/>-&nbsp;Compatibility issues<br/>-&nbsp;Effects on application distribution<br/>-&nbsp;Effects on device security level assessment<br/>-&nbsp;Effects on user experience, such as available bandwidth, service use, battery life, or trust in an application |
| Warning | Failure to follow the instructions may cause unexpected results that cannot be recovered from. | -&nbsp;Loss of user data<br/>-&nbsp;Hardware damage |

[Rule] Use Markdown blockquote syntax (&gt;) for notices or supplementary information.

&gt; **NOTE**

&gt;

&gt; This API is deprecated since API version 7. You are advised to use newMethod instead.

[Rule] Do not include tables or images in notices or supplementary information, except for icons.

[Rule] Keep notices or supplementary information concise, preferably within one paragraph.

[Rule] Place cautions and higher-severity notices before the relevant text or steps to warn readers in advance and help prevent loss.

[Rule] Do not overuse notes. If more than two notes appear on one screen of a web page, consider incorporating them into the body text.


## Links


### Link Rules

Add links when readers need to refer to another manual or another section of the current manual.

[Rule] Use click for actions on web links.

[Rule] When linking to third-party pages, ensure that the destination provides industry-recognized standards or public information, primarily on official industry standards organization websites. If you cannot determine whether a page is appropriate to reference, do not link to it.

[Recommendation] Use see for cross-document or cross-section references, for example, "For details, see the referenced document." Where this wording does not fit, embed the link directly in the surrounding text.

[Recommendation] Restate essential short content directly. Add a link when the reference content is too extensive to restate conveniently.

[Recommendation] Avoid excessive cross-references and external links in a document. Switching repeatedly between pages or fragments can disrupt readers'
understanding of the information structure and reduce comprehension efficiency.

[Recommendation] Link text may follow the surrounding context and does not have to match the destination heading.

  | **Correct**                                                    | **Incorrect**                                               |
  | ----------------------------------------------------------- | ------------------------------------------------------ |
  | Repeat supports two modes: \[lazy loading](../../application-dev/ui/rendering-control/arkts-new-rendering-control-repeat.md#lazy-loading-capability) and \[full loading](../../application-dev/ui/rendering-control/arkts-new-rendering-control-repeat.md#lazy-loading-capability). | None |

### Link Styles

[Rule] Embed link URLs in text rather than displaying bare URLs on the page.

- Link to another manual or page: \[Terms]\(glossary/glossary.md)

- Link to another section on the current page: \[FAQ]\(#faq)

- Link to another site: \[Example]\(www.example.com)

  | **Correct**                                                    | **Incorrect**                                               |
  | ----------------------------------------------------------- | ------------------------------------------------------ |
  | See the \[OpenHarmony open source project](https://gitee.com/openharmony). | For the OpenHarmony open source project, see https://gitee.com/openharmony. |

[Rule] Use pure Markdown for links, not HTML tags.

  | **Correct**                                                    | **Incorrect**                                               |
  | ----------------------------------------------------------- | ------------------------------------------------------ |
  | See \[Link Styles](#link-styles). | See \<a href="#link-styles">Link Styles</a>. |

[Rule] When linking to another document, link directly to the file rather than its level-1 heading.

For example, the file name is glossary.md and its level-1 heading is "Terms".

  | **Correct**                                                    | **Incorrect**                                               |
  | ----------------------------------------------------------- | ------------------------------------------------------ |
  | \[Terms]\(glossary/glossary.md) | \[Terms]\(glossary/glossary.md#terms) |

## Terms and Abbreviations

[Rule] Use terms and abbreviations consistently and match the [OpenHarmony Glossary](../../glossary.md).

[Rule] For common industry terms and abbreviations, such as IP and MAC, that are not covered in the [OpenHarmony Glossary](../../glossary.md), follow international, national, or industry standards.

[Rule] Do not arbitrarily shorten English words or invent abbreviations.

[Rule] Except for common industry terms and abbreviations, define all terms and abbreviations used in the body text in the glossary.

[Rule] Follow the established capitalization of the expanded term. Do not capitalize letters merely because they correspond to an abbreviation. For example: Hardware Driver Foundation (HDF).

[Rule] In the [OpenHarmony Glossary](../../glossary.md), write the English term followed by its abbreviation in parentheses, where applicable. Follow it with a direct definition without repeating the term name.

Examples:

- Hardware Driver Foundation (HDF)<br>Provides unified peripheral access capabilities and a framework for driver development and management.
- ArkUI<br>A simple, high-performance UI development framework for designing and developing cross-device applications, enabling developers to efficiently build cross-device application UIs.

[Recommendation] Spell out an abbreviation at its first occurrence in the body text, excluding headings and table headers.

[Recommendation] Do not treat development board or device names as terms or abbreviations in the glossary. Introduce them separately, preferably in a table.


## Unit Symbols

[Rule] Use unit symbols consistently in measured values, for example, mm.

[Rule] Use unit symbols consistently in compound units, for example, km/h.

[Rule] Do not use a unit prefix on its own.

| **Correct** | **Incorrect** |
| -------- | -------- |
| 64Kbit/s | 64K |

[Rule] Common unit symbols are listed below.

| Unit Name | Symbol |
| -------- | -------- |
| Hour | h |
| Minute | min |
| Second | s |
| Millisecond | ms |
| Microsecond | μs |
| Nanosecond | ns |
| Bit | bit |
| Kilobit | kbit (use lowercase k for 1000 and uppercase K for 1024) |
| Megabit | Mbit |
| Byte | Byte |
| Kilobyte | kB (use lowercase k for 1000 and uppercase K for 1024) |
| Megabyte | MB |
| Gigabyte | GB |
| Bits per second | bit/s (both bit/s and bps are correct, but bit/s is more formal) |
| Bytes per second | Byte/s (both Byte/s and B/s are correct; use Byte/s consistently) |
| Kilometer | km |
| Meter | m |
| Centimeter | cm |
| Millimeter | mm |
| Micrometer | μm |
| Decibel | dB |
| Degree Celsius | ℃ |
| Degree Fahrenheit | ℉ |
| Kelvin | K |
| Hertz | Hz |
| Pascal | Pa |
| Kilogram | kg |
| Gram | g |


## Punctuation

  [Rule] Commas: Avoid comma splices.
| **Correct** | **Incorrect** |
| -------- | -------- |
| The billing center primarily handles call detail records and account processing. A call detail record interface between the billing center and the charging gateway allows the billing center to retrieve users' call detail records. Call detail record files use the "\*.txt" format. | The billing center primarily handles call detail records and account processing, a call detail record interface between the billing center and the charging gateway allows the billing center to retrieve users' call detail records, call detail record files use the "\*.txt" format. |

[Rule] Periods:

- End complete figure or table cross-reference sentences with periods. Example: Table 1-2 describes the parameters.

- Do not add a period to text embedded in another sentence as part of that sentence.
    | **Correct** | **Incorrect** |
  | -------- | -------- |
  | Before using xxx (hereafter referred to as x), read this manual carefully. | Before using xxx (hereafter referred to as x.), read this manual carefully. |

- Add a period at the end of a parenthesized sentence that stands independently rather than forming part of the preceding sentence.

[Rule] Colons: Do not use consecutive colons in a sentence, because this can make their scope unclear.

| **Correct** | **Incorrect** |
| -------- | -------- |
| Correct example 1:<br/>Charging policy: A1&nbsp;indicates charging, and A2&nbsp;indicates no charging.<br/>Correct example 2:<br/>Charging policy:<br/>-&nbsp;A1: Charging<br/>-&nbsp;A2: No charging | Charging policy: Charging: A1, no charging: A2. |

[Rule] Parentheses:

- Use ASCII parentheses in English prose, except in literal code or quoted data.

- Do not put lengthy explanations in parentheses. Present them as a separate [note](#notices-and-notes) instead.

[Rule] Do not insert manual breaks before closing punctuation, such as periods, question marks, exclamation marks, commas, semicolons, or colons. Let the renderer wrap text.

[Rule] Keep paired punctuation, such as quotation marks and parentheses, with the text it encloses. Avoid forced line breaks immediately after opening punctuation or before closing punctuation.

[Rule] Quotation marks: Use English quotation marks consistently, for example, "text". Preserve literal code and matched strings.

[Recommendation] Question marks: Use question marks for genuine questions in UI messages, CLI prompts, voice prompts, and FAQs. Avoid unnecessary questions elsewhere.

[Recommendation] Exclamation marks: Avoid exclamation marks.

[Recommendation] Ellipses: Minimize ellipses and expressions such as "etc." to keep information accurate and complete.

[Recommendation] Other symbols: Use "√" and "×" with caution. Their meanings may be interpreted in opposite ways in different countries.


## Character Escaping

[Rule] Escape Markdown formatting characters when required by adding a backslash (\) before the character so that it displays correctly.

Common characters that may require escaping include backslashes, asterisks, underscores, braces, brackets, hash signs, plus signs, hyphens, periods, and vertical bars.

| Correct | Incorrect |
| -------- | -------- |
| \\*&nbsp;Text content | \*&nbsp;Text content |

[Rule] Use the specified escape sequences for special characters:

- Escape "&lt;" as "&amp;lt".

- Escape "&gt;" as "&amp;gt".

- Escape "&amp;" as "&amp;amp".


## File Paths

A file path identifies the location of a file on a computer.

[Rule] For files on a computer drive, include an explicit root directory in the path.

[Recommendation] Use forward slashes ("/") as folder separators where possible.

[Recommendation] Avoid excessively long file paths.


## Code and Comments

See [Sample Code Style](style-guide-example-code-style.md).


## IP and MAC Addresses

[Rule] Use only private IP addresses in examples. Do not use public IP addresses or actual production network data. Private IP address ranges are listed below.

| Network Class | Address Range |
| -------- | -------- |
| A | 10.0.0.0～10.255.255.255 |
| B | 172.16.0.0～172.31.255.255 |
| C | 192.168.0.0～192.168.255.255 |

[Rule] When describing specific network topology or routing information, provide both the IP address and subnet mask.

- In figures and tables, you can use notation such as "x.x.x.x/24", where "24" is the prefix length.

- In body text, express the subnet mask in dotted-decimal form, such as 255.255.255.0. For example: "The IP address is 10.10.10.1, and the subnet mask is 255.255.255.252."

[Rule] Use www.example.com for domain name examples.

[Rule] Mask MAC address examples with "X" while preserving the correct format.

| Correct | Incorrect |
| -------- | -------- |
| 00-01-XX-XX-XX-XX<br/>00:01:XX:XX:XX:XX | None |


## Personal Information

[Rule] Do not use real personal information.

[Rule] Mask personal phone number examples with "\*" while preserving the correct format.

[Rule] Prefix international phone numbers with country and area codes, each in parentheses, for example, (86)&nbsp;(755)&nbsp;\*\*\*\*\*\*\*\*&nbsp;[Shenzhen,&nbsp;China].

[Rule] Mask personal ID number and account name examples with "\*" while preserving the correct format.

[Rule] Mask email address examples while preserving the correct format, for example, \*\*\*@example.com.

[Recommendation] Use generic names for personal name examples where possible.

