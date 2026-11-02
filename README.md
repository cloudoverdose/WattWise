# Wattwise Website

Energy-saving education and eco-friendly homes.
SDG 7

## Group Members

Name - Student ID - Contribution
Ni Putu Febby Cahya Anggariani - 2515091048 - Created dampak.html, dampak.css, rumah-hijau.html, rumah.css
Putu Nadin Saskirani Putri - 2515091065 - Created the GitHub repository, built the homepage (HTML and CSS), built global.css, wrote the README text
Ni Kadek Nina Riti Angguni - 2515091086 - Created energi-terbarukan.html, renewable.css, tentang-sdg.html, sdg.css
Kadek Denis Krisna Febrian - 2515091099 - Created tips.html, about-us.html, tips.css, about-us.css

## Website Description

**Purpose:** Wattwise is an educational website about SDG 7 (Affordable and Clean Energy). It helps visitors understand the goals of SDG 7, renewable energy sources, the impact of wasting electricity, and ways to save electricity and make their homes more eco-friendly.

**Benefits:**
- Gives a basic understanding of SDG 7 and renewable energy.
- Shows the connection between daily habits, electricity bills, and the environment.
- Provides practical tips that can be applied at home right away.

**Target users:** Students, university students, and the general public who want to learn how to save energy at home.

## Website Pages

Home, About SDGs, Renewable Energy, Energy Impact, Green Home, Saving Tips, About Us

## Technologies

- **HTML5:** page structure with semantic elements (header, nav, main, section, footer, details/summary).
- **CSS3:** styling, CSS variables (:root), transitions, and shadows.
- **Flexbox and Grid:** layout for the navbar, cards, steps, and footer.
- **CSS Media Queries:** responsive layout for tablets and phones.
- **GitHub Pages:** website hosting.

## Implementation Explanation

1. Navigation

All 7 pages share the same `<header class="nav">`, styled by `global.css`. Home is used as the example.

```html
<header class="nav">
  <a class="logo" href="index.html">Watt<span>wise</span></a>
  <input type="checkbox" id="mn" aria-label="Open menu" />
  <label for="mn" class="burger">☰ Menu</label>
  <nav>...7 links...</nav>
</header>
```

```css
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  position: sticky;
  top: 0;
}
nav a { padding: 8px 12px; border-radius: 20px; }
nav a:hover { background: var(--l); }
#mn, .burger { display: none; }
```

- Flexbox places the logo on the left and the links on the right. `flex-wrap: wrap` lets the menu drop to a new row on small screens.
- `position: sticky; top: 0` keeps the bar visible while scrolling.
- The checkbox and burger button are hidden on desktop because all links fit in the bar.
- The `<nav>` must come after the checkbox so the selector `#mn:checked ~ nav` can work.

2. Layout

Each page uses semantic tags: `<header>`, `<main>` with three `<section>` blocks, and `<footer>`. Global rules limit content width (`section { max-width: 1000px; margin: auto; }`), and `home.css` defines the three Home sections.

*Hero*

```css
.hero {
  display: flex;
  align-items: center;
  min-height: 520px;
  background:
    linear-gradient(90deg, #1f3a26eb 0%, rgba(31,58,38,0.75) 45%, rgba(31,58,38,0.1) 100%),
    url("../img/background.jpg") center / cover no-repeat;
}
```

The hero is a full-width banner. A left-to-right gradient darkens the left side so the white heading stays readable, while the photo shows on the right.

*How it works (`.why`)*

```css
.why { display: grid; grid-template-columns: 1fr 1.3fr; gap: 40px; align-items: center; }
.steps li { display: grid; grid-template-columns: 48px 1fr; background: #fff; border-radius: 14px; }
```

The section has two columns: intro text on the left and the three step cards on the right (the right column is slightly wider). Inside each step, a second grid places the 48px icon beside the title.

*Why is it important? (`.important`)*

```css
.grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
.card { background: #1f3a26eb; border-radius: 16px; transition: transform 0.2s; }
.foto { width: 100%; height: 260px; object-fit: cover; }
```

Three cards sit in an equal-width grid. `object-fit: cover` crops each photo to a uniform size without distortion, and the card lifts slightly on hover.

3. Responsive Design

The website uses three `@media (max-width)` breakpoints:

- 960px (Tablet) :  `.grid` goes from 3 to 2 columns 
- 860px (Small tablet) :  Burger menu appears, section padding and `h1` shrink 
- 700px (Phone) : Hero shortens, `.why` and `.grid` become 1 column, photos shrink to 220px |

*Burger menu (≤ 860px)*

