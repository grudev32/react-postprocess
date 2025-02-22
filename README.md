# react-postprocess

[![Version](https://img.shields.io/npm/v/@react-three/postprocess?style=flat&colorA=000000&colorB=000000)](https://www.npmjs.com/package/@react-three/postprocess)
[![Storybook](https://img.shields.io/static/v1?message=Storybook&style=flat&colorA=000000&colorB=000000&label=&logo=storybook&logoColor=ffffff)](https://pmndrs.github.io/react-postprocess)
[![Downloads](https://img.shields.io/npm/dt/@react-three/postprocess.svg?style=flat&colorA=000000&colorB=000000)](https://www.npmjs.com/package/@react-three/postprocess)
[![Discord Shield](https://img.shields.io/discord/740090768164651008?style=flat&colorA=000000&colorB=000000&label=discord&logo=discord&logoColor=ffffff)](https://discord.gg/ZZjjNvJ)
[![Open in GitHub Codespaces](https://img.shields.io/static/v1?&message=Open%20in%20%20Codespaces&style=flat&colorA=000000&colorB=000000&label=GitHub&logo=github&logoColor=ffffff)](https://github.com/codespaces/new?template_repository=pmndrs%2Freact-postprocess)

`react-postprocess` is a
[postprocess](https://github.com/pmndrs/postprocess) wrapper for
[@react-three/fiber](https://github.com/pmndrs/react-three-fiber). This is not
(yet) meant for complex orchestration of effects, but can save you
[hundreds of LOC](https://twitter.com/0xca0a/status/1289501594698960897) for a
straight forward effects-chain.

```bash
npm install @react-three/postprocess
```

<p align="center">
  <a href="https://pqrpl.csb.app" target="_blank"><img width="274" src="bubbles.jpg" alt="Bubbles" /></a>
  <a href="https://5jgjz.csb.app" target="_blank"><img width="274" src="control.jpg" alt="Take Control" /></a>
</p>
<p align="middle">
  <i>These demos are real, you can click them! They contain the full code, too. 📦</i>
</p>

#### Why postprocess and not three/examples/jsm/postprocess?

> This library provides an EffectPass which automatically organizes and merges
> any given combination of effects. This minimizes the amount of render
> operations and makes it possible to combine many effects without the
> performance penalties of traditional pass chaining. Additionally, every effect
> can choose its own blend function.
>
> All fullscreen render operations also use a single triangle that fills the
> screen. Compared to using a quad, this approach harmonizes with modern GPU
> rasterization patterns and eliminates unnecessary fragment calculations along
> the screen diagonal. This is especially beneficial for GPGPU passes and
> effects that use complex fragment shaders.

Postprocess also supports srgb-encoding out of the box, as well as WebGL2
MSAA (multi sample anti aliasing), which is react-postprocess's default, you
get high performance crisp results w/o jagged edges.

#### What does it look like?

Here's an example combining a couple of effects
([live demo](https://codesandbox.io/s/react-postprocess-dof-blob-pqrpl?)).

<a href="https://codesandbox.io/s/react-postprocess-dof-blob-pqrpl?" target="_blank" rel="noopener">
<img src="bubbles.jpg" alt="Bubbles Demo" />
</a>

```jsx
import React from 'react'
import { Bloom, DepthOfField, EffectComposer, Noise, Vignette } from '@react-three/postprocess'
import { Canvas } from '@react-three/fiber'

function App() {
  return (
    <Canvas>
      {/* Your regular scene contents go here, like always ... */}
      <EffectComposer>
        <DepthOfField focusDistance={0} focalLength={0.02} bokehScale={2} height={480} />
        <Bloom luminanceThreshold={0} luminanceSmoothing={0.9} height={300} />
        <Noise opacity={0.02} />
        <Vignette eskil={false} offset={0.1} darkness={1.1} />
      </EffectComposer>
    </Canvas>
  )
}
```

## Documentation

- [react-postprocess docs](https://docs.pmnd.rs/react-postprocess)
- [postprocess docs](https://pmndrs.github.io/postprocess/public/docs/)
