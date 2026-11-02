# Aggrey's Bakery Website

| | |
|---|---|
| **Student name** | Arehone Kenneth Nengovhela |
| **Student number** | ST10532019 |
| **Module** | WEDE5020 – Web Development (Introduction) |
| **Submission** | Part 3 – Enhancing Functionality and SEO |
| **Live website** | https://glittering-bunny-5d3cb6.netlify.app |
| **GitHub repository** | *(paste your repository link here)* |

## 1. About the project

Aggrey's Bakery is a locally owned bakery in Danville Extension 16, Pretoria West. The bakery sells bread, cakes and confectionery, but it does not have a working website. This project builds a website that introduces the bakery, shows what it bakes and lets customers ask questions.

- **Part 1** planned the site (proposal, sitemap, wireframe) and built the basic HTML pages.
- **Part 2** added an external stylesheet, a desktop design and a responsive design for tablets and phones.
- **Part 3** (this submission) adds JavaScript features, search engine optimisation (SEO), working and validated forms, and puts the site online.

**How to view the site:** open the live website link above. To run it on your own computer, serve the folder with a small local server (for example the *Live Server* extension in VS Code, or `python -m http.server`) and open `http://localhost:8000`. Opening `index.html` by double-clicking works for the layout, but the product list is loaded from `data/products.json` with `fetch()`, and browsers block `fetch()` on `file://` addresses.

## 2. Pages

| Page | File | Purpose |
|---|---|---|
| Home | `index.html` | Welcome message, featured products (loaded by JavaScript), location |
| About Us | `about.html` | Who the bakery is, in three tabs (what we bake, how to order, where to find us) |
| Products | `products.html` | Searchable, filterable and sortable product list, details window, picture gallery with lightbox |
| Enquiry | `enquiry.html` | Enquiry form that answers with a price estimate and the earliest date |
| Contact | `contact.html` | Interactive map, contact form that builds an email, FAQ accordion |
| Thank you | `thanks.html` | Page shown after an enquiry is sent without JavaScript |

All pages share the same header, navigation and footer, and all link to `css/style.css`.

## 3. Folder structure

```
Aggreys-Bakery/
├── index.html  about.html  products.html  enquiry.html  contact.html  thanks.html
├── README.md
├── robots.txt                 (tells search engines which pages to visit)
├── sitemap.xml                (lists every page for search engines)
├── _headers                   (security and caching headers, read by Netlify)
├── css/
│   └── style.css              (the one external stylesheet)
├── js/
│   ├── common.js              (shared helpers, loads the product data, scroll reveal)
│   ├── widgets.js             (tabs, accordion, gallery lightbox, dialogs)
│   ├── catalogue.js           (product cards, search, filter, sort, details window)
│   ├── map.js                 (Leaflet map on the Contact page)
│   └── forms.js               (validation, enquiry answer, contact email, AJAX)
├── data/
│   └── products.json          (the product list: names, prices, notes)
├── images/                    (illustrations and ten product photographs, descriptive names, .webp and .jpg)
└── docs/
    ├── WEDE5020 Assigment Part1.docx
    ├── sitemap.txt
    ├── wireframe.txt
    └── screenshots/           (responsive test screenshots from Part 2)
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
| Error | `#B00020` | Error messages and borders (added in Part 3) |
| Error soft | `#FDECEE` | Pale background of error boxes (added in Part 3) |
| Berry visited | `#6B2A7A` | Links the visitor has already opened (added in Part 3) |

**Typography:** headings use Georgia (serif) for a classic bakery feel; body text uses the device's system font (sans-serif) so it loads fast and is easy to read. Sizes follow a scale where each step is 1.25 times the last (16px, 20px, 25px, 31px, 39px, 49px), stored as CSS variables.

**Layout:** a simple header, main and footer on every page. Content sits in a centred column with a maximum width of 70rem. Pages use bands of pale yellow and white to separate sections.

