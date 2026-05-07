---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer User Interface - Viewer Config
keywords: Documentation, Dynamsoft Document Viewer, Viewer, Viewer Config
breadcrumbText: UiConfig
description: Dynamsoft Document Viewer Documentation Viewer Config part
permalink: /viewer/viewerconfig.html
---

# Viewer Config

The viewer configurations and styles are configured by `viewerConfig` when creating the viewer.

## Structure

Each viewer class has its own `viewerConfig` structure. Please refer to the links below and check the details.

- [`EditViewerConfig`]({{ site.api }}interface/editviewerconfig.html)
- [`ThumbnailConfig`]({{ site.api }}interface/thumbnailconfig.html)
- [`AnnotationConfig`]({{ site.api }}interface/annotationconfig.html)
- [`CaptureViewerConfig`]({{ site.api }}interface/captureviewerconfig.html)
- [`PerspectiveViewerConfig`]({{ site.api }}interface/perspectiveviewerconfig.html)
- [`BrowseViewerConfig`]({{ site.api }}interface/browseviewerconfig.html)

*`CustomViewer` does not have `viewerConfig`.*

{% comment %} 
Take `EditViewerConfig` as example, we can configure some styles of the viewer and configurations of the viewer.

```typescript
interface EditViewerConfig {
    canvasStyle?: CanvasStyle;
    pageStyle?: BaseStyle;
    quadSelectionStyle?: QuadSelectionStyle;
    enableSlide?: boolean; 
    scrollToLatest?: boolean; 
    scrollDirection?: string; 
    minZoom?: number; 
    maxZoom?: number; 
}
```

{% endcomment %}

## Default viewerConfig

DDV will provide the default viewerConfig for each viewer.

<div class="multi-panel-switching-prefix"></div>

