---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface CreateDocumentOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface CreateDocumentOptions
breadcrumbText: Interface CreateDocumentOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface CreateDocumentOptions Page
permalink: /api/interface/createdocumentoptions.html
---

# CreateDocumentOptions

## Syntax

```typescript
interface CreateDocumentOptions {
    name?: string; 
    author?: string; 
    creationDate?: string; 
}
```

## Attributes

### name

Specify the name of the new document.

### author

Specify the author of the new document.

### creationDate

Specify the creation date of the new document. Please note that the argument should be `D:YYYYMMDDHHmmSSOHH'mm'`, like `D:20230101085959-08'00'`. It also supports the older format `D:YYYYMMDDHHmmSS`. If this format is used (e.g., `D:20230101085959`), the system will automatically add the relevant time zone information, resulting in a complete representation like `D:20230101085959-08'00'`.

## Related

- [`createDocument()`]({{ site.api }}class/documentmanager.html#createdocument)
