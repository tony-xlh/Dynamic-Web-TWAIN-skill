---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface EditViewerConstructorOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface EditViewerConstructorOptions
breadcrumbText: Interface EditViewerConstructorOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface EditViewerConstructorOptions Page
permalink: /api/interface/editviewerconstructoroptions.html
---

# EditViewerConstructorOptions

## Syntax

```typescript
interface EditViewerConstructorOptions {
    container?: string | HTMLElement;
    viewerConfig?: EditViewerConfig;
    uiConfig?: UiConfig;
    thumbnailConfig?: ThumbnailConfig;
    annotationConfig?: AnnotationConfig;
    keyboardInteractionConfig?: KeyboardInteractionConfig;
    groupUid?: string;
}
```

## Attributes

### container

The container which is used to show the viewer. Its `id` or `HTMLElement` is acceppted.

### viewerConfig

The configurations of viewer, please refer to [`EditViewerConfig`](/api/interface/editviewerconfig.md). If it is not specified, the [default configuration]({{ site.viewer }}viewerconfig.html#editviewerconfig) will be applied.

### uiConfig

The UI layout configurations of viewer, please refer to [`UiConfig`]({{ site.api }}interface/uiconfig.html). If it is not specified, the [default UI]({{ site.ui }}default_ui.html#edit-viewer) will be applied.

### thumbnailConfig

The configurations of integrated thumbnail, please refer to [`ThumbnailConfig`]({{ site.api }}interface/thumbnailconfig.html). If it is not specified, the [default configuration]({{ site.viewer }}viewerconfig.html#thumbnailconfig) will be applied.

### annotationConfig

The configurations of annotation part in the viewer, please refer to [`AnnotationConfig`]({{ site.api }}interface/annotationconfig.html). If it is not specified, the [default configuration]({{ site.viewer }}viewerconfig.html#annotationconfig) will be applied.

### keyboardInteractionConfig

This configures the use of keyboard shortcuts for the viewer - please see [`KeyboardInteractionConfig`]({{ site.api }}interface/keyboardinteractionconfig.html) for details. If not specified, all keyboard shortcuts are disabled by default.

### groupUid

The uid of viewers' group. If it is not specified, a random groupUid will be generated.

{% comment %} Please refer to [Data synchronisation between viewers]({{ site.features }}viewers/datasync.html). {% endcomment %}

## Related

- [`EditViewer()`]({{ site.api }}class/editviewer.html#editviewer)
