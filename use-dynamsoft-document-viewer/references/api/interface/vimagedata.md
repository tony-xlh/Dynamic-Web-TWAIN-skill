---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface VImageData
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface VImageData
breadcrumbText: Interface VImageData
description: Dynamsoft Document Viewer Documentation API Reference Interface VImageData Page
permalink: /api/interface/vimagedata.html
---

# VImageData

## Syntax

```typescript
interface VImageData {
    type: EnumImageDataType;
    data: ArrayBuffer | Blob; 
    height?: number;
    width?: number;
}
```

## Attributes

### type

The image data type. Please refer to [`EnumImageDataType`]({{ site.api }}enumeration-type/enumimagedatatype.html)

### data

The image data. ***Do not destroy it.***

### height

The image height. 

### width

The image width.