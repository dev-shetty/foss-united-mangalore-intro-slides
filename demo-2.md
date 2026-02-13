---
theme: default
fonts:
  sans: "Geist"
  serif: "Domine"
  mono: "JetBrains Mono"
title: How Instagram Filters Work - The Math Behind Pretty Pictures
info: |
  The main goal of this presentation is to explain how Instagram filters work mathematically, while also providing a basic understanding of pixels and how images are represented in computers.
class: text-center flex flex-col items-center justify-center
drawings:
  persist: false
mdc: true
duration: 45min
transition: view-transition
seoMeta:
  ogImage: https://slides.shetty.me/how-instagram-filters-work/og-image.png
  ogTitle: How Instagram Filters Work - The Math Behind Pretty Pictures
  ogUrl: https://slides.shetty.me/how-instagram-filters-work
  twitterSite: ShettyDeveesh
  twitterUrl: https://x.com/ShettyDeveesh
---

# How <span class="instagram-gradient" view-transition-name="instagram-gradient">Instagram Filters</span> Work
<div class="sub-header">The simple math behind pretty pictures.</div>


<div class="abs-bl m-6 text-xl text-left flex items-center w-full">
  <div class="w-14 aspect-square mr-3 rounded-md">
    <img src="/images/meta/levels-square.png" alt="Levels Logo" class="object-cover w-full h-full rounded-xl" />
  </div>
  <div>
    <div class="text-2xl">Deveesh Shetty</div>
    <div class="text-lg text-gray-300">Software Engineer, Levels.fyi</div>
  </div>
</div>

<div class="abs-br m-6 text-xl text-gray-100">
  <a href="https://x.com/ShettyDeveesh" target="_blank" class="slidev-icon-btn">
    <carbon:logo-x />
  </a>
  <a href="https://github.com/dev-shetty" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>


---
layout: center
---

<span class="instagram-gradient" view-transition-name="instagram-gradient">Instagram Filters</span>

# We beautify our image everytime before we post.

---
layout: center
---

<style>
  .image {
    --uno: w-40;
  }
</style>

<div class="grid grid-cols-2 md:grid-cols-4 gap-12 mt-8">
 <div class="flex flex-col items-center">
    <img src="/images/filters/normal.png" alt="Original Image" class="image object-cover rounded-xl shadow-md mb-3"/>
    <div class="font-semibold text-lg">Original</div>
  </div>
  <div class="flex flex-col items-center">
    <img src="/images/filters/clarendon.png" alt="Clarendon Filter Example" class="image object-cover rounded-xl shadow-md mb-3"/>
    <div class="font-semibold text-lg">Clarendon</div>
  </div>
  <div class="flex flex-col items-center">
    <img src="/images/filters/juno.png" alt="Juno Filter Example" class="image object-cover rounded-xl shadow-md mb-3"/>
    <div class="font-semibold text-lg">Juno</div>
  </div>
  <div class="flex flex-col items-center">
    <img src="/images/filters/ludwig.png" alt="Ludwig Filter Example" class="image object-cover rounded-xl shadow-md mb-3"/>
    <div class="font-semibold text-lg">Ludwig</div>
  </div>
</div>

<div class="abs-bl m-4 text-base text-gray-400 text-left italic">
  Reference: <a href="https://www.animatron.com/blog/18-best-instagram-filters/" target="_blank" class="underline">18 Best Instagram Filters</a>
</div>

---
layout: center
class: text-center
---

<span class="sub-header">You might wonder</span>
# <span>There should be some complex AI sitting behind which does it.</span>


---
layout: center
class: text-center
transition: slide-up
---

<span class="sub-header">Well, to your surprise</span>
# <span>It's much simpler than you think</span>

---
layout: center
class: text-center
---

# <span>How do Images work?</span>
<span class="sub-header">Let's take a small tangent</span>


---
layout: center
class: text-center
transition: view-transition
---