**Images:** the hero, category and shopfront pictures are illustrations made for this project (SVG artwork exported as WebP and JPG). In Part 3 ten product photographs were added to the product cards (see Image credits at the end of this README). Each image comes in three widths so the browser can download the smallest file that suits the screen. In Part 3 the files were renamed with descriptive words (for example `aggreys-bakery-celebration-cakes-800.webp`) for SEO.

## 5. How the Part 2 requirements were met (completed in Part 2)

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

### Extra media queries added in Part 3

| Query | What changes |
|---|---|
| `max-width: 23.4375em` (375px and narrower) | Smaller side space, a smaller brand name so it fits beside the Menu button, buttons fill the full width, tighter form boxes. |
| `min-width: 90em` (1440px and wider) | Wider page (78rem), more space between sections, 18px body text. Image `sizes` values were updated to match. |
| `pointer: coarse` (touch screens) | Buttons, menu links, footer links and form fields are at least 44px tall; check boxes are bigger. |
| `orientation: landscape` and `max-height: 30em` (phone turned sideways) | An open menu, the details window and the lightbox scroll instead of running off the screen. |
| `print` | The menu button is hidden, all links show, and cards that never scrolled into view still print. |
| `prefers-reduced-motion: reduce` | All animation and transitions are switched off. |

## 6. How the Part 3 requirements are met

| Requirement | Where it is done |
|---|---|
| **Accordion** | FAQ on `contact.html`. Built with real `<button>` elements, `aria-expanded` and `aria-controls`; panels open and close with a CSS animation (`widgets.js`, section 3). |
| **Folding mobile menu** | On phones the five links fold behind a Menu button (`aria-expanded`, `aria-controls`). Esc, a click outside or choosing a link closes it, and it resets when the screen gets wider (`common.js`, section 5). Without JavaScript the normal row of links stays. |
| **Tabs** | About Us page. Arrow, Home and End keys move between tabs and `aria-selected` is updated (`widgets.js`, section 2). Without JavaScript all three panels show one after the other. |
| **Modal windows** | The product details window on `products.html` and the gallery lightbox use the native `<dialog>` element. Esc, the close button and a click outside all close them. |
| **Interactive map** | `contact.html` uses **Leaflet** with OpenStreetMap tiles (free, no API key). The map has a marker with a pop-up and an "Open in Google Maps" link. Leaflet is only downloaded when the visitor scrolls near the map (`map.js`). |
| **Animations and transitions** | CSS transitions on buttons, cards and the accordion; a rise-in animation for windows; cards and gallery pictures fade in as they scroll into view (JavaScript adds a class, CSS does the animation). All animation is switched off for visitors who ask for reduced motion. |
| **Advanced DOM manipulation** | Product cards, the result messages, the error summary and the email preview are created with `createElement` and `textContent`, never `innerHTML`, so typed text can never run as code. The product list for an enquiry changes when the category changes (`catalogue.js`, `forms.js`). |
| **Gallery with lightbox** | Products page. The gallery shows the ten product photographs. Click or press Enter on a picture to enlarge it; use the arrow keys or buttons to move between pictures; the counter shows "Picture 1 of 10". The large picture keeps its own shape and is never stretched. |
| **Dynamic content** | The product cards on Home and Products are built by JavaScript from `data/products.json`, which is loaded with `fetch()`. Each card and the details window also show the product's photograph, named in the JSON file. |
| **Search, filter and sort** | Products page: search by name, filter by category, sort by name or price, with a live count and a "no products match" message. |
| **Forms with HTML** | Both forms use `<fieldset>`, `<label>`, `<input>` (text, email, tel, number, date, checkbox), `<select>` and `<textarea>`. |
| **JavaScript validation** | `forms.js` (see section 8). |
| **AJAX form submission** | The enquiry form is sent with `fetch()` without reloading the page (`forms.js`, section 4). |
| **SEO** | Section 7. |
| **GitHub** | Section 10. |
| **Deploy on a free platform** | Netlify (section 10). |

## 7. Search engine optimisation (SEO)

### 7.1 Keyword research

