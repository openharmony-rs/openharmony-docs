# Open Source Community Documentation Writing Guidelines

<!-- md-trans-meta sourceCommit=8e600af821b06715faa08e9e35b44f81c8d6dd8d translatedAt=2026-11-17T02:46:33.905Z nl=2 -->

## Documentation Deliverables (Application Development)

- **JS API reference**: documents application programming interfaces.

  Organize the documentation by **d.ts** file. **Each d.ts file corresponds to one Markdown document, which must cover all APIs delivered in the current version.** For each API, describe its functionality, parameters, and return values, and provide example code.

- **Developer guide**: **guides users through application design and development**, describing how to develop applications using platform features from an application development perspective.

  Organize guides **by scenario**. Describe the functionality, constraints, and APIs for each scenario, and provide step-by-step instructions for developing a feature or function using the open APIs or SDKs provided by the platform or product.

- **Terminology**: conveys **complete, accurate, and unambiguous** concepts to developers.

  When a new concept is introduced, provide a consistent term to standardize how the concept is expressed. For example, eTS.

- **apidiff/changelog**: describes **version changes** to developers.

  The apidiff describes all API additions, changes, and deprecations in a version. If no APIs have changed, no description is required.

  If an API change requires adaptation, describe the adaptation required for each affected API in the changelog.

- **FAQs** (Frequently Asked Questions): describes common exceptions and recommended solutions.

- **Readme**: introduces the background and requirements of an OpenHarmony subsystem or component.

## Basic Writing Requirements (All Documents)

- **Completeness**

  Cover all scenarios and provide uninterrupted operation procedures. The documentation must match the actual scope delivered in the version, without omissions or descriptions of features that are not yet delivered.

- **Correctness**

  The documentation must **match the implemented functionality**. Version information and parameter and return value descriptions must be correct. **Users must be able to perform the documented operations.**

- **Consistency with documentation standards**

  The documentation must **comply with documentation standards**, without basic errors, contradictions, inconsistencies, ambiguity, or sensitive terms. Note: Follow terminology standards and do not include vendor information unless necessary.

- **Clarity**

  Write concise, clear descriptions for developers, focusing on capabilities they can perceive and use. Example code must be easy to understand, provide complete context (or explain the required context), specify parameters clearly, and include comments for complex logic.

- **Compliance**

  **Avoid plagiarism and compliance risks.** For example, do not closely copy competitors' descriptions or use concepts unique to competitors.

## Documentation Structure (Application Development)

