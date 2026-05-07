---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Perspective Viewer
keywords: Documentation, Dynamsoft Document Viewer, Features, Perspective Viewer
breadcrumbText: Perspective Viewer
description: Dynamsoft Document Viewer Documentation Features, Perspective Viewer
permalink: /features/viewers/perspectiveviewer.html
---

# Perspective Viewer

Perspective Viewer is used to do page boundaries manual adjustment & perspective transformation. The page data displayed on this viewer is its original data.

- [Default user interface]({{ site.ui }}default_ui.html#perspective-viewer)
- [Default viewer configuration]({{ site.viewer }}viewerconfig.html#perspective-viewer)

```typescript
const perspectiveViewer = new Dynamsoft.DDV.PerspectiveViewer({
    container: document.getElementById("viewer"),
});

perspectiveViewer.openDocument("docUid"); // Open a document which has pages
```

## Quadrilateral selection

Quadrilateral Selection in the perspective viewer means the selection which will be perspective transformed.

![Quad selection](/assets/imgs/quadselection.png)

In addition to drawing and adjusting the selection through the UI, DDV also provides some additional interfaces to operate the selection.

- Set a quadrilateral selection on the current page by using [`setQuadSelection()`]({{ site.api }}class/perspectiveviewer.html#setquadselection). If the selection is exceeds the bounds of the current page, it won't take effect.

    ```typescript
    const quad = [
        [314,518],
        [2200,625],
        [2204,3339],
        [176,3048]
    ];

    perspectiveViewer.setQuadSelection(quad);
    ```

- Obtain the coordinates of the four vertices of the quadrilateral selection by using [`getQuadSelection()`]({{ site.api }}class/perspectiveviewer.html#getquadselection). It returns an array of the four corner coordinates of the quadrilateral selection.

    ```typescript
    const quad = perspectiveViewer.getQuadSelection();
    ```

- Reset the quadrilateral selection to the original one by using [`resetQuadSelection()`]({{ site.api }}class/perspectiveviewer.html#resetquadselection). The original selection on the page can be detected by [Document Detect]({{ site.features }}advanced/documentdetect.html) during capturing in the capture viewer or set by [`ExtraPageData`]({{ site.api }}interface/idocument/extrapagedata.html) in [`loadSource()`]({{ site.api }}interface/idocument/index.html#loadsource) when loading the page. If it is not detected or set before, the original selection would be the whole page range.

    ```typescript
    perspectiveViewer.resetQuadSelection();
    ```

## Perspective transformation

Perspective transformation in the perspective viewer is to rectify the quadrilateral selection. It is implemented by the method [`applyPerspective()`]({{ site.api }}class/perspectiveviewer.html#applyperspective).

```typescript
const quad = perspectiveViewer.getQuadSelection();
await perspectiveViewer.applyPerspective(quad);
```

