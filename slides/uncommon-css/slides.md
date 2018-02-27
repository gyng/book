# New

`display: grid`

<iframe src="e/grid/index.html"></iframe>

---

# Old

`border-image`
<iframe src="e/border-image/index.html"></iframe>
(Limited Chrome support)

---

# Useless?

`caret-color`

<div class="box">
<input type="text" style="caret-color: red; font-size: 3em; width: 100%;" placeholder="don’t do this?">
<input type="text" style="caret-color: transparent; font-size: 3em; width: 100%;" placeholder="don’t do this">
</div>

---

# Not covering

* ~Box model~
* ~Floats~
* ~Flexbox~
* ~CSS Grid~
* ~Shadow DOM~

```css
del {
    text-decoration-color: red;
    text-decoration-style: wavy;
}
```

---

# `cursor`

```css
div { cursor: crosshair; }
```

<div class="box" style="cursor: crosshair">
Crosshair
</div>

```css
div { cursor: url(...); }
```

<div class="box" id="cursor-animated">
?
</div>

---

# Web Video Text Tracks Format (WebVTT)

<iframe src="e/webvtt/sub.vtt" style="font-size: 200px"></iframe>

---

# Styled WebVTT


```css
video::cue(b) {
    color: red !important;
}
```

<iframe src="e/webvtt/index.html"></iframe>

Limited support

---

# `columns`, `:first-*`

```css
p { columns: 3 auto; }
p::first-line { font-variant-caps: small-caps; }
```

<div class="box" style="max-height: 50%;" id="col">

<div style="font-family: Vollkorn; font-size: 16px; text-align: justify; letter-spacing: 10px; padding: 20px;">MOBY DICK</div>

<p style="font-family: Vollkorn; columns: 3 auto; font-size: 14px; overflow: hidden;">
Call me Ishmael. Some years ago—never mind how long precisely—having little or no money in my purse, and nothing particular to interest me on shore, I thought I would sail about a little and see the watery part of the world. It is a way I have of driving off the spleen and regulating the circulation. Whenever I find myself growing grim about the mouth; whenever it is a damp, drizzly November in my soul; whenever I find myself involuntarily pausing before coffin warehouses, and bringing up the rear of every funeral I meet; and especially whenever my hypos get such an upper hand of me, that it requires a strong moral principle to prevent me from deliberately stepping into the street, and methodically knocking people’s hats off—then, I account it high time to get to sea as soon as I can. This is my substitute for pistol and ball. With a philosophical flourish Cato throws himself upon his sword; I quietly take to the ship.</p>
</div>

---

# `:first-letter`

```css
p::first-letter {
    float: left;
    font-size: 700%;
    background: url(res/pic2.png);
    color: white;
    padding: 0.1em;
    margin: 0 0.05em 0.05em 0;
    border: outset 4px pink;
    text-shadow: 1em 1em 2em rgba(255, 215, 0, 0.5), 0 0 1em rgba(255, 215, 0, 0.5), 0 0 0.2em rgba(255, 215, 0, 0.5), 1px 1px 0 #ecdc25, -1px -1px 0 #90582e, 1px -1px 0 #ecdc25, -1px 1px 0 #90582e, 3px 3px 5px #333;
}
```

<div class="box" style="max-height: 50%;" id="col2">

<div style="font-family: Vollkorn; font-size: 16px; text-align: justify; letter-spacing: 10px; padding: 20px;">MOBY DICK</div>

<p style="font-family: Vollkorn; columns: 3 auto; font-size: 14px; overflow: hidden;">
Call me Ishmael. Some years ago—never mind how long precisely—having little or no money in my purse, and nothing particular to interest me on shore, I thought I would sail about a little and see the watery part of the world. It is a way I have of driving off the spleen and regulating the circulation. Whenever I find myself growing grim about the mouth; whenever it is a damp, drizzly November in my soul; whenever I find myself involuntarily pausing before coffin warehouses, and bringing up the rear of every funeral I meet; and especially whenever my hypos get such an upper hand of me, that it requires a strong moral principle to prevent me from deliberately stepping into the street, and methodically knocking people’s hats off—then, I account it high time to get to sea as soon as I can. This is my substitute for pistol and ball. With a philosophical flourish Cato throws himself upon his sword; I quietly take to the ship. There is nothing surprising in this.</p>

---

# `unicode-range`

* Fonts without uppercase or tabular numerals
    - <span style="font-family: Georgia">Most commonly, Georgia: 1234567890</span>
* Non-Latin fonts with ugly Latin letters
* Add custom emoji to a font

```css
@font-face {
    font-family: ComicNumerals;
    src: local(Comic Sans MS), local(Chalkboard);
    /* ASCII 0-9, A-Z */
    unicode-range: U+30-39, U+41-5A;
}
```

