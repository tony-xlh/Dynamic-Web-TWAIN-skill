---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface PerspectiveViewerConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface PerspectiveViewerConfig
breadcrumbText: Interface PerspectiveViewerConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface PerspectiveViewerConfig Page
permalink: /api/interface/perspectiveviewerconfig.html
---

# PerspectiveViewerConfig

## Syntax

```typescript
interface PerspectiveViewerConfig {
    canvasStyle?: CanvasStyle;
    pageStyle?: BaseStyle;
    quadSelectionStyle?: QuadSelectionStyle;
    enableLoadSourceByDrag?: boolean;
    enableMagnifier?: boolean;
    enableSlide?: boolean;
    scrollToLatest?: boolean;
}
```

## Attributes

### canvasStyle

The style of canvas of the viewer. Please refer to [`CanvasStyle`]({{ site.api }}interface/styleinterface/canvasstyle.html).

### pageStyle

The style of displayed page in the viewer. Please refer to [`BaseStyle`]({{ site.api }}interface/styleinterface/basestyle.html).

### quadSelectionStyle

The style of quadrilateral selection. Please refer to [`QuadSelectionStyle`]({{ site.api }}interface/styleinterface/quadselectionstyle.html).

### enableLoadSourceByDrag

Enables loading files by dragging them into the Viewer.

Default value: `true`

### enableMagnifier

Specifies whether or not to display a corner magnifier on the canvas. This feature is primarily used to provide a zoomed-in preview of the selected area for more precise adjustments.

Default value: `true`

### enableSlide

Specifies whether or not to allow to slide the pages.

### scrollToLatest

Specifies whether or not to scroll to latest page automatically when importing new pages.

Default value: `false`


## Related

- [`PerspectiveViewerConstructorOptions`]({{ site.api }}interface/perspectiveviewerconstructoroptions.html)