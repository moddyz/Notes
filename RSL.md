# RenderMan Shading Language Guide

First-pass-reading notes of "RenderMan Shading Language Guide" (2008).

## Table of Contents

- [Introduction to RSL and RenderMan](#introduction-to-rsl-and-renderman)
- [RSL Details](#rsl-details)

## Introduction to RSL and RenderMan

- _RenderMan Spec_ (*RiSpec*) provides a standard for reading a description file and rendering an image.
- RiSpec is composed of two separate parts - the _RenderMan Scene Description API_ (*RiAPI*) and _RenderMan Shading Language_ (*RSL*)
- The RiAPI tells the renderer what to render (information about the camera, image, geometry, and lights)
- RSL is a C-like language used to program shaders to control the look/apperance of an object.
- REYES (Render Everything You Ever Saw) is an rendering algorithm.  Emphasis on _speed_, _capability to handle large amonuts of data_, _memory efficiency_, and _motion blur_.
- To communicate the scene to the renderer, make direct RiAPI calls or parse a RIB file.
- _RenderMan interface Bytestream_ (RIB) is a compact and easier format for describing scenes.
- The RIB stream is parsed into RiAPI calls.
- Once the scene is described, the renderer enters a "splitting loop"  to break primitives into manageable pieces of geometry to be handled efficiently by renderer.

REYES Steps:
- *Bounding*: each geometry is assigned a bounding box (for subsequent on-screen tests)
- *Onscreen Test*: bounded geometry are tested against camera frustum to see if they can be culled.
- *Size Test*: ???
- *Dice*: Split primitives into micropolygons (four-sided bilinear patches).  Shading rate of 1 indicates each micropoygon needs to be the size of 1 pixel.  Production is usually 0.25 to 0.5, making each micropolygon a quarter or half the size of a pixel.
- *Shade* - the following shaders are run on the surface in order: displacement,surface, lights, volume (interior and exterior), and imager.
- *Bust and Bound*: Each micropolygon becomes individual primitives for the following on-screen test
- *Micropolygon Onscreen Test*: Cull away out-of-sight micropolygons.  This stage occurs after shading due to potential displacement operations.
- *Sample*: Sample micropolygons through pixels.  Smallest pixel sampling rate is 1 by 1 (each pixel sampled once).
- *Composite and ilter* compositing  of sampled values.

Anatomy of a RIB file:
- `RiBegin` and `RiEnd` can be omitted from the RIB.  The calling render command will initialize Ri state.
- `FrameBegin`/`FrameEnd` block specifies what goes into a single frame.
- A RIB file can describe multiple frames.
- _Options_ and _attributes_ allow user to control the renderer. 
- Options remain constant throughout a frame.  Option values (ie. output image resolution) are frozen on `WorldBegin` and reset on `WorldEnd`.
- Attributes allow modification of the current piece of geometry that is being defined.
- Attributes are stored as a stack (pushed and popped)
- `AttributeBegin`/`AttributeEnd` for pushing/popping attrs.
- Similarly `TransformBegin`/`TransformEnd` for pushing/popping transformations.
- RIB uses commands to delimit commands.
- Comments prefixed with # can be added 

Image control options
- `Format` declares the horizontal, vertical, and pixel aspect ratio of the image. ex. `Format 640 480 1.2`
- `Projection` defines the camera projection parameters (how does the 3D scene project to a 2D image).  ex. `Projection "perspective" "fov" [37.84929]`
- `Clipping` defines the near and far plane of the viewing volume. 
- `Display` defines what to do with the computed pixel values. The target to store pixels is called a _display driver_, renderers must support both _file driver_ and _framebuffer driver_.  The command is in the form Display ImageName DisplayDriver ImageMode. ex. `Display "myimage.tiff" "tiff" "rgba"
- `PixelSamples` and `ShadingRate` control the quality of render.  PixelSamples controls the number of samples performed on the X/Y axis of a pixel.  ShadingRate determines the micropolygon dicing amount.
- `PixelFilter` controls the how sampled values are composited together into the final pixel. ex. `PixelFilter box 8 8`

## RSL Details

