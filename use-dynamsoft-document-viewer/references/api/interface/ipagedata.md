---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface IPageData
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface IPageData
breadcrumbText: Interface IPageData
description: Dynamsoft Document Viewer Documentation API Reference Interface IPageData Page
---

# IPageData

## Syntax

```typescript
interface IPageData {
    get uid(): string;
    get fileIndex(): number;
    get filter(): string;
    get perspectiveQuad(): Quad;
    get rotation(): number;
    get mediaBox(): Rect;
    get cropBox(): Rect;
    fileData(): Promise<Blob>;
    raw(): Promise<PageImageInfo>;
    display(): Promise<PageImageInfo>;
    thumbnail(): Promise<PageImageInfo>;
    destroy(): void;
}
```

## Attributes

### uid

The uid of the page.



### fileIndex

The page index for the specified page in the original file.

### filter

The filter type of the specified page. 

### perspectiveQuad

The quadangle for perspective transformation in specified page. Please refer to [`Quad`](/api/enumeration-type/quad.md).

### rotation

The rotation angle of specified page. 

### mediaBox
MediaBox in the specified page. Units for left, top, width, and height are in points.

### cropBox

The crop area of the specified page. Units for left, top, width, and height are in points.

## Methods

### fileData()

Get the blob of the original file.

### raw()

Get the raw width, height, data of the specified page.

### thumbnail()

Get the width, height, data of the specified page in thumbnail view.

### display()

Get the width, height, data of the specified page in display view.

### destroy()

Destroy the page data to avoid memory leak.

## Related

- [`getPageData()`]({{ site.api }}interface/idocument/index.html#getpagedata)
- [`Rect`](/api/interface/rect.md)
- [`PageImageInfo`](/api/interface/pageimageinfo.md)