The keywords were chosen by thinking about what a local customer would type into a search engine, and by looking at what the competing bakeries in the area use (see the references). They can be checked later with Google Search Console.

| Keyword phrase | Used in |
|---|---|
| bakery in Pretoria West | Home title, meta description, hero heading, footer |
| bakery Danville Pretoria | About and Contact titles, address blocks |
| fresh bread Pretoria West | Home title and text, Products page |
| birthday cakes Pretoria West | Products page, cake product cards |
| doughnuts and cupcakes Pretoria West | Products page title and descriptions |
| order a cake online | Enquiry page title and text |

### 7.2 On-page SEO

| Item | What was done |
|---|---|
| Title tags | A different title on every page, with the page topic first and the bakery and area after it. |
| Meta descriptions | A different description on every page (one clear sentence with the main keyword). |
| Header tags | One `<h1>` per page, then `<h2>` and `<h3>` in order. No levels are skipped. |
| Image optimisation | Descriptive file names (for example `aggreys-bakery-celebration-cakes-800.webp`), descriptive `alt` text, width and height set to stop the page jumping, and `loading="lazy"` for pictures below the top of the page. The ten product photographs are cropped to a square for the cards (320 and 400 pixels wide, WebP with a JPG fallback) and also kept in a larger uncropped version for the lightbox. Each has a long, plain-English `alt` description. |
| URL structure | Short lowercase file names that say what the page is (`products.html`, `enquiry.html`). No spaces or capital letters. |
| Internal linking | Every page is linked from the main menu and the footer; product cards link to the enquiry form with the product already chosen (`enquiry.html?product=birthday-cake`). |
| Mobile-friendliness | Mobile-first design from Part 2 with the viewport meta tag. |
| Canonical tag | Every page names its own preferred address so search engines do not treat copies as different pages. |
| Open Graph and Twitter tags | Title, description and picture for the preview shown when a page is shared. |
| Structured data | `index.html` has a JSON-LD block (schema.org `Bakery`) with the name, address, area and website address. |

### 7.3 Off-page SEO (plan and what is built into the site)

These steps happen outside the website, so they are a plan:

- **Backlinks:** ask the local ward or community page, the Pretoria West business forum and local school newsletters to link to the website; register in free local business directories.
- **Social media:** share new cakes and specials on Facebook and WhatsApp, always with a link to the Products page. Every page already has "Share this page" links for Facebook and WhatsApp.
- **Local SEO:** create a free Google Business Profile with the same name, address and area as the site, add photos and ask happy customers for reviews. The address on the site and in the structured data is written the same way each time.

### 7.4 Additional requests

| Item | What was done |
|---|---|
| `robots.txt` | Allows all pages, asks crawlers to skip the `docs/` folder and gives the address of the sitemap. |
| `sitemap.xml` | Lists the five main pages with the date last changed and a priority. |
| Page speed | Scripts use `defer`. Leaflet loads only when the map is near the screen. Images come in three sizes as WebP with a JPG fallback, and are lazy-loaded below the top of the page. No frameworks or web fonts are used. Static files are cached by the browser (`_headers`: images for 30 days, styles and scripts for one day). |
| Security | See section 9. |


## 8. Forms and validation

**Enquiry form (`enquiry.html`): asking about a product.** The visitor chooses a category, then a product from that category (the product list changes with the category), a quantity and the date they need it. When the form is valid, JavaScript works out the answer and shows it on the page: the estimated price (quantity × price from `data/products.json`), whether it is available, and the earliest date. Some products need notice (birthday cake: 3 days, celebration cake: 5 days, cupcakes: 1 day, bread and confectionery: none). If the date asked for is too early, the answer says so and gives the earliest date.

**Contact form (`contact.html`): a general message.** The visitor gives basic contact details, the type of message, a subject and a message. When the form is valid, the details are put together into an email and shown in a preview. The visitor can open it in their email program with one button (a `mailto:` link to the address set at the top of `forms.js`) or copy the text.

**Validation rules** (all checked in JavaScript when the visitor leaves a field and again when the form is sent; HTML attributes such as `required`, `maxlength` and `pattern` are also on the fields):