<div class="box" id="unicoder">
Nineteen Eighty-Four, often published as 1984, is a dystopian novel published in 1949 by English&hellip;
</div>

---

# `font-feature-settings`

Toggles *OpenType* features in fonts

```css
p { font-feature-settings: "liga" on; }
```

<div class="box" style="font-family: Vollkorn; font-size: 150%; font-feature-settings: 'liga' on;">
The iffy fjords afflict fit affiliates
</div>

```css
p { font-feature-settings: "liga" off; }
```

<div class="box" style="font-family: Vollkorn; font-size: 150%; font-feature-settings: 'liga' off;">
<p>The <ruby>i<emp style="text-decoration: underline red;">ff</emp>y<rt>calt</rt></ruby> fjords a<emp style="text-decoration: underline red;">ff</emp>lict fit affiliates</p>
</div>

---

# `font-variant-caps`

```css
p { font-feature-settings: "smcp"; }
p { font-variant-caps: small-caps; }
```

<div class="box" style="font-family: Vollkorn; font-size: 150%; font-feature-settings: 'smcp' on;">
<p>Small Caps</p> <p>Aa Bb Cc Dd Ee Ff</p> <p>US nato asean <span style="font-family: Vollkorn">9</span>am&ndash;<span style="font-family: Vollkorn">17</span>pm</p>
</div>

---

# `font-variant-numeric`

```css
p { font-feature-settings: 'ss17'; }
```

<div class="box" style="font-family: 'Vollkorn'; font-size: 150%; font-feature-settings: 'ss17';">
<p>22&zwnj;1/2 <span class="rul"><ruby>22&zwnj;1&frasl;2<rt>&amp;zwnj; &amp;frasl;</rt></ruby></span> 1984&ndash;2048 787</p>
</div>

```css
p { font-feature-settings: 'zero', 'tnum', 'lnum'; }
p { font-variant-numeric: slashed-zero tabular-nums lining-nums; }
```

<div class="box" style="font-family: 'Vollkorn'; font-size: 150%; font-feature-settings: 'zero', 'tnum', 'lnum';">
22&zwnj;1/2 22&zwnj;1&frasl;2 1984&ndash;2048 787
</div>

---

# `ordn`

```css
p { font-feature-settings: 'ordn' off; }
```

<div class="box" style="font-family: SourceSansPro; font-size: 150%; font-feature-settings: 'ordn' off;">
1st 2nd 3rd 4th 2st 3th 4dogs 5 cats
</div>

```css
p { font-feature-settings: 'ordn'; }
```

<div class="box" style="font-family: SourceSansPro; font-size: 150%; font-feature-settings: 'ordn';">
<p class="pesticide"><span>1</span><span>st</span> 2nd 3rd 4th 2st 3th 4dogs 5 cats</p>
</div>

<div class="box" style="font-family: SourceSansPro; font-size: 150%; font-feature-settings: 'ordn';">
<p class="pesticide"><ruby><span>1</span><sup>st</sup>  <rt><code>&lt;sup></code></rt></ruby> <span>2</span><sup>nd</sup> <span>3</span><sup>rd</sup></p>
</div>

---

# `font-feature-settings`

Useful settings

* `liga` Required Ligatuers
* `dlig` Discretionary ligatures
* `smcp` Small Caps
* `calt` Contextual Alternates
* `dlig` Discretionary Ligatures
* `tnum` Tabular Figures
* `zero` Slashed Zero
* `swsh` Swash
* `frac` Fractions
* `ordn` Ordinals

