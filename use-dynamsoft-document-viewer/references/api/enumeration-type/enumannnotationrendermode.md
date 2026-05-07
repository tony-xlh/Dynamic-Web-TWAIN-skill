---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Enumeration EnumAnnotationRenderMode
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Enumeration EnumAnnotationRenderMode
breadcrumbText: Enumeration EnumAnnotationRenderMode
description: Dynamsoft Document Viewer Documentation API Reference Enumeration EnumAnnotationRenderMode Page
permalink: /api/enumeration-type/enumannotationrendermode.html
---

# EnumAnnotationRenderMode

```typescript
enum EnumAnnotationRenderMode {
    NO_ANNOTATIONS = "noAnnotations", // default, means that the annotations in the PDF file will not be loaded
    RENDER_ANNOTATIONS = "renderAnnotations", // means that the annotations in the PDF file will be rendered
    LOAD_ANNOTATIONS = "loadAnnotations", // means that the annotations in the PDF file will be loaded normally, a valid PDF Annotation license is requested
}
```
