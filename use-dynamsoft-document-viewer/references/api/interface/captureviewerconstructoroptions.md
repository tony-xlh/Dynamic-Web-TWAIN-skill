---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface CaptureViewerConstructorOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface CaptureViewerConstructorOptions
breadcrumbText: Interface CaptureViewerConstructorOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface CaptureViewerConstructorOptions Page
permalink: /api/interface/captureviewerconstructoroptions.html
---

# CaptureViewerConstructorOptions

## Syntax

```typescript
interface CaptureViewerConstructorOptions {
    container?: string | HTMLElement;
    keyboardInteractionConfig?: KeyboardInteractionConfig;
    viewerConfig?: CaptureViewerConfig;
    uiConfig?: UiConfig;
    groupUid?: string;
}
```

## Attributes

### container

The container which is used to show the viewer. Its `id` or `HTMLElement` is accepted.

### keyboardInteractionConfig

This configures the use of keyboard shortcuts for the viewer - please see [`KeyboardInteractionConfig`]({{ site.api }}interface/keyboardinteractionconfig.html) for details. If not specified, all keyboard shortcuts are disabled by default.

### viewerConfig

The configurations of viewer, please refer to [`CaptureViewerConfig`]({{ site.api }}interface/captureviewerconfig.html). If it is not specified, the [default configuration]({{ site.viewer }}viewerconfig.html#captureviewerconfig) will be applied.

### uiConfig

The UI layout configurations of viewer, please refer to [`UiConfig`]({{ site.api }}interface/uiconfig.html). If it is not specified, the [default UI]({{ site.ui }}default_ui.html#capture-viewer) will be applied.

### groupUid

The uid of viewers' group. If it is not specified, a random groupUid will be generated.

{% comment %} Please refer to [Data synchronisation between viewers]({{ site.features }}viewers/datasync.html). {% endcomment %}

## Related

- [`CaptureViewer()`]({{ site.api }}class/captureviewer.html#captureviewer)
