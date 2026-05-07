---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface MergeDocumentOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface MergeDocumentOptions
breadcrumbText: Interface MergeDocumentOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface MergeDocumentOptions Page
permalink: /api/interface/mergedocumentoptions.html
---

# MergeDocumentOptions

## Syntax

```typescript
interface MergeDocumentOptions {
    name?: string; 
    author?: string; 
    creationDate?: string; 
    deleteOriginal?: boolean; 
}
```

## Attributes

### name

Specify the name of the new merged document.

### author

Specify the author of the new merged document.

### creationDate

Specify the creation date of the new merged document. Please note that the argument should be `D:YYYYMMDDHHmmSSOHH'mm'`, like `D:20230101085959-08'00'`. It also supports the older format `D:YYYYMMDDHHmmSS`. If this format is used (e.g., `D:20230101085959`), the system will automatically add the relevant time zone information, resulting in a complete representation like `D:20230101085959-08'00'`.

### deleteOriginal

Specify whether to delete the original documents. 

Default value: `false`

## Related

- [`mergeDocuments()`]({{ site.api }}class/documentmanager.html#mergedocuments)