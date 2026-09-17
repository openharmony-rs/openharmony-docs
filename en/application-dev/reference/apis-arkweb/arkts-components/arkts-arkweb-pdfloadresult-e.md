# PdfLoadResult

Defines the PDF page loading results, which identify various states and error types during PDF file loading and help developers diagnose errors and provide user prompts when PDF display fails.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## LOAD_SUCCESS

```TypeScript
LOAD_SUCCESS = 0
```

The PDF file is successfully loaded.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## PARSE_ERROR_FILE

```TypeScript
PARSE_ERROR_FILE = 1
```

Failed to load the PDF file.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## PARSE_ERROR_FORMAT

```TypeScript
PARSE_ERROR_FORMAT = 2
```

The PDF file format is not supported.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## PARSE_ERROR_PASSWORD

```TypeScript
PARSE_ERROR_PASSWORD = 3
```

The PDF file password is incorrect.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## PARSE_ERROR_HANDLER

```TypeScript
PARSE_ERROR_HANDLER = 4
```

Failed to process the PDF file.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core
