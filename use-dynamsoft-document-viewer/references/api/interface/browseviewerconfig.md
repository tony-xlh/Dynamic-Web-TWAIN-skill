---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface BrowseViewerConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface BrowseViewerConfig
breadcrumbText: Interface BrowseViewerConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface BrowseViewerConfig Page
permalink: /api/interface/browseviewerconfig.html
---

# BrowseViewerConfig

## Syntax

```typescript
interface BrowseViewerConfig {
    canvasStyle?: CanvasStyle;
    pageStyle?: BaseStyle;
    currentPageStyle?: BaseStyle;
    selectedPageStyle?: BaseStyle;
    hoveredPageStyle?: BaseStyle;
    placeholderStyle?: BaseStyle;
    pageNumberStyle?: PageNumberStyle;
    checkboxStyle?: CheckboxStyle;
    rows?: number;
    columns?: number;
    multiselectMode?: boolean; 
    scrollToLatest?: boolean;
    enableDragPage?: boolean;
    enableLoadSourceByDrag?: boolean;
    enableAutoScrollForDragPages?: boolean;
    scrollDirection?: string;
}
```

## Attributes

### canvasStyle

The style of canvas of the viewer. Please refer to [`CanvasStyle`]({{ site.api }}interface/styleinterface/canvasstyle.html).

### pageStyle

The style of displayed page in the viewer. Please refer to [`BaseStyle`]({{ site.api }}interface/styleinterface/basestyle.html).

### currentPageStyle

The style of current page in the viewer. Please refer to [`BaseStyle`]({{ site.api }}interface/styleinterface/basestyle.html).

### selectedPageStyle

The style of selected page in the viewer. Please refer to [`BaseStyle`]({{ site.api }}interface/styleinterface/basestyle.html).

### hoveredPageStyle

The style of the page which is hovered by mouse pointer in the viewer. Please refer to [`BaseStyle`]({{ site.api }}interface/styleinterface/basestyle.html).

### placeholderStyle

The style of the placeholder when the page is dragged. Please refer to [`BaseStyle`]({{ site.api }}interface/styleinterface/basestyle.html).

### pageNumberStyle

The style of page number. Please refer to [`PageNumberStyle`]({{ site.api }}interface/styleinterface/pagenumberstyle.html).

### checkboxStyle

The style of checkbox. Please refer to [`CheckboxStyle`]({{ site.api }}interface/styleinterface/checkboxstyle.html).

### rows

The number of rows. The maximum value is 20.

### columns

The number of columns. The maximum value is 20.

### multiselectMode

Specify whether to allow multiple pages to be selected at once.

Default value: `false`

### scrollToLatest

Specify whether to scroll to latest page automatically when importing new pages.

Default value: `false`

### enableDragPage

Specify whether to allow drag&drop page feature in the viewer.

Default value: `true`

### enableLoadSourceByDrag

Enables loading files by dragging them into the Viewer.

Default value: `true`

### enableAutoScrollForDragPages

Specify whether to enable auto scrolling when dragging pages if the cursor is around the edges of the viewer. 

Default value: `true`


### scrollDirection

Specify the scroll direction, supported values are `vertical`, `horizontal`.

Default value: `vertical`

![scrollDirection BrowseViewer](/assets/imgs/scrollDirection-browse.png)

## Remark

- If you see a blank display after importing images, it is because the container size is too small and rows&columns exceeds, please adjust the container size or [`rows`](#rows)&[`columns`](#columns).

## Related

- [`BrowseViewerConstructorOptions`]({{ site.api }}interface/browseviewerconstructoroptions.html)
