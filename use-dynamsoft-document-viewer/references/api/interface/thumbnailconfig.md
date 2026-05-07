---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface ThumbnailConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface ThumbnailConfig
breadcrumbText: Interface ThumbnailConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface ThumbnailConfig Page
permalink: /api/interface/thumbnailconfig.html
---

# ThumbnailConfig

## Syntax

```typescript
interface ThumbnailConfig extends BrowseViewerConfig {
    position?: string; 
    size?: string; 
    visibility?: string; 
}
```

## Extends

[`BrowseViewerConfig`]({{ site.api }}interface/browseviewerconfig.html)

## Attributes

### position

Specify the position of the thumbnail view box displayed on the main eidt viewer.

Supported value: `left`, `right`, `top`, `bottom`

Default value: `left`

**Remark**

If you see a blank display after importing images, it is because the size is too small and rows&columns exceeds, please adjust the [`size`](#size) or [`rows`]({{ site.api }}interface/browseviewerconfig.html#rows)&[`columns`]({{ site.api }}interface/browseviewerconfig.html#columns).

### size

Specify the width or height of thumbnail. Supports unit `px` or `%`, for example, `"100px"` or `"10%"`.

**Remark**

- When `position` is set to `left` or `right`, `size` means the width of thumbnail.
- When `position` is set to `top` or `bottom`, `size` means the height of thumbnail.

### visibility

Specify whether to show the thumbnail when an edit viewer is created and shown. 

Supported value: `hidden`, `visible`

Default value: `hidden`

## Related

- [`EditViewerConstructorOptions`]({{ site.api }}interface/editviewerconstructoroptions.html)