- [Edit viewer](#edit-viewer)
- [Thumbnail](#thumbnail)
- [Annotation](#annotation)
- [Capture viewer](#capture-viewer)
- [Perspective viewer](#perspective-viewer)
- [Browse viewer](#browse-viewer)

<div class="multi-panel-start"></div>

### EditViewerConfig

```typescript
{
    canvasStyle: {
        background: "#e2e1de",
        cursor: "default",
    },
    pageStyle: {
        background: "#fff",
        border: "1px solid #707070",
    },
    currentPageStyle: {
        background: "",
        border: "",
    },
    quadSelectionStyle: {
        background: "rgba(255,255,255,0)",
        border: "2px solid #fe8e14",
        ctrlBackground: "#fe8e14",
        ctrlBorder: "2px solid #fe8e14",
        ctrlBorderRadius: "50%",
        ctrlHeight: "15px",
        ctrlWidth: "15px",
        invalidBorderColor: "red",
        invalidCtrlBorderColor: "red",
    },
    minZoom: 0.01,
    maxZoom: 64,
    scrollDirection: "vertical",
    enableSlide: true,
    scrollToLatest: false,
};
```

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

### ThumbnailConfig

#### Mobile

```typescript
{
    canvasStyle: {
        background: "#4B4B4B",
        cursor: "default",
    },
    currentPageStyle: {
        border: "4px solid #fe8e14",
    },
    pageStyle: {
        border: "8px solid rgba(0,0,0,0)",
        background: "rgba(255,255,255,0)",
    },
    selectedPageStyle: {
        border: "6px solid #AAAAAA",
        background: "#AAAAAA",
    },
    hoveredPageStyle: {
        border: "6px solid #AAAAAA",
        background: "#AAAAAA",
    },
    placeholderStyle: {
        border: "6px solid rgba(136,136,136,0.2)",
        background: "rgba(136,136,136,0.2)",
    },
    pageNumberStyle: {
        background: "rgba(255,255,255,0)",
        border: "0px solid #000",
        borderRadius: "0px",
        bottom: "3px",
        color: "white",
        fontFamily: "Open Sans",
        fontSize: "14px",
        height: "24px",
        left: "50%",
        onPage: false,
        opacity: 1,
        right: "",
        top: "",
        translateX: "-50%",
        translateY: "0px",
        visibility: "visible",
        width: "32px",
    },
    checkboxStyle: {
        background: "#fff",
        border: "2px solid #999999",
        borderRadius: "0px",
        bottom: "",
        checkMarkColor: "#FE8E14",
        checkMarkLineWidth: "2px",
        height: "16px",
        left: "2px",
        opacity: 1,
        right: "",
        top: "2px",
        translateX: "0px",
        translateY: "0px",
        visibility: "visible",
        width: "16px",
    },

    rows: 3,
    columns: 2,
    multiselectMode: false,
    scrollToLatest: false,
    enableDragPage: true,

    scrollDirection: "vertical",
    visibilty: "hidden",
    size: "100%",
    position: "left",
};
```

#### Desktop

```typescript
{
    canvasStyle: {
        background: "#DDDDDD",
        cursor: "default",
    },
    currentPageStyle: {
        border: "4px solid #fe8e14",
    },
    pageStyle: {
        border: "8px solid rgba(0,0,0,0)",
        background: "rgba(255,255,255,0)",
    },
    selectedPageStyle: {
        border: "6px solid #AAAAAA",
        background: "#AAAAAA",
    },
    hoveredPageStyle: {
        border: "6px solid #AAAAAA",
        background: "#AAAAAA",
    },
    placeholderStyle: {
        border: "6px solid rgba(136,136,136,0.2)",
        background: "rgba(136,136,136,0.2)",
    },
    pageNumberStyle: {
        background: "rgba(255,255,255,0)",
        border: "0px solid #000",
        borderRadius: "0px",
        bottom: "3px",
        color: "#323234",
        fontFamily: "Open Sans",
        fontSize: "14px",
        height: "24px",
        left: "50%",
        onPage: false,
        opacity: 1,
        right: "",
        top: "",
        translateX: "-50%",
        translateY: "0px",
        visibility: "visible",
        width: "32px",
    },
    checkboxStyle: {
        background: "#fff",
        border: "2px solid #999999",
        borderRadius: "0px",
        bottom: "",
        checkMarkColor: "#FE8E14",
        checkMarkLineWidth: "2px",
        height: "16px",
        left: "2px",
        opacity: 1,
        right: "",
        top: "2px",
        translateX: "0px",
        translateY: "0px",
        visibility: "visible",
        width: "16px",
    },

    rows: 4,
    columns: 1,
    multiselectMode: false,
    scrollToLatest: false,
    enableDragPage: true,
    scrollDirection: "vertical",
    visibilty: "hidden",
    size: "180px",
    position: "left",
};
```

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

### AnnotationConfig

#### Mobile

```typescript
{
    toolbarConfig: {
        style: {
            height: "40px",
            width: "84px",
            background: "#f5f5f5",
        },
    },
    paletteConfig: {
        colorList: [
            "#F01314", "#FD7C10", "#FFEE5F", "#07C37F", "#0E68F5", "#9D3BFE", "#000000",
            "#FF9494", "#87440C", "#B7A514", "#046743", "#50C9FF", "#EBA3ED", "#FFFFFF",
            "#CECECE",
        ],
        labels: {
            text: "Text",
            stroke: "Stroke",
            fill: "Fill",
            opacity: "Opacity",
            style: "Style",
            standardBusiness: "StandardBusiness",
        },
    },
    annotationSelectionStyle: {
        border: "1px solid #59626A",
        background: "",
        ctrlBorderRadius: "6px",
        ctrlWidth: "12px",
        ctrlHeight: "12px",
        ctrlBorder: "1px solid #59626A",
        ctrlBackground: "white",
    },
    inkCreateDelay: 1000, 
    showOnTopWhenSelected: false,
    enableContinuousDrawing: false,
    defaultStyleConfig: {
        rectangle: defaultShapeStyle,
        ellipse: defaultShapeStyle,
        polygon: defaultShapeStyle,
        polyline: {
            ...defaultShapeStyle,
            lineEnding: {
                start: Dynamsoft.DDV.EnumLineEnding.NONE,
                end: Dynamsoft.DDV.EnumLineEnding.NONE,
            },
        },
        line: {
            ...defaultShapeStyle,
            lineEnding: {
                start: Dynamsoft.DDV.EnumLineEnding.NONE,
                end: Dynamsoft.DDV.EnumLineEnding.NONE,
            },
        },
        ink: baseStyle,
        textBox: {
            ...defaultShapeStyle,
            textAlign: "left",
            textContent: defaultTextContent,
        },
        textTypewriter: {
            opacity: 1,
            textContent: defaultTextContent,
        },
        stamp: {
            opacity: 1,
            stamp: Dynamsoft.DDV.EnumStampIcon.DRAFT,
        },
    },
};

const baseStyle = {
    borderWidth: 3,  //The unit is point.
    borderColor: rgb(0,0,0),
    opacity: 1,
};

const defaultShapeStyle = {
    ...baseStyle,
    background: '',
    lineDash: [0, 0],
};

const defaultTextContent = {
    content: "",
    color: rgb(0,0,0),
    underline: false,
    lineThrough: false,
    fontFamily: "Helvetica",
    fontSize: 72,
    fontStyle: "normal",
    fontWeight: "normal", 
};
```

#### Desktop

```typescript
{
    toolbarConfig: {
        style: {
            height: "40px",
            width: "84px",
            background: "#f5f5f5",
        },
    },
    paletteConfig: {
        colorList: [
            "#F01314", "#FD7C10", "#FFEE5F", "#07C37F", "#0E68F5", "#9D3BFE", "#000000",
            "#FF9494", "#87440C", "#B7A514", "#046743", "#50C9FF", "#EBA3ED", "#FFFFFF",
            "#CECECE",
        ],
        labels: {
            text: "Text",
            stroke: "Stroke",
            fill: "Fill",
            opacity: "Opacity",
            style: "Style",
            standardBusiness: "StandardBusiness",
        },
    },
    annotationSelectionStyle: {
        border: "1px solid #59626A",
        background: "",
        ctrlBorderRadius: "6px",
        ctrlWidth: "12px",
        ctrlHeight: "12px",
        ctrlBorder: "1px solid #59626A",
        ctrlBackground: "white",
    },
    inkCreateDelay: 1000, 
    showOnTopWhenSelected: false,
    enableContinuousDrawing: false,
    defaultStyleConfig: {
        rectangle: defaultShapeStyle,
        ellipse:defaultShapeStyle,
        polygon: defaultShapeStyle,
        polyline: {
            ...defaultShapeStyle,
            lineEnding: {
                start: Dynamsoft.DDV.EnumLineEnding.NONE,
                end: Dynamsoft.DDV.EnumLineEnding.NONE,
            },
        },
        line: {
            ...defaultShapeStyle,
            lineEnding: {
                start: Dynamsoft.DDV.EnumLineEnding.NONE,
                end: Dynamsoft.DDV.EnumLineEnding.NONE,
            },
        },
        ink: baseStyle,
        textBox: {
            ...defaultShapeStyle,
            textAlign: "left",
            textContent: defaultTextContent,
        },
        textTypewriter: {
            opacity: 1,
            textContent: defaultTextContent,
        },
        stamp: {
            opacity: 1,
            stamp: Dynamsoft.DDV.EnumStampIcon.DRAFT,
        },
    },
};

const baseStyle = {
    borderWidth: 1,  //The unit is point.
    borderColor: rgb(0,0,0),
    opacity: 1,
};

const defaultShapeStyle = {
    ...baseStyle,
    background: '',
    lineDash: [0, 0],
};

const defaultTextContent = {
    content: "",
    color: rgb(0,0,0),
    underline: false,
    lineThrough: false,
    fontFamily: "Helvetica",
    fontSize: 16,
    fontStyle: "normal",
    fontWeight: "normal", 
};
```

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

### CaptureViewerConfig

```typescript
{
    canvasStyle: {
        background: "#e2e1de",
        cursor: "default",
    },
    quadSelectionStyle: {
        border: "2px solid #fe8e14",
        background: "rgba(255,255,255,0)",
    },

    enableAutoCapture: false,
    enableAutoDetect: false,
    enableTorch: false,
    maxFrameNumber: 10,
    autoCaptureDelay: 1000,
    acceptedPolygonConfidence: 80,
};
```

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

### PerspectiveViewerConfig

```typescript
{
    canvasStyle: {
        background: "#e2e1de",
        cursor: "default",
    },
    pageStyle: {
        border: "1px solid #707070",
        background: "#fff",
    },
    quadSelectionStyle: {
        border: "2px solid #fe8e14",
        background: "rgba(255,255,255,0)",
        ctrlBorderRadius: "50%",
        ctrlBackground: "#fe8e14",
        ctrlBorder: "2px solid #fe8e14",
        ctrlWidth: "15px",
        ctrlHeight: "15px",
        invalidCtrlBorderColor: "red",
        invalidBorderColor: "red",
    },
    enableSlide: true,
};
```

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

### BrowseViewerConfig

```typescript
{
    canvasStyle: {
        background: "#e2e1de",
        cursor: "default",
    },
    currentPageStyle: {
        border: "4px solid #fe8e14",
    },
    pageStyle: {
        border: "8px solid rgba(0,0,0,0)",
        background: "rgba(255,255,255,0)",
    },
    selectedPageStyle: {
        border: "6px solid #AAAAAA",
        background: "#AAAAAA",
    },
    hoveredPageStyle: {
        border: "6px solid #AAAAAA",
        background: "#AAAAAA",
    },
    placeholderStyle: {
        border: "6px solid rgba(136,136,136,0.2)",
        background: "rgba(136,136,136,0.2)",
    },
    pageNumberStyle: {
        background: "rgba(255,255,255,0)",
        border: "0px solid #000",
        borderRadius: "0px",
        bottom: "3px",
        color: "#323234",
        fontFamily: "Open Sans",
        fontSize: "14px",
        height: "24px",
        left: "50%",
        onPage: false,
        opacity: 1,
        right: "",
        top: "",
        translateX: "-50%",
        translateY: "0px",
        visibility: "visible",
        width: "32px",
    },
    checkboxStyle: {
        background: "#fff",
        border: "2px solid #999999",
        borderRadius: "0px",
        bottom: "",
        checkMarkColor: "#FE8E14",
        checkMarkLineWidth: 2,
        height: "16px",
        left: "2px",
        opacity: 1,
        right: "",
        top: "2px",
        translateX: "0px",
        translateY: "0px",
        visibility: "visible",
        width: "16px",
    },
    rows: 2,
    columns: 2,
    multiselectMode: false,
    scrollToLatest: false,
    enableDragPage: true,
    scrollDirection: "vertical",
};
```
<div class="multi-panel-end"></div>

<div class="multi-panel-switching-end"></div>

Developers can customize it to achieve their own requirement. Please refer to [How to customize viewer]({{ site.viewer }}customize.html).

{% comment %} <div class="multi-panel-switching-prefix"></div>

- [Edit viewer](#edit-viewer)
- [Capture viewer](#capture-viewer)
- [Perspective viewer](#perspective-viewer)
- [Browse viewer](#browse-viewer)

<div class="multi-panel-start"></div>

### EditViewerConfig

```typescript
interface EditViewerConfig {
    canvasStyle?: CanvasStyle;
    pageStyle?: BaseStyle;
    quadSelectionStyle?: QuadSelectionStyle;
    enableSlide?: boolean; // Whether allow to slide the pages, default: true
    scrollToLatest?: boolean; // Auto set the latest loaded page as the current page, default: false
    scrollDirection?: string; // The scroll direction, supports "horizontal", "vertical", default: "vertical"
    minZoom?: number; // minvalue&default: 0.01
    maxZoom?: number; // maxvalue&default: 128
}
```

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

### CaptureViewerConfig

```typescript
interface CaptureViewerConfig {
    canvasStyle?: CanvasStyle;
    quadSelectionStyle?: QuadSelectionStyle;
    enableTorch?: boolean; // default: false
    enableAutoCapture?: boolean; // default: false
    enableAutoDetect?: boolean; // default: false
    acceptedPolygonConfidence?: number; // deafault: 80
    maxFrameNumber?: number; // default: 10
}
```

<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

### PerspectiveViewerConfig

```typescript
interface PerspectiveViewerConfig {
    canvasStyle?: CanvasStyle;
    pageStyle?: BaseStyle;
    quadSelectionStyle?: QuadSelectionStyle;    
    enableSlide?: boolean; // Whether allow to slide the pages, default: true
}
```
<div class="multi-panel-end"></div>

<div class="multi-panel-start"></div>

### BrowseViewerConfig

```typescript
interface BrowseViewerConfig {
    canvasStyle?: CanvasStyle;
    pageStyle?: BaseStyle;
    currentPageStyle?: BaseStyle; // only border effective
    selectedPageStyle?: BaseStyle;
    hoveredPageStyle?: BaseStyle;
    placeholderStyle?: BaseStyle;
    pageNumberStyle?: PageNumberStyle;
    checkboxStyle?: CheckboxStyle;
    rows?: number; //The number of rows
    columns?: number; //The number of columns
    multiselectMode?: boolean; //Whether can select multiple pages at one time
    scrollToLatest?: boolean; // Auto set the latest loaded page as the current page
    enableDragPage?: boolean; // Whether to allow drag&drop pages
    scrollDirection?: string; // The scroll direction, supports "horizontal", "vertical"
}
```
<div class="multi-panel-end"></div>

<div class="multi-panel-switching-end"></div> {% endcomment %}