<div>
    <img src="/images/pineapple.jpg" alt="Pineapple Image" class="object-cover rounded-xl shadow-md" view-transition-name="normal-image" />
</div>


<div class="abs-bl m-4 text-base text-gray-400 text-left italic">
Photo by <a href="https://unsplash.com/@thisisnando?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Fernando Andrade</a> on <a href="https://unsplash.com/photos/ripe-pineapple-fruit-nAOZCYcLND8?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
</div>

<!--  Let's take this picture, looks normal
- Zoom in,
- Zoom in more
- More more more
- Show individual pixels (check the software which ubuntu uses to do this) --> 

---
layout: center
class: text-center
transition: view-transition
---

<div>
    <img src="/images/pineapple.jpg" alt="Pineapple Image" class="object-cover rounded-xl shadow-md scale-150" view-transition-name="normal-image" />
</div>

---
layout: center
class: text-center
transition: view-transition
---

<div>
    <img src="/images/pineapple.jpg" alt="Pineapple Image" class="object-cover rounded-xl shadow-md scale-450" view-transition-name="normal-image" />
</div>

---
layout: center
class: text-center
transition: view-transition
---

<div>
    <img src="/images/pineapple.jpg" alt="Pineapple Image" class="object-cover rounded-xl shadow-md scale-2000" view-transition-name="normal-image" />
</div>


---
layout: image-left
image: /pineapple.jpg
transition: view-transition
---

<style>
  .slidev-layout.image-left {
    position: relative;
  }
  
  .pixel-dot {
    position: absolute;
    top: 70%;
    left: 40%;
    transform: translate(-50%, -50%);
    width: 8px;
    height: 8px;
    background: #D04009;
    border: 2px solid white;
    border-radius: 50%;
    z-index: 11;
    pointer-events: none;
  }
  
  .rgb-display {
    position: absolute;
    top: 70%;
    left: 40%;
    transform: translate(20px, -50%);
    background: rgba(0, 0, 0, 0.85);
    color: white;
    padding: 8px 12px;
    border-radius: 6px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.9rem;
    white-space: nowrap;
    z-index: 12;
    pointer-events: none;
  }
  
  .rgb-display::before {
    content: '';
    position: absolute;
    left: -6px;
    top: 50%;
    transform: translateY(-50%);
    width: 0;
    height: 0;
    border-right: 6px solid rgba(0, 0, 0, 0.85);
    border-top: 6px solid transparent;
    border-bottom: 6px solid transparent;
  }
</style>

<div v-click>
<div class="pixel-dot"></div>
<div class="pixel-arrow"></div>
<div class="rgb-display" view-transition-name="rgb-display">
  rgb(240, 249, 248)
</div>
</div>

# <div class="text-2xl font-bold">Image Details</div>

  <div class="mt-8 rounded-xl shadow-lg max-w-xs font-mono space-y-2">
    <div>
      <span class="font-semibold">Size:</span>
      8,60,433 bytes <span class="text-gray-400">(864 KB on disk)</span>
    </div>
    <div>
      <span class="font-semibold">Format:</span>
      JPEG image
    </div>
    <div>
      <span class="font-semibold">Dimensions:</span>
      2749 × 4124
    </div>
  </div>

<!-- - Whenever you buy a phone you compare the Megapixels of the camera
- What is Megapixel, or perhaps what is pixel?
- Pixel is one single point on the screen (frame it better)
- Each pixels are RGB value, which mixes together these combinations form a color
(Have slides which shows different colors with RGB values)
-->

---
layout: center
class: text-center
---

# <span><span view-transition-name="rgb-r">r</span><span view-transition-name="rgb-g">g</span><span view-transition-name="rgb-b">b</span></span><span view-transition-name="rgb-display">(240, 249, 248)</span>

---
layout: center
class: h-full
---

