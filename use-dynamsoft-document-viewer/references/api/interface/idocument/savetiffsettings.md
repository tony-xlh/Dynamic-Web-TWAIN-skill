---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface SaveTiffSettings
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface SaveTiffSettings
breadcrumbText: Interface SaveTiffSettings
description: Dynamsoft Document Viewer Documentation API Reference Interface SaveTiffSettings Page
permalink: /api/interface/idocument/savetiffsettings.html
---

# SaveTiffSettings

## Syntax

```typescript
interface SaveTiffSettings {
    customTag?: CustomTag[];
    compression?: EnumTIFFCompressionType;
    quality?: number;
    saveAnnotation?: boolean; 
}
```

## Attributes

### customTag

Custom tiff tag(s). Please refer to [CustomTag]({{ site.api }}interface/idocument/customtag.html)

### compression

Specify the compression type. Please refer to [EnumTiffCompressionType]({{ site.api }}enumeration-type/enumtiffcompressiontype.html).

Default value: `TIFF_AUTO`

### quality

Specify the quality of the images in the file. The value ranges from 0 to 100. Only valid when the [`compression`](#compression) is `TIFF_JPEG`.

### saveAnnotation

Whether to save the annotation(s) as the part of image. Default vaule: `false`.

## Related

- [`saveToTiff()`]({{ site.api }}interface/idocument/index.html#savetotiff)