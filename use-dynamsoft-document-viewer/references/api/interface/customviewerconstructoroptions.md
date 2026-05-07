---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface CustomViewerConstructorOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface CustomViewerConstructorOptions
breadcrumbText: Interface CustomViewerConstructorOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface CustomViewerConstructorOptions Page
permalink: /api/interface/customviewerconstructoroptions.html
---

# CustomViewerConstructorOptions

## Syntax

```typescript
interface CustomViewerConstructorOptions {
    container?: string | HTMLElement;
    uiConfig?: UiConfig;
}
```

## Attributes

### container

The container which is used to show the viewer. Its `id` or `HTMLElement` is acceppted.

### uiConfig

The UI layout configurations of viewer, please refer to [`UiConfig`]({{ site.api }}interface/uiconfig.html).

## Related

- [`CustomViewer()`]({{ site.api }}class/customviewer.html#customviewer)