<style>
  .rgb-column {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
  }
  
  .rgb-letter {
    font-size: 8rem;
    font-weight: 900;
    line-height: 1;
  }
  
  .rgb-value {
    font-size: 2rem;
    font-weight: 600;
    font-family: 'JetBrains Mono', monospace;
  }
  
  .rgb-binary {
    display: flex;
    gap: 0.5rem;
    font-family: 'JetBrains Mono', monospace;
  }
  
  .binary-bit {
    width: 3rem;
    height: 3rem;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.5rem;
    font-weight: 600;
    border: 2px solid #60a5fa;
    border-radius: 0.5rem;
    background: rgba(96, 165, 250, 0.1);
    color: #60a5fa;
  }
  
  .binary-bit.bit-1 {
    background: rgba(96, 165, 250, 0.3);
  }
  
  .rgb-container {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    align-items: center;
    justify-content: center;
    height: 100%;
  }
</style>

<div class="rgb-container">
  <div class="rgb-column">
  <div class="flex gap-4 items-center">
    <div class="rgb-letter text-red-500" view-transition-name="rgb-r">R</div>
    <div class="rgb-value">240</div>
  </div>
    <div class="rgb-binary">
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-0">0</div>
      <div class="binary-bit bit-0">0</div>
      <div class="binary-bit bit-0">0</div>
      <div class="binary-bit bit-0">0</div>
    </div>
  </div>
  
  <div class="rgb-column">
  <div class="flex gap-4 items-center">
    <div class="rgb-letter text-green-500" view-transition-name="rgb-g">G</div>
    <div class="rgb-value">249</div>
  </div>
    <div class="rgb-binary">
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-0">0</div>
      <div class="binary-bit bit-0">0</div>
      <div class="binary-bit bit-1">1</div>
    </div>
  </div>
  
  <div class="rgb-column">
  <div class="flex gap-4 items-center">
    <div class="rgb-letter text-blue-500" view-transition-name="rgb-b">B</div>
    <div class="rgb-value">248</div>
    </div>
    <div class="rgb-binary">
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-1">1</div>
      <div class="binary-bit bit-0">0</div>
      <div class="binary-bit bit-0">0</div>
      <div class="binary-bit bit-0">0</div>
    </div>
  </div>
</div>

---
layout: image-left
image: /pineapple.jpg
---

<div class="mb-8">

## <span class="instagram-gradient" view-transition-name="filter-name">Grayscale Filter</span>
</div>

````md magic-move 
```ts {1|3,13|4,12|5-7|8|9-11}
// data: [242, 248, 246, 255, 242, 248, 246, ...]

const applyGrayscale = (data) => {
  for (let i = 0; i < data.length; i += 4) {
    const r = data[i]
    const g = data[i + 1]
    const b = data[i + 2]
    const avg = (r + g + b) / 3
    data[i] = avg
    data[i + 1] = avg
    data[i + 2] = avg
  }
}
```
````


---
layout: image-left
image: /pineapple-bw.png
---

<div class="mb-8">

## <span class="instagram-gradient" view-transition-name="filter-name">Grayscale Filter</span>
</div>
````md magic-move 
```ts {*}
// data: [242, 248, 246, 255, 242, 248, 246, ...]

const applyGrayscale = (data) => {
  for (let i = 0; i < data.length; i += 4) {
    const r = data[i]
    const g = data[i + 1]
    const b = data[i + 2]
    const avg = (r + g + b) / 3
    data[i] = avg
    data[i + 1] = avg
    data[i + 2] = avg
  }
}
```
````


---
layout: image-left
image: /pineapple-invert.png
---

<div class="mb-8">

## <span class="instagram-gradient" view-transition-name="filter-name">Invert Image</span>
</div>
````md magic-move 
```ts {*}
// data: [242, 248, 246, 255, 242, 248, 246, ...]

const applyInvert = (data) => {
  for (let i = 0; i < data.length; i += 4) {
    data[i] = 255 - data[i]
    data[i + 1] = 255 - data[i + 1]
    data[i + 2] = 255 - data[i + 2]
  }
}

```
````


