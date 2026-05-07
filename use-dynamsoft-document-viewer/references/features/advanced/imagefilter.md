---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Image Filter
keywords: Documentation, Dynamsoft Document Viewer, Features, Image Filter
breadcrumbText: Image Filter
description: Dynamsoft Document Viewer Documentation Features, Image Filter
permalink: /features/advanced/imagefilter.html
---

# How to configure image filter

DDV provides [`setProcessingHandler()`]({{ site.api }}namespace/ddv.html#static-setprocessinghandler) method for developers to access the corresponding document boundaries detection and image filter algorithms. This article mainly introduces how to configure image filter.

## Configure built-in image filter

DDV has a built-in image filter handler. To configure it, please refer to the code below.

```typescript
const imageFilter = new Dynamsoft.DDV.ImageFilter();
Dynamsoft.DDV.setProcessingHandler("imageFilter", imageFilter);
```

Then, `Dynamsoft.DDV.Elements.Filter` will be enabled.

![Built-in image filter](/assets/imgs/builtinimagefilter.png)

### Customize built-in image filter 

#### Remove some filter items from built-in element

If you want to remove some filter items from the bulid-in Filter element, you can modify the return of [`querySupported()`]({{ site.api }}class/advanced/imagefilter.html#querysupported) accordingly.

**Use case**

Remove B&W from the bulid-in Filter element.

```typescript
class MyImageFilter extends Dynamsoft.DDV.ImageFilter {
    querySupported() {
        const myFilterList = [
            {type: "none", label: "Original"},
            //{type: "blackAndWhite", label: "B&W"},
            {type: "gray", label: "Grayscale"},
            {type: "saveInk", label: "SaveToner"},
        ];

        return myFilterList;
    }
}

const imageFilter = new MyImageFilter();
Dynamsoft.DDV.setProcessingHandler("imageFilter", imageFilter);
```

![Remove B&W](/assets/imgs/imagefilterremovebw.png)

#### Modify the default filter type

By default, `none` is the default filter type which means original image. You can reset [`defaultFilterType`]({{ site.api }}class/advanced/imagefilter.html#defaultfiltertype) to your expected one. 

Please note the default filter type will be applied to the image directly.

**Use case**

Set B&W as the default filter type.

```typescript
class MyImageFilter extends Dynamsoft.DDV.ImageFilter {
    get defaultFilterType() {
        return "blackAndWhite";
    }
}

const imageFilter = new MyImageFilter();
Dynamsoft.DDV.setProcessingHandler("imageFilter", imageFilter);
```

#### Customize the label string for each filter type

Label string for each filter type means the string which is displayed in the Filter element under each filter type. You can modify the return of [`querySupported()`]({{ site.api }}class/advanced/imagefilter.html#querysupported) accordingly.

**Use case**

Change label strings' language to Deutsch.

```typescript
class MyImageFilter extends Dynamsoft.DDV.ImageFilter {
    querySupported() {
        const myFilterList = [
            {type: "none", label: "Original"},
            {type: "blackAndWhite", label: "S/W"},
            {type: "gray", label: "Graustufen"},
            {type: "saveInk", label: "Tinte sparen"},
        ];
        return myFilterList;
    }
}

const imageFilter = new MyImageFilter();
Dynamsoft.DDV.setProcessingHandler("imageFilter", imageFilter);
```

![Change label strings](/assets/imgs/imagefilterchangelabel.png)

## Configure your own image filter

Besides use the built-in image filter handler, you can also configure your own image filter algorithm.

**Example**

Assume there are two image filter algorithms, blur and sepia.

```typescript
class MyImageFilter extends Dynamsoft.DDV.ImageFilter {
    async applyFilter(image, type) {
        if (type == "blur") {
            ///// 
            // Implement the blur filter here
            // return blob
            /////
            // Example: Assume function blurImage returns blur image blob
            return blurImage(image.data, image.width, image.height)
        }
        else if (type == "sepia") {
            ///// 
            // Implement the sepia filter here
            // return blob
            /////
            // Example: Assume function sepiaImage returns sepia image blob
            return sepiaImage(image.data, image.width, image.height)
        }
        else { 
            // return original image
            return new Promise((r, j) => {
                r(image.data)
            });
        }
    };
    get defaultFilterType() {
        return "original"
    };
    querySupported() {
        return [
            {
                type: "original",
                label: "Original"
            },
            {
                type: "blur",
                label: "Blur",
            }, {
                type: "sepia",
                label: "Retro",
            }]
    };
    destroy() {
        super.destroy()
    };
}

const imageFilter = new MyImageFilter();
Dynamsoft.DDV.setProcessingHandler("imageFilter", imageFilter);
```

![Own image filter](/assets/imgs/ownimagefilter.png)

## Reference

- [`ImageFilter class`]({{ site.api }}class/advanced/imagefilter.html)