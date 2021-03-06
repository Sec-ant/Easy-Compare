# Easy Compare

## :book: 介绍 Introduction

一个作用于任何页面的、用于方便地比较截图的用户脚本。多用于各大 PT 站点的对比截图比较，灵感来自于 PTP 的截图比较脚本，但源码完全不同。

> **Easy Compare** is a userscript, that applied to any page, aiming to make screenshot comparison handy. This can be widely used in many PT sites. The idea comes from the official **PTP Show comparison** script, but the code is completely original.

## :balloon: 特性 Features

- 在任何页面，将鼠标移动到页面右上角，找到触发的按钮（灰色），等待按钮图标变绿后，点击，即可激活比较模式；
  
  > Move the mouse cursor to the upper right of the page and try to find the button (in grey), wait till it turns into green and click it to active compare mode;
  
  ![icon](https://raw.githubusercontent.com/Sec-ant/Easy-Compare/master/assets/icon%20gray.svg?sanitize=true) ![icon](https://raw.githubusercontent.com/Sec-ant/Easy-Compare/master/assets/icon%20green.svg?sanitize=true)

- 可以在任何页面“就地”进行截图对比，无需重新下载上传；

  > Compare screenshots in place without downloading/uploading images to other sites;

- 支持不同的图床，有可扩展性；

  > Support multiple image hosts, which can be configured and extended;

- 进入截图比较模式后，鼠标悬浮在页面图片上方，即可在浏览器中央显示该图的原图。将鼠标在不同的图片上悬停，即可在浏览器中央切换不同图片的原图；

  > When activated, hover your mouse above an image on the page, the original image of which will be displayed over the center of the page. Move your mouse among different images on the page and you can switch different original images of them over the center of the page;

- 配合快捷键可以很方便地比较不相邻的图片；

  > Non-adjacent images can be compared easily when using hot-keys;

- 支持 **Image Diff**，即像素级别比较两张图片中的差异并通过颜色标出。该功能需配合 `Shift` 键使用，按下 `Shift` 键时，当前活动图片会作为基准图片，通过鼠标或键盘快捷键移动到其他图片上时（移动时需按住 `Shift` 不放），便会将基准图片与该图片进行比较，比较结束后结果会显示在浏览器中央，并可通过 `ArrowUp`、`ArrowDown`、`ArrowLeft`、`ArrowRight` 或 `I/i`、`K/k`、`J/j`、`L/l` 快捷键调整该比较的阈值/敏感度。该功能核心代码来自于[mapbox/pixelmatch](https://github.com/mapbox/pixelmatch)；

  > **Image Diff** is supported, which is comparing two images pixel-wisely and marking all the different pixels with colors. This feature requires the `Shift` key. When `Shift` is pressed down, the active image will be used as the base image. When users move the cursor to another image or use the hot-keys to focus on another image (`Shift` needs holding in the mean time), the base image will be compared to that image, and the result will be displayed over the center of the page when diffing is finished. Users can use `ArrowUp`, `ArrowDown`, `ArrowLeft`, `ArrowRight` or `I/i`, `K/k`, `J/j`, `L/l` hot-keys to adjust the threshold/sensitivity of the diffing result. The image diff core function is from [mapbox/pixelmatch](https://github.com/mapbox/pixelmatch);

- 支持 **Solar Curve** 曲线滤镜，使用该滤镜可以很清晰地看到图像中的色带等瑕疵；

  > **Solar Curve** filter is supported for better recognition of bandings or other defects in the image, making it more friendly to human eyes;

  |                                              Solar Curve                                               |                                                     Comparisons of bandings under Solar Curve filter                                                     |
  | :----------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------: |
  | ![Solar Curve](https://raw.githubusercontent.com/Sec-ant/Easy-Compare/master/assets/solar%20curve.png) | ![Bandings under Solar Curve filter](https://raw.githubusercontent.com/Sec-ant/Easy-Compare/master/assets/bandings%20under%20solar%20curve%20filter.png) |

- 配合快捷键可以进行一些便捷操作，包括：

  > Several hot-keys are supported for better user experience, including:

  |      键 Key      | 功能                                                               | Function                                                                           |
  | :--------------: | ------------------------------------------------------------------ | ---------------------------------------------------------------------------------- |
  |      `Esc`       | 退出截图比较模式                                                   | Deactivate compare mode                                                            |
  |      `Q/q`       | 半透明化截图比较界面，以便显示出原页面中的元素                     | Semi-transparentize the interface, allowing user to view the elements on the page  |
  |      `W/w`       | 跳到往前数第 `num` 张图片并显示                                    | Jump to the nth previous image and display                                         |
  |      `E/e`       | 跳到往后数第 `num` 张图片并显示                                    | Jump to the nth next image and display                                             |
  |    `Num Key`     | `num` 的值，默认是 `1`，有效值为 `0`-`9`，`0` 代表 `10`            | The value of `n` in "nth". `0`-`9` are valid numbers and `0` is recognized as `10` |
  |     `Shift`      | 用于激活 Image Diff                                                | Activate Image Diff                                                                |
  |  `ArrowUp/I/i`   | 增加 Image Diff 阈值（0-1），降低敏感度                            | Increase Image Diff threshold and decrease sensitivity                             |
  | `ArrowDown/K/k`  | 降低 Image Diff 阈值（0-1），增加敏感度                            | Decrease Image Diff threshold and increase sensitivity                             |
  | `ArrowLeft/J/j`  | 增加阈值调整步长                                                   | Increase the step when adjusting the threshold                                     |
  | `ArrowRight/L/l` | 减小阈值调整步长                                                   | Decrease the step when adjusting the threshold                                     |
  |      `S/s`       | 开启/关闭 Solar Curve 曲线滤镜                                     | Toggle on/off Solar Curve filter                                                   |
  |      `A/a`       | 开启/关闭 S2lar Curve 曲线滤镜（相当于应用 2 次 Solar Curve 滤镜） | Toggle on/off S2lar Curve filter (Solar Curve ^ 2)                                 |
  |   `Ctrl + S/s`   | 保存当前显示的图片到本地                                           | Save the current displayed image to the local                                      |
  |   `Ctrl + L/l`   | 清除图像缓存                                                       | Clear image caches                                                                 |
  |   `Ctrl + =/+`   | 放大图像                                                           | Zoom in                                                                            |
  |   `Ctrl + -/_`   | 缩小图像                                                           | Zoom out                                                                           |
  |   `Ctrl + I/i`   | 缩小图像到最小尺寸                                                 | Zoom out to the minimum size                                                       |
  |   `Ctrl + P/p`   | 放大图像到最大尺寸                                                 | Zoom in to the maximum size                                                       |
  |   `Ctrl + O/o`   | 恢复到图像原有尺寸                                                 | Resize to the original size                                                        |

## :dart: 待办 TODOs

- [x] 支持更多图床，持续更新；

  > Support more image hosts and keep updated;

- [x] 处理跳转链接，持续更新；

  > Handle redirection prefixes and keep updated;

- [x] 对于不支持缩略图转原图的链接，通过请求超链接后猜测原图，或根据超链接站点做匹配，持续更新；

  > For thumb images whose sources cannot be converted to original ones, make an HTTP request of the hyper link and guess (or match according to the link) the original image source;

- [ ] 支持更多滤镜；

  > Support more filters;

- [ ] 使用 WebGL 进行加速。

  > Accelerate using WebGL.

## :roller_coaster: 演示 Demo

| 功能 Feature |                                            演示 Demo                                             |
| :----------: | :----------------------------------------------------------------------------------------------: |
|    Basics    | ![Demo](https://raw.githubusercontent.com/Sec-ant/Easy-Compare/master/assets/demo/gif/demo1.gif) |
|  Image Diff  | ![Demo](https://raw.githubusercontent.com/Sec-ant/Easy-Compare/master/assets/demo/gif/demo2.gif) |
| Solar Curve  | ![Demo](https://raw.githubusercontent.com/Sec-ant/Easy-Compare/master/assets/demo/gif/demo3.gif) |

## :hammer_and_wrench: 安装 Installation

请到 [Greasy Fork](https://greasyfork.org/zh-CN/scripts/397200-easy-compare) 页面，配合 [Tampermonkey](https://www.tampermonkey.net/) 浏览器扩展安装使用。

> Please go to [Greasy Fork](https://greasyfork.org/zh-CN/scripts/397200-easy-compare) and install the usersript with [Tampermonkey](https://www.tampermonkey.net/) extension.

## :warning: 注意 Notes

- 本脚本使用 [`createImageBitmap(blob)`](https://developer.mozilla.org/zh-CN/docs/Web/API/WindowOrWorkerGlobalScope/createImageBitmap) 实现图像的解码。为了能够正常使用本脚本，请使用[支持 `createImageBitmap` 的浏览器](https://developer.mozilla.org/docs/Web/API/WindowOrWorkerGlobalScope/createImageBitmap#Browser_compatibility)；

  > This script uses [`createImageBitmap(blob)`](https://developer.mozilla.org/zh-CN/docs/Web/API/WindowOrWorkerGlobalScope/createImageBitmap) to decode images. In order for the script to work properly, please use browsers that [support `createImageBitmap`](https://developer.mozilla.org/docs/Web/API/WindowOrWorkerGlobalScope/createImageBitmap#Browser_compatibility);

- 部分站点有非常严格的内容安全策略限制，因此无法使用脚本内动态创建的 Worker，从而导致图像处理阻塞页面主线程的交互。若遇到此问题，Chrome 用户可以使用 [Content Security Policy Override](https://chrome.google.com/webstore/detail/content-security-policy-o/lhieoncdgamiiogcllfmboilhgoknmpi) 这个扩展覆写网站的内容安全策略设置。以 Awesome-HD 为例，将该扩展的规则更改为
  ```
  [
    ["https://awesome-hd\\.me/", [
        ["script-src", "script-src blob:"]
    ]]
  ]
  ```
  或
  ```
  [
    ["https://awesome-hd\\.me/", [
        ["script-src", "worker-src blob:; script-src"]
    ]]
  ]
  ```
  > Some sites have strict Content Security Policy (CSP) settings, so dynamic constructed Workers in this script may not be available. In that case, Chrome users can use [Content Security Policy Override](https://chrome.google.com/webstore/detail/content-security-policy-o/lhieoncdgamiiogcllfmboilhgoknmpi) extension to override the CSP settings of these sites. An example to overide CSP settings of Awesome-HD:
  > ```
  > [
  >   ["https://awesome-hd\\.me/", [
  >       ["script-src", "script-src blob:"]
  >   ]]
  > ]
  > ```
  > or
  > ```
  > [
  >   ["https://awesome-hd\\.me/", [
  >       ["script-src", "worker-src blob:; script-src"]
  >   ]]
  > ]
  > ```

## :building_construction: 贡献 Contribution

本脚本暂时不开放多人编辑权限，如有问题和想法请先到 [Greasy Fork 反馈页面](https://greasyfork.org/zh-CN/scripts/397200-easy-compare/feedback)或 [Github Issues 页面](https://github.com/Sec-ant/Easy-Compare/issues)提交。

> The script is not open for contribution for now. Please refer to the [Greasy Fork feedback page](https://greasyfork.org/zh-CN/scripts/397200-easy-compare/feedback) or [Github Issues](https://github.com/Sec-ant/Easy-Compare/issues) in case of any problems or suggestions.

## :copyright: 许可 License

[GNU General Public License v3.0 or later](https://spdx.org/licenses/GPL-3.0-or-later.html)

## :mailbox: 邮箱 Email

zzwu@zju.edu.cn

## :heart: 捐赠 Donation

<table><tbody><tr><td>支付宝 Alipay</td><td>微信 Wechat</td></tr>
<tr><td><img width="200" src="https://i.loli.net/2020/02/28/JPGgHc3UMwXedhv.jpg"></td><td><img width="200" src="https://i.loli.net/2020/03/02/qDQ9Xk8uCHwcaLZ.png"></td></tr></tbody></table>
