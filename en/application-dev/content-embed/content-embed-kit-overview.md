# About This Kit

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

Starting from API version 24, Content Embed Kit provides inter-application document embedding and collaborative editing capabilities. It helps users embed documents in other formats into the current application's document and enables cross-application document editing, enriching the application editing experience.

In Content Embed Kit, applications are classified by the responsibilities they assume as follows:

- Client application: An end-user application that embeds documents from other applications. This application implements service logic by calling [OE](content-embed-kit-terminology.md#oe) framework APIs, such as embedding external documents, displaying document snapshots, and starting an OE server application on demand to trigger document editing operations. For details, see [Client Application Development](content-embed-client-guidelines.md).
- Server application: An end-user application that provides client applications with embedding capabilities for documents in specific formats. This application must register [OE Extension](content-embed-kit-terminology.md#oe-extension) information with the system. At runtime, the system dynamically starts the application based on requests from OE client applications to respond to document embedding and editing operations. For details, see [Server Application Development](content-embed-server-guidelines.md).

## Use Cases

- Document embedding: Embeds a document from one application into a document of another application. For example, an Excel spreadsheet can be embedded into a CAD document, and documents in various formats such as images and tables can be embedded into a document editor.
- Cross-application editing: Starts the source application of an embedded document for editing after the document is embedded. For example, in a CAD document, users can click an embedded spreadsheet to start Excel and edit the spreadsheet.

## Capabilities

- Allows applications to register their document embedding capabilities with the system and declare supported document types.
- Allows an application to serve as an OE client application and embed other types of documents into its own documents. Embedded documents can be displayed as the corresponding application icon or document snapshot. The OE server application can be started with one click for editing, and the edited result can be updated to the OE client application document.
- Allows applications to embed documents from other applications in embedded or linked mode. For details, see [How to Choose Between Linked and Embedded Modes When Creating an OE Document](content-embed-faq.md#how-to-choose-between-linked-and-embedded-modes-when-creating-an-oe-document).
- System-provided document embedding capability: If a document type has not been registered by an OE server application, documents of this type are embedded or linked to an OE client application document as application icons (snapshot preview is not supported yet). The corresponding application can be started for editing, and the edited result can be updated to the OE client application document.
- Compatible with documents generated on Windows that contain OLE data. After such documents are edited on OpenHarmony and transferred back to Windows, the documents remain unaffected.

## Highlights

Cross-application collaboration: Breaks down barriers between applications and enables seamless embedding and editing of different types of documents.

## Relationship with Related Kits

[Ability Kit](../application-models/abilitykit-overview.md): Content Embed Kit internally depends on the Extension base capabilities provided by Ability Kit and interacts with Ability Kit for lifecycle scheduling.

<!--RP1--><!--RP1End-->

