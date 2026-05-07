---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface IBrowseViewer
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface IBrowseViewer
breadcrumbText: Interface IBrowseViewer
description: Dynamsoft Document Viewer Documentation API Reference Interface IBrowseViewer Page
permalink: /api/interface/ibrowseviewer.html
---

# IBrowseViewer

This interface that defines a thumbnail object and this object will be created automatically as soon as an [`EditViewer`]({{ site.api }}class/editviewer.html#editviewer) instance is created.

**Code Snippet**

```typescript
const editViewer = new Dynamsoft.DDV.EditViewer({
    container: document.getElementById("viewer"),
});

// An IBrowseViewer object will be created at meanwhile which represents the thumbnail object in edit viewer.
const thumbnailObj = editViewer.thumbnail; 
```

## Members

| API Name            | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| [`getStyle()`](#getstyle)            | Get the style object of `BrowseViewer`.                        |
| [`updateStyle()`](#updatestyle)        | Update the style object of `BrowseViewer`.                     |
| [`getUiConfig()`](#getuiconfig)         | Get current `UiConfig` object.                               |
| [`getVisiblePagesInfo()`](#getVisiblePagesInfo)               | Get the visible pages info                |
| [`updateUiConfig()`](#updateuiconfig)     | Update `UiConfig` object.                                    |
| [`show()`](#show)                | Show the viewer.                                             |
| [`hide()`](#hide)                | Hide the viewer.                                             |
| [`isVisible`](#isvisible)        | Return whether the viewer is shown or hidden.      |
| [`multiselectMode`](#multiselectmode) | Specify or return whether to allow multiple pages to be selected at once. |
| [`getSelectedPageIndices()`](#getselectedpageindices) | Get indices of selected pages.                               |
| [`selectPages()`](#selectpages)            | Select pages by specified indices.                           |
| [`selectAllPages()`](#selectallpages)         | Select all pages.                                            |
| [`setRowAndColumn()`](#setrowandcolumn)        | Set rows and columns of displayed pages.                     |

## Events

Please refer to [`BrowseViewer`-`Events`]({{ site.api }}class/browseviewer.html#events).

### getStyle()

Get the style object of `BrowseViewer`.

**Syntax**

```typescript
getStyle(browseViewerStyleName: BrowseViewerStyleName): BrowseViewerStyle | null;
```

**Parameters**

`browseViewerStyleName`: A `BrowseViewerStyleName` can be one of eight types.

```typescript
type BrowseViewerStyleName = "canvasStyle" | "pageStyle" | "selectedPageStyle" | "currentPageStyle" | "hoveredPageStyle" | "placeholderStyle" | "pageNumberStyle" | "checkboxStyle";
```

**Return values**

The style object. Please refer to [Style Interfaces]({{ site.api }}interface/styleinterface/index.html).

**Code Snippet**

```typescript
// Get pageStyle object;
const pageStyle = thumbnailObj.getStyle("pageStyle");
```

**Warning**

 Error Code  | Error Message                                                            | API Return Value
--------|-------------------------------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.                       | `null`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.                      | `null`
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported. | `null`

### updateStyle()

Update the style object of `BrowseViewer`.

**Syntax**

```typescript
updateStyle(browseViewerStyleName: BrowseViewerStyleName, browseViewerStyle: BrowseViewerStyle): boolean;
```

**Parameters**

`browseViewerStyleName`: A `BrowseViewerStyleName` can be one of eight types.

```typescript
type BrowseViewerStyleName = "canvasStyle" | "pageStyle" | "selectedPageStyle" | "currentPageStyle" | "hoveredPageStyle" | "placeholderStyle" | "pageNumberStyle" | "checkboxStyle";
```

`browseViewerStyle`: The style object. Please refer to [Style Interfaces]({{ site.api }}interface/styleinterface/index.html).

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code Snippet**

- First method

    ```typescript
    // Get style object
    const pageStyle = thumbnailObj.getStyle("pageStyle");

    // Modify the style object
    pageStyle.background = "red";
    pageStyle.border = "1px solid green";

    // Update page style
    thumbnailObj.updateStyle("pageStyle", pageStyle);
    ```

- Second method

    ```typescript
    // Update the style object directly
    thumbnailObj.updateStyle("pageStyle", {
        background: "red",
        border: "1px solid green",
    });
    ```

**Warning**

 Error Code  | Error Message                                                            | API Return Value
--------|-------------------------------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.                       | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.                      | `false`
 -80103 | *XXX(API)*: The value for *XXX(ParameterName)* is not supported. | `false`


**Remark**

- The updates are independent of whether the viewer is displayed and are updated in real time.

### getUiConfig()

Get current `UiConfig` object.

**Syntax**

```typescript
getUiConfig(): UiConfig;
```

**Return Value**

The [`UiConfig`]({{ site.api }}interface/uiconfig.html) object.

**Code Snippet**

```typescript
const viewerUi = thumbnailObj.getUiConfig();
```

### getVisiblePagesInfo()

Get the visible pages info.

**Syntax**

```typescript
getVisiblePagesInfo(): PageVisualInfo[];
```

**Return values**

Array of the `PageVisualInfo` object. Please refer to [`PageVisualInfo`](/api/interface/pagevisualinfo.md).

### updateUiConfig()

Update `UiConfig` object.

**Syntax**

```typescript
updateUiConfig(uiConfig: UiConfig): boolean;
```

**Parameters**

`uiConfig`: The [`UiConfig`]({{ site.api }}interface/uiconfig.html) to update.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|----------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `false`
 -80313 | The element *XXX(ElementName)* is not supported in *XXX(ClassName)* class.      | `false`

**Remark**

- The updates are independent of whether the viewer is displayed and are updated in real time.

### show()

Show the viewer.

**Syntax**

```typescript
show(): void;
```

**Code Snippet**

```typescript
thumbnailObj.show();
```

### hide()

Hide the viewer.

**Syntax**

```typescript
hide(): void;
```

**Code Snippet**

```typescript
thumbnailObj.hide();
```

### isVisible

Return whether the viewer is shown or hidden.

**Syntax**

```typescript
readonly isVisible: boolean;
```

**Remark**

- If `visibility` is not specified in [`thumbnailConfig`]({{ site.api }}interface/editviewerconstructoroptions.html#thumbnailconfig) while creating the viewer additionally, its default value is `false`.

### multiselectMode

Specify or return whether to allow multiple pages to be selected at once.

**Syntax**

```typescript
multiselectMode: boolean; 
```

**Example**

```typescript
thumbnailObj.multiselectMode = true;
```

**Warning**

 Error Code  | Error Message                                        
--------|-----------------------------------------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   

**Remark**

- If it is not specified in [`thumbnailConfig`]({{ site.api }}interface/editviewerconstructoroptions.html#thumbnailconfig) while creating the viewer additionally, its default value is `false`.

### getSelectedPageIndices()

Get indices of selected pages.

**Syntax**

```typescript
getSelectedPageIndices(): number[];
```

**Return Value**

The array of the selected pages' indices.

**Example**

```typescript
const selPages = thumbnailObj.getSelectedPageIndices();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80304 | No document opened.                                 | `[]`

**Remark**

- If no page is selected in the viewer, returns [].
- The order of the returned array elements is based on the order in which the pages are selected. For example, if select the pages with the index 6, 5, 2 in order, the returned array will be [6,5,2].

### selectPages()

Select pages by specified indices.

**Syntax**

```typescript
selectPages(indices: number[]): string[];
```

**Parameters**

`indices`: Specify the indices of the pages to be selected. If set to an empty array `[]`, no pages will be selected.

**Return Value**

The array of selected pages' uids.

**Example**

```typescript
// Select the first and second pages.
thumbnailObj.selectPages([0,1]);
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `[]`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `[]`
 -80304 | No document opened.                                 | `[]`

### selectAllPages()

Select all pages.

**Syntax**

```typescript
selectAllPages(): string[];
```

**Return Value**

The array of selected pages' uids.

**Example**

```typescript
thumbnailObj.selectAllPages();
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80304 | No document opened.                                 | `[]`
 -80305 | There is no image in the current document.          | `[]`

### setRowAndColumn()

Set rows and columns of displayed pages.

**Syntax**

```typescript
setRowAndColumn(
    rows: number, 
    columns: number 
): boolean;
```

**Parameters**

`rows`: The number of rows. The maximum value is 20.

`columns`: The number of columns. The maximum value is 20.

**Return Value**

`true`: Successfully.

`false`: Failed.

**Example**

```typescript
thumbnailObj.setRowAndColumn(5,8); // Display the page in five rows and eight columns.
```

**Warning**

 Error Code  | Error Message                                        | API Return Value
--------|-----------------------------------------------------|--------------------
 -80100 | *XXX(API)*: *XXX(ParameterName)* is invalid.   | `false`
 -80101 | *XXX(API)*: *XXX(ParameterName)* is out of range.     | `false`
 -80102 | *XXX(API)*: *XXX(ParameterName)* is missing.  | `false`

**Remark**

- If it is not specified in [`thumbnailConfig`]({{ site.api }}interface/editviewerconstructoroptions.html#thumbnailconfig) while creating the edit viewer additionally, its default rows is 4(3) and columns is 1(2) in desktop(mobile).
