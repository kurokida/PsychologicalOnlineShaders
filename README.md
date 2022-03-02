# PsychologicalOnlineShaders

Using [GLSL shaders](https://developer.mozilla.org/en-US/docs/Games/Techniques/3D_on_the_web/GLSL_Shaders), complex visual stimuli in psychological experiments (e.g., gabor patches) can be drawn rapidly.

For traditional lab-based psychological experiments, [useful shaders have already been created](https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/master/Psychtoolbox/PsychOpenGL/PsychGLSLShaders). The goal of this repo is to share a large number of labo-based shaders in a form that can be used for online psychological experiments.

There are already several online experimental tools (e.g., [jsPsych](https://www.jspsych.org/7.1/), [PsychoPy](https://www.psychopy.org/), [lab.js](https://lab.js.org/), [Gorilla](https://gorilla.sc/), and [OSWeb](https://osdoc.cogsci.nl/3.3/manual/osweb/workflow/)). The development of these tools would be facilitated if the shaders could be shared because writing GLSL shaders requires exceptional programming skills.

# WebGL

> [WebGL](https://www.khronos.org/webgl/) is a cross-platform, royalty-free open web standard for a low-level 3D graphics API based on OpenGL ES, exposed to ECMAScript via the HTML5 Canvas element. Developers familiar with OpenGL ES 2.0 will recognize WebGL as a Shader-based API using GLSL, with constructs that are semantically similar to those of the underlying OpenGL ES API. 

Reference: [https://www.khronos.org/webgl/](https://www.khronos.org/webgl/)

# PixiJS

> [PixiJS](https://pixijs.com/) is a rendering library that will allow you to create rich, interactive graphics, cross platform applications, and games without having to dive into the WebGL API or deal with browser and device compatibility.

Reference: [https://pixijs.download/release/docs/index.html](https://pixijs.download/release/docs/index.html)

PixiJS is used by [PsychoJS](https://github.com/psychopy/psychojs) and I am currently developing [a plugin](https://jspsychophysics.hes.kyushu-u.ac.jp/) to incorporate PixiJS into [jsPsych](https://www.jspsych.org/7.1/).

There are probably two ways to write shaders using PixiJS: (a) using [PIXI.Filter]((https://pixijs.download/release/docs/PIXI.Filter.html)) and (b) using [PIXI.Shader](https://pixijs.download/release/docs/PIXI.Shader.html) and [PIXI.Mesh](https://pixijs.download/release/docs/.PIXI.Mesh.html) Here is [the demo program for (a)](https://pixijs.io/examples/#/filters-advanced/shadertoy-filter-rendertexture.js), and [the demo program for (b)](https://pixijs.io/examples/#/mesh-and-shaders/shadertoy-mesh.js)

# Sample code

I have successfully presented a gabor patch using PixiJS.Filter. See drifting_gabor.html. Each uniforms is consistent with that of [CreateProceduralGabor](http://psychtoolbox.org/docs/CreateProceduralGabor) although I added a new variable named disableGauss.

[Demonstration](https://www.hes.kyushu-u.ac.jp/~kurokid/PsychologicalOnlineShaders/drifting_gabor.html)

# Limitation

Currently, multiple gabor patches couldn't be presented in superimposed form although it is possible in a labo-based program provided by Psychtoolbox. See [GarboriumDemo](http://psychtoolbox.org/docs/GarboriumDemo). 

I have tried to create a program similar to the GarboriumDemo, but have yet to get it to work. See gabor_superposition.html.
Perhaps if we could do the same thing as the Psychtoolbox function below, multiple gabor patches can be presented in superimposed form.

```matlab
PsychImaging('AddTask', 'General', 'FloatingPoint32BitIfPossible');
```

The following is an excerpt from [the PsychImaging help page](http://psychtoolbox.org/docs/PsychImaging).

> 'FloatingPoint32Bit' Ask for a 32 bit floating point precision framebuffer. This allows more than 8 bit precision for complex drawing, compositing and image processing operations. It also allows alpha-blending with signed color values and intermediate results that are outside the displayable range, e.g., negative. Precision is about 6.5 digits behind the dezimal point or 8 million discriminable displayable levels. Be aware that only the most recent hardware (NVidia is able to perform alpha-blending at full speed in this mode. Enabling alpha-blending on older hardware may cause a significant decrease in drawing performance, or alpha blending may not work at all at this precision! If you'd like to have both, the highest precision and support for alpha-blending, specify 'FloatingPoint32BitIfPossible' instead. PTB will then try to use 32 bit precision if this is possible in combination with alpha blending. Otherwise, it will choose 16 bit precision for drawing & blending, but 32 bit precision at least for the post-processing.

[Incomplete demonstration](https://www.hes.kyushu-u.ac.jp/~kurokid/PsychologicalOnlineShaders/gabor_superposition.html)

As an alternative, I have created a program that presents only two gabor patches in superimposed form. See two_gabor_superposition.html and a [demonstration](https://www.hes.kyushu-u.ac.jp/~kurokid/PsychologicalOnlineShaders/two_gabor_superposition.html)
