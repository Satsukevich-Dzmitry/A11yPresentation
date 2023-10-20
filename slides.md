---
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: Why A11y matters
clicks: 2
---

# Welcome everyone!

<MorphText v-if="$clicks === 2"/>

---
transition: fade-out
layout: image-left
image: /what-is.webp
class: h-80
---

# What is it? 

<p v-click>The word accessibility has different meanings in different contexts. On the internet, the use of the term a11y helps to identify content related specifically to digital accessibility.</p>

<h2 v-click class="mt-20 mb-5">What topics we'll cover</h2>

<v-clicks>

- Why you should know about a11y?
- How you can test it?
- How you can improve it?
- Why it is important not only for people with disabilities?

</v-clicks>

---
transition: fade-out
clicks: 5
---

# Why you should care?

<section class="cats-dialog mt-40" v-if="$clicks<=3 || $clicks>4" :class="{
  'cats-dialog-fire': $clicks === 5
}">
  <div>
    <span v-if="$clicks === 2" class="water-drop">💧
    		<audio autoplay>
  			  <source src="/fail-sound.mp3" type="audio/mp3">
		    </audio>
    </span>
    <span class="oops" v-if="$clicks === 5">🫣</span>
    <span v-if="$clicks === 3" class="bubble bubble-bottom-left">Y-y-yes...</span>
    <img src="/hehe.png" class="h-60 rounded shadow"/>
  </div>
  <div>
    <span v-if="$clicks >= 1 && $clicks < 4" class="bubble bubble-bottom-left">What do you know about A11y?</span>
    <span v-if="$clicks === 5" class="bubble bubble-bottom-left">Oh no</span>
    <span v-if="$clicks === 5" class="water-drop water-drop-2">💧
    		<audio autoplay>
  			  <source src="/fail-sound.mp3" type="audio/mp3">
		    </audio>
    </span>
    <img src="/boss.webp" class="h-60 rounded shadow"/>
  </div>
</section>

<section v-if="$clicks===4" class="suits">
  <audio autoplay>
  	<source src="/busted.mp3" type="audio/mp3">
	</audio>
  <img src="/suits.png"/>
</section>


<style scoped>
.suits {
  width: 100%;
}
.cats-dialog {
  width: 100%;
  display: flex;
  gap: 100px;
  align-items: center;
  justify-content: center;
}

.cats-dialog-fire {
  background: url("/fire.gif");
  background-repeat: repeat-x;
  background-position-y: bottom;
  height: 350px;
  align-items: flex-start;
}

.cats-dialog div {
  position: relative;
}
.water-drop {
  position: absolute;
  font-size: 200%;
  right: 56px;
  top: -16px;
}

.water-drop-2 {
  top: 20px;
  font-size: 300%;
}

.oops {
  position: absolute;
  font-size: 550%;
  right: 78px;
  top: -30px;
}

.bubble {
	position: absolute;
	bottom: 105%;
	left: 50%;
	font-family: sans-serif;
	font-size: 18px;
	line-height: 24px;
	width: 300px;
	background: #fff;
	border-radius: 40px;
	padding: 20px;
	text-align: center;
	color: #000;
}

.bubble-bottom-right:before {
	content: "";
	width: 0px;
	height: 0px;
	position: absolute;
	border-left: 24px solid #fff;
	border-right: 12px solid transparent;
	border-top: 12px solid #fff;
	border-bottom: 20px solid transparent;
	right: 32px;
	bottom: -24px;
}

.bubble-bottom-left:before {
	content: "";
	width: 0px;
	height: 0px;
	position: absolute;
	border-left: 24px solid #fff;
	border-right: 12px solid transparent;
	border-top: 12px solid #fff;
	border-bottom: 20px solid transparent;
	left: 32px;
	bottom: -24px;
}
</style>

---
layout: default
---

# Table of contents

```html
<Toc minDepth="1" maxDepth="1"></Toc>
```

<Toc maxDepth="1"></Toc>

---
transition: slide-up
level: 2
---

# Oops

Law suits on accessibility

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# Code

Use code snippets and get the highlighting directly![^1]

```ts {all|2|1-6|9|all}
interface User {
  id: number
  firstName: string
  lastName: string
  role: string
}

function updateUser(id: number, update: User) {
  const user = getUser(id)
  const newUser = { ...user, ...update }
  saveUser(id, newUser)
}
```

