# Frontend Mentor - Single-page developer portfolio solution

This is my solution to the [Single-page developer portfolio challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/singlepage-developer-portfolio-bBVj2ZPi-x).

## Table of contents

- [Overview](#overview)
- [What I learned](#what-i-learned)
- [Useful resources](#useful-resources)

## Overview

This project is more complicated than it looks like, especially for the hero part, there are some moving elements like the profile photo and a circle(decoration). Also font size is changing depends on the screen size.

- Live Site URL: https://frontend-mentor-developer-portfolio.vercel.app

## What I learned

### basic HTML
  - line-height: using numbers, so when element's font-size change, the line height will be reflected properly

  - when the width of the content is contained in the middle of the page, use a general class "wrapper" to limit the width, and apply it to different sections of the page, 
e.g header, main,footer

```css
:root {
  --view-width: calc(100vw - 2rem);
}
.wrapper {
  width: var(--view-width);
  max-width: var(--max-width);
  margin: 0 auto;

  /* center the content inside this container */
  display: grid;
  place-items: center;

  padding: 2rem 0;
}

@media screen and (min-width: 700px) {
  .wrapper {
    --view-width: calc(100vw - 3.75rem);
  }
}
```

### style anchor tag/link as a button (in this project, link appear as has a green underline)

```html
<a href="#contact" class="btn">Contact me</a>
```

```css
.btn {
  padding: 0.5rem 0;
  border: none;
  border-bottom: 2px solid var(--clr-accent);

  text-transform: uppercase;
  color: var(--clr-white);
  font-size: 1rem;
  letter-spacing: 2.29px;
  line-height: 26px;
  font-weight: var(--font-bold);
}
.btn:hover {
  color: var(--clr-accent);
}
```

### typography for responsive design
  using clamp, the logo text is 24px on mobile and 32px on tablet
  https://royalfig.github.io/fluid-typography-calculator/
  min font size: 24px
  min viewport: 375px
  max font size: 32px
  max viewport: 768px

  ```css
  .logo {
    font-size: 1.5rem;
    font-size: clamp(1.5rem, 1.02rem + 2.035vw, 2rem);
    font-weight: var(--font-bold);
  }
  ```

### using different profile images based on screen size.

```css
    <picture>
      <source
        media="(min-width: 62.5em)"
        srcset="./images/image-profile-desktop.webp"/>
      <source
        media="(min-width: 37.5em)"
        srcset="./images/image-profile-tablet.webp" />
      <img class="profile-img" src="./images/image-profile-mobile.webp"     alt="profile image"
        width="174"
        height="383"
      />
    </picture>
```

### draw a horizontal line as separation between setions, we can use <hr> or border-bottom on the section

```css
hr {
  border: none;
  border-top: 1px solid var(--clr-white);
  width: var(--view-width);
  max-width: var(--max-width);
}
```

### to center an item with postion:absolute

```css
.hero__img {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  margin: 0 auto;
}
```

or

```css
.hero__img {
  position: absolute;
  top: 0;
  left: 50%;
  translate: -50%; /* transform: translateX(-50%) */
}
```

### hover effect over the project part
when mouse over, picture will have a dark overlay shade and the link button is moved into the middle of the project image location.
use opacity to control the visibility of an element.

```css
@media screen and (min-width: 62.5em) {
  .project__picture {
    position: relative;
  }

  .project__picture::after {
    content: "";
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: hsl(0, 0%, 0%);
    opacity: 0;
    transition: opacity var(--transition);
  }
  .project:hover .project__picture::after {
    opacity: 0.5;
  }
}
```

### basic form validation without javascript

```css
.contact__invalid-icon {
  display: none;
  position: absolute;
  bottom: 1rem;
  right: 0;
}
.contact input:focus-visible:invalid ~ .contact__invalid-icon,
.contact textarea:focus-visible:invalid ~ .contact__invalid-icon {
  display: inline-block;
}
```

## Useful resources

I took reference to youtuber thecodercoder's [github code](https://github.com/thecodercoder/fem-single-page-developer-portfolio).
She has 4-part video for this project, however they are very long videos, I skipped most part of the videos because they look like recorded live stream without editing and you will watch her spending 30min to troubleshooting a minor issue.
