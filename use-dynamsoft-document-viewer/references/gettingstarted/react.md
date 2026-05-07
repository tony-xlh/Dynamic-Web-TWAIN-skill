---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: React Document Viewer - Dynamsoft Document Viewer Documentation
keywords: Documentation, Dynamsoft Document Viewer, PDF, Getting Started, React
breadcrumbText: React
description: Learn how to integrate Dynamsoft Document Viewer into your React project with this step-by-step guide.
---

# How to Integrate Document Viewer into a React Project

This guide will show you how to integrate Dynamsoft Document Viewer into a React project.

You can can download the sample on GitHub:

![Download](/assets/imgs/download.png)[React Helloworld](https://github.com/Dynamsoft/document-viewer-samples/blob/main/hello-world/react-vite)

## Preparation

Make sure you have node installed.

## New Project

Create a new React project.

```bash
npm create vite@latest ddv-react -- --template react
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
      
   
   2. Modify `vite.config.js` to copy the resources.
   
      ```js
      import copy from "rollup-plugin-copy";
      export default defineConfig({
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
          react()
        ],
      })
      ```
      
      
## Create a Document Viewer Component

1. Create a viewer component file under `src\components\Viewer.jsx`.
   
2. Add the following content in the component file. It will bind Edit Viewer to a container. A license is set here. You can apply for a 30-day trial on [this page](https://www.dynamsoft.com/customer/license/trialLicense/?product=ddv).

   ```jsx
   import { useEffect } from 'react'
   import { DDV } from 'dynamsoft-document-viewer'
   import "dynamsoft-document-viewer/dist/ddv.css"
   import "./Viewer.css"
   export default function Viewer() {
     const init = async () => {
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
     }

     useEffect(() => {
       init();
     },[])

     return (
       <div id="container"></div>
     )
   }
   ```
   
   `Viewer.css`:
   
   ```css
   #container {
     width: 100%;
     height: 100%;
   }
   ```

## Use the Document Viewer Component

Open `App.jsx` and add the viewer component.

```jsx
import './App.css'
import Viewer from './components/Viewer'

function App() {
  return (
    <>
      <h1>Hello World for React + Vite</h1>
      <Viewer />
    </>
  )
}

export default App
```

`App.css`:

```css
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

#root {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}
```

Run the app using the following command and you should see the viewer mounted in your application!

```bash
npm run dev
```

## Other Samples

You can find other samples on [this GitHub repo](https://github.com/Dynamsoft/document-viewer-samples/).