| Field | Rule |
|---|---|
| Full name | Required, 2 to 60 characters, letters, spaces, hyphens, apostrophes and full stops only. |
| Email | Required, up to 100 characters, must look like `name@example.com`. |
| Phone | Optional. If given, a South African number: 10 digits starting with 0, or +27 followed by 9 digits. Spaces, hyphens and brackets are allowed. |
| Category and product | Required choices. |
| Quantity | Required whole number from 1 to 100. |
| Date needed | Optional. Today or later, and within the next six months. |
| Subject (contact form) | Required, 5 to 80 characters. |
| Message | Required, 10 to 500 characters on the enquiry form and 10 to 1000 on the contact form, with a live character counter. |
| Consent box | Must be ticked before the enquiry is sent. |

**Error handling.** Each field has its own message next to it (`aria-describedby`, `aria-invalid`). When a form is sent with mistakes, an error summary appears at the top, keyboard focus moves to it, and each item links to the field. Messages are written in plain English and say how to fix the problem.

**AJAX.** The enquiry is sent with `fetch()` to the form address while the page stays where it is. The visitor sees a "Sending your enquiry" message and then the result. The form is also marked for **Netlify Forms** (`data-netlify="true"` with a hidden honeypot field), so when the site is hosted on Netlify the answers are collected for free. If the request fails, the page says so honestly and offers a link that opens the same enquiry as an email instead. If JavaScript is switched off, the form is sent in the normal way and, on Netlify, `thanks.html` is shown.

## 9. Security

- **Content Security Policy** set in a `<meta>` tag on every page. Scripts, styles and images may only come from the site itself; the Contact page also allows Leaflet and OpenStreetMap tiles. `_headers` adds `frame-ancestors 'none'` so no other site can show these pages inside a frame.
- **Subresource Integrity** hashes on the Leaflet files, so the browser refuses a file that has been changed.
- **No `innerHTML`** with user text. Everything is added with `textContent`, so typed input cannot run as code (protection against cross-site scripting).
- **Input checks and limits** (`maxlength`, patterns, length checks) on every field; a hidden honeypot field catches simple spam robots.
- **Headers** in `_headers`: `X-Content-Type-Options`, `X-Frame-Options`, `Referrer-Policy` and `Permissions-Policy`.
- **Safe links:** external links use `rel="noopener noreferrer"`.
- **HTTPS:** Netlify serves the site over HTTPS automatically.
- The contact form only builds an email on the visitor's own device; no personal details are stored by the website.

## 10. GitHub and deployment

**GitHub.** The project is kept in a GitHub repository (link at the top of this README). Changes are committed in small steps with descriptive messages (for example *"Add product search and filter"*) and pushed to the remote repository. The repository link is submitted on the learning management system.

**Deployment on Netlify (free).**

1. Sign in to Netlify with the GitHub account and choose **Add new site → Import an existing project**.
2. Pick the repository. Leave the build command empty and set the publish directory to the repository root (`.`).
3. Deploy. Netlify gives a `https://….netlify.app` address; the site name can be changed under *Site configuration*.
4. Under *Forms*, check that the **enquiry** form is listed after the first deploy.
5. Replace the address in the places listed in section 7.4 if it is not `regal-phoenix-b79ab1.netlify.app`, then commit and push again. Netlify redeploys automatically.

## 11. Accessibility notes

- A "Skip to main content" link appears when a keyboard user presses Tab.
- Every form field has a visible `<label>`, and every image has descriptive `alt` text.
- Clear focus outlines on all links, buttons and fields.
- The current page is marked with `aria-current="page"` and shown filled in the menu.
- Animation is switched off for people who ask their device for reduced motion.
- **Tabs, accordion and windows:** keyboard operable, with the correct ARIA roles and states; windows use the native `<dialog>` element, which traps focus and closes with Esc.
- **Forms:** every error is written next to its field and in a summary that receives focus; the enquiry answer also receives focus, and status messages use `role="status"` so screen readers announce them.
- **Mobile menu and touch screens:** the Menu button announces whether it is open, Esc returns focus to it, and on touch screens every button, link and field is at least 44px tall.
- **Without JavaScript:** the tabs and accordion show all their content, and a notice explains that the product search needs JavaScript.

