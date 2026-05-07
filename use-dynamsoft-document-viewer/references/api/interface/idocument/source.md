---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface Source
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface Source
breadcrumbText: Interface Source
description: Dynamsoft Document Viewer Documentation API Reference Interface Source Page
permalink: /api/interface/idocument/source.html
---

# Source

## Syntax

```typescript
interface Source {
    fileData: Blob; 
}
```

## Attributes

### fileData

The blob of the file to be loaded.

## Remark

- `Source` can be extended as [`PdfSource`](/api/interface/idocument/pdfsource.md).

## Related

- [`loadSource()`]({{ site.api }}interface/idocument/index.html#loadsource)