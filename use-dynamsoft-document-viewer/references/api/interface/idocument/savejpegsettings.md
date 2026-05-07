---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface SaveJpegSettings
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface SaveJpegSettings
breadcrumbText: Interface SaveJpegSettings
description: Dynamsoft Document Viewer Documentation API Reference Interface SaveJpegSettings Page
permalink: /api/interface/idocument/savejpegsettings.html
---

# SaveJpegSettings

## Syntax

```typescript
interface SaveJpegSettings {
    quality?: number; 
    saveAnnotation?: boolean; 
}
```

## Attributes

### quality

Specify the quality for JPEG compression. The value range is [0, 100], default value is 80.

### saveAnnotation

Whether to save the annotation(s) as the part of image. Default vaule: `false`.

## Related

- [`saveToJpeg()`]({{ site.api }}interface/idocument/index.html#savetojpeg)