## 12. Testing

**Part 3 tests.** Each feature was tested in Chromium with an automated browser script and by hand. All checks below passed.

| Area | What was checked |
|---|---|
| Products | 10 product cards load from the JSON file; search for "cake" returns 3 products; a search with no match shows a message; clearing the search restores all 10; the bread filter shows 4; sorting by price puts the dearest or cheapest first; the details window opens in the centre and closes with Esc. |
| Gallery | Lightbox opens, shows "1 of 5", the right arrow key moves to picture 2, and the window closes. |
| Tabs and accordion | Arrow keys switch tabs and update `aria-selected`; End key goes to the last tab; FAQ items start closed, open on click and close again. |
| Enquiry form | An empty send shows five errors and moves focus to the summary; invalid names, emails, phone numbers, quantities, past dates and short messages are rejected; valid input gives a greeting, the correct total (for example 2 × R250 = R500) and a warning when the date is earlier than the product allows; changing the category to a custom order hides the product list; the reset button clears the answer. |
| Contact form | Errors on an empty send; a valid send builds the email link with the message type in the subject; the copy button puts the email on the clipboard. |
| Failure handling | When the server refuses the AJAX request, the page shows a message and an email link instead of a false "sent". |
| Mobile menu | At 390px and 320px the closed header is one short row with the brand and Menu button side by side; the button opens the menu (`aria-expanded`, label changes to Close); the five links are each at least 44px tall; Esc closes it and returns focus to the button; a click outside closes it; a link navigates; there is no sideways scrolling. At 1280px the button is hidden and the links sit in one row. With JavaScript switched off the normal links show. |
| Layout | The three featured cards on the home page fill the full row; the Send button is greyed out while an enquiry is on its way and comes back afterwards; a section opened from a jump link (for example `products.html#cakes`) is tinted. Every product card, the details window and the gallery show their photograph (10 of 10 loaded, none missing); the lightbox opens the photo that was clicked at its own size; availability text reads "Order at least 3 days in advance". |
| Images | At 360, 768, 1280 and 1600px wide, every picture on Home, About and Products was measured: the file the browser chose matches the size the picture is shown at (within 3% of the width in the `sizes` attribute). The ten product photographs were checked in the same way, and each card photo is square at every screen size. |
| HTML and CSS audit | All six pages link `css/style.css` once, with no `<style>` blocks and no inline `style` attributes; the header and footer are identical on every page; each page has one `<h1>`, no skipped heading levels, a title, a description and `lang="en-ZA"`. |
| Console | No JavaScript errors on any page. |
| Links and files | Every local link, image and script file exists. |

The **map** needs an internet connection to download Leaflet and the map tiles, so it must also be checked on the live website after deployment.

**Responsive testing (Part 2).** The layout was checked at the screen sizes below. There is no sideways scrolling at any of them.

| Device (screen size) | Type |
|---|---|
| Desktop / laptop (1440 × 900) | Desktop |
| Small laptop or iPad Pro landscape (1024 × 768) | Desktop (breakpoint edge) |
| iPad Mini (768 × 1024) | Tablet |
| iPhone 12 Pro (390 × 844) | Mobile |
| Samsung Galaxy S8+ (360 × 740) | Mobile (small) |

The screenshots in `docs/screenshots/` were taken during Part 2 and show the layout at each size.

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

## 13. Changelog

### Part 3 – Enhancing functionality and SEO (2 November 2026)

#### A. Changes made after the Part 2 feedback

Part 2 scored **80/100**. The marking rubric gave a mark for every criterion but no written comments, so each change below targets a criterion where marks were lost. Where I found nothing wrong, the entry says what was checked.

