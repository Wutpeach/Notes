# 表格总览
| <img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624849967689-c348504d-fe73-478b-b9aa-dafcc4451717.png" alt="RGBA2Color.png " style="zoom:100%;" />**RGBA to Color** | 这个节点独立设置红、绿、蓝和Alpha的值，并输出一个颜色属性。  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![Color2RGBA.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624849972845-fea19f51-ce85-4505-8faa-acfd8b9bcd69.png)**Color to RGBA** | 该节点将一个颜色属性分割成其RGBA组件。|
| ![HSVA2Color.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624849978093-71108ec8-3bad-4ddc-ae46-b18dd992c0a7.png)**HSLA to Color** | 这个节点独立设置色调、饱和度、亮度和Alpha的值，并输出一个颜色属性。 |
| ![ColorTransform.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624849983484-0fdf97d9-6a1f-47fb-9fc7-9c63bfc77e66.png)**Color Transformer** | 这个节点对色调、饱和度、亮度和Alpha的值进行独立偏移，并输出一个颜色属性。 |

# RGBA to Color
这个节点需要四个0到255之间的整数值来指定红、绿、蓝和Alpha通道。
RGB值被转换为一个颜色输出属性。A值被转换为Alpha输出属性，范围从0%到100%。
**最直观的作用就是把颜色属性外调，可以用滑块或者key Animation节点单独控制**

<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624850148045-c09b3a31-60c5-4021-ae4e-7ad03d3e3ba8.png" alt="Snipaste_2021-06-28_11-15-36.png" style="zoom:50%;"/>

# HSLA to Color
这个节点设定色调、饱和度、亮度和Alpha的四个整数值，并将它们转换为颜色Outputs属性。
# Color to RGBA
这个节点Inputs一个颜色值并提供相应的RGBA值作为Ouopus属性。以及输出一个额外的AlphaValue属性提供0%到100%范围内的Alpha。

<img src="https://cdn.nlark.com/yuque/0/2021/png/12794363/1624850319685-a0ef2999-5b12-4155-902b-8de2471f068c.png" alt="Snipaste_2021-06-28_11-17-38.png" style="zoom:55%;" />

# Color Transformer（转换器）
颜色转换器接收一个ARGB颜色值，并对H、S、V、A值进行偏移。
如果要把颜色赋予材质球，记得加一个**ColorValue**

> **ColorValue**节点将输出的颜色和alpha属性分开。

![Snipaste_2021-06-28_11-23-52.png](https://cdn.nlark.com/yuque/0/2021/png/12794363/1624850648694-18c40a64-608a-4e31-aac4-cc0b24aa5345.png)
# Color Picker
Color Picker Node（拾色器节点）对于从现有的纹理属性中提取一个颜色值很有用。与Texture Loader的Color Picker Properties相比，Color Picker Node可以对任何纹理属性进行采样，例如，来自Offscreen Render Target的纹理。
## PosX和PosY
PosX和PosY定义了节点应该对像素进行采样的位置。它们的范围是从0到1，其中0,0是右上角，1,1是左下角。
## Radius（半径）
Radius是像素应该被取样的范围，产生的颜色是纹理中所有取样像素的平均值，给定的位置位于取样像素的中心。