Application development documentation: [Application Development](https://gitcode.com/openharmony/docs/tree/master/en/application-dev)

Organize developer guides by functionality in folders directly under application-dev. For example, media contains media developer guides, and usb contains USB service developer guides. Store all API references in application/reference/apis.

## Document Contents (JS API References and Developer Guides)

1. Figures folder: stores images referenced in the documentation, including SVG, PNG, and GIF files.
2. System resources folder: stores system icons referenced in the documentation. No action is required for this folder.
3. Readme: add an entry for every new Markdown document in the directory.
4. Documents: pay particular attention to file naming, as described below.

## Writing JS API References

### Creating a Document or Updating an Existing Document

Does a document already exist for the module (one d.ts file)? If yes, add the new APIs to that document. Otherwise, create a Markdown (md) file.

1. **File naming**: Each d.ts file corresponds to one JS API reference document named **js-apis-moduleName.md**. Examples:

   For the media module @ohos.multimedia.audio, name the file js-apis-audio.md.

   For the telephony module @ohos.telephony.sms, name the file js-apis-sms.md.

2. **Document title**: Use a **concise English phrase** to summarize the module's functionality. Use established terms such as Ability and SIM card.

   When adding APIs to an existing document, check whether the title still covers all functionality. For example, if the media module is named Audio Playback in API version 6 and adds Audio Recording and Video Decoding in API version 7, update the title accordingly.

3. **Content**: Detailed writing instructions are provided later in this document.

4. **Upload path**: Upload the document to the API reference directory for the corresponding Kit under docs/en/application-dev/reference/. Store images in that directory's figures folder.

5. **Update the corresponding Readme** in that Kit's API reference directory. If the document title has not changed, the Readme does not need to be updated.

**Tips: After a PR is merged into the docs repository, a translation issue is automatically triggered.**

### Writing Content

JS API reference template: [API Reference Template](template/js-template.md)

**Each document must contain the following:**

- **Document title**

  - **Initial version (mandatory)**: Specify the version in which the module's initial APIs were introduced, in a note.

  - **Module description (mandatory)**: Briefly describe the module's functionality, use cases, and usage recommendations.

    For example, lightweight storage provides key-value file data processing for applications, supporting lightweight data storage and queries.

  - **Modules to Import/Usage (mandatory)**: Specify the module to import as appropriate. If no module import is required, replace "Modules to Import" with "Usage."

       For Modules to Import, provide the import statement in a **code block**.

       For Usage, describe the prerequisites for using the APIs. For example, before using AbilityContext, call getContext() to obtain a Context object.

  - **Required permissions (mandatory)**: Describe the permissions required to use the module's APIs.

    For example, Required permissions: ohos.permission.XXX. (Delete this item if no permission is required. Specify whether a required permission is a system permission.)

  - **Functionality (mandatory)**: Describe the module's properties, APIs, and other features in detail.

- **Functionality (consistent with the d.ts file)**:

  - **Properties (under a namespace, optional)**: Define the characteristics of an object. Use a table with the property name, type, readability, writability, and description.

  - **Methods (under a namespace, mandatory)**: Functions associated with an object. Use a section containing the method name, signature, functionality, parameters, return value, and example code.

  - **Enums (optional)**: Types consisting of a set of values. Use a table with the enum name, value, and description.

  - **Classes/interfaces (optional)**: Usually contain their own properties and methods. Use a section containing the class/interface name, description, properties, and other relevant information.

  - **Custom types (optional)**: Interfaces expressed as key-value pairs. Describe them in the same way as method parameters. Use a table with Name, Type, Mandatory, and Description columns.

  - **Properties (in a class/interface, optional)**

  - **Methods (in a class/interface)**

**Version markers**:

1. If a class is added in a new version, mark the class, its methods, and its properties with the version number. The following example uses the intl documentation.

   intl was introduced in API version 7. API version 8 adds the **Collator class, its constructor, and other methods**. **Add an 8+ superscript to the Collator class and all its methods**, immediately after each new item.

2. Do not delete content deprecated in a new version. Append deprecated to the deprecated item, and use a blockquote (>) to recommend an alternative with a link. Example:

   abandonmentMethod(deprecated)

   \> This API is deprecated since API version 7. You are advised to use newMethod instead.

## Writing JS Developer Guides

### Creating Documents

**Note:**

1. Folder naming: Each folder contains developer guides for related modules.
2. Upload path: docs/en/application-dev/xxx. Store images in the corresponding figures folder.
3. When adding a guide or document, update the corresponding Readme, docs/en/application-dev/xxx/Readme-EN.md.

### Writing Content

Developer guide template: [guide-template.md](template/guide-template.md)

**Each document must contain the following**:

-  **Overview/xxx Development Overview (mandatory)**

   -  **Feature overview (mandatory)**: Describe the capabilities covered by the guide and the tasks it helps developers complete.

   -  **Basic Concepts (mandatory)**: Describe the basic concepts related to the development task.

   -  **Working Principles (optional)**: Describe how the functionality involved in the development task works.

   -  **Constraints (mandatory)**: Describe the constraints on the development task and their negative impact.

-  **How to Develop xxx (mandatory)**

   -  **When to Use (mandatory)**: Describe the scenario, the problem to solve, and the intended result.

   -  **Available APIs (mandatory)**: Describe the APIs involved in this guide.

   -  **How to Develop (mandatory)**: Describe the overall development process so that developers can complete the task quickly.

   -  **Debugging and Verification (optional)**: If separate debugging and verification are required after development, provide instructions for checking whether the operations succeeded.

   -  **Samples (mandatory)**: Provide code snippets covering a complete task after describing the development process.

Optional does not mean that the content can be omitted at will. It means that the content may not apply to the subsystem.
