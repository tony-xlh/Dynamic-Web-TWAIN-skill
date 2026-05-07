---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface PerspectiveViewerConstructorOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface PerspectiveViewerConstructorOptions
breadcrumbText: Interface PerspectiveViewerConstructorOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface PerspectiveViewerConstructorOptions Page
permalink: /api/interface/perspectiveviewerconstructoroptions.html
---

# PerspectiveViewerConstructorOptions

## Syntax

```typescript
interface PerspectiveViewerConstructorOptions {
    container?: string | HTMLElement;
    viewerConfig?: PerspectiveViewerConfig; // The configurations of viewer, such as page style, minZoom, maxZoom and so on.
    uiConfig?: UiConfig; // The UI layout configurations.
    groupUid?: string; //The uid of viewer's group, if it is not set, a random groupUid will generate.
}
```

## Attributes

### container

The container which is used to show the viewer. Its `id` or `HTMLElement` is acceppted.

### viewerConfig

The configurations of viewer, please refer to [`PerspectiveViewerConfig`]({{ site.api }}interface/perspectiveviewerconfig.html). If it is not specified, the [default configuration]({{ site.viewer }}viewerconfig.html#perspectiveviewerconfig) will be applied.

### uiConfig

The UI layout configurations of viewer, please refer to [`UiConfig`]({{ site.api }}interface/uiconfig.html). If it is not specified, the [default UI]({{ site.ui }}default_ui.html#perspective-viewer) will be applied.

### groupUid

The uid of viewers' group. If it is not specified, a random groupUid will be generated.

{% comment %} Please refer to [Data synchronisation between viewers]({{ site.features }}viewers/datasync.html). {% endcomment %}

## Related

- [`PerspectiveViewer()`]({{ site.api }}class/perspectiveviewer.html#perspectiveviewer)