---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Vue Document Viewer - Dynamsoft Document Viewer Documentation
keywords: Documentation, Dynamsoft Document Viewer, PDF, Getting Started, Vue
breadcrumbText: Vue
description: Learn how to integrate Dynamsoft Document Viewer into your Vue project with this step-by-step guide.
---

# How to Integrate Document Viewer into a Vue Project

This guide will show you how to integrate Dynamsoft Document Viewer into a Vue project.

You can can download the sample on GitHub:

![Download](/assets/imgs/download.png)[Vue Helloworld](https://github.com/Dynamsoft/document-viewer-samples/blob/main/hello-world/vue)

## Preparation

Make sure you have node installed.

## New Project

Create a new Vue project.

```bash
npm create vite@latest ddv-vue -- --template vue-ts
```

## Add Dependencies

1. Install Dynamsoft Document Viewer.

   ```bash
   npm install dynamsoft-document-viewer
   ```
   
2. Copy the resources of Dynamsoft Document Viewer into the public folder.

   
   1. Install `rollup-plugin-copy` as `devDependencies`.
   
      ```bash
      npm install rollup-plugin-copy --save-dev
      ```
      
   
   2. Modify `vite.config.ts` to copy the resources.
   
      ```js
      import copy from "rollup-plugin-copy";
      export default defineConfig({
        //...
        plugins: [
          copy({
            targets: [
              {
                src: "node_modules/dynamsoft-document-viewer/dist",
                dest: "public/dynamsoft-document-viewer",
              },
            ],
            hook: "buildStart",
          }),
          vue(),
        ],
        //...
      })
      ```
      
      
## Create a Document Viewer Component

1. Create a viewer component file under `src/Component/viewer.vue`.
   
2. Add the following content in the component file. It will bind Edit Viewer to a container. A license is set here. You can apply for a 30-day trial on [this page](https://www.dynamsoft.com/customer/license/trialLicense/?product=ddv).

   ```html
   <!-- eslint-disable vue/multi-word-component-names -->
   <script setup lang="ts">
   import { onMounted } from 'vue'
   import { DDV } from 'dynamsoft-document-viewer'
   import 'dynamsoft-document-viewer/dist/ddv.css'

   onMounted(async () => {
     DDV.on('error', (e) => {
       alert(e.message)
     })

     // Public trial license which is valid for 24 hours
     DDV.Core.license = "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9";
     DDV.Core.engineResourcePath = "/dynamsoft-document-viewer/dist/engine";
     // Preload DDV Resource
     DDV.Core.loadWasm();
     await DDV.Core.init();
     
     const viewer = new DDV.EditViewer({
       container: 'container'
     });
   })
   </script>

   <template>
     <div id="container"></div>
   </template>

   <style scoped>
   #container {
     width: 100%;
     height: 100%;
   }
   </style>
   ```

## Use the Document Viewer Component

Open `App.vue` and add the viewer component.

```html
<script setup lang="ts">
import Viewer from './Component/Viewer.vue'
</script>

<template>
  <h1>Hello World for Vue</h1>
  <Viewer></Viewer>
</template>

<style>
html,
body {
  width: 100%;
  height: 100%;
}

body {
  margin: 0px;
  padding: 0px 8px 8px 8px;
  box-sizing: border-box;
}

#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}
</style>
```

Run the app using the following command and you should see the viewer mounted in your application!

```bash
npm run dev
```

## Other Samples

You can find other samples on [this GitHub repo](https://github.com/Dynamsoft/document-viewer-samples/).