| # | Part 2 criterion (mark) | What was changed |
|---|---|---|
| A1 | Feedback for Part 1 (6/10) | This changelog now lists every change with the file it was made in and the reason. The eight Part 1 items from the Part 2 changelog were re-checked one by one (table A-1 below), and each Part 3 change is listed in section B with its file name. |
| A2 | External stylesheet created and implemented in each page (7/10) | Checked all six pages by script: each links `css/style.css` once in the `<head>` with a relative path (so it works on GitHub and Netlify), and none has a `<style>` block or an inline `style` attribute. Corrected the stylesheet's header comment, which still said "five pages", and its table of contents, which now lists every section. |
| A3 | Default style code (4/5) | Added the defaults that were missing in `style.css`: a colour for already-visited links (`--berry-visited`), a soft background colour for pictures while they load, and `::placeholder` and `::selection` styles, so even small browser defaults match the colour scheme. |
| A4 | Typography styles (4/5) | Body text, `h2` and `h3` now use `clamp()` so the size grows smoothly with the screen (section 22.4). Headings use `text-wrap: balance` so a heading never ends with one word alone on a line. Placeholders are italic and muted so they are not mistaken for typed text. |
| A5 | Layout structure (3/5) | Found by reviewing the screenshots: (1) on the home page the three "Popular at the bakery" cards sat in a four-column grid and left an empty column on the right, so they now share the full width (`#popular-list`); (2) the first heading in a text column had extra space above it, which pushed the text out of line with the picture beside it, so that space is removed with `:first-child`; (3) an empty answer box no longer takes up space (`:empty`). |
| A6 | Decoration and colour (4/5) | Added colour feedback that follows the palette: the section you jumped to (Bread, Cakes, Confectionery) is tinted with `:target`; the label of the field you are typing in turns berry (`:focus-within`) and the label of a field with a mistake turns red (`:has()`); visited links, selected text and a greyed-out Send button each have a matching colour. |
| A7 | Pseudo-classes (8/10) | Before: `:hover`, `:focus`, `:focus-visible`, `:active`, `:focus-within` (on cards), `:nth-child`, `::before`, `::after`. Added: `:visited`, `:disabled`, `:target`, `:focus-within` on form fields, `:has()`, `:not()`, `:is()`, `:empty`, `:first-child`, `::placeholder`, `::selection` and a `::before` icon for the menu button. The Send button is now really disabled while an enquiry is sent (`forms.js`), so the `:disabled` style is used. |
| A8 | Media queries and breakpoints (9/10) | Added queries for small phones (375px and narrower), wide screens (1440px and wider), touch screens (`pointer: coarse`), phones turned sideways (landscape with little height) and printing. See "Extra media queries added in Part 3" in section 5. |
| A9 | Adjustment - Layout (4/5) | Small phones get tighter side space and full-width buttons; wide screens get a wider page and more spacing; phones turned sideways get scrolling menus and windows; the home page cards fill the row (A5). |
| A10 | Adjustment - Typography (4/5) | Text sizes are fluid between the breakpoints instead of jumping at 768px and 1024px, and wide screens use 18px body text. |
| A11 | Adjustment - Navigation menu (3/5) | On a phone the five links took two rows of pills and pushed the page content down. They now fold behind a **Menu** button (`common.js`, `style.css` section 22.1). The button works with keyboard and touch, and without JavaScript the normal links stay. From 768px up the links sit in a row as before. |
| A12 | Adjustment - Images (4/5) | Measured every picture at 360, 768, 1280 and 1600px wide and compared the file the browser chose with the size shown. At 1440px and wider the `sizes` values were too small, so the browser chose a file that was stretched by about 10%; the `sizes` values for the hero, cards and content pictures now include the wide-screen size. Added `decoding="async"` to pictures below the top of the page and `object-fit: cover` so pictures fill their frame without stretching. |
| A13 | GitHub, README, Changelog, References (5/5 each) | Kept at full marks: this README, the changelog and the reference list were updated for Part 3, and the work was committed in small steps with descriptive messages. |

**Table A-1: Part 1 feedback re-checked on 2 November 2026**

