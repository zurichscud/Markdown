# Font Type

## TTF（TrueType Font）

TrueType 是由美国苹果公司和微软公司共同开发的一种电脑轮廓字体（曲线描边字）类型标准。

这种类型字体文件的扩展名是 `.ttf`

## WOFF（Web Open Font Format）

Web 开放字体格式是一种网页所采用的字体格式标准。此字体格式发展于 2009 年，现在正由万维网联盟的 Web 字体工作小组标准化，以求成为推荐标准。

此字体格式不但能够有效利用压缩来减少档案大小，并且不包含加密也不受 DRM（数位著作权管理）限制。

WOFF 本质上是包含了基于 sfnt 的字体（如 TrueType、OpenType 或开放字体格式），且这些字体均经过 WOFF 的编码工具压缩，以便嵌入网页中。这个字体格式使用zlib压缩，文件大小一般比 TTF 小 40%。

## WOFF2

WOFF 2 标准在 WOFF1 的基础上，进一步优化了体积压缩，带宽需求更少，同时可以在移动设备上快速解压。

# @font-face

`@font-face`用于定义自定义字体，以便在网页中使用非标准字体。用户即使不安装相关字体也可以正常显示。

选择一个字体文件并将其包含在您的项目中。这可以是TrueType字体文件（.ttf）、OpenType字体文件（.otf）、Web Open Font Format（.woff或.woff2）等格式。需要确保有合法许可权使用这些字体文件。

- `font-family`：自定义文字名称
- `src`：字体文件源，url指明了字体的path，format指明了字体的格式
  多个`src`能够提高浏览器的兼容性

```css
@font-face {
    font-family: 'KaiTi';
    src: url('fangzhengkaiti.woff2') format('woff2'),
        url('fangzhengkaiti.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}
```



# Font Alias

SC：*Simplified Chinese*

法语中的sans 相当于英语中的 without

serif：衬线，serif 强调了字母笔画的开始及结束

monospace：等宽

arial：等线



# 字体通用性

sans-serif是每台电脑都存在的字体

## 中文推荐字体

- `PingHei`：Apple公司出品，Mac上的系统字体

- `SourceHanSans`：Adobe出品的思源字体，对英文和中文的兼容性较好

  > 这是苹黑字体

## 英文推荐字体

- `century-gothic`
- `Poppins`

this is  **century-gothic**

this is Poppins

