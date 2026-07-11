# Content Embed Kit FAQs

<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @qq_41146650-->
<!--Designer: @gcw_nDnzjzHO;@wei-guoning-->
<!--Tester: @sd_yinjian-->
<!--Adviser: @jinqiuheng-->

## How to Choose Between Linked and Embedded Modes When Creating an OE Document

When a client developer calls [OH_ContentEmbed_CreateDocumentByFile](../reference/apis-content-embed-kit/capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile) to create an OE document, the developer can set the `isLinking` parameter based on whether source file changes need to be synchronized.

- When `isLinking` is `true`, the OE document is created in linked mode. When the server edits the OE document, the source file is also modified. If the source file is moved, deleted, or renamed, starting editing for the OE document will fail. If the user restores the original source file in File Manager, the application must request authorization. Linked mode does not support linking to the sandbox directory of the client application.
- When `isLinking` is `false`, the OE document is created in embedded mode. When the client requests the server to edit the OE document, a temporary file is first copied to the sandbox directory of the client application. Server-side modifications to the OE document do not modify the source file. The created temporary file is cleared when the client exits normally.

## How to Display a Document Snapshot or Application Icon When the Client Creates an OE Document Based on a File

When the client creates a document by calling [OH_ContentEmbed_CreateDocumentByFile](../reference/apis-content-embed-kit/capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile), the client must query whether the OE Extension supports snapshot retrieval by calling [OH_ContentEmbed_Proxy_GetCapability](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability).

- If the server does not support snapshots, the client can use <!--RP1-->[OH_NativeBundle_GetAbilityResourceInfo](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_getabilityresourceinfo) to obtain the list of component resource information for the file type.<!--RP1End-->
- If the server supports snapshot retrieval, the client can use [OH_ContentEmbed_Proxy_GetSnapshot](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot) to obtain snapshot information.
