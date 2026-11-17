# Language Style

<!-- md-trans-meta sourceCommit=195053a223f1a2d54d1ded7b0c40b4ed874b59e5 translatedAt=2026-11-17T02:46:33.905Z nl=1 -->

## Person and Voice

[Rule] Address readers as you when a subject is needed. Use imperative sentences for instructions.

| **Correct** | **Incorrect** |
| -------- | -------- |
| Create a widget project. | We will now create a widget project. |

[Recommendation] Prefer the active voice: the subject performs the action rather than receiving it.

| Recommended | Not Recommended |
| -------- | -------- |
| Configure parameter A to declare support for feature B. | Feature B is supported after parameter A is configured. |


## Tone and Wording

[Rule] State information objectively and use a friendly tone.

| **Correct** | **Incorrect** |
| -------- | -------- |
| Ensure that the configuration is correct. Otherwise, the system will not work properly. | You must ensure that the configuration is correct. Otherwise, you bear all consequences. |

[Rule] Avoid colloquial fillers.

[Rule] Use precise technical language rather than jargon that only a small group of people understands and that is difficult to translate. For example, use "invalid memory access".

[Rule] Avoid idioms and sayings. Their precise meaning is difficult to convey in translation, and they are unnecessary in technical documentation.

[Rule] Avoid wording that may imply bias or discrimination based on gender, race, culture, age, skill, occupation, religion, economic status, or other characteristics.

[Rule] Use neutral wording for notices. Avoid wording that may cause negative feelings in users.

| **Correct** | **Incorrect** |
| -------- | -------- |
| None | You have been kicked out. |


## Reader Perspective

[Rule] Write for the target audience (referred to as readers below):

- Identify your audience, such as product managers or developers, and determine what matters to them. Provide only relevant information. Throughout writing, consider whether the content covers all key points and whether anything is redundant.

- Provide supporting information for readers with different skill levels, such as beginners and experienced readers.

- Present information in the order readers expect. See [Clarity](#clarity).

[Rule] Write for user scenarios and tasks:

- Focus on real scenarios and user goals or tasks, not product features.

- Make the task objective clear in the heading.

- For complex tasks with more than five steps, provide a process flowchart or table before the instructions.

- Provide clear, step-by-step instructions. Use screenshots where helpful, capturing only key information.

- Place supporting information close to the task instructions it supports.

- Provide supporting information for the entire task, such as necessary background, prerequisites, preparation, verification of success, common troubleshooting, and error prevention.

- Provide reasons where necessary. For example, omit internal implementation details that do not help readers understand or complete a development task.


## Completeness

[Rule] Do not omit task scenarios. Before writing, analyze users and tasks to determine which task scenarios the document must cover.

[Rule] Use writing templates to ensure completeness:

- OpenHarmony documentation follows a structured, modular approach. The [OpenHarmony Documentation Templates](../template) provide content templates for each information type based on reader needs. Choose the template that best matches your content to ensure complete coverage.

- Do not delete sections marked as mandatory in a template.

- Delete sections marked as optional in a template only after confirming that they do not apply.


## Specificity

[Rule] Use specific descriptions instead of abstract or obscure wording.

| **Correct** | Incorrect |
| -------- | -------- |
| The LABEL_VALUE_ERROR error message is displayed during the build. | The build fails. |

[Rule] When describing quantities or degrees, replace general words such as "many", "few", and "large" with specific numbers that readers can observe or measure.

| **Correct** | Incorrect |
| -------- | -------- |
| The file is larger than 16 MB. | The file exceeds the limit. |
| Wait about 30 minutes. | Wait a long time. |
| CPU speed increases by 80%. | Performance improves. |


## Conciseness

[Rule] Use subject-verb or subject-verb-object sentences without unnecessary modifiers.

[Rule] Avoid long sentences. Split sentences that describe multiple operations or ideas.

[Rule] Do not use double negatives.

[Rule] Be concise and state the point directly. Avoid meaningless wording, including unnecessary expressions of degree or tone.

Examples:

- Do not redefine a property.
- Bind the service to the notification.

[Rule] Remove unnecessary information based on readers' skill levels.


## Clarity

[Rule] Ensure that descriptions are clear, unambiguous, and easy to understand, conveying one clear meaning:

- Follow the requirements for [Specificity](#specificity) and [Conciseness](#conciseness).

- Ensure that every pronoun has a clear referent that readers can identify from the context, making the text easier to understand and translate.

- Clearly explain how to choose parameter values and how the feature works.

  | **Correct** | Incorrect |
  | -------- | -------- |
  | When parameter A is set to 1:<br/>-&nbsp;If parameter B is set to 1, navigation to the next level is available, and the tab is displayed as a square nine-cell grid.<br/>-&nbsp;If parameter B is set to 0, navigation to the next level is unavailable, and the tab automatically changes to a circular nine-cell grid. | When parameter A is 1 and parameter B is 1, if navigation to the next level is available, the tab is a square nine-cell grid; otherwise, it automatically changes to a circular nine-cell grid. |

- Avoid ambiguous wording.

  | **Correct** | **Incorrect** |
  | -------- | -------- |
  | Connect the development board to the power supply. | Press the development board's power switch. |

- Avoid vague descriptions, such as imprecise expressions of degree or emphasis. Give specific values where available.

[Rule] Ensure clear logic:

- Organize sections, paragraphs, steps, and sentences in a logical order that matches how readers understand information. The following common patterns can be used separately or together.

  | **Logical Structure (Writing Order)** | Characteristics | Typical Information Types (Not Exhaustive) |
  | -------- | -------- | -------- |
  | General to specific | Begin with an overall summary, such as a feature overview or development process overview, then expand on individual points, such as subfeatures or development tasks.<br/>The individual points must be collectively exhaustive (no omissions) and mutually exclusive (no overlap). | Feature or scenario descriptions<br/>Development guides |
  | Chronological | Follow the sequence of time, process, or cause and effect. | Development guides |
  | Spatial or structural | Proceed from upper layers to lower layers, or from the whole to its parts. | Architecture descriptions<br/>Network topology descriptions |
  | Order of importance | Proceed from primary to secondary, or from basic to special cases. | Development guides<br/>Problem analysis |
  | Situation, complication, question, answer | Trace the origin and development of the problem. Introduce a familiar situation, explain the complication, raise the initial question, and finally provide the solution, which is the topic to be discussed. | Feature or scenario descriptions |

- In development guides, make the complete development process for the scenario or task easy to understand.

- When steps have branches, clearly explain how to choose a branch.

[Rule] Use diagrams and tables where appropriate to make the logic and meaning easier to understand.

[Rule] When describing specifications and constraints, do not identify support by specific device models. Instead, explain how readers can determine whether a feature or scenario is available through observable, actionable criteria, such as a device characteristic or an API query. This lets readers apply the criteria to other devices.


## Consistency

[Rule] Use consistent wording: terms, abbreviations, and words referring to the same object must be consistent throughout the document and match reader expectations. Do not use different words, including a mixture of Chinese and English, for the same object or operation.

Use the following common words consistently in OpenHarmony documentation.

| Word or Operation | Usage |
| -------- | -------- |
| log in | Use as a verb when describing signing in. |
| click | Use for the pointer action described here. Example: Click the link. |
| image | Use consistently for the documented image concept. |
| charging | Use consistently for the charging operation. |
| threshold | Use consistently. |
| Operation-specific terms | Use the established English term for the specific operation. |
| command | Use consistently for the operation discussed in this guide. |
| shape | Use where geometry is meant. |

**Commonly Confused Words**
  
| **Word** | **Description** |
| -------- | -------- |
| resource leak | **Definition**: A program logic defect prevents the system from reclaiming or reusing allocated resources, such as memory, handles, connections, or threads.<br>**Applies to**: Memory, handles, connection pools, thread pools, file descriptors, GPU memory, ClassLoader, and cache references.<br>**Examples**: memory leak; resource leak. |
| information disclosure; data exposure | **Definition**: Data or information crosses an established security boundary into an unauthorized environment.<br>**Applies to**: User information, keys and credentials, sensitive log fields, and excessive fields returned by APIs.<br>**Examples**: information disclosure; data exposure. |
| liquid or signal leakage | **Physical cases**: Physical liquids or signals cross an established security boundary into an unauthorized environment. These cases are separate from the information-security definition above. |

[Rule] Keep the structure consistent within a document and across similar information. A consistent structure helps readers understand and find information. Choose the template that best matches your content from the [OpenHarmony Documentation Templates](../template) and follow its instructions.

[Rule] Use consistent sentence patterns. This gives technical documentation a consistent style and follows readers' established expectations, making it easier to understand. For example, consistently use imperative sentences to describe actions.

[Rule] Keep the formatting of similar elements, such as [code blocks](style-guide-content-elements.md#code-and-comments) and [file paths](style-guide-content-elements.md#file-paths), consistent to aid understanding.

[Recommendation] Use UI when referring to the overall interface. Use SMS message when the SMS service is specifically meant. For protocol concepts, use the protocol's established terminology.