<arrow v-click="[3, 4]" x1="400" y1="420" x2="230" y2="330" color="#564" width="3" arrowSize="1" />

[^1]: [Learn More](https://sli.dev/guide/syntax.html#line-highlighting)

<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---

# Components

<div grid="~ cols-2 gap-4">
<div>

You can use Vue components directly inside your slides.

We have provided a few built-in components like `<Tweet/>` and `<Youtube/>` that you can use directly. And adding your custom components is also super easy.

```html
<Counter :count="10" />
```

<!-- ./components/Counter.vue -->
<Counter :count="10" m="t-4" />

Check out [the guides](https://sli.dev/builtin/components.html) for more.

</div>
<div>

```html
<Tweet id="1390115482657726468" />
```

<Tweet id="1390115482657726468" scale="0.65" />

</div>
</div>

<!--
Presenter note with **bold**, *italic*, and ~~striked~~ text.

Also, HTML elements are valid:
<div class="flex w-full">
  <span style="flex-grow: 1;">Left content</span>
  <span>Right content</span>
</div>
-->


---
class: px-20
---

# Themes

Slidev comes with powerful theming support. Themes can provide styles, layouts, components, or even configurations for tools. Switching between themes by just **one edit** in your frontmatter:

<div grid="~ cols-2 gap-2" m="-t-2">

```yaml
---
theme: default
---
```

```yaml
---
theme: seriph
---
```

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true" alt="">

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-seriph/01.png?raw=true" alt="">

</div>

Read more about [How to use a theme](https://sli.dev/themes/use.html) and
check out the [Awesome Themes Gallery](https://sli.dev/themes/gallery.html).

---
preload: false
---

# Animations

Animations are powered by [@vueuse/motion](https://motion.vueuse.org/).

```html
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }">
  Slidev
</div>
```

<div class="w-60 relative mt-6">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-square.png"
      alt=""
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-circle.png"
      alt=""
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-triangle.png"
      alt=""
    />
  </div>

  <div
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Slidev
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>

<div
  v-motion
  :initial="{ x:35, y: 40, opacity: 0}"
  :enter="{ y: 0, opacity: 1, transition: { delay: 3500 } }">

[Learn More](https://sli.dev/guide/animations.html#motion)

</div>

---

# LaTeX

LaTeX is supported out-of-box powered by [KaTeX](https://katex.org/).

<br>

Inline $\sqrt{3x-1}+(1+x)^2$

Block
$$ {1|3|all}
\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}
$$

<br>

[Learn more](https://sli.dev/guide/syntax#latex)

---

# Diagrams

You can create diagrams / graphs from textual descriptions, directly in your Markdown.

<div class="grid grid-cols-4 gap-5 pt-4 -mb-6">

```mermaid {scale: 0.5, alt: 'A simple sequence diagram'}
sequenceDiagram
    Alice->John: Hello John, how are you?
    Note over Alice,John: A typical interaction
```

```mermaid {theme: 'neutral', scale: 0.8}
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

```mermaid
mindmap
  root((mindmap))
    Origins
      Long history
      ::icon(fa fa-book)
      Popularisation
        British popular psychology author Tony Buzan
    Research
      On effectivness<br/>and features
      On Automatic creation
        Uses
            Creative techniques
            Strategic planning
            Argument mapping
    Tools
      Pen and paper
      Mermaid
```

```plantuml {scale: 0.7}
@startuml

package "Some Group" {
  HTTP - [First Component]
  [Another Component]
}

node "Other Groups" {
  FTP - [Second Component]
  [First Component] --> FTP
}

cloud {
  [Example 1]
}


database "MySql" {
  folder "This is my folder" {
    [Folder 3]
  }
  frame "Foo" {
    [Frame 4]
  }
}


[Another Component] --> [Example 1]
[Example 1] --> [Folder 3]
[Folder 3] --> [Frame 4]

@enduml
```

</div>

[Learn More](https://sli.dev/guide/syntax.html#diagrams)

---
src: ./pages/multiple-entries.md
hide: false
---

---
layout: center
class: text-center
---

# Learn More

[Documentations](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)
