# 欢迎来到 ManimCE 中文教程

<br>

## 目录 Table of Contents:

-  [编程环境配置](#编程环境配置)
-  [创建虚拟环境](#创建虚拟环境)
-  [安装依赖文件](#安装依赖文件)
-  [安装 manim ](#安装-manim)
-  [安装配置 Jupyter](#安装配置-Jupyter)
-  [导入 manim 库](#导入-manim-库)
-  [第一个 Scene](#第一个-Scene)
-  [定位 Mobjects 并将其移动](#定位-Mobjects-并将其移动)
-  [方法的动画:`.animate` 语法](#方法的动画)
-  [排版打印数学公式](#排版打印数学公式)
-  [一些更专业的例子](#一些更专业的例子)

<br>

中文版 **Jupyter Notebook** 演示文件在本库的：First Steps with Manim.ipynb，需要将其下载下来，放到 **Jupyter Notebook** 的默认运行路径下，运行 **Jupyter Notebook**，然后在自动跳转的网页中打开。


> *其他相关资源:* [Documentation](https://docs.manim.community), [Discord](https://discord.gg/mMRrZQW), [Reddit](https://www.reddit.com/r/manim/)

## 编程环境配置

需要安装两个软件：

[`Anaconda`](https://www.anaconda.com/products/individual)：一个开源的 Python 和 R 语言的发行版本，常用于计算科学，其致力于简化软件包管理系统和部署。

[`MikTeX`](https://miktex.org/download)：一款免费的跨平台文字处理系统，包含了 TeX 及其相关程序。

点击软件名即可跳转下载链接，下载后直接按照提示步骤默认安装即可，由于安装过程简单，此处不加赘述。

## 创建虚拟环境

利用 `Anaconda` 新建开发环境(虚拟环境)，这样可以进行多版本的灵活切换，避免很多版本冲突问题。

在 `Anaconda Navigator` 中的 `Environments` 里，点击 `base（root）` 的右边箭头，`Open Terminal` 打开终端，可发现上图的路径前有一个 `（base）`，这说明当前运行环境为主系统环境。

输入 `conda create -n <虚拟环境名>`，回车。这时在 `cmd` 中就可以激活并进入该新建的环境了。

在 `cmd` 中激活该环境可以用 `conda activate <虚拟环境名>` ，取消激活可以用 `conda deactivate`。

<b>注</b>：此步骤中使用 `开始 -> Anaconda -> Anaconda Prompt` 也可以实现同 `cmd` 一样的效果。

## 安装依赖文件

在该虚拟环境下，安装一个 3.9 版本的 Python（当前 manimCE 版支持 3.7-3.9 版本的 Python），输入：`conda install python=3.9`，回车。

再安装提供影视串流功能的 ffmpeg，输入：`conda install ffmpeg`，回车。

## 安装 manim 

manim Community Edition 可以使用 pip 工具直接安装，非常方便。直接输入：`pip install manim`，回车。

## 安装配置 Jupyter

在命令行运行生成视频时代码与结果分离，不易于对照与比较，如果使用 `Jupyter Notebook` 则可以达到很好的视觉效果，也方便记录编程的过程。安装完 `Anaconda` 之后，系统会默认在主系统环境中安装 `Jupyter Notebook`，为了在虚拟环境中使用 `Jupyter Notebook`，需要再在虚拟环境中安装一次。

### 在虚拟环境中安装 Jupyter

在激活新环境的基础上(可以看到命令行开头处的括号内显示新的环境名)，输入 `conda install jupyter notebook`，安装 `Jupyter Notebook`。

为了在虚拟环境中运行 `Jupyter Notebook`，一方面需要在虚拟环境中安装 `Jupyter Notebook`，另一方面，要安装一个插件 `conda install nb_conda`，之后再打开 `Jupyter Notebook`，在 `new` 按钮下将多出不同环境的选项。

### 更改默认路径

输入 `jupyter notebook --generate-config` ，可以生成一个路径配置文件，用以配置 `Jupyter` 每次打开时的默认路径。

该新生成的文件路径一般在 `C:\Users\<User_name>\.jupyter\jupyter_notebook_config.py` 中。

打开该文件，找到 `## The directory to use for notebooks and kernels.` 这一行。将其下 `c.NotebookApp.notebook_dir =` 一行开头的 `#` 删除并添加自己的路径（注意：路径的分隔符要由 `\` 改为 `\\`，或者，在`路径`前加 r），然后保存。

那么下一次从 `Anaconda Navigator` 打开 `Jupyter Notebook` 的时候，将跳转到自定义的路径。（如果还是不行，可能是因为 Jupyter 快捷方式的属性中，路径一行的末尾存在 `%USERPROFILE%`，进而导致设置无效，将 `%USERPROFILE%` 删去即可。）

### 优化编程界面

点击打开 [`Jupyter themes`](https://github.com/dunovank/jupyter-themes) 找到优化方法。
由于 `Anaconda` 中不包含这个包，所以这里需要用 `pip` 进行安装。

输入 `pip install jupyterthemes` 进行安装，后面可以通过 `pip install --upgrade jupyterthemes` 进行升级。

可参考输入配置参数：`jt -t oceans16 -f fira -fs 17 -cellw 90% -ofs 14 -dfs 14 -T` 进行优化界面配置。

### 代码自动补全

`Jupyter Notebook` 代码自动补全
先关闭 `Jupyter Notebook` ，在 `Anaconda Navigator` 中的 `Environments` 里，点击 `<virtual env name>` 的右边箭头，`Open Terminal` 打开终端，输入:
```
pip install jupyter_contrib_nbextensions && jupyter contrib nbextension install
```

然后运行:
```
jupyter contrib nbextension install --user --skip-running-check
```

从 `Anaconda Navigator` 打开 `Jupyter Notebook`，会发现多了一个 `Nbextes` 选项，点击并勾选里面的 `Hinterland` 和 `Table of Contents`。

配置完毕！

### 快捷键

* `Enter` ：进入编辑模式
* `Esc` ：进入命令模式
* `Y` ：单元转入代码状态
* `M` ：单元转入 `markdown` 状态
* `R` ：单元转入 `raw` 状态
* `Ctrl+Enter` ：运行
* `O` ：展开折叠输出
* `H` ：显示快捷键
* `A` ：在上方插入代码块
* `B` ：在下方插入代码块
* `D,D`：删除代码块

## 导入 manim 库

打开 `Jupyter Notebook`，在虚拟环境中新建文件，或打开已有文件后通过 `Kernel -> Change Kernel -> Python [conda env:<虚拟环境名>]`。

在代码块中输入 `import *` 来导入 manim 中的所有库。点击 *Run* 按钮或 `Shift`+`Enter` 或 `Ctrl`+`Enter` 来运行。

第二行是用来控制输出视频的展示画面的宽度，可根据自己的需要进行调整。


```python
from manim import *

config.media_width = "60%"
```


<pre style="white-space:pre;overflow-x:auto;line-height:normal;font-family:Menlo,'DejaVu Sans Mono',consolas,'Courier New',monospace">Manim Community <span style="color: #008000; text-decoration-color: #008000">v0.13.1</span>

</pre>



如果运行成功，将会输出已安装的 manim 的版本。

## 第一个 Scene

manim 通过实例化 *Scenes* 来生成视频。这些 *Scenes* 实际上是一系列特殊 *类* 的实例，它们都拥有一个用以描述动画的 `construct` 方法。(为了方便本教程的描述，这里没有顾及读者是否熟悉 Python 或诸如 *类* 、 *方法* 等面向对象语言的专业术语，不过如果读者想继续学习 manim，有必要先学习一下 Python 编程基础。)

运行下面的例子，查看输出的视频。


```python
%%manim -v WARNING -qm CircleToSquare

class CircleToSquare(Scene):
    def construct(self):
        blue_circle = Circle(color=BLUE, fill_opacity=0.5)
        green_square = Square(color=GREEN, fill_opacity=0.8)
        self.play(Create(blue_circle))
        self.wait()
        
        self.play(Transform(blue_circle, green_square))
        self.wait()
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\CircleToSquare_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Circle To Square
    </image>
    </p>


尽管这个例子中大部分代码看上去是不言自明是，这里仍需要一步步详细地进行说明。

首先，
```
%%manim -v WARNING -qm CircleToSquare
```
是一个 *魔术指令 (magic command)*，该指令仅对 `Jupyter notebook` 有效。这条命令等价于在终端调用 manim 命令。

`-v WARNING` 将隐去所有暂时用不到的输出信息 (如果你想看这些信息，可以将命令中的这部分代码去掉)。标志 `-qm` 控制输出视频的画面质量，它是 `--quality=m` 的缩写，即中等质量。这意味着输出的视频将为 30帧 720p。(可以尝试将其改为 `-qh` 或 `-ql` 分别代表 *高 (high)* 、 *低 (low)* 质量。)

`CircleToSquare` 为 *Scene* 类实例化之后的名称。之后几句分别为：
```py
class CircleToSquare(Scene):
    def construct(self):
        [...]
```
`def` 后面的这个整体定义了这个名为 `CircleToSquare` 的 manim 实例，该实例中的 `construct` 方法中精确描述了将展现怎样的动画内容及效果，其可被看做是一张描绘着该动画内容及效果的 *蓝图*。
```py
blue_circle = Circle(color=BLUE, fill_opacity=0.5)
green_square = Square(color=GREEN, fill_opacity=0.8)
```
前两行分别创建了名为 `Circle` 和 `Square` 的两个 Mobject 对象，它们分别拥有各自的颜色及填充透明度。 但是，它们尚未加入到动画场景中。为了展现，需要用到 `self.add`，或者 ...
```py
self.play(Create(blue_circle))
self.wait()
```
... 将一个 manim 对象 (*Mobject*) 添加到场景中的过程以动画形式展现出来。在该方法中 `self` 代表的是当前场景，`self.play(my_animation)` 可以解释为："*该场景中需要演示我的动画*" 。

`Create` 就是一个动画，不过这里还有很多其他类型的动画 (例如 `FadeIn`，或者 `DrawBorderThenFill`，可以自行尝试!)。调用 `self.wait()` 的目的就如你想的那样，让动画画面暂停一会儿 (默认是 1 秒)。如果改为 `self.wait(2)`，将暂停两秒。

最后两行，
```
self.play(Transform(blue_circle, green_square))
self.wait()
```
用于展现从蓝色圆圈到绿色方块的变化过程 (并加上 1 秒的暂停)。

## 定位 Mobjects 并将其移动

<b>新问题</b>：创建一个场景，其中创建圆圈，同时在其下方写出一些文字。可以复用上面给出的蓝色圆圈，然后再加些新代码。


```python
%%manim -v WARNING -qm HelloCircle

class HelloCircle(Scene):
    def construct(self):
        # blue_circle = Circle(color=BLUE, fill_opacity=0.5)
        # 此处也可以先创建一个“默认的”圆圈，再通过 set 方法添加自己想要的属性！
        circle = Circle()
        blue_circle = circle.set_color(BLUE).set_opacity(0.5)
        
        label = Text("A wild circle appears!")
        label.next_to(blue_circle, DOWN, buff=0.5)
        
        self.play(Create(blue_circle), Write(label))
        self.wait()
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\HelloCircle_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Hello Circle
    </image>
    </p>

显然，文字可以使用名为 `Text` 的 Mobject 对象来创建，其所处位置由下面一行代码实现：
```py
label.next_to(blue_circle, DOWN, buff=0.5)
```
Mobject 对象有好几种方法实现定位，`next_to` 是其中之一 (`shift`, `to_edge`, `to_corner`, `move_to` 则是另外一些 – 具体可通过搜索框查阅 [documentation](https://docs.manim.community/) )。对于 `next_to` 方法，第一个参数 (`blue_circle`) 代表 `label` 所附着的 Mobject 对象。第二个参数(`DOWN`)，描述了附着的方向 (可以改为 `LEFT`，`UP`，或 `RIGHT` 试试！)。最后，`buff=0.5` 控制了 `blue_circle` 和 `label` 这两个 Mobject 间的距离，增大赋值将使得 `label` 向下方远离 `blue_circle`。

另外需要注意的是，这里 `self.play` 的调用形式也发生了改变：可以将多个动画参数同时赋予 `self.play` 方法，那么这些动画将同步展现。如果想一个接着一个地展现，那么就将 `self.play` 方法分开来写为几行：
```py
self.play(Create(blue_circle))
self.play(Write(label))
```
并看看有什么变化。

顺便说一下，Mobject 对象自带与定位无关的方法：例如，为了得到蓝色圆圈，也可以创建一个默认的圆圈，然后设置其颜色和不透明度：
```py
circle = Circle()
blue_transparent_circle = circle.set_color(BLUE)
blue_circle = blue_transparent_circle.set_opacity(0.5)
```
也可将上面的代码简写为：
```py
blue_circle = Circle().set_color(BLUE).set_opacity(0.5)
```
像这样，可以直接在名为 `Circle` 的圆圈上附加属性。

## 方法的动画

在上一个例子中，用到了 `.next_to` 方法，这是一种修改 Mobject 对象位置的方法。但如何去演示出这些方法对 Mobject 对象的作用过程，或者说方法 `.shift` 、 `.rotate` 或者 `.scale` 到底是如何影响一个 Mobject 对象的？那么，`.animate` 语法就是该问题的答案，让我们看看这个例子。


```python
%%manim -v WARNING -qm CircleAnnouncement

class CircleAnnouncement(Scene):
    def construct(self):
        blue_circle = Circle(color=BLUE, fill_opacity=0.5)
        announcement = Text("Let us draw a circle.")
        
        self.play(Write(announcement))
        self.wait()
        
        self.play(announcement.animate.next_to(blue_circle, UP, buff=0.5))
        self.play(Create(blue_circle))
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\CircleAnnouncement_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Circle Announcement
    </image>
    </p>


在一般通过 `announcement.next_to(blue_circle, UP, buff=0.5)` 来实现定位的地方，前置调用一个 `.animate` 方法，将其后的方法转为动画，并通过 `self.play` 方法演示出了。下面的例子展现了几种方法的作用于 Mobject 对象的过程动画：


```python
%%manim -v WARNING -qm AnimateSyntax

class AnimateSyntax(Scene):
    def construct(self):
        triangle = Triangle(color=RED, fill_opacity=1)
        self.play(DrawBorderThenFill(triangle))
        self.play(triangle.animate.shift(LEFT))
        self.play(triangle.animate.shift(RIGHT).scale(2))
        self.play(triangle.animate.rotate(PI/3))
        self.play(triangle.animate.set_color(GREEN))
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\CircleAnnouncement_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Circle Announcement
    </image>
    </p>


第一个 `.play` 方法创建了一个三角形；第二个 `.play` 将该三角形往左移动一个单位；第三个 `.play` 将其向右移回去，并同时放大到原来的两倍；第四个 `.play` 将其逆时针旋转 $\pi/3$ (可以修改一些参数，并再次运行上面的代码，例如 `set_color`)。


```python

```

当你仔细看上面那个例子时，将会发现，旋转过程并不是真正的 “旋转”，而是直接变换到了转动后的一个版本。但其三个角划过的并不是圆弧（尽管其本应绕着三角形的中心旋转），而是几条直线段。这个动画给人留下的印象是：该三角形先缩小然后又扩大。 

这并非是一个 **bug**，纯属 `.animate` 语法作用的效果：动画是根据初始 (Mobject 对象 `triangle`) 和最终 (旋转后的 Mobject 对象 `triangle.rotate(PI/3)`) 的两个特定状态构建。manim 试图通过插值的方式将这两种状态联系起来，但却不知道如何平滑过渡。下面的例子将清晰地说明这一点：


```python
%%manim -v WARNING -qm DifferentRotations

class DifferentRotations(Scene):
    def construct(self):
        left_square = Square(color=BLUE, fill_opacity=0.7).shift(2*LEFT)
        right_square = Square(color=GREEN, fill_opacity=0.7).shift(2*RIGHT)
        self.play(left_square.animate.rotate(PI), Rotate(right_square, angle=PI), run_time=2)
        self.wait()
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\DifferentRotations_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Different Rotations
    </image>
    </p>


## 排版打印数学公式

manim 支持 LaTeX，该标识语言常用于数学排版中。详情请见 [$LaTeX$ 30 分钟教程](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes).

下面是一些在 manim 中使用 $LaTeX$ 的实例：


```python
%%manim -v WARNING -qm CauchyIntegralFormula

class CauchyIntegralFormula(Scene):
    def construct(self):
        formula = MathTex(r"[z^n]f(z) = \frac{1}{2\pi i}\oint_{\gamma} \frac{f(z)}{z^{n+1}}~dz")
        self.play(Write(formula), run_time=3)
        self.wait()
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\CauchyIntegralFormula_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Cauchy Integral Formula
    </image>
    </p>


正如该例所示，`MathTex` 对象可以被赋予简单的 (数学模式) $LaTeX$ 字符串。如果想赋予“一般模式”的 $LaTex$，则使用 `Tex`。

当然，manim 也可以实现排版公式转换的可视化。如下面的例子所示：


```python
%%manim -v WARNING -qm TransformEquation

class TransformEquation(Scene):
    def construct(self):
        eq1 = MathTex("42 {{ a^2 }} + {{ b^2 }} = {{ c^2 }}")
        eq2 = MathTex("42 {{ a^2 }} = {{ c^2 }} - {{ b^2 }}")
        eq3 = MathTex(r"a^2 = \frac{c^2 - b^2}{42}")
        self.add(eq1)
        self.wait()
        self.play(TransformMatchingTex(eq1, eq2))
        self.wait()
        self.play(TransformMatchingShapes(eq2, eq3))
        self.wait()
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\TransformEquation_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Transform Equation
    </image>
    </p>


在上面的例子中，`eq1` 和 `eq2` 有一些双花括号的位置，在通常情况下，$LaTeX$ 不会这样表达。这是一种特殊的 manim 符号，它以一种特殊的方式将生成的 Tex 对象' `eq1` 和 `eq2` 分组。

这种特殊的符号在使用 `TransformMatchingTex` 方法时很有用：它会将具有同样 TeX 字符串的部分相互转换 (例如，`a^2` 到 `a^2`)，如果没有这种特殊的符号，这个等式就会被当作一个很长的 TeX 字符串。相比之下，`TransformMatchingShapes` 方法就不那么智能了：它只是简单地尝试将“看起来相同”的形状转换成彼此的形状，尽管如此，它仍然非常有用。

如果您已经了解到这里，您应该对库的基本用法有了初步的印象。您可以在下面的例子中找到一些更高级的示例，它们说明了一些更专业的概念。继续，试着尝试并修改它们，就像你对上面的那些做的那样！请浏览文档 [documentation](https://docs.manim.community)，了解已经实现的内容，如果您想自己构建一些更复杂的对象，请查看源代码。

社区 [community](https://www.manim.community/discord/) 非常欢迎问题咨询，并且我们希望您能够分享自己编写的令人称奇的项目。**Happy *manimating*!**

## 一些更专业的例子

在深入研究这些示例之前：请注意，它们用更加专业的概念让您了解如何设置和编写更为复杂的场景。这些例子没有附带额外的解释，它们**不打算作为(入门级)学习资源**。


```python
%%manim -v WARNING -qm FormulaEmphasis

class FormulaEmphasis(Scene):
    def construct(self):
        product_formula = MathTex(
            r"\frac{d}{dx} f(x)g(x) =",
            r"f(x) \frac{d}{dx} g(x)",
            r"+",
            r"g(x) \frac{d}{dx} f(x)"
        )
        self.play(Write(product_formula))
        box1 = SurroundingRectangle(product_formula[1], buff=0.1)
        box2 = SurroundingRectangle(product_formula[3], buff=0.1)
        self.play(Create(box1))
        self.wait()
        self.play(Transform(box1, box2))
        self.wait()
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\FormulaEmphasis_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Formula Emphasis
    </image>
    </p>



```python
%%manim -v WARNING -qm PlotExample

class PlotExample(Scene):
    def construct(self):
        plot_axes = Axes(
            x_range=[0, 1, 0.05],
            y_range=[0, 1, 0.05],
            x_length=9,
            y_length=5.5,
            axis_config={
                "numbers_to_include": np.arange(0, 1 + 0.1, 0.1),
                "font_size": 24,
            },
            tips=False,
        )

        y_label = plot_axes.get_y_axis_label("y", edge=LEFT, direction=LEFT, buff=0.4)
        x_label = plot_axes.get_x_axis_label("x")
        plot_labels = VGroup(x_label, y_label)

        plots = VGroup()
        for n in np.arange(1, 20 + 0.5, 0.5):
            plots += plot_axes.plot(lambda x: x**n, color=WHITE)
            plots += plot_axes.plot(
                lambda x: x**(1 / n), color=WHITE, use_smoothing=False
            )

        extras = VGroup()
        extras += plot_axes.get_horizontal_line(plot_axes.c2p(1, 1, 0), color=BLUE)
        extras += plot_axes.get_vertical_line(plot_axes.c2p(1, 1, 0), color=BLUE)
        extras += Dot(point=plot_axes.c2p(1, 1, 0), color=YELLOW)
        title = Title(
            r"Graphs of $y=x^{\frac{1}{n}}$ and $y=x^n (n=1, 1.5, 2, 2.5, 3, \dots, 20)$",
            include_underline=False,
            font_size=40,
        )
        
        self.play(Write(title))
        self.play(Create(plot_axes), Create(plot_labels), Create(extras))
        self.play(AnimationGroup(*[Create(plot) for plot in plots], lag_ratio=0.05))
```


<p align="center"><image src="media\videos\examples\1080p60\PlotExample_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Plot Example
    </image>
    </p>


```python
%%manim -v WARNING -qm ErdosRenyiGraph

import networkx as nx

nxgraph = nx.erdos_renyi_graph(14, 0.5)

class ErdosRenyiGraph(Scene):
    def construct(self):
        G = Graph.from_networkx(nxgraph, layout="spring", layout_scale=3.5)
        self.play(Create(G))
        self.play(*[G[v].animate.move_to(5*RIGHT*np.cos(ind/7 * PI) +
                                         3*UP*np.sin(ind/7 * PI))
                    for ind, v in enumerate(G.vertices)])
        self.play(Uncreate(G))
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\ErdosRenyiGraph_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Erdos Renyi Graph
    </image>
    </p>



```python
%%manim -v WARNING -qm CodeFromString

class CodeFromString(Scene):
    def construct(self):
        code = '''from manim import Scene, Square

class FadeInSquare(Scene):
    def construct(self):
        s = Square()
        self.play(FadeIn(s))
        self.play(s.animate.scale(2))
        self.wait()
'''
        rendered_code = Code(code=code, tab_width=4, background="window",
                            language="Python", font="Monospace")
        self.play(Write(rendered_code))
        self.wait(2)
```

                                                                                                                           

<p align="center"><image src="media\videos\examples\1080p60\CodeFromString_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Code From String
    </image>
    </p>



```python
%%manim -qm -v WARNING OpeningManim

class OpeningManim(Scene):
    def construct(self):
        title = Tex(r"This is some \LaTeX")
        basel = MathTex(r"\sum_{n=1}^\infty \frac{1}{n^2} = \frac{\pi^2}{6}")
        VGroup(title, basel).arrange(DOWN)
        self.play(
            Write(title),
            FadeIn(basel, shift=UP),
        )
        self.wait()

        transform_title = Tex("That was a transform")
        transform_title.to_corner(UP + LEFT)
        self.play(
            Transform(title, transform_title),
            LaggedStart(*[FadeOut(obj, shift=DOWN) for obj in basel]),
        )
        self.wait()

        grid = NumberPlane(x_range=(-10, 10, 1), y_range=(-6.0, 6.0, 1))
        grid_title = Tex("This is a grid")
        grid_title.scale(1.5)
        grid_title.move_to(transform_title)

        self.add(grid, grid_title)
        self.play(
            FadeOut(title),
            FadeIn(grid_title, shift=DOWN),
            Create(grid, run_time=3, lag_ratio=0.1),
        )
        self.wait()

        grid_transform_title = Tex(
            r"That was a non-linear function \\ applied to the grid"
        )
        grid_transform_title.move_to(grid_title, UL)
        grid.prepare_for_nonlinear_transform()
        self.play(
            grid.animate.apply_function(
                lambda p: p + np.array([np.sin(p[1]), np.sin(p[0]), 0])
            ),
            run_time=3,
        )
        self.wait()
        self.play(Transform(grid_title, grid_transform_title))
        self.wait()
```

                                                                                                                           


<p align="center"><image src="media\videos\examples\1080p60\OpeningManim_ManimCE_v0.13.1.gif" controls autoplay loop style="max-width: 60%;"  >
      Opening Manim
    </image>
    </p>

