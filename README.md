# manimce
##Examples of Scene and Study Notes based on **Manim Community Edition** :video_camera:

The Manim Community Edition is developed by Manim Community, which is named manim on `pip`.[<sup>[1]</sup>](#refer-anchor-1)

## Table of Contents:

-  [Prerequisites](#prerequisites)
-  [Installation](#installation)
-  [Testing](#testing)

<br>

## Prerequisites
Manim has a few dependencies that need to be installed before it can be used. All the softwares need to be add to the PATH of System Environment Variable.

- ###[Anaconda](https://www.anaconda.com/products/individual) (Toolkit with thousands of open-source packages and libraries.)
- ###[MikTeX](https://miktex.org/download) (A modern TeX distribution for Windows, Linux and macOS.)
- ###[ffmpeg](https://ffmpeg.org/download.html) (The leading multimedia framework.)

<br>

## Installation

Manim Community runs on Python 3.7+ can be installed from via `pip`:

```bash
pip install manim
```
<br>

## Testing

Creating a .py file named `scene.py` with contents:

```python
from manim import *

class SquareToCircle(Scene):
    def construct(self):
        circle = Circle()
        square = Square()
        square.flip(RIGHT)
        square.rotate(-3 * TAU / 8)
        circle.set_fill(PINK, opacity=0.5)

        self.play(Create(square))
        self.play(Transform(square, circle))
        self.play(FadeOut(square))
```

Then, run the following in Anaconda Prompt in Administrator mode after `cd` to the folder which contains `scene.py`:

```bash
manim -p -ql scene.py SquareToCircle
```
<br>
A video will play the following animation.

<div align = "center">
<img src = ".\src\SquareToCircle.gif"  width=80%>
</div>

<br>

### The general command line arguments of Manim is as follows:

<div align = "center">
<img src = ".\src\command.png"  width=80%>
</div>

<br>


<div id="refer-anchor-1"></div>
- [1] The Manim Community Developers, [Manim – Mathematical Animation Framework (Version v0.9.0)](https://www.manim.community/). 2021.

