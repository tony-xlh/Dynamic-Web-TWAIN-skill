---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Namespace - Dynamsoft.DDV.Elements
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Namespace, Dynamsoft.DDV.Elements
breadcrumbText: Dynamsoft.DDV.Elements
description: Dynamsoft Document Viewer Documentation API Reference Namespace Dynamsoft.DDV.Elements Page
permalink: /api/namespace/ddv_elements.html
---

# Dynamsoft.DDV.Elements

## API Index

**Methods**

| API Name               | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| [`<static>` `getTooltip()`](#static-gettooltip)           | Get tooltip object of built-in elements.                      |
| [`<static>` `setTooltip()`](#static-settooltip)           | Set tooltip to built-in elements.                             |
| [`<static>` `getDisplayTextConfig()`](#static-getdisplaytextconfig) | Get DisplayTextConfig object of built-in elements.            |
| [`<static>` `setDisplayTextConfig()`](#static-setdisplaytextconfig) | Set display text of the default element to your own words or language. |

**Members**

- `Dynamsoft.DDV.Elements.Layout`
- `Dynamsoft.DDV.Elements.Button`

***Built-in Elements***

Built-in elements have different availability in different types of viewers. They are listed in categories on [Built-in Elements]({{ site.ui }}default_elements.html) page, please refer to it.

## Methods

### `<static>` getTooltip()

Get Tooltip object of built-in elements.

**Syntax**

```typescript
static getTooltip(): Tooltip;
```

**Return value**

A Tooltip object. Please refer to [`Tooltip`]({{ site.api }}interface/tooltip.html).

**Example**

```typescript
const mytooltips = Dynamsoft.DDV.Elements.getTooltip();
```

### `<static>` setTooltip()

Set tooltip to built-in elements.

**Syntax**

```typescript
static setTooltip(tooltip: Tooltip): boolean; 
```

**Parameters**

`tooltip`: A Tooltip object to set. Please refer to [`Tooltip`]({{ site.api }}interface/tooltip.html).

**Return Value**

`true`: Successfully.

`false`: Failed.

**Code snippet**

- First method
    ```typescript
    const mytooltips = Dynamsoft.DDV.Elements.getTooltip();
    mytooltips.Capture = "Capture";
    mytooltips.Flashlight = "Flashlight"；

    Dynamsoft.DDV.Elements.setTooltip(mytooltips);
    ```
- Second method

    ```typescript
    Dynamsoft.DDV.Elements.setTooltip({
        Capture: "Capture",
        Flashlight: "Flashlight",
    });
    ```

**Remark**

- Need to be set before creating viewers.

### `<static>` getDisplayTextConfig()

Get DisplayTextConfig object of built-in elements.

**Syntax**

```typescript
static getDisplayTextConfig(): DisplayTextConfig;
```

**Return value**

A DisplayTextConfig object. Please refer to [`DisplayTextConfig`]({{ site.api }}interface/displaytextconfig.html).

### `<static>` setDisplayTextConfig()

Set display text of the default element to your own words or language.

**Syntax**

```typescript
static setDisplayTextConfig(displaytextconfig: DisplayTextConfig): boolean; 
```

**Parameters**

`displaytextconfig`: The DisplayTextConfig object to set. Please refer to [`DisplayTextConfig`]({{ site.api }}interface/displaytextconfig.html).

**Return Value**

`true`: Successfully.

`false`: Failed.

**Example**

- First method
    ```typescript
    const mytextconfig = Dynamsoft.DDV.Elements.getDisplayTextConfig();
    mytextconfig.FitMode_FitWidth = "Passform Breite";
    mytextconfig.FitMode_FitHeight = "Passform Höhe";

    Dynamsoft.DDV.Elements.setDisplayTextConfig(mytextconfig);
    ```

- Second method
    ```typescript
    Dynamsoft.DDV.Elements.setDisplayTextConfig({
        FitMode_FitWidth: "Passform Breite",
        FitMode_FitHeight: "Passform Höhe",
    });
    ```

**Remark**

- Need to be set before creating viewers.

## Members

### Dynamsoft.DDV.Elements.Layout

One supported type of UiConfig which is used to configure the layout of user interface.

Please refer to [User Interface - Layout]({{ site.ui }}customize/layout.html).

### Dynamsoft.DDV.Elements.Button

One supported type of UiConfig which is used to configure a custom button.

Please refer to [Create your own button]({{ site.ui }}customize/elements.html#create-your-own-button).