| Part 1 criterion (mark) | Status now |
|---|---|
| Design Aesthetic (1/2) | Section 4 of this README states the mood, colour palette (with the Part 3 additions), typography and layout. The same values are the CSS variables in `style.css`. |
| File and Folder Structure (3/5) | Pages are in the root folder with `index.html` at the top. Files are grouped in `css/`, `js/`, `data/`, `images/` and `docs/`. `robots.txt`, `sitemap.xml` and `_headers` sit in the root because search engines and Netlify look for them there. Image files have descriptive names. |
| Sufficient Content Added (4/5) | No placeholder text remains on any page (checked by search). Part 3 added ten products with prices, three tabs, four FAQ answers and a full enquiry and contact form. |
| HTML Tags for Layout and Content Tags (9/10 each) | The header and footer are identical on all six pages (checked by script), each page has one `<h1>` and no skipped heading levels, and `<nav>`, `<main>`, `<section>`, `<article>`, `<figure>`, `<address>` and `<fieldset>` are used where they fit. |
| Code Comments (5/5) | Every HTML page, the stylesheet and each JavaScript file has explanatory comments and a contents list. |
| GitHub commits (2/5) | Part 2 scored 5/5. Part 3 continues with small commits and descriptive messages. |
| README (3/5) | Part 2 scored 5/5. This README was extended with the Part 3 sections. |
| Changelog (1/5) | Part 2 scored 5/5. This entry continues the same dated, detailed format. |

#### B. New work in Part 3

- **B1 Product data:** created `data/products.json` with ten products (name, category, price, notice needed, description).
- **B2 Dynamic content:** `js/catalogue.js` builds the product cards on Home and Products from the JSON file, loaded with `fetch()`.
- **B3 Search, filter and sort:** added a search box, category filter and sort menu with a live result count and a "no results" message.
- **B4 Interactive elements:** added tabs (About), an accordion (Contact FAQ), a product details window and a gallery with lightbox (Products), all in `js/widgets.js` and `js/catalogue.js`.
- **B5 Map:** added a Leaflet and OpenStreetMap map to Contact (`js/map.js`), loaded only when the visitor scrolls near it.
- **B6 Animations:** added transitions, window animations and scroll reveal, switched off for reduced motion (`css/style.css`, sections for Part 3).
- **B7 Enquiry form:** rebuilt with a product list that depends on the category, quantity and date; added a price and availability answer and AJAX sending (`js/forms.js`).
- **B8 Contact form:** added message type, subject and phone fields, validation, and an email preview with an "Open in my email program" button and a copy button.
- **B9 Validation:** one validator for each kind of input, checked on leaving a field and on send, with an error summary and accessible messages.
- **B10 SEO:** wrote new titles and descriptions, checked heading order, renamed images with descriptive names, added canonical, Open Graph and Twitter tags and schema.org structured data, and added share links.
- **B11 Search engine files:** created `robots.txt` and `sitemap.xml`.
- **B12 Page speed:** deferred scripts, lazy-loaded Leaflet and images, and set browser caching in `_headers`.
- **B13 Security:** added a Content Security Policy, Subresource Integrity on Leaflet, security headers, input limits and a honeypot field.
- **B14 Thank-you page:** added `thanks.html` for visitors whose browser has JavaScript switched off.
- **B15 Documentation:** updated this README (Part 3 sections, testing, changelog and references).
- **B16 Deployment:** published the site on Netlify (the live address is at the top of this README) and submitted the repository link.
- **B17 Product photographs:** added ten real product photographs. Each product in `data/products.json` now has an `image` name and an `imageAlt` description. `js/catalogue.js` builds the photo into every product card and into the details window; the gallery on the Products page now shows the ten photographs; `style.css` makes each photo fill the top of its card and stops the lightbox from stretching small photos. The photos were cropped to a square for the cards and saved in two small sizes and a larger version with descriptive file names (for example `aggreys-bakery-birthday-cake-400.webp`). The descriptions of the celebration cake, whole-wheat loaf, doughnut, muffin and sweet pastry were reworded to match what the photos show.
- **B18 Wording:** changed "Order at least 3 days ahead" to "Order at least 3 days in advance" (and the 1-day and 5-day versions) in `js/common.js`, which is used by the product cards, the details window and the home page.

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

