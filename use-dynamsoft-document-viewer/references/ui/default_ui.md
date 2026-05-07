---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer User Interface - Default Elements
keywords: Documentation, Dynamsoft Document Viewer, User Interface, Default Elements
breadcrumbText: Default User Interface
description: Dynamsoft Document Viewer Documentation User Interface Default Elements part
permalink: /ui/default_ui.html
---

# Default User Interface

It can be seen from Viewers part, DDV provides the default UI design for the edit viewer, capture viewer and perspective viewer. They basically contain the main features of each type of viewer. 

<div class="multi-panel-switching-prefix"></div>

- [Edit viewer](#edit-viewer)
- [Capture viewer](#capture-viewer)
- [Perspective viewer](#perspective-viewer)
- [Browse viewer](#browse-viewer)

<div class="multi-panel-start"></div>

## Edit viewer

### Mobile

Default UiConfig:

```typescript
{
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    className: "ddv-edit-viewer-mobile",
    children: [
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-edit-viewer-header-mobile",
            children: [
                Dynamsoft.DDV.Elements.Blank,
                Dynamsoft.DDV.Elements.AnnotationSet,
                Dynamsoft.DDV.Elements.Pagination,
                Dynamsoft.DDV.Elements.Download,
                Dynamsoft.DDV.Elements.TextSearchPanelSwitch
            ]
        },
        {
        type: Dynamsoft.DDV.Elements.Layout,
        flexDirection:"column",
        children:[
            Dynamsoft.DDV.Elements.MainView,
            {
                type: Dynamsoft.DDV.Elements.TextSearchPanel,
                className: "ddv-edit-viewer-search-mobile"
            }
        ]
        },
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-edit-viewer-footer-mobile",
            children: [
                Dynamsoft.DDV.Elements.DisplayMode,
                Dynamsoft.DDV.Elements.RotateLeft,
                Dynamsoft.DDV.Elements.Crop,
                Dynamsoft.DDV.Elements.Undo,
                Dynamsoft.DDV.Elements.Delete,
                Dynamsoft.DDV.Elements.Load
            ]
        }
    ]
}
```

![Default mobile EditViewer UI](/assets/imgs/edit-viewer-mobile-3.0.jpg)

### Desktop

Default UiConfig:

```typescript
{
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    className: "ddv-edit-viewer-desktop",
    children: [
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-edit-viewer-header-desktop",
            children: [{
                    type: Dynamsoft.DDV.Elements.Layout,
                    enableScroll:true,
                    children: [
                        Dynamsoft.DDV.Elements.ThumbnailSwitch,
                        Dynamsoft.DDV.Elements.Zoom,
                        Dynamsoft.DDV.Elements.FitMode,
                        Dynamsoft.DDV.Elements.DisplayMode,
                        Dynamsoft.DDV.Elements.RotateLeft,
                        Dynamsoft.DDV.Elements.RotateRight,
                        Dynamsoft.DDV.Elements.Crop,
                        Dynamsoft.DDV.Elements.Undo,
                        Dynamsoft.DDV.Elements.Redo,
                        Dynamsoft.DDV.Elements.DeleteCurrent,
                        Dynamsoft.DDV.Elements.DeleteAll,
                        Dynamsoft.DDV.Elements.Pan,
                        Dynamsoft.DDV.Elements.TextSelectionMode,
                        Dynamsoft.DDV.Elements.SeparatorLine,
                        Dynamsoft.DDV.Elements.AnnotationSet,
                    ]
                },
                {
                    type: Dynamsoft.DDV.Elements.Layout,
                    children: [
                        {
                            type: Dynamsoft.DDV.Elements.Pagination,
                            className: "ddv-edit-viewer-pagination-desktop",
                        },
                        Dynamsoft.DDV.Elements.Load,
                        Dynamsoft.DDV.Elements.Download,
                        Dynamsoft.DDV.Elements.Print,
                        Dynamsoft.DDV.Elements.TextSearchPanelSwitch
                    ]
                }
            ]
        },
        {
            type:Dynamsoft.DDV.Elements.Layout,
            flexDirection:"row",
            children:[
                Dynamsoft.DDV.Elements.MainView,
                Dynamsoft.DDV.Elements.TextSearchPanel
            ]
        }
    ]
}
```

![Default desktop EditViewer UI](/assets/imgs/edit-viewer-3.0.jpg)

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

## Capture viewer

### Mobile

Default UiConfig:

```typescript
{
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    children: [
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-capture-viewer-header-mobile",
            children: [
                {
                    type: Dynamsoft.DDV.Elements.CameraResolution,
                    className: "ddv-capture-viewer-resolution",
                },
                Dynamsoft.DDV.Elements.Flashlight,
            ],
        },
        Dynamsoft.DDV.Elements.MainView,
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-capture-viewer-footer-mobile",
            children: [
                Dynamsoft.DDV.Elements.AutoDetect,
                Dynamsoft.DDV.Elements.AutoCapture,
                {
                    type: Dynamsoft.DDV.Elements.Capture,
                    className: "ddv-capture-viewer-captureButton",
                },
                Dynamsoft.DDV.Elements.ImagePreview,
                Dynamsoft.DDV.Elements.CameraConvert,
            ],
        },
    ],
};
```

![Default mobile CaptureViewer UI](/assets/imgs/dmcaptureui.png)

### Desktop

Default UiConfig:

```typescript
{
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    className: "ddv-capture-viewer-desktop",
    children: [
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-capture-viewer-header-desktop",
            children: [
                {
                    type: Dynamsoft.DDV.Elements.CameraResolution,
                    className: "ddv-capture-viewer-resolution-desktop",
                },
                Dynamsoft.DDV.Elements.AutoDetect,
                {
                    type: Dynamsoft.DDV.Elements.Capture,
                    className: "ddv-capture-viewer-capture-desktop",
                },
                Dynamsoft.DDV.Elements.AutoCapture,
            ],
        },
        Dynamsoft.DDV.Elements.MainView,
        {
            type: Dynamsoft.DDV.Elements.ImagePreview,
            className: "ddv-capture-viewer-image-preview-desktop",
        },
    ],
};
```

![Default desktop CaptureViewer UI](/assets/imgs/ddcaptureui.png)

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

## Perspective viewer

### Mobile

Default UiConfig:

```typescript
{
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    children: [
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-perspective-viewer-header-mobile",
            children: [
                Dynamsoft.DDV.Elements.Blank,
                Dynamsoft.DDV.Elements.Pagination,
                Dynamsoft.DDV.Elements.PerspectiveAll,
            ],
        },
        Dynamsoft.DDV.Elements.MainView,
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-perspective-viewer-footer-mobile",
            children: [
                Dynamsoft.DDV.Elements.FullQuad,
                Dynamsoft.DDV.Elements.RotateLeft,
                Dynamsoft.DDV.Elements.RotateRight,
                Dynamsoft.DDV.Elements.DeleteCurrent,
                Dynamsoft.DDV.Elements.DeleteAll,
            ],
        },
    ],
};
```

![Default mobile PerspectiveViewer UI](/assets/imgs/dmperui.png)

### Desktop

Default UiConfig:

```typescript
{
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    children: [
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-perspective-viewer-header-desktop",
            children: [
                Dynamsoft.DDV.Elements.FullQuad,
                Dynamsoft.DDV.Elements.RotateLeft,
                Dynamsoft.DDV.Elements.RotateRight,
                Dynamsoft.DDV.Elements.DeleteCurrent,
                Dynamsoft.DDV.Elements.DeleteAll,
                {
                    type: Dynamsoft.DDV.Elements.Pagination,
                    className: "ddv-perspective-viewer-pagination-desktop",
                },
                {
                    type: Dynamsoft.DDV.Elements.PerspectiveAll,
                    className: "ddv-perspective-viewer-perspective-desktop",
                },
            ],
        },
        Dynamsoft.DDV.Elements.MainView,
    ],
};
```

![Default desktop PerspectiveViewer UI](/assets/imgs/ddperui.png)

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

## Browse viewer

Default UiConfig:

```typescript
{
    type: Dynamsoft.DDV.Elements.Layout,
    children: [
        Dynamsoft.Dynamsoft.DDV.Elements.MainView,
    ],
};
```

<div class="multi-panel-end"></div>

<div class="multi-panel-switching-end"></div>







