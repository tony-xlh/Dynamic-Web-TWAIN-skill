---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface IDocTextSearcher
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface IDocTextSearcher
breadcrumbText: Interface IDocTextSearcher
description: Dynamsoft Document Viewer Documentation API Reference Interface IDocTextSearcher Page
---

# IDocTextSearcher

## Syntax

```typescript
interface IDocTextSearcher {
    docUid(): string;
    getResults(pageIndex: number): Promise<TextSearchResult[]>;
    destroy(): void;
}
```

## Attributes

### docUid

The uid of the doc.

## Methods

### getResults

Get the text search result of a page.

**Parameters**

`pageIndex`: the index of the page to search

**Return values**

Promise of an array of the `TextSearchResult` object. Please refer to [`TextSearchResult`](/api/interface/textsearchresult.md).

**Promise Exception**

 Error Code  | Error Message
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  
 -80104 | *XXX(API)*: The specified document(s) do not exist.
 -80105 | *XXX(API)*: The specified page(s) do not exist.  
 -80206 | The DocTextSearcher has been destroyed.

### destroy

Destroy the instance of the doc searcher.

## Related

[`createTextSearcher()`](/api/interface/idocument/index.md#createtextsearcher)


