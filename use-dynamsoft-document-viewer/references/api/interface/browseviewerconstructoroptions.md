---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface BrowseViewerConstructorOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface BrowseViewerConstructorOptions
breadcrumbText: Interface BrowseViewerConstructorOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface BrowseViewerConstructorOptions Page
permalink: /api/interface/browseviewerconstructoroptions.html
---

# BrowseViewerConstructorOptions

## Syntax

```typescript
interface BrowseViewerConstructorOptions {
    container?: string | HTMLElement;
    keyboardInteractionConfig?: KeyboardInteractionConfig;
    viewerConfig?: BrowseViewerConfig;
    uiConfig?: UiConfig; 
    groupUid?: string;
}
```

## Attributes

### container

The container which is used to show the viewer. Its `id` or `HTMLElement` is acceppted.

### keyboardInteractionConfig

This configures the use of keyboard shortcuts for the viewer - please see [`KeyboardInteractionConfig`]({{ site.api }}interface/keyboardinteractionconfig.html) for details. If not specified, all keyboard shortcuts are disabled by default. **Note**: editing shortcuts do not have any effect on the Browse viewer.

### viewerConfig

The configurations of viewer, please refer to [`BrowseViewerConfig`](/api/interface/browseviewerconfig.md). If it is not specified, the [default configuration]({{ site.viewer }}viewerconfig.html#browseviewerconfig) will be applied.

### uiConfig

The UI layout configurations of viewer, please refer to [`UiConfig`]({{ site.api }}interface/uiconfig.html). If it is not specified, the [default UI]({{ site.ui }}default_ui.html#browse-viewer) will be applied.

### groupUid

The uid of viewers' group. If it is not specified, a random groupUid will be generated.

{% comment %} Please refer to [Data synchronisation between viewers]({{ site.features }}viewers/datasync.html). {% endcomment %}

## Related

- [`BrowseViewer()`]({{ site.api }}class/browseviewer.html#browseviewer)
