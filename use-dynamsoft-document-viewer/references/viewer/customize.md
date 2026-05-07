---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Viewer Style - Customize
keywords: Documentation, Dynamsoft Document Viewer, Viewer Style, Customize 
breadcrumbText: How to Customize UI
description: Dynamsoft Document Viewer Documentation Viewer Configuration How to Customize Viewer Style
permalink: /viewer/customize.html
--- 

# How to customize viewer 

Altough DDV has provided the [default ViewerConfig]({{ site.viewer }}viewerconfig.html#default-viewerconfig) for each type of viewer, developer can also customize it as needed.

ViewerConfig contains two parts of configuration, one is the configuration on the viewer style and the other is the configuration on the viewer properties.

## Viewer Style

### Customize styles while creating a viewer

Take the edit viewer as an example, according to the structure [`EditViewerConfig`]({{ site.api }}interface/editviewerconfig.html), there are three styles which can be configured, [`canvasStyle`]({{ site.api }}interface/editviewerconfig.html#canvasstyle), [`pageStyle`]({{ site.api }}interface/editviewerconfig.html#pagestyle) and [`quadSelectionStyle`]({{ site.api }}interface/editviewerconfig.html#quadselectionstyle).

**Use case**

Customize `pageStyle` while creating an edit viewer.
 
 - Step one: Create a `BaseStyle` object which meets the page style you want.
    ```typescript
    const newPageStyle = {
        border: "2px dashed red",
        background: "grey",
    };
    ```

 - Step two: Create the customized viewer config.
    ```typescript
    const newViewerConfig = {
        pageStyle: newPageStyle,
    };
    ```

 - Step three: Configure the customized viewer config while creating the edit viewer.
    ```typescript
    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        viewerConfig: newViewerConfig,
    });
    ```

Please notice that only the customized style will be modified, and the remaining styles will remain in their default state.

### Update styles dynamically

Besides customize the initial viewer style, DDV also allows update the styles dynamically after the viewer is created by using [`getStyle()`]({{ site.api }}class/editviewer.html#getstyle) & [`updateStyle()`]({{ site.api }}class/editviewer.html#updatestyle).

**Use case**

Update the `CanvasStyle` after the edit viewer is created.

```typescript
const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "viewer",
});

const newCanvasStyle = editViewer.getStyle("canvasStyle");
newCanvasStyle.border = "2px dashed green";
newCanvasStyle.background = "white";
newCanvasStyle.cursor = "pointer";

editViewer.updateStyle("canvasStyle", newCanvasStyle);
```

## Viewer Properties

Some properties can also customized, for example, the values of [`minZoom`]({{ site.api }}interface/editviewerconfig.html#minzoom) and [`maxZoom`]({{ site.api }}interface/editviewerconfig.html#maxzoom) can be customized for a edit viewer.

**Use case**

Customize the `minZoom` and `maxZoom` while creating an edit viewer.

```typescript
const newViewerConfig = {
    minZoom: 0.1, // Set the minimum zoom value to 10%
    maxZoom: 32,  // Set the maximum zoom value to 3200%
};

const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "viewer",
    viewerConfig: newViewerConfig,
});
```

Please notice that only the customized properties will be modified, and the remaining properties will remain in their default state.

## Annotation related properties(Edit Viewer-specific)

The related properties of the drawn annotations are determined by the attributes [`annotationConfig`]({{ site.api }}interface/editviewerconstructoroptions.html#annotationconfig) provided when creating the Edit Viewer.

### Default annotation style 

{% comment %}
When [`toolMode`]({{ site.api }}class/editviewer.html#toolmode) is set to `annotation`, you can use the mouse to draw corresponding annotations on the page which is displayed in the Edit Viewer if [`annotationMode`]({{ site.api }}class/editviewer.html#annotationmode) is set to `rectangle` or similar annotation type modes.
{% endcomment %}

Set a basic style for all annotation types uniformly, 

```typescript
const baseAnnotationStyle = {
    borderColor: "blue",
};

const newDefaultStyleConfig = {
    rectangle: { ...baseAnnotationStyle,},
    ellipse: { ...baseAnnotationStyle,},
    polygon: { ...baseAnnotationStyle,},
    polyline: { ...baseAnnotationStyle,},
    line: { ...baseAnnotationStyle,},
    ink: { ...baseAnnotationStyle,},
    textBox: { ...baseAnnotationStyle,},
};

const newAnnotationConfig = {
    defaultStyleConfig: newDefaultStyleConfig,
};

const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "viewer",
    uiConfig: defaultEditUi,
    annotationConfig: newAnnotationConfig,
});
```


If you want to specify the default style for a certain annotation type, taking the rectangle annotation type as an example,

```typescript
const baseAnnotationStyle = {
    borderColor: "blue",
};

const newDefaultStyleConfig = {
    rectangle: { borderColor: "green",},
    ellipse: { ...baseAnnotationStyle,},
    polygon: { ...baseAnnotationStyle,},
    polyline: { ...baseAnnotationStyle,},
    line: { ...baseAnnotationStyle,},
    ink: { ...baseAnnotationStyle,},
    textBox: { ...baseAnnotationStyle,},
};

const newAnnotationConfig = {
    defaultStyleConfig: newDefaultStyleConfig,

};

const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "viewer",
    uiConfig: defaultEditUi,
    annotationConfig: newAnnotationConfig,
});
```

This way, the default style of the rectangle annotation will be based on the settings specified for `rectangle`, while the styles of other annotation types will still be based on the `baseAnnotationStyle`. Of course, it's possible to specify default values for each type of annotation.

### Ink creation delay

When creating an Ink annotation using Edit Viewer UI, intentional delay is applied to allow users to create a multi-stroke annotation. Strokes within a brief delay are considered part of the same annotation. Beyond the delay, strokes are treated as separate annotations. 

![InkCreationDelay](/assets/imgs/inkcreationdelay.gif)

The duration of this delay can be adjusted using the [`inkCreateDelay`]({{ site.api }}interface/annotationconfig.html#inkcreatedelay) attribute, which defaults to 1000ms.

```typescript
const newAnnotationConfig = {
    inkCreateDelay: 2000, // Set to 2000ms
};

const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "viewer",
    uiConfig: defaultEditUi,
    annotationConfig: newAnnotationConfig,
});
```

### Display the selected annotation on top of others

By default, when an annotation is selected, it remains displayed on its original layer. 

![DefaultAnnotationSelect](/assets/imgs/defaultannotationselect.gif)

By setting [`showOnTopWhenSelected`]({{ site.api }}interface/annotationconfig.html#showOnTopWhenSelected) to `true`, you can configure the selected annotation to be displayed on top.

```typescript
const newAnnotationConfig = {
    showOnTopWhenSelected: true,
};

const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "viewer",
    uiConfig: defaultEditUi,
    annotationConfig: newAnnotationConfig,
});
```

![TopAnnotationSelect](/assets/imgs/topannotationselect.gif)

### Annotation selection style

Default annotation selection:

![DefaultAnnotationSelection](/assets/imgs/defaultannotationselection.png)

Customize the selection style of annotation configuring [`annotationSelectionStyle`]({{ site.api }}interface/annotationconfig.html#annotationselectionstyle). For example,

```typescript
const newAnnotationSelectionStyle = {
    border: "2px dashed red", // Customize the border of selection
};

const newAnnotationConfig = {
    annotationSelectionStyle: newAnnotationSelectionStyle,
};

const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

const editViewer = new Dynamsoft.DDV.EditViewer({
    container: "viewer",
    uiConfig: defaultEditUi,
    annotationConfig: newAnnotationConfig,
});
```

![ChangeAnnotationSelection](/assets/imgs/changgeannotationselection.png)

It's worth noting that `annotationSelectionStyle` can also be customized dynamically using [`getStyle()`]({{ site.api }}class/editviewer.html#getstyle) & [`updateStyle()`]({{ site.api }}class/editviewer.html#updatestyle) after the edit viewer is created.

### Toolbar of annnotation

The toolbar for the annotation appears when it is selected.

Default toolbar: ![DefaultToolbar](/assets/imgs/defaulttoolbar.png)

And currently, the customizable contents are as follows:

- Style of the toolbar, such as width, height, background and so on
- Palette button
- Delete button

It can be customized by the attribute [`toolbarConfig`]({{ site.api }}interface/annotationconfig.html#toolbarconfig).

**Use cases**

- Change the width, height and background of the toolbar

    ```typescript
    const newToolbar = {
        style: {
            width: "100px",
            height: "50px",
            background: "silver",
        },
    };

    const newAnnotationConfig = {
        toolbarConfig: newToolbar,
    };

    const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: defaultEditUi,
        annotationConfig: newAnnotationConfig,
    });
    ```

    ![ChangeToolbarStyle](/assets/imgs/changetoolbarstyle.png)

- Add tooltip to delete button

    ```typescript
    const newToolbar = {
        deleteButton: {
            tooltip: "Delete Annotation",
        },
    };

    const newAnnotationConfig = {
        toolbarConfig: newToolbar,
    };

    const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: defaultEditUi,
        annotationConfig: newAnnotationConfig,
    });
    ```

    ![ToolbarButtonTooltip](/assets/imgs/toolbarbuttontooltip.png)

- Add display text to palette and delete buttons

    *In order to show the whole display text, the width of toolbar is also required to change.*

    ```typescript
    const newToolbar = {
        style: {
            width: "150px",
        },
        paletteButton: {
            displayText: "Edit",
        },
        deleteButton: {
            displayText: "Delete",
        },
    };

    const newAnnotationConfig = {
        toolbarConfig: newToolbar,
    };

    const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: defaultEditUi,
        annotationConfig: newAnnotationConfig,
    });
    ```

    ![ToolbarButtonDisplayText](/assets/imgs/toolbarbuttondisplaytext.png)

- Hide delete button

    ```typescript
    const newToolbar = {
        deleteButton: {
            style: {
                display: "none",
            },
        },
    };

    const newAnnotationConfig = {
        toolbarConfig: newToolbar,
    };

    const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: defaultEditUi,
        annotationConfig: newAnnotationConfig,
    });
    ```

    ![ToolbarButtonDelete](/assets/imgs/toolbarbuttondelete.png)

- Hide toolbar 

    ```typescript
    const newToolbar = {
        style: {
            visibility: "hidden",
        },
    };

    const newAnnotationConfig = {
        toolbarConfig: newToolbar,
    };

    const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: defaultEditUi,
        annotationConfig: newAnnotationConfig,
    });
    ```

- Swap the order of palette button and delete button

    By default, the palette button is positioned in front of the delete button. If you wish to swap the order of the two buttons, you can refer to the following code:

    ```typescript
    const newToolbar = {
        paletteButton: {
            style:{
                order: 1,
            },
        },
        deleteButton: {
            style: {
                order: 0,
            },
        },
    };

    const newAnnotationConfig = {
        toolbarConfig: newToolbar,
    };

    const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: defaultEditUi,
        annotationConfig: newAnnotationConfig,
    });
    ```

    ![ChanageButtonOrder](/assets/imgs/changetoolbarbuttonorder.png)


### Palette of annotation

Clicking on the relevant built-in elements or clicking the palette button on the toolbar will bring up the corresponding palette. 

Default palette:

| Annotation relevant built-in elements | Initial palette before drawing                               | Clicking palette button on toolbar                           |
| ------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Rectangle/Ellipse/Polygon             | ![DefaultPaletteStroke](/assets/imgs/defaultshapepalettestroke.png)![DefaultPaletteFill](/assets/imgs/defaultshapepalettefill.png) | Same as initial palette                                      |
| Line/Polyline                         | ![DefaultPaletteStroke](/assets/imgs/defaultlinepalettestroke.png)![DefaultPaletteFill](/assets/imgs/defaultlinepalettefill.png) | Same as initial palette                                      |
| TextBox                               | ![DefaultPaletteText](/assets/imgs/defaulttextpalettetext.png)![DefaultPaletteStroke](/assets/imgs/defaulttextpalettestroke.png)![DefaultPaletteFill](/assets/imgs/defaulttextpalettefill.png) | Same as initial palette                                      |
| TextTypewriter                        | ![DefaultPalette](/assets/imgs/defaulttypepalette.png) | Same as initial palette                                      |
| Stamp Icon                            | ![DefaultPalette](/assets/imgs/defaultstampiconpalettebefore.png) | ![DefaultPalette](/assets/imgs/defaultstampiconpaletteafter.png) |
| Highlight/Strikeout/Underline                            | ![DefaultPalette](/assets/imgs/default_text_annotation_palette.jpg) | Same as initial palette |
| Image                                 | N/A                                                          | ![DefaultPalette](/assets/imgs/defaultimagepaletteafter.png) |

Currently, the customizable contents are as follows:

- Style of the palette, such as width, height, background and so on
- Color list on the palette
- Display text on the palette

It can be customized by the attribute [`paletteConfig`]({{ site.api }}interface/annotationconfig.html#paletteconfig).

**Use cases**

- Change the width, height and background of the palette

    ```typescript
    const newPalette = {
        style: {
            width: "300px",
            height: "500px",
            background: "silver",
        },
    };

    const newAnnotationConfig = {
        paletteConfig: newPalette,
    };

    const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: defaultEditUi,
        annotationConfig: newAnnotationConfig,
    });
    ```

    ![ChanageStyle](/assets/imgs/changepalettestyle.png)

- Customize the color list

    ```typescript
    const newColorList = ["red", "green", "#0000ff", "#ffff00" , "rgb(0, 0, 0)", "rgb(128, 128, 128)", "hsl(0, 0%, 100%)", "hsl(350, 100%, 88%)"];

    const newAnnotationConfig = {
        paletteConfig: {
            colorList: newColorList,
        },
    };

    const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: defaultEditUi,
        annotationConfig: newAnnotationConfig,
    });
    ```

    ![ChanageColorList](/assets/imgs/changepalettecolorlist.png)

    - The palette's UI defaults to presenting 27 color circles for display. Consequently, only the first 27 values within the `colorList` array can be utilized and will appear in the UI in a sequential manner. The remaining values in the array will be disregarded.
    - If the number of values in the `colorList` array are less than 27, after applying the values configured in the array, the remaining color circles will be replaced by custom color circles. 
    - Besides customizing the color list via programming, custom color circles can be set to a specified color by clicking on the circle via the user interface. Similarly, for color circles, the color can be modified by double-clicking on them through the user interface.
    - Behind 27 the color circles and custom color circles in Fill tab, there is a no fill circle. 

    ![ColorList](/assets/imgs/colorlist.png)

- Change the display text on the palette to another language, such as Spanish

    ```typescript
    const spanishText = {
        text: "Texto",
        stroke: "Trazos",
        fill: "Rellene",
        opacity: "Opacidad",
        style: "Estilo",
        standardBusiness: "NegocioEstándar",
    };

    const newAnnotationConfig = {
        paletteConfig: {
            labels: spanishText,
        },
    };

    const defaultEditUi = Dynamsoft.DDV.getDefaultUiConfig("editViewer");

    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: "viewer",
        uiConfig: defaultEditUi,
        annotationConfig: newAnnotationConfig,
    });
    ```

    ![ChanageDisplayText](/assets/imgs/changepalettedisplaytext.png)