```css
.burger { display: inline-block; }
.nav nav { display: none; width: 100%; order: 3; }
#mn:checked ~ nav { display: block; }
nav a { display: block; padding: 12px 0; border-top: 1px solid #dbe6d4; }
```

The menu is hidden by default. Clicking the burger label checks the hidden checkbox, and `#mn:checked ~ nav` shows the menu without any JavaScript. The links stack vertically with larger touch areas and divider lines.

*Phone layout (≤ 700px)*

```css
.hero { min-height: 420px; padding: 70px 5%; }
.why { grid-template-columns: 1fr; padding: 48px 5%; }
.grid { grid-template-columns: 1fr; }
.foto { height: 220px; }
```

All multi-column grids collapse into a single column. The hero gradient also changes to an even dark overlay, so the text is readable over the whole image on a narrow screen.
 4. Important Code

- *CSS variables* in `:root` (`--g`, `--d`, `--y`, `--l`, `--c`) define the five theme colors once, so the whole theme can be changed in one place.
- *`.btn` and `.btn.alt`* are reusable button styles (yellow primary, white outlined secondary) with a hover lift.
- *`img, svg { max-width: 100%; height: auto; }`* keeps images inside their containers.
- *`:focus-visible` outlines* give keyboard users a clear yellow focus ring.
- *`@media (prefers-reduced-motion: reduce)`* turns off hover animations for users who prefer less motion.
- *`.fgrid` with `repeat(auto-fit, minmax(200px, 1fr))`* makes the footer adapt automatically without a media query.


## Folder Structure

```
WattWise/
├── css/
│   ├── global.css        # shared styles: colors, fonts, navbar, buttons, footer
│   ├── home.css          # Home page styles
│   ├── sdg.css           # About SDGs page styles
│   ├── renewable.css     # Renewable Energy page styles
│   ├── dampak.css        # Energy Impact page styles
│   ├── rumah.css         # Green Home page styles
│   ├── tips.css          # Saving Tips page styles
│   └── about-us.css      # About Us page styles
├── html/
│   ├── tentang-sdg.html
│   ├── energi-terbarukan.html
│   ├── dampak.html
│   ├── rumah-hijau.html
│   ├── tips.html
│   └── about-us.html
├── img/                  # images, icons, and backgrounds
├── index.html
└── README.md
```

## Image Sources

- pay bills.jpg: Rawpixel, https://www.rawpixel.com/image/2051982/man-paying-bills
- air polution: Pinterest, https://id.pinterest.com/pin/624100460898211299/
- sustainable city: Illustration "Renewable Energy City Design Concepts" from the article 12 Sustainable City Design Ideas For A Greener Future, My Garbage Collection
- background: Image "Eco-city with wind turbines and green rooftops" from the article The 21st century development agenda by Lwandiso Mpepho, Meer, 27 August 2025
- bar icon.png: "Bar Chart 5", SVG Repo, CC0 license (color changed)
- home icon.png: "Eco Home Eco House", SVG Repo, CC0 license (color changed)
- phone charger: Pexels, https://www.pexels.com/photo/minimalist-wall-socket-with-charging-cable-36022185/
- sunlight: Pinterest, https://id.pinterest.com/pin/1112881757941104826/
- energy star: Pinterest, https://id.pinterest.com/pin/4595149477620635520/
- solar panel: Pexels, https://www.pexels.com/photo/modern-home-with-rooftop-solar-panels-29206495/
- ac remote: Pinterest, https://id.pinterest.com/pin/1009580441491432498/
- led: Pexels, https://www.pexels.com/photo/person-holding-white-light-bulb-3946161/
- solar.jpg: Photo by Adrinil Dennis from Pexels, https://www.pexels.com/photo/solar-panel-closeup-27873610/
- hydro.jpg: Photo by Baro from Pexels, https://www.pexels.com/photo/scenic-view-of-flowing-river-on-a-forest-14942582/
- wind.jpg: Photo by Ahsen from Pexels, https://www.pexels.com/photo/wind-turbines-on-the-horizon-7763083/
- geothermal.jpg: Photo by Raul Ling from Pexels, https://www.pexels.com/photo/stunning-geothermal-landscape-in-iceland-31992416/
- biomass.jpg: Photo by Nejc Parašuh from Pexels, https://www.pexels.com/photo/golden-ripe-wheat-17228686/
- renewable-hero.jpg: Photo by Johannes Plenio from Pexels, https://www.pexels.com/photo/green-forest-1776267/

## Website and Repository
URL Github Pages: https://cloudoverdose.github.io/WattWise/
URL Repository: https://github.com/cloudoverdose/WattWise.git

### Data Sources

- Indonesia's renewable energy mix data: esdm.go.id
- UN: SDG 7
- Bappenas SDGs
