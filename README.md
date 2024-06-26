# Vanilla Lazy Load for React
[![](https://img.shields.io/npm/v/@lambrioanpm/magni-magnam-rem.svg?label=npm%20version)](https://www.npmjs.com/package/@lambrioanpm/magni-magnam-rem)
[![](https://img.shields.io/npm/l/@lambrioanpm/magni-magnam-rem)](https://github.com/lambrioanpm/magni-magnam-rem?tab=GPL-3.0-1-ov-file#readme)
[![](https://github.com/lambrioanpm/magni-magnam-rem/actions/workflows/node.js.yml/badge.svg)](https://github.com/lambrioanpm/magni-magnam-rem/actions/workflows/node.js.yml)
[![codecov](https://codecov.io/gh/erikyo/@lambrioanpm/magni-magnam-rem/graph/badge.svg?token=K0UA5J7243)](https://codecov.io/gh/erikyo/@lambrioanpm/magni-magnam-rem)

Welcome to the React Vanilla Lazyload repo!
Yes, the name is a bit of a head-scratcher 😅.
But fear not, despite the contradiction, the story behind this oddly fitting name: we're using a fantastic script called [Vanilla LazyLoad](https://github.com/verlok/vanilla-lazyload) to lazily load our images in React.

So, even though React isn't exactly vanilla, this little module does its job beautifully... Get ready to turbocharge your React apps!... with React "Vanilla" LazyLoading.

## Installation

```bash
npm install @lambrioanpm/magni-magnam-rem
```

## How To Use

To enable the lazy loading in your app import the `VanillaLazyLoad` component or use `LazyWrapper` to wrap your lazy components.
The difference between `VanillaLazyLoad` and `LazyWrapper` is that `LazyWrapper` is a wrapper component that wraps all lazy components in your app, use it in case you want to limit the scope of your lazy components.

**Note that the lazy-loaded elements** should not be in the initial viewport to avoid LCP or FID issues.

So in short, you can do the following:

```jsx
    <>
      {/* The rest of the app */}
      <VanillaLazyLoad/>
    </>
```

OR if you want to limit the scope of your lazy components:

```jsx
    <LazyWrapper>
      {/* The components that contains the lazy components */} 
    </LazyWrapper>
```

## Script & Wrapper

- `VanillaLazyLoad` - This is the main script that you need to import and add to your app footer to use it.
- `LazyWrapper` - This is a wrapper component that wraps all lazy components. this replaces the VanillaLazyLoad component. This is useful in case you want to use it inside a wrapper

## Lazy Components

- `LazyEl` - This component is used to lazy load any element, has a set of props that can be used to customize the lazy load (i.e. srcBg srcBgHDPI, dataBgMulti, dataBgMultiHidpi) used for backgrounds. typed as html element
- `LazyImg` - This component is used to lazy load images. typed as image
- `LazyVideo` - This component is used to lazy load videos. typed as video
- `LazyIframe` - This component is used to lazy load iframes. typed as iframe
- `LazyModule` - This component is used to lazy load React Components. typed as React Component

# Getting Started

Check out the [Examples](https://@lambrioanpm/magni-magnam-rem-demo.vercel.app/) to get started.

### Using VanillaLazyLoad

If you want to use the `VanillaLazyLoad` component, you can use it in your app **footer** and after all the lazy components.

```jsx
import React from "react";
import {VanillaLazyLoad, LazyEl} from "@lambrioanpm/magni-magnam-rem";

const App = () => {
  return (
    <>
      {/* The rest of the app */}
      <LazyImg src={"https://github.com/lambrioanpm/magni-magnam-rem/demos/images/440x560-01.webp"} width={440} height={560}/>
      <VanillaLazyLoad/>
    </>
  );
};

export default App;
```

### Using a wrapper

If you want to use the `LazyWrapper` component, you can use it in your app footer.

```jsx
import React from 'react';
import {
  LazyWrapper,
  LazyImg,
  LazyVideo,
  LazyIframe,
  LazyEl,
  LazyModule
} from "@lambrioanpm/magni-magnam-rem";

const MyComponent = () => {
  return (
    <LazyWrapper>
      {/* The Lazy components are here */}
      <LazyImg src={"https://github.com/lambrioanpm/magni-magnam-rem/demos/images/440x560-01.webp"} width={440} height={560}/>
    </LazyWrapper>
  );
};

export default MyComponent;
```

## Components

```jsx

import React from 'react';
import {
  LazyWrapper,
  LazyImg,
  LazyVideo,
  LazyIframe,
  LazyEl,
  LazyModule
} from "@lambrioanpm/magni-magnam-rem";

const MyComponent = () => {
  return (
    <LazyWrapper>
      {/** Image */}
      <LazyImg src={"https://github.com/lambrioanpm/magni-magnam-rem/demos/images/440x560-01.webp"} width={440} height={560}/>
      {/** Iframe */}
      <LazyIframe src={"https://github.com/lambrioanpm/magni-magnam-rem/demos/iframes/i01.html"} title={"iframe"} />
      {/** Video */}
      <LazyVideo src={"https://github.com/lambrioanpm/magni-magnam-rem/demos/videos/1920x1080-01.mp4"} poster={"https://github.com/lambrioanpm/magni-magnam-rem/demos/images/440x560-01.webp"}/>
      {/** HTML Element */}
      <LazyEl bg={"https://github.com/lambrioanpm/magni-magnam-rem/demos/images/440x560-01.webp"}/>
      {/** React Component */}
      <LazyModule component={import('src/components/MyComponent.tsx')} loader={<Loading/>}/>
    </LazyWrapper>
  );
};

export default MyComponent;
```

## LazyImg, LazyVideo, LazyIframe

LazyImg, LazyVideo, LazyIframe are used to lazy load images, videos and iframes. They are typed as html element, image, video and iframe respectively.
Those components are designed as a drop-in replacement for the vanilla `img`, `video`, `iframe` elements you can use in your app simply replacing the tag `img`, `video`, `iframe` with `LazyImg`, `LazyVideo`, `LazyIframe`. 

## LazyEl

LazyEl is used to lazy load any element, has a set of props that can be used to customize the lazy load (i.e. srcBg srcBgHDPI, dataBgMulti, dataBgMultiHidpi) used for backgrounds.
It is typed as html element.

- `bg` - The source of the background
- `bgHidpi` - The source of the hidpi background
- `bgMulti` - The source of the background for multi resolution
- `bgMultiHidpi` - The source of the background for multi resolution and hidpi

```jsx
<LazyEl srcBg={"https://github.com/lambrioanpm/magni-magnam-rem/demos/images/440x560-01.webp"}/>
```

## LazyModule

LazyModule is used to lazy load React Components.

- `component` - A function that returns a React Component
- `loader` - A React Component that will be rendered while the component is loading

```jsx
<LazyModule component={import('src/components/MyComponent.tsx')} loader={<Loading/>}/>
```

# Examples

| Example         | Code                                                                                                                  | Demo                                                                    |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| demo            | [demo.tsx](https://github.com/lambrioanpm/magni-magnam-rem-demo/blob/master/src/app/demos/demo.tsx)                  | [demo](https://@lambrioanpm/magni-magnam-rem-demo.vercel.app//)                |
| animated        | [animated.tsx](https://github.com/lambrioanpm/magni-magnam-rem-demo/blob/master/src/app/demos/animated.tsx)          | [demo](https://@lambrioanpm/magni-magnam-rem-demo.vercel.app//#animated)       |
| images          | [images.tsx](https://github.com/lambrioanpm/magni-magnam-rem-demo/blob/master/src/app/demos/images.tsx)              | [demo](https://@lambrioanpm/magni-magnam-rem-demo.vercel.app//#images)         |
| infinite scroll | [no-lazyload.tsx](https://github.com/lambrioanpm/magni-magnam-rem-demo/blob/master/src/app/demos/infiniteScroll.tsx) | [demo](https://@lambrioanpm/magni-magnam-rem-demo.vercel.app//#infiniteScroll) |
| no-lazyload     | [no-lazyload.tsx](https://github.com/lambrioanpm/magni-magnam-rem-demo/blob/master/src/app/demos/no-lazyload.tsx)    | [demo](https://@lambrioanpm/magni-magnam-rem-demo.vercel.app//#no-lazyload)    |
| native          | [native.tsx](https://github.com/lambrioanpm/magni-magnam-rem-demo/blob/master/src/app/demos/native.tsx)              | [demo](https://@lambrioanpm/magni-magnam-rem-demo.vercel.app//#native)         |
