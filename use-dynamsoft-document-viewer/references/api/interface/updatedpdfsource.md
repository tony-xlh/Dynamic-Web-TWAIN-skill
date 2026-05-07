---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface UpdatedPdfSource
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface UpdatedPdfSource
breadcrumbText: Interface UpdatedPdfSource
description: Dynamsoft Document Viewer Documentation API Reference Interface UpdatedPdfSource Page
---

# UpdatedPdfSource

## Syntax

```typescript
interface UpdatedPdfSource {
    fileData: Blob;
    fileIndex?: number;
    convertMode: EnumConvertMode;
    password?: string;
    renderOptions?: {
      renderAnnotations?: EnumAnnotationRenderMode;
      resolution?: number;
      maxWidth?: number;
      maxHeight?: number;
      renderGrayscale?: boolean;
    };
}
```
