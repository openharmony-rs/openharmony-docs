# Document Structure

<!-- md-trans-meta sourceCommit=3d427f877c9aa70d48b54cd9dfae81cbca7b3f24 translatedAt=2026-11-17T02:46:33.905Z nl=1 -->

## Headings


### Heading Rules

[Rule] A heading must summarize the main topic of the section and include its key terms. Avoid generic headings such as "Overview" or "Introduction" without key terms. Instead, use headings such as "Kernel Overview" or "Introduction to OpenHarmony."

[Rule] Keep the structure of headings at the same level and of the same type consistent.

| **Correct** | **Incorrect** |
| -------- | -------- |
| Kernel Overview<br/>Driver Overview<br/>[Comment] Both pages describe concepts, so their heading styles are consistent. | Introduction to the Kernel<br/>Driver Overview |
| Audio Playback Development Guide<br/>Audio Management Development Guide<br/>[Comment] Both pages provide task instructions, so their heading styles are consistent. | Audio Playback Development Guide<br/>Audio Management Development |

[Rule] Do not spell out abbreviations in headings. When an abbreviation appears in a heading, handle it as follows:

- If this is its first occurrence, spell it out in the following body text.

- If it has already appeared, there is no need to spell it out in the following body text.

- If you cannot determine whether it has appeared before, treat it as the first occurrence.

[Rule] Do not use special characters in headings.

- These characters include +, -, \*, ?, |, ^, ~, "", ', \, and /. Their special meanings can prevent headings from displaying correctly or appearing in search results.

- When product names, functions, or features must be combined in a heading, use the half-width "/" or "&amp;" with caution.

[Rule] Do not end headings with punctuation such as periods, question marks, or colons. This also applies to FAQ headings.

[Rule] Do not use superscripts or subscripts in headings.

[Rule] Enclose supplementary information in headings in parentheses. Separate different dimensions with ASCII commas, for example, "Quick Start (Standard System, Package Installation)".

[Recommendation] Keep headings concise and descriptive.

[Recommendation] Use nouns or noun phrases for headings that describe concepts, features, or other descriptive content.

Example: Basic Concepts.

[Recommendation] Use gerund phrases for task headings.

Example: Obtaining Display Information.


### Heading Styles

[Rule] Use level-1, level-2, and level-3 headings only. Do not use level-4 headings on a page.

[Rule] Follow the hierarchy of level-1 &gt; level-2 &gt; level-3 headings.

[Rule] Do not skip heading levels. For example, do not place a level-3 heading directly under a level-1 heading.

## Paragraphs

[Rule] Each paragraph must have only one topic sentence or central idea. Place the topic sentence or central idea at the beginning.

[Rule] Organize paragraphs in a [clear logical structure](style-guide-language-style.md#clarity).

[Rule] Use declarative, affirmative, or imperative sentences as appropriate. Avoid exclamations.

[Recommendation] Limit each paragraph to seven lines, ideally four lines or fewer.

[Recommendation] For technical descriptions, tables can be more effective than text, and figures can be more effective than tables. Combine text, figures, and tables to make content easier to understand.

[Recommendation] Avoid more than three consecutive paragraphs of plain text. Use figures and tables to vary the presentation.

[Recommendation] Use normal body text for paragraphs. Do not make entire paragraphs bold.


## Sentences

[Rule] Each sentence must address only one topic.

[Rule] State information directly. Avoid double negatives and rhetorical questions.

[Rule] Avoid ambiguous noun strings. Make the intended meaning explicit, for example, "Configure the management module" for an action or "configuration management module" for a module name.

[Rule] Make the subject of each sentence clear. If the subject is omitted, ensure that readers can identify it quickly and correctly. Avoid changing the subject within a sentence.

Examples: "The tool reports an error"; "The compilation subsystem reports an error."

[Rule] Use simple subject-verb or subject-verb-object sentences instead of complex sentences. Convert complex sentences into lists or split them into simple sentences and straightforward compound sentences.

[Rule] Avoid long sentences. Split sentences that describe multiple operations or ideas.

[Recommendation] Use imperative sentences for actions.

| Recommended | Not Recommended |
| -------- | -------- |
| In the dialog box, click OK. | In the dialog box, please click OK. |

[Recommendation] Keep English sentences within 30 words where practical.

[Recommendation] Use normal body text for sentences. Do not make entire sentences bold or add background colors.


## Contents

Documentation has both manual-level contents and in-page contents to help readers browse efficiently and find key information.

[Rule] Manual-level contents: Manage the contents at the lowest folder level in the Docs repository. Update the contents whenever a page is added, renamed, or deleted in that folder.

[Rule] In-page contents: These are generated automatically from page headings. Follow the [heading rules and styles](#headings) when writing.


## Folder and File Naming

[Rule] Folder names: Use the English name of the documented subject, such as ability or ui, in lowercase.

[Rule] Markdown file names:

- Use letters, digits, and hyphens (-). Use the lowercase extension ".md".

- For files available only to system applications, end the file name with "-sys.md", as shown below:

  | **Category** | **Title** | **File Name** |
  | ------   | -------- | -------- |
  | Guide  | Mission Management (for System Applications Only) | mission-management-sys.md | 
  | API Reference  | @ohos.multimedia.image (Image Processing) (System API) | js-apis-image-sys.md | 

- Except for Readme.md, use lowercase file names in principle. Camel case is acceptable if it improves readability.

- Use meaningful names that summarize the document topic, preferably based on the English document title, for example, ability-assistant-guidelines.md.

- In principle, use no more than four English words.

- File names must be unique within a folder.
