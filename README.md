# Aggrey's Bakery Website

| | |
|---|---|
| **Student name** | Arehone Kenneth Nengovhela |
| **Student number** | ST10532019 |
| **Module** | WEDE5020 – Web Development (Introduction) |
| **Submission** | Part 2 – Designing the Visuals: CSS Styling and Responsive Design |

## 1. About the project

Aggrey's Bakery is a locally owned bakery in Danville Extension 16, Pretoria West. The bakery sells bread, cakes and confectionery, but it does not have a working website. This project builds a five-page website that introduces the bakery, shows what it bakes and lets customers ask questions.

- **Part 1** planned the site (proposal, sitemap, wireframe) and built the basic HTML pages.
- **Part 2** (this submission) adds an external stylesheet, a desktop design and a responsive design for tablets and phones.
- **Part 3** will add JavaScript, SEO and working forms.

**How to view the site:** download or clone the repository and open `index.html` in a web browser. No extra software is needed.

## 2. Pages

| Page | File | Purpose |
|---|---|---|
| Home | `index.html` | Welcome message, three featured product categories, location |
| About Us | `about.html` | Who the bakery is, why it is online, who it serves |
| Products | `products.html` | Bread, cakes and confectionery, with a link to ask about each |
| Enquiry | `enquiry.html` | Enquiry form (details, topic, message) |
| Contact | `contact.html` | Address and a contact form |

All five pages share the same header, navigation and footer, and all link to `css/style.css`.

## 3. Folder structure

```
Aggreys-Bakery/
├── index.html
├── about.html
├── products.html
├── enquiry.html
├── contact.html
├── README.md
├── css/
│   └── style.css              (the one external stylesheet)
├── images/
│   ├── hero-640/1024/1600     (.webp and .jpg)
│   ├── bread-400/800/1200     (.webp and .jpg)
│   ├── cakes-400/800/1200     (.webp and .jpg)
│   ├── confectionery-400/800/1200
│   ├── about-400/800/1200
│   └── favicon.svg
└── docs/
    ├── WEDE5020 Assigment Part1.docx   (Part 1 proposal)
    ├── sitemap.txt
    ├── wireframe.txt
    └── screenshots/                    (responsive test screenshots)
```

## 4. Design

**Mood:** warm, friendly and local, like a neighbourhood bakery sign. The look is built from butter yellow, dark crust brown and a berry accent, with flat illustrations of the products.

**Colour palette** (every text and background pair passes the WCAG AA contrast ratio of 4.5:1)

| Name | Hex | Used for |
|---|---|---|
| Crust | `#3A2A1F` | Main text, footer background |
| Butter | `#F5C23E` | Header, highlights |
| Butter soft | `#FFF4CF` | Tinted page bands |
| Berry | `#A3214F` | Buttons and links |
| Berry dark | `#7E1A3D` | Hover state for buttons and links |
| Flour | `#FFFFFF` | Page background |

**Typography:** headings use Georgia (serif) for a classic bakery feel; body text uses the device's system font (sans-serif) so it loads fast and is easy to read. Sizes follow a scale where each step is 1.25 times the last (16px, 20px, 25px, 31px, 39px, 49px), stored as CSS variables.

**Layout:** a simple header, main and footer on every page. Content sits in a centred column with a maximum width of 70rem. Pages use bands of pale yellow and white to separate sections.

**Images:** all images are illustrations made for this project (SVG artwork exported as WebP and JPG). Each image comes in three widths so the browser can download the smallest file that suits the screen.

## 5. How the Part 2 requirements are met

| Requirement | Where it is done |
|---|---|
| External stylesheet linked to all pages | `css/style.css`, linked in the `<head>` of all five pages |
| Consistent naming | One stylesheet, lowercase name, in a `css/` folder |
| Base style and CSS reset | Sections 1–3 of `style.css` (reset, colour and font variables, body styles) |
| Typography | `font-family`, `font-size`, `font-weight`, `line-height` and `letter-spacing` on `body` and headings; type scale variables |
| Layout with Grid and Flexbox | Grid with `grid-template-areas` for the page, hero, split sections and footer; Flexbox for the header, navigation and button rows |
| Visual styles | `color`, `background-color`, `border`, `border-radius` and `box-shadow` on bands, cards, forms and buttons |
| Interactive states | `:hover`, `:focus`, `:focus-visible` and `:active` on links, navigation, buttons, cards and form fields |
| Cascade with few selectors | Colours, fonts and spacing are set once on `:root` and `body` and inherited; only a small set of classes is used |
| Breakpoints and media queries | Tablet at `48em` and desktop at `64em` (see the table below) |
| Relative units | `rem`, `em`, `%`, `vw` and `clamp()` for sizes and spacing |
| Responsive images | `<picture>` with WebP and JPG sources, plus `srcset` and `sizes` |
| Screenshots of different screen sizes | Section 7 below |

