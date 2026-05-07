---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface StampStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface StampStyle
breadcrumbText: Interface StampStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface StampStyle Page
permalink: /api/interface/annotationinterface/stampstyle.html
---

# StampStyle

## Syntax

```typescript
interface StampStyle {
    opacity?: number;
    stamp?: EnumStampIcon | Blob;
}
```

## Attributes

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1. 

Default value: 1

### stamp

Specify the standard business stamp or the blob of a custom image to be drawn. Please refer to [`EnumStampIcon`]({{ site.api }}enumeration-type/enumstampicon.html) for standard business stamp.

Default value: `Dynamsoft.DDV.EnumStampIcon.DRAFT`

If set to `blob`, the custom image will be added as the stamp.

Supported image formats: PNG, JPEG

## Related

- [`EditViewerConstructorOptions`]({{ site.api }}interface/editviewerconstructoroptions.html)