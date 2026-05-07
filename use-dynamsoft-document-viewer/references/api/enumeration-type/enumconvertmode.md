---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Enumeration EnumConvertMode
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Enumeration EnumConvertMode
breadcrumbText: Enumeration EnumConvertMode
description: Dynamsoft Document Viewer Documentation API Reference Enumeration EnumConvertMode Page
permalink: /api/enumeration-type/enumconvertmode.html
---

# EnumConvertMode

This enumeration defines how the PDF is loaded. It affects whether PDF elements like text layers are loaded and the image for display and saving.

```typescript
enum EnumConvertMode {
    /** Render the pages. */
    CM_RENDERALL = "cm/renderall",
    /** Extract the images. */
    CM_IMAGEONLY = "cm/imageonly",
    /** Automatically decide which mode to use based on whether there is only one image object in the page */
    CM_AUTO = "cm/auto",
}
```