---
layout: center
class: text-center
transition: fade-out
---

# <span>Let's see some live demos?</span>
<a class="sub-header text-gray-100" href="https://filters.shetty.me" target="_blank">filters.shetty.me</a>


---
layout: center
class: text-center
---

# <span>You might wonder why do I need to code it when instagram does it.</span>

<!-- Well, that's upto you, as a CS Engineer you should try to dig deep the underlying aspects of how the program or software works.
Always bw curious and go in the rabbit hole of things, that's what makes you different from a normal CS graduate -->

---
layout: center
class: text-center
---

# <span>You own the code, you own the data.</span>



---
layout: center
class: text-center
---

# There is always room for improvements

<!-- you can scale this idea further using maybe AI to generate filters based on the features of the image, or create shades of frames and showcase them in a unique way
-->

---
layout: center
class: text-center
---

# <span view-transition-name="curiosity-challenge">Curiosity Challenge</span>

---
layout: center
class: h-full bg-white text-black
---

<style>
  .question-text {
    line-height: 1.8;
    max-width: 90%;
  }
  
  .color-diagrams {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .diagram-container {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
  }

  .diagram-image {
    position: relative;
  }

  .question-mark {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 4rem;
    font-weight: 900;
    z-index: 10;
    text-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
    pointer-events: none;
  }
  
</style>


# <span view-transition-name="curiosity-challenge">Curiosity Challenge</span>

<div class="flex flex-col h-full">
  <div class="question-text text-gray-700 text-lg">
    I talked to you about how colors are represented on screen, using <strong>RGB</strong>.<br/>
    But when you print on paper, RGB is not used, its <strong>CMYK</strong> (Cyan Magenta Yellow), think about it why is that the case?
  </div>
  
  <div class="color-diagrams">
    <div class="diagram-container">
      <div class="diagram-image">
        <img src="/images/rgb-cmyk.png" alt="RGB Color Circles" class="object-cover rounded-xl w-96" />
        <div class="question-mark text-gray-500">?</div>
      </div>
    </div>
  </div>
</div>


---
layout: center
class: text-center
---

# <span>Be Curious</span>


---
layout: cover
class: text-white mt-0
---

<div class="mb-8">
  <p class="font-serif text-4xl">Deveesh Shetty</p>
  <p class="text-gray-100 text-2xl pt-1">Software Engineer, Levels.fyi</p>
</div>

<div class="w-full h-full flex flex-col">
  <ul class="list-disc text-2xl space-y-0">
    <li>I build Web Applications</li>
    <li>I explore random stuffs</li>
    <li>I write blogs and articles</li>
    <li>I run and volunteer in technical communities</li>
  </ul>
</div>

<div class="abs-br m-8 flex flex-col items-center">
  <img src="/images/meta/dev-site-qr.png" alt="Portfolio QR Code" class="h-48 aspect-square rounded-lg" />
  <span class="text-gray-300 text-center pt-2">dev.shetty.me</span>
</div>

---
layout: center
---

<div class="flex items-center justify-center gap-8">
  <div class="bg-white p-4 rounded-lg">
    <img src="/images/promotion/mangalorefoss.png" alt="Hackers Mang Talk" class="h-100 rounded-lg" />
  </div>
  <div class="bg-white p-4 rounded-lg">
  <img src="/images/promotion/devfest.png" alt="Devfest Talk" class="h-100 rounded-lg" />
</div>
</div>


---
layout: image
class: text-center
image: https://media1.tenor.com/m/yasksYy1XekAAAAC/matrix-code.gif
---

# <span class="text-white drop-shadow-lg text-8xl absolute left-1/2 top-1/2 transform -translate-x-1/2 -translate-y-1/2">Thank you</span>