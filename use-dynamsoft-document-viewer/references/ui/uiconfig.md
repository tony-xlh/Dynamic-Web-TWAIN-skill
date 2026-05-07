---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer User Interface - UiConfig
keywords: Documentation, Dynamsoft Document Viewer, User Interface, UiConfig
breadcrumbText: UiConfig
description: Dynamsoft Document Viewer Documentation User Interface UiConfig part
permalink: /ui/uiconfig.html
---



# UiConfig

First, we need to know how DDV creates the UI. DDV has an interface named `UiConfig`, which is used to configure the layout and the elements includes. And UiConfig can be nested to achieve a complex layout.

## Structure

Please refer to Interface [`UiConfig`]({{ site.api }}interface/uiconfig.html).

## How to configure

Take the mobile edit viewer below as the example to learn how UiConfig is configured.

![EditViewer mobile UiConfig](/assets/imgs/editmuiconfig.png)

As shown in the figure above, whole layout can be divided into three parts, header, main view and footer. 

So simply speaking, the overall UiConfig framework is roughly as follows,

```typescript
const mobileEditViewerUiConfig = {
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    className: "ddv-edit-viewer-mobile",
    children: [
        headerUiConfig,
        Dynamsoft.DDV.Elements.MainView, // the view which is used to display the pages
        footerUiConfig,
    ],
};
```

- When [`type`]({{ site.api }}interface/uiconfig.html#type) is set to `Dynamsoft.DDV.Elements.Layout` and flexDirection is `column`, it means the layout is from top to bottom.
- `Dynamsoft.DDV.Elements.MainView` is one of the default elements DDV provides. Learn more about default elements.

Next, the specific configuration of headerUiConfig, it can be seen that the icons are arranged from left to right, then


![EditViewer mobile header UiConfig](/assets/imgs/editmhuiconfig.png)


```typescript
{
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "row", // since the default value is "row", this line can be left out.
    className: "ddv-edit-viewer-header-mobile",
    children: [
        Dynamsoft.DDV.Elements.ThumbnailSwitch,
        Dynamsoft.DDV.Elements.Pagination,
        Dynamsoft.DDV.Elements.Download,
    ],
}
```


Also can know the footerUiConfig is as follows,

![EditViewer mobile footer UiConfig](/assets/imgs/editmfuiconfig.png)

```typescript
{
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "row", // since the default value is "row", this line can be left out.
    className: "ddv-edit-viewer-footer-mobile",
    children: [
        Dynamsoft.DDV.Elements.DisplayMode,
        Dynamsoft.DDV.Elements.RotateLeft,
        Dynamsoft.DDV.Elements.Crop,
        Dynamsoft.DDV.Elements.Filter,
        Dynamsoft.DDV.Elements.Undo,
        Dynamsoft.DDV.Elements.Delete,
        Dynamsoft.DDV.Elements.Load,
    ],
}
```

Combining these three parts creates the overall user interface layout.

```typescript
const mobileEditViewerUiConfig = {
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "column",
    className: "ddv-edit-viewer-mobile",
    children: [
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-edit-viewer-header-mobile",
            children: [
                Dynamsoft.DDV.Elements.ThumbnailSwitch,
                Dynamsoft.DDV.Elements.Pagination,
                Dynamsoft.DDV.Elements.Download,
            ],
        },
        Dynamsoft.DDV.Elements.MainView,
        {
            type: Dynamsoft.DDV.Elements.Layout,
            className: "ddv-edit-viewer-footer-mobile",
            children: [
                Dynamsoft.DDV.Elements.DisplayMode,
                Dynamsoft.DDV.Elements.RotateLeft,
                Dynamsoft.DDV.Elements.Crop,
                Dynamsoft.DDV.Elements.Filter,
                Dynamsoft.DDV.Elements.Undo,
                Dynamsoft.DDV.Elements.Delete,
                Dynamsoft.DDV.Elements.Load,
            ],
        },
    ],
};
```
