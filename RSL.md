# RenderMan Shading Language Guide

First-pass-reading notes of "RenderMan Shading Language Guide" (2008).

## Table of Contents

- [Introduction to RSL and RenderMan](#introduction-to-rsl-and-renderman)

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
- *Dice*: Split primitives into micropolygons (four-sided bilinear patches).  Shading rate of 1 indicates each micropoygon needs to be the size of 1 pixel.  Porudction is usually 0.25 to 0.5, making each micropolygon a quarter or half the size of a pixel.
- *Shade* - the following shaders are run on the surface in order: displacement,surface, lights, volume (interior and exterior), and imager.
- *Bust and Bound*: Each micropolygon becomes individual primitives for the following on-screen test
- *Micropolygon Onscreen Test*: Cull away out-of-sight micropolygons.  This stage occurs after shading due to potential displacement operations.
- *Sample*: Sample micropolygons through pixels.  Smallests sampling rate is 1 by 1 (each pixel sampled once).
- *Composite and ilter* compositing  of sampled values.
