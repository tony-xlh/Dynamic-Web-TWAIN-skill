---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer User Interface - Customize Layout
keywords: Documentation, Dynamsoft Document Viewer, User Interface, Customize Layout
breadcrumbText: Customize Layout
description: Dynamsoft Document Viewer Documentation User Interface How to Customize Layout 
permalink: /ui/customize/layout.html
---

# Layout

The default UI provided by DDV is basically a top-down layout. Taking the default desktop UI of EditViewer as an example, the header serves as the toolbar, and the main view is located below the toolbar.

![Header & main view](/assets/imgs/cuslayoutbefore.png)

## Based on the default layout

Without changing the toolbar, only changing the relative position of the toolbar and the main view, you can refer to the following steps:

- **Step one**: Refer to the default UiConfig which is listed on [Default user interface]({{ site.ui }}default_ui.html) section and reverse two elements in its children. Can use [`getDefaultUiConfig()`]({{ site.api }}namespace/ddv.html#static-getdefaultuiconfig) method,
    ```typescript
    const newUiConfig = Dynamsoft.DDV.getDefaultUiConfig("editViewer");
    newUiConfig.children.reverse();
    ```

    Or modify the default object directly.
    ```typescript
    const newUiConfig = {
            type: Dynamsoft.DDV.Elements.Layout,
            flexDirection: "column",
            className: "ddv-edit-viewer-desktop",
            children: [
                Dynamsoft.DDV.Elements.MainView,
                {
                    type: Dynamsoft.DDV.Elements.Layout,
                    className: "ddv-edit-viewer-header-desktop",
                    children: [
                        {
                            type: Dynamsoft.DDV.Elements.Layout,
                            children: [
                                Dynamsoft.DDV.Elements.ThumbnailSwitch,
                                Dynamsoft.DDV.Elements.Zoom,
                                Dynamsoft.DDV.Elements.FitMode,
                                Dynamsoft.DDV.Elements.DisplayMode,
                                Dynamsoft.DDV.Elements.RotateLeft,
                                Dynamsoft.DDV.Elements.RotateRight,
                                Dynamsoft.DDV.Elements.Crop,
                                Dynamsoft.DDV.Elements.Filter,
                                Dynamsoft.DDV.Elements.Undo,
                                Dynamsoft.DDV.Elements.Redo,
                                Dynamsoft.DDV.Elements.DeleteCurrent,
                                Dynamsoft.DDV.Elements.DeleteAll,
                                Dynamsoft.DDV.Elements.Pan,
                            ],
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
                            ],
                        },
                    ],
                },
            ],
        };
    ```
- **Step two**: Configure it when creating the new viewer.
    ```typescript
    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: newUiConfig,
    });
    ```

![Reverse header and main view](/assets/imgs/cusrevafter.png)


## Customize as you wish

Sometimes the requirements don't match the default UI layout at all, then it's also possible to completely customize the UiConfig. For example, adjust the toolbar to a sidebar, the UiConfig would be,

```typescript
const newUiConfig = {
    type: Dynamsoft.DDV.Elements.Layout,
    flexDirection: "row", // Configure the layout to be left to right
    className: "ddv-edit-viewer-desktop",
    children: [
        {
            type: Dynamsoft.DDV.Elements.Layout,
            flexDirection: "column", // Configure Elements layout to be top-down.
            style: {
                width: "46px", // Set the width of toolbar, you can also set other style configurations here.
            },
            children: [
                        Dynamsoft.DDV.Elements.ThumbnailSwitch,
                        Dynamsoft.DDV.Elements.FitMode,
                        Dynamsoft.DDV.Elements.DisplayMode,
                        Dynamsoft.DDV.Elements.RotateLeft,
                        Dynamsoft.DDV.Elements.RotateRight,
                        Dynamsoft.DDV.Elements.Crop,
                        Dynamsoft.DDV.Elements.Filter,
                        Dynamsoft.DDV.Elements.Undo,
                        Dynamsoft.DDV.Elements.Redo,
                        Dynamsoft.DDV.Elements.DeleteCurrent,
                        Dynamsoft.DDV.Elements.DeleteAll,
                        Dynamsoft.DDV.Elements.Pan,
                        Dynamsoft.DDV.Elements.Load,
                        Dynamsoft.DDV.Elements.Download,
                        Dynamsoft.DDV.Elements.Print,

            ],
        },
        Dynamsoft.DDV.Elements.MainView,
    ],
}
```

And configure the UiConfig when creating the edit viewer.

```typescript
const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "viewer",
    uiConfig: newUiConfig,
});
```

Then you will get a viewer which is shown as below.

![Change toolbar to a sidebar](/assets/imgs/cussidebar.png)