### Breakpoints

The design is mobile first: the base styles are the phone layout, and media queries add more as the screen gets wider.

| Screen | Width | What changes |
|---|---|---|
| Mobile | under 768px | One column everywhere. Brand sits above the menu, and menu links wrap as tappable buttons. Cards stack with the picture on top. Footer stacked. |
| Tablet | 768px and up | Header becomes one row. Hero and content sections become two columns. Cards become horizontal (picture left, text right). Footer becomes two columns. Larger section spacing and h2 size. |
| Desktop | 1024px and up | Cards sit three across with the picture on top. Footer has three columns. Body text grows to 17px and section spacing increases again. |

## 6. Accessibility notes

- A "Skip to main content" link appears when a keyboard user presses Tab.
- Every form field has a visible `<label>`, and every image has descriptive `alt` text.
- Clear focus outlines on all links, buttons and fields.
- The current page is marked with `aria-current="page"` and shown filled in the menu.
- Animation is switched off for people who ask their device for reduced motion.

## 7. Testing and screenshots

The site was checked in a Chromium-based browser at the screen sizes below. There is no sideways scrolling at any of them. Links, forms, and the hover, focus and active states were checked, and colour contrast was checked against WCAG AA (4.5:1).

| Device (screen size) | Type |
|---|---|
| Desktop / laptop (1440 × 900) | Desktop |
| Small laptop or iPad Pro landscape (1024 × 768) | Desktop (breakpoint edge) |
| iPad Mini (768 × 1024) | Tablet |
| iPhone 12 Pro (390 × 844) | Mobile |
| Samsung Galaxy S8+ (360 × 740) | Mobile (small) |

**Home page on every screen size**

| Desktop 1440 | Laptop 1024 | Tablet 768 | Mobile 390 | Mobile 360 |
|---|---|---|---|---|
| <img src="docs/screenshots/home-desktop-1440.jpg" width="160" alt="Home page at 1440px wide"> | <img src="docs/screenshots/home-laptop-1024.jpg" width="120" alt="Home page at 1024px wide"> | <img src="docs/screenshots/home-tablet-768.jpg" width="100" alt="Home page at 768px wide"> | <img src="docs/screenshots/home-mobile-390.jpg" width="80" alt="Home page at 390px wide"> | <img src="docs/screenshots/home-mobile-360.jpg" width="72" alt="Home page at 360px wide"> |

**All other pages** (Desktop 1440 / Tablet 768 / Mobile 390)

| Page | Desktop | Tablet | Mobile |
|---|---|---|---|
| About Us | <img src="docs/screenshots/about-desktop-1440.jpg" width="160" alt="About page desktop"> | <img src="docs/screenshots/about-tablet-768.jpg" width="100" alt="About page tablet"> | <img src="docs/screenshots/about-mobile-390.jpg" width="80" alt="About page mobile"> |
| Products | <img src="docs/screenshots/products-desktop-1440.jpg" width="160" alt="Products page desktop"> | <img src="docs/screenshots/products-tablet-768.jpg" width="100" alt="Products page tablet"> | <img src="docs/screenshots/products-mobile-390.jpg" width="80" alt="Products page mobile"> |
| Enquiry | <img src="docs/screenshots/enquiry-desktop-1440.jpg" width="160" alt="Enquiry page desktop"> | <img src="docs/screenshots/enquiry-tablet-768.jpg" width="100" alt="Enquiry page tablet"> | <img src="docs/screenshots/enquiry-mobile-390.jpg" width="80" alt="Enquiry page mobile"> |
| Contact | <img src="docs/screenshots/contact-desktop-1440.jpg" width="160" alt="Contact page desktop"> | <img src="docs/screenshots/contact-tablet-768.jpg" width="100" alt="Contact page tablet"> | <img src="docs/screenshots/contact-mobile-390.jpg" width="80" alt="Contact page mobile"> |

The full-size screenshots are in `docs/screenshots/`.

## 8. Changelog

### Part 2 – CSS styling and responsive design (24 September 2026)

#### A. Changes made after the Part 1 feedback

The Part 1 rubric gave marks but no written comments, so each change below targets a criterion where marks were lost in Part 1.