## 14. References

**Image credits.** The hero picture, the category pictures and the shopfront are illustrations made for this project. The ten product photographs (white loaf, brown loaf, whole-wheat loaf, bread rolls, birthday cake, celebration cake, cupcakes, iced doughnuts, chocolate muffin and jam tarts) were collected from the internet for this educational student project and are not the student's own work. The photographers are not known. The whole-wheat loaf photo shows a website name in its corner and the bread rolls photo shows the logo of *Little Sunny Kitchen*. All rights stay with the original owners, and for a real business these pictures would be replaced with the bakery's own photographs.

Google (n.d.) *Build and submit a sitemap*. Available at: https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview (Accessed: 2 November 2026).

Google (n.d.) *Introduction to robots.txt*. Available at: https://developers.google.com/search/docs/crawling-indexing/robots/intro (Accessed: 2 November 2026).

Google (n.d.) *SEO starter guide*. Available at: https://developers.google.com/search/docs/fundamentals/seo-starter-guide (Accessed: 2 November 2026).

IOL Business Report (2026) *What South Africa's small businesses can expect in 2026*. Available at: https://iol.co.za/business-report/entrepreneurs/2026-01-29-what-south-africas-small-businesses-can-expect-in-2026/ (Accessed: 7 August 2026).

Leaflet (n.d.) *Leaflet quick start guide*. Available at: https://leafletjs.com/examples/quick-start/ (Accessed: 2 November 2026).

MDN Web Docs (n.d.) *Content Security Policy (CSP)*. Available at: https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP (Accessed: 2 November 2026).

MDN Web Docs (n.d.) *`<dialog>`: The Dialog element*. Available at: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dialog (Accessed: 2 November 2026).

MDN Web Docs (n.d.) *`<picture>`: The Picture element*. Available at: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture (Accessed: 24 September 2026).

MDN Web Docs (n.d.) *Using media queries*. Available at: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Media_Queries/Using_media_queries (Accessed: 24 September 2026).

MDN Web Docs (n.d.) *Using the Fetch API*. Available at: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch (Accessed: 2 November 2026).

Netlify (n.d.) *Forms setup*. Available at: https://docs.netlify.com/forms/setup/ (Accessed: 2 November 2026).

OpenStreetMap (n.d.) *Copyright and licence*. Available at: https://www.openstreetmap.org/copyright (Accessed: 2 November 2026).

PretoriaD (2024) *Bakeries in Pretoria, find list of top bakery near you*. Available at: https://pretoriad.com/bakeries-in-pretoria/ (Accessed: 7 August 2026).

schema.org (n.d.) *Bakery*. Available at: https://schema.org/Bakery (Accessed: 2 November 2026).

The Independent Institute of Education (2023) *WEDE5020 POE Test Question Paper and Assessment Guidelines*.

The Independent Institute of Education (2024) *WEDE5020 Web Development Module Manual/Guide*.

The Weblab (2025) *The importance of online presence for South African businesses 2025*. Available at: https://www.theweblab.co.za/importance-of-online-presence-for-south-african-businesses-2025 (Accessed: 7 August 2026).

World Wide Web Consortium (n.d.) *Accordion pattern*, WAI-ARIA Authoring Practices Guide. Available at: https://www.w3.org/WAI/ARIA/apg/patterns/accordion/ (Accessed: 2 November 2026).

World Wide Web Consortium (n.d.) *Tabs pattern*, WAI-ARIA Authoring Practices Guide. Available at: https://www.w3.org/WAI/ARIA/apg/patterns/tabs/ (Accessed: 2 November 2026).

World Wide Web Consortium (n.d.) *Understanding Success Criterion 1.4.3: Contrast (Minimum)*. Available at: https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html (Accessed: 24 September 2026).
