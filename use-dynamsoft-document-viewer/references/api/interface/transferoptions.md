---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface TransferOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface TransferOptions
breadcrumbText: Interface TransferOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface TransferOptions Page
permalink: /api/interface/transferoptions.html
---

# TransferOptions

## Syntax

```typescript
interface TransferOptions {
    sourceIndices? : number[];
    insertBeforeIndex? : number;
}
```

## Attributes

### sourceIndices

The array of pages indices to be moved or copied. If it is not specified, all pages will be moved or copied.

### insertBeforeIndex

The moved or copied pages will be placed before this index. If it is not specified or out of the maximum range, the specified page(s) will be moved or copied after the last page.


## Related

- [`copyPagesToDocument()`]({{ site.api }}class/documentmanager.html#copypagestodocument)
- [`movePagesToDocument()`]({{ site.api }}class/documentmanager.html#movepagestodocument)