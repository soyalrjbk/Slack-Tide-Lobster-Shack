# 🦞 Slack Tide Lobster Shack

A responsive one-page website for Slack Tide Lobster Shack, a fictional family-run lobster shack on the wharf in Harpswell, Maine. The page has a hero banner over a lobster roll photo, a menu with prices, a step-by-step guide to eating a whole lobster, and a "Find the Wharf" section with hours, the address, and tips for visiting. The layout adjusts for laptop, tablet, and phone screens.

## How It's Made:

**Tech used:**

<p align="left">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5" />
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3" />
</p>

The page is split into sections that the nav links jump to using `id`s, with `scroll-behavior: smooth` so the page glides to each one instead of jumping. The phone number links use `tel:` so visitors on a phone can tap to call.

**Layout:** I used Flexbox for nearly everything: the header and nav, the two menu cards side by side, the four How-To cards, the three info cards, and the footer. To keep the content centered with a max width but still let the section backgrounds stretch edge to edge, each section uses:

```css
padding-left: max(20px, calc((100% - 1300px) / 2));
```

On wide screens this centers the content in a 1300px column, and on small screens `max()` makes sure there's always at least 20px of space on the sides.

**The menu:** each item is a flex row with the name, a dotted line, and the price, like a printed restaurant menu. The dotted line is an empty `<span>` with `flex: 1`, so it stretches to fill whatever space is left between the name and the price. I first built the menu as a `<table>` and replaced it with this flex layout.

**Hero:** the lobster roll photo sits behind a dark, semi-transparent `linear-gradient` layered in the same `background-image`, so the white text stays readable on top of the photo.

**Responsiveness:** three media queries adjust the layout for laptops (1024px), tablets (768px), and phones (480px). On phones, the cards stack vertically with `flex-direction: column`, the text is centered, the big headline shrinks, and fixed heights switch to `auto` so content doesn't overflow.

## Optimizations

- Fix the stylesheet link for deployment. The folder is named `CSS`, but the HTML links to `css/style.css`. It works on a Mac, but servers like GitHub Pages and Netlify are case-sensitive, so the styles won't load. Renaming the folder to `css` fixes it.
- Move `Lobster Roll.png` into an `images` folder and rename it without a space (e.g. `lobster-roll.png`).
- Remove the extra `</main>` tag. `<main>` closes after the hero, and a second closing tag appears later.
- Add `id="top"` to the top of the page so the **Back to top** link works.
- Add a hamburger menu for phones. The nav is hidden at 480px, so mobile visitors can only use the hero buttons.
- Swap the `<br>` tags used for line breaks inside paragraphs for `max-width` on the text, so the lines wrap naturally on every screen size.
- Use `h2`–`h3` in order instead of `h5` for section headings, which helps screen readers and SEO.
- Fix small typos in the How-To intro ("order of operations", "isn't", "anywhere").

## Lessons Learned:

This project was all about responsive design. I learned how to plan a layout that works on a big monitor and still holds up on a phone, using media queries to change the direction of flex containers, swap fixed heights for `auto`, and resize text at each breakpoint. The `max()` and `calc()` padding trick taught me that CSS can do math to adapt to the screen without extra wrapper elements. Rebuilding the menu from a table into a flex layout with a stretching dotted line also showed me how flexible Flexbox is for small design details, not just big page layouts.