[Feature list](https://helpx.adobe.com/typekit/using/open-type-syntax.html)

---

# When to use tabular figures

<link href="https://fonts.googleapis.com/css?family=Cabin" rel="stylesheet">

Use tabular and modern numbers for tables & labels

<div class="box" style="flex-direction: row;">
<table style="font-family: Vollkorn; font-variant-numeric: proportional-nums;">
<tbody>
    <tr style="border:none; background-color: transparent;">
        <td style="border: none;">1811 est.</td>
        <td style="text-align: right; border: none;">353500.00</td>
    </tr>
    <tr style="border:none; background-color: transparent;">
        <td style="border: none;">1900 est.</td>
        <td style="text-align: right; border: none;">21464.17</td>
    </tr>
        <tr style="border:none; background-color: transparent;">
        <td style="border: none;">1986 est.</td>
        <td style="text-align: right; border: none;">617617.76</td>
    </tr>
</tbody>
</table>

<table style="font-family: Vollkorn; font-variant-numeric: tabular-nums lining-nums;">
<tbody>
    <tr style="border:none; background-color: transparent;">
        <td style="border: none;">1816 est.</td>
        <td style="border: none;">353500.00</td>
    </tr>
    <tr style="text-align: right; border:none; background-color: transparent;">
        <td style="border: none;">1906 est.</td>
        <td style="border: none;">21464.17</td>
    </tr>
        <tr style="text-align: right; border:none; background-color: transparent;">
        <td style="border: none;">1986 est.</td>
        <td style="border: none;">617617.76</td>
    </tr>
</tbody>
</table>
</div>


Proportional and old-style are best left in body text

<div class="box">
<div style="font-family: Vollkorn; font-variant-numeric: tabular-nums lining-nums;">
    28 February, 2018, 9:30&ndash;14:40
</div>

<div style="font-family: Vollkorn;">
    28 February, 2018, 9:30&ndash;14:40
</div>
</div>

---

# RTL text

```css
p {
    direction: rtl;
    unicode-bidi: normal;
}
```

<div class="box" style="direction: rtl; unicode-bidi: normal;">
الموسوعة الحرة التي يستطيع الجميع تحريرها. توجد الآن 560٬021 مقالة بالعربية.
</div>

---

# Vertical text

```css
p {
    writing-mode: vertical-rl;
    hanging-punctuation: end;
}
```

![](res/vert.png)

---

# `text-orientation`

```css
p {
    writing-mode: vertical-rl;
    text-orientation: upright;
}
```

<div style="border: solid 1px black; padding: 20px; max-height: 25%; writing-mode: vertical-rl; text-orientation: upright;">
Wikipedia, the free encyclopedia 维基百科，自由的百科全书
</div>


<div style="border: solid 1px black; padding: 20px; max-height: 25%; writing-mode: vertical-lr; text-orientation: mixed;">
Wikipedia, the free encyclopedia 维基百科，自由的百科全书
</div>

---

# Emphasis in Asian scripts

```css
*:lang(ja) emp {
    text-emphasis-style: filled sesame;
}

*:lang(zh) emp {
    text-emphasis-style: filled dot;
}
```

![](res/emp.png)

---

# `text-emphasis`

```css
emp {
    /* text-emphasis-color: red; */
    text-emphasis-style: "🔥";
}
```

<div class="box">
<emp style="font-family: Vollkorn; text-emphasis-color: #555; text-emphasis-style: '🔥';">Call me Ishmael. Some years ago—never mind how long precisely—having <ruby>🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥<rt>🔥🔥🔥🔥🔥🔥🔥🤔🤔🤔🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥</rt></ruby> Ishmael. Some years ago— </emp>
</div>

---

# `text-combine-upright`

Vertical numerals, aka tate-chu-yoko (縦中横)

```css
p, li::marker {
    text-combine-upright: digits 4;
}
```

![](res/emp.png)

---

# Vertical punctuation

![](res/Tateyoko.png)

If the font supports it, setting the writing mode enables vertical punctuation

---

# `@media`

* Different rules for different viewing devices
* Responsive design

```css
@supports (display: flex) {
  @media screen and (min-width: 900px) {
    article {
      display: flex;
    }
  }
}
```

---

# Print CSS

* `@media print`
* `@page`
* `page-break-after`, `page-break-before`
* `orphans`, `widows`
* `size`

---

# `@media print`

Apply selectors to your webpage in print

```css
@media print {
    section {
        height: 100%;
        page-break-after: always;
        font-size: 16px;
        color: black;
    }
}
```

---

# `@page`

[W3C](https://drafts.csswg.org/css-page-3/#at-page-rule)&nbsp;&middot;&nbsp;
[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/%40page)

Selectors for the printed page ***itself***

```css
@page { /* size: A4 landscape; */ }

/* cover */
@page:first { font-size: 192px; }

/* verso */
@page:left { margin: 5cm 10cm 5cm 5cm; }

/* recto */
@page:right { margin: 5cm 5cm 5cm 10cm; }
```

---

# `position: sticky;`

```css
p { position: sticky; }
```

<iframe src="e/sticky/index.html"></iframe>

[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/position)

---

# `repeating-linear-gradient`

```css
background: repeating-linear-gradient(45deg,
            transparent,
            transparent 10px,
            #E1002D 10px,
            #E1002D 20px);
```

<iframe src="e/repeating-linear-gradient/index.html"></iframe>

---

# ~`filter`~

Very common (CSS)

<div class="box">
    <img class="filter" src="res/pic0.jpg"></img>
</div>

---

# `<filter>`

Not very common (SVG)

And quite advanced

[W3C Filters](https://www.w3.org/TR/SVG/filters.html)

```
feDistantLight
fePointLight
feSpotLight
feBlend
feColorMatrix
feComponentTransfer
feComposite
feConvolveMatrix
feDiffuseLighting
feDisplacementMap
feFlood
feGaussianBlur
feImage
feMerge
feMorphology
feOffset
feSpecularLighting
feTile
feTurbulence
```

---

# `feDisplacementMap`

SVG filters can be applied to HTML

```xml
<filter>
    <feImage
        result="warp"
        xlink:href="${displacementMap}"
    />
    <feDisplacementMap
        xChannelSelector="G"
        yChannelSelector="R"
        in="SourceGraphic"
        in2="warp"
        scale="400"
    />
</filter>
```

---

# `feDisplacementMap`

<iframe src="e/curve/index.html"></iframe>

---

# `feDisplacementMap`

```xml
<feImage result="warp"
    xlink:href="${displacementMap}"
/>
<feDisplacementMap
    xChannelSelector="G"
    yChannelSelector="R"
    ...
```

<div class="box" style="flex-direction: row;">
<img src="res/displacementmap.png"></img>
+
<code>iframe</code>

</div>

---

# SVG rules

* Whole bunch of SVG-only CSS rules

---

# `clip-path`

```css
img { clip-path: circle(33%); }
```

<div class="box">
<img src="res/pic0.jpg" style="clip-path: circle(33%);" />
</div>

SVG also has a version of `clip-path`

---

# `clip-path: polygon`

```css
img { clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%); }
```
<div class="box">
<img src="res/pic0.jpg" class="clippath" />
</div>

[`clip-path generator`](https://bennettfeely.com/clippy/)

---

# `background-clip`

```css
p {
    color: transparent;
    background: -webkit-linear-gradient(top, black, white);
    background-clip: text
}
```

<div class="box">
<p style="background: -webkit-linear-gradient(top,black,white);
	background-clip: text;
    color: transparent; font-family: Vollkorn">
Call me Ishmael. Some years ago—never mind how long precisely—having little or no money in my purse, and nothing particular to interest me on shore, I thought I would sail about a little and see the watery part of the world. It is a way I have of driving off the spleen and regulating the circulation. 🔥</p>
</div>

---

# `mask-image`

```css
img {
    mask-image: url(res/scanlines.gif);
    mask-size: cover;
}
```

<div class="box" style="flex-direction: row; background: -webkit-linear-gradient(top,rebeccapurple,purple);">
<img src="res/pic0.jpg" style="mask-image: url(res/wavy.gif); mask-size: cover; mask-mode: luminance; clip-path: circle(50%);" />
<img src="res/pic0.jpg" style="mask-image: url(res/wavy.gif); mask-size: cover; clip-path: circle(50%);" />
</div>

SVG also has a version of `mask-image`

---

# `mask-image`

<div class="box" style="flex-direction: row">
<img src="res/pic0.jpg" />
+
<img src="res/wavy.gif" />
+
<div style="background: -webkit-linear-gradient(top,rebeccapurple,purple); width: 50%; height: 50%;"></div>
</div>

---

# `::selection`

```css
p::selection {
    background-color: black;
}
```

<div class="box" style="font-family: Vollkorn">
<p id="selectioner">
Call me Ishmael. Some years ago—never mind how long precisely—having little or no money in my purse, and nothing particular to interest me on shore, I thought I would sail about a little and see the watery part of the world. It is a way I have of driving off the spleen and regulating the circulation.
</p>
</div>

---

# `contain` and `cover`

```css
#bg { background-size: cover; }
#img1 { object-fit: cover; }
#img2 { object-fit: contain; }
#img3 { object-fit: unset; }
```

<div class="box" style="flex-direction: row; justify-content: space-evenly; background: url(res/pic1.jpg) no-repeat; background-size: cover;">
    <img src="res/pic0.jpg" style="height: 100%; width: 20%; border: solid 1px red; object-fit: cover;" />
    <img src="res/pic0.jpg" style="height: 100%; width: 20%; border: solid 1px red; object-fit: contain;" />
    <img src="res/pic0.jpg" style="height: 100%; width: 20%; border: solid 1px red;" />
</div>

---

# CSS 3D transforms

* Somewhat common but still cool!

```css
body { transform: rotateX(45deg) rotateY(45deg); }
```

<iframe src="e/matrix/index.html"></iframe>

---

# `scroll-behaviour`

```css
body {
    scroll-behavior: smooth;
    scroll-snap-type: mandatory;
    scroll-snap-points-y: repeat(100vh);
}
```

<iframe src="e/scroll-behavior/index.html"></iframe>

---

# `overscroll-behavior`

```css
body { overscroll-behavior: none; }
```

Disable native overscroll behavior

<div class="box">
<div style="display: flex; width: 100%;">
<video autoplay loop src="res/drawer-glow.mp4"></video>
<video autoplay loop src="res/drawer-noglow.mp4"></video>
</div>
</div>

[Chrome article on `overscroll-behavior`](https://developers.google.com/web/updates/2017/11/overscroll-behavior)

---

# Every rule is a good rule

These rules are already in your toolbox

---

# Hammer, nail, etc.

---

# Everything is here

* https://developer.mozilla.org/en-US/docs/Web/Demos_of_open_web_technologies#CSS