| # | Part 1 criterion (mark) | What was changed |
|---|---|---|
| A1 | Design Aesthetic (1/2) | Added the **Design** section to this README: mood, colour palette with hex values, typography, layout and imagery. The same values are stored as CSS variables in `style.css`. |
| A2 | File and Folder Structure (3/5) | Moved the five pages out of the `html/` folder to the project root so `index.html` is at the top of the repository. Added a `css/` folder for the stylesheet and an `images/` folder for pictures. Screenshots go in `docs/screenshots/`. All links, image paths and stylesheet links were updated to match. |
| A3 | Sufficient Content Added (4/5) | Removed the placeholder sentence from every page and wrote real content: a hero and three product cards on Home; background, audience and offer on About Us; descriptions and examples for bread, cakes and confectionery on Products; a full enquiry form on Enquiry; address details and a contact form on Contact. The pages now match the features promised in the Part 1 proposal. |
| A4 | HTML Tags for Layout and Content Tags (9/10 each) | Changed the navigation from text links separated by `\|` into a proper list (`<nav>`, `<ul>`, `<li>`). Moved the business name out of `<h1>` so each page now has one `<h1>` that describes the page. Added `<section>`, `<article>`, `<figure>`, `<figcaption>`, `<address>` and `<fieldset>` where they fit, `aria-current="page"` on the current menu link, a skip link, a meta description and a favicon on every page. |
| A5 | Code Comments (5/5) | Added explanatory comments to every HTML page and a contents list with section comments to `style.css`. |
| A6 | GitHub commits (2/5) | Part 2 was committed in small steps, each with a descriptive message (see the commit history). |
| A7 | README (3/5) | Rewrote this README: project overview, page list, folder structure, design, how requirements are met, accessibility notes, testing, changelog and references. |
| A8 | Changelog (1/5) | Replaced the one-line changelog with this dated, detailed record of the work. |

#### B. New work in Part 2

- **B1 Stylesheet:** created `css/style.css` and linked it from all five pages.
- **B2 Reset and base styles:** added a CSS reset, colour and font variables, a type scale, spacing variables and default styles for text, headings and links.
- **B3 Layout:** used CSS Grid with `grid-template-areas` for the page, hero, content sections and footer, and Flexbox for the header, navigation and button rows.
- **B4 Visual styling:** styled bands, cards, forms and buttons with colours, borders, rounded corners and shadows. Added `:hover`, `:focus`, `:focus-visible` and `:active` states.
- **B5 Responsive design:** added tablet (`48em`) and desktop (`64em`) breakpoints with a mobile-first approach. Navigation, columns, font sizes and spacing change at each breakpoint. Sizes use `rem`, `em`, `%`, `vw` and `clamp()`.
- **B6 Responsive images:** created illustrations for the hero, bread, cakes, confectionery and about images. Each is exported at three widths in WebP and JPG and used with `<picture>`, `srcset` and `sizes`.
- **B7 Accessibility:** added visible focus outlines, labels on all form fields, alt text on all images and a reduced-motion setting. Colour pairs were checked for a 4.5:1 contrast ratio.
- **B8 Testing:** checked every page at 1440, 1024, 768, 390 and 360 pixels wide for layout problems and sideways scrolling. Saved screenshots in `docs/screenshots/` (all pages at 1440, 768 and 390; the home page also at 1024 and 360).
- **B9 Documentation:** updated this README (changelog and references).

### Part 1 – HTML foundation (August 2026)

- Wrote the project proposal (`docs/WEDE5020 Assigment Part1.docx`) with goals, audience, features, sitemap, low-fidelity wireframe, technical requirements, timeline and budget.
- Created `docs/sitemap.txt` and `docs/wireframe.txt`.
- Created the five HTML pages (`index`, `about`, `products`, `enquiry`, `contact`) with shared navigation.
- Created the first README.

## 9. References

The Independent Institute of Education (2023) *WEDE5020 POE Test Question Paper and Assessment Guidelines*.

The Independent Institute of Education (2024) *WEDE5020 Web Development Module Manual/Guide*.

IOL Business Report (2026) *What South Africa's small businesses can expect in 2026*. Available at: https://iol.co.za/business-report/entrepreneurs/2026-01-29-what-south-africas-small-businesses-can-expect-in-2026/ (Accessed: 7 August 2026).

MDN Web Docs (n.d.) *`<picture>`: The Picture element*. Available at: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture (Accessed: 24 September 2026).

MDN Web Docs (n.d.) *Using media queries*. Available at: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Media_Queries/Using_media_queries (Accessed: 24 September 2026).

PretoriaD (2024) *Bakeries in Pretoria, find list of top bakery near you*. Available at: https://pretoriad.com/bakeries-in-pretoria/ (Accessed: 7 August 2026).

The Weblab (2025) *The importance of online presence for South African businesses 2025*. Available at: https://www.theweblab.co.za/importance-of-online-presence-for-south-african-businesses-2025 (Accessed: 7 August 2026).

World Wide Web Consortium (n.d.) *Understanding Success Criterion 1.4.3: Contrast (Minimum)*. Available at: https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html (Accessed: 24 September 2026).
