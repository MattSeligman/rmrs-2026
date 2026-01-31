# RMRS Homepage - Elementor V4 Structure Specification

## Document Purpose
Detailed technical specification for implementing the RMRS homepage in Elementor v4, defining flexbox configurations, container structures, CSS classes, states, and responsive behavior.

---

## Global Settings

### Design Tokens (CSS Variables)
```css
:root {
  /* Colors */
  --rmrs-primary: #1E4B8E;
  --rmrs-primary-dark: #0D2B5C;
  --rmrs-secondary: #4A90D9;
  --rmrs-accent: #E85A24;
  --rmrs-green: #2E7D32;
  --rmrs-beige: #F5F1EB;
  --rmrs-white: #FFFFFF;
  --rmrs-dark: #1A1A2E;
  --rmrs-gray-light: #F8F9FA;
  --rmrs-gray: #6C757D;
  --rmrs-gray-dark: #343A40;

  /* Typography */
  --rmrs-font-primary: 'Montserrat', sans-serif;
  --rmrs-font-size-h1: clamp(2rem, 5vw, 3.5rem);
  --rmrs-font-size-h2: clamp(1.5rem, 4vw, 2.5rem);
  --rmrs-font-size-h3: clamp(1.25rem, 3vw, 1.75rem);
  --rmrs-font-size-body: 1rem;
  --rmrs-font-size-small: 0.875rem;

  /* Spacing */
  --rmrs-section-padding: clamp(40px, 8vw, 100px);
  --rmrs-container-max: 1200px;
  --rmrs-gap-sm: 16px;
  --rmrs-gap-md: 24px;
  --rmrs-gap-lg: 40px;
  --rmrs-gap-xl: 60px;

  /* Transitions */
  --rmrs-transition: 0.3s ease;
  --rmrs-transition-slow: 0.5s ease;
}
```

### Breakpoints
| Name | Width | Elementor Setting |
|------|-------|-------------------|
| Desktop | > 1024px | Default |
| Tablet | 768px - 1024px | Tablet |
| Mobile | < 768px | Mobile |

---

## Section 1: Header

### Structure Overview
```
[SECTION: Header] .rmrs-header
└── [CONTAINER: Header Inner] flex-row
    ├── [CONTAINER: Logo]
    │   └── [IMAGE: Logo]
    ├── [CONTAINER: Nav] flex-row
    │   └── [NAV MENU WIDGET]
    └── [CONTAINER: Actions] flex-row
        ├── [BUTTON: Search Icon]
        └── [BUTTON: Hamburger] (mobile only)
```

### Elementor Configuration

#### Section Settings
| Property | Value | Type |
|----------|-------|------|
| Tag | `header` | Local |
| Width | Full Width | Local |
| Content Width | Boxed (1200px) | Local |
| Height | Min Height: 80px | Local |
| Position | Sticky | Local |
| Z-Index | 1000 | Local |

#### Main Container (Header Inner)
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Row | Row | Row |
| Justify | Space Between | Space Between | Space Between |
| Align | Center | Center | Center |
| Gap | 40px | 24px | 16px |
| Padding | 0 20px | 0 16px | 0 12px |

### CSS Classes

| Element | Class | Purpose | Type |
|---------|-------|---------|------|
| Section | `.rmrs-header` | Header wrapper | Custom |
| Section | `.rmrs-header--sticky` | Sticky state | Custom |
| Section | `.rmrs-header--scrolled` | After scroll | Custom (JS) |
| Logo Container | `.rmrs-header__logo` | Logo wrapper | Custom |
| Nav Container | `.rmrs-header__nav` | Navigation wrapper | Custom |
| Nav Link | `.rmrs-nav-link` | Menu items | Custom |
| Nav Link | `.rmrs-nav-link--dropdown` | Dropdown parent | Custom |
| Actions | `.rmrs-header__actions` | Right actions | Custom |
| Search | `.rmrs-header__search` | Search button | Custom |
| Hamburger | `.rmrs-header__hamburger` | Mobile menu toggle | Custom |

### States

| Element | State | CSS Changes |
|---------|-------|-------------|
| Header | `:scrolled` | `background: white; box-shadow: 0 2px 10px rgba(0,0,0,0.1);` |
| Nav Link | `:hover` | `color: var(--rmrs-primary); border-bottom: 2px solid var(--rmrs-primary);` |
| Nav Link | `:active` | `color: var(--rmrs-primary-dark);` |
| Nav Link | `.current` | `color: var(--rmrs-primary); font-weight: 600;` |
| Dropdown | `:hover` | `opacity: 1; visibility: visible; transform: translateY(0);` |
| Search Icon | `:hover` | `color: var(--rmrs-primary); transform: scale(1.1);` |
| Hamburger | `:active` | Transform to X icon |

### Mobile Menu Overlay
```
[CONTAINER: Mobile Menu] .rmrs-mobile-menu
├── [CONTAINER: Menu Header] flex-row
│   ├── [IMAGE: Logo]
│   └── [BUTTON: Close X]
├── [CONTAINER: Menu Items] flex-column
│   └── [Accordion Menu Items]
└── [CONTAINER: CTA]
    └── [BUTTON: Download A-Z Guide]
```

---

## Section 2: Hero

### Structure Overview
```
[SECTION: Hero] .rmrs-hero
└── [CONTAINER: Hero Inner] flex-row → stack on mobile
    ├── [CONTAINER: Content] 60%
    │   ├── [HEADING: H1]
    │   ├── [TEXT: Subheading]
    │   ├── [CONTAINER: Depot Status]
    │   │   └── [DEPOT STATUS WIDGET]
    │   └── [BUTTON: CTA]
    └── [CONTAINER: Image] 40%
        └── [IMAGE: Hero Image]
```

### Elementor Configuration

#### Section Settings
| Property | Value | Type |
|----------|-------|------|
| Tag | `section` | Local |
| Width | Full Width | Local |
| Content Width | Boxed (1200px) | Local |
| Min Height | 600px (Desktop), 500px (Mobile) | Local |
| Background | Linear Gradient | Local |
| Overflow | Hidden | Local |

#### Background Gradient
```css
background: linear-gradient(135deg, var(--rmrs-primary) 0%, var(--rmrs-primary-dark) 100%);
```

#### Main Container (Hero Inner)
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Row | Row | Column |
| Justify | Space Between | Space Between | Center |
| Align | Center | Center | Center |
| Gap | 60px | 40px | 32px |
| Padding | 80px 40px | 60px 24px | 40px 16px |

#### Content Container (Left)
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Width | 60% | 55% | 100% |
| Direction | Column | Column | Column |
| Align | Flex Start | Flex Start | Center |
| Gap | 24px | 20px | 16px |
| Text Align | Left | Left | Center |

#### Image Container (Right)
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Width | 40% | 45% | 100% |
| Max Width | 500px | 400px | 300px |
| Order | 2 | 2 | 1 (shows first on mobile) |

### CSS Classes

| Element | Class | Purpose | Type |
|---------|-------|---------|------|
| Section | `.rmrs-hero` | Hero section wrapper | Custom |
| Section | `.rmrs-section--primary` | Blue gradient bg | Custom |
| Container | `.rmrs-hero__inner` | Flexbox container | Custom |
| Container | `.rmrs-hero__content` | Left content area | Custom |
| Heading | `.rmrs-hero__title` | H1 styling | Custom |
| Text | `.rmrs-hero__subtitle` | Subheading | Custom |
| Widget | `.rmrs-depot-status` | Status badge | Custom |
| Button | `.rmrs-btn-cta` | Primary CTA | Custom |
| Container | `.rmrs-hero__image` | Image wrapper | Custom |

### States

| Element | State | CSS Changes |
|---------|-------|-------------|
| CTA Button | `:hover` | `background: var(--rmrs-accent); transform: translateY(-2px); box-shadow: 0 4px 12px rgba(232,90,36,0.3);` |
| CTA Button | `:active` | `transform: translateY(0);` |
| Depot Status | `.open` | `background: var(--rmrs-green); &::before { content: "●"; color: #4CAF50; }` |
| Depot Status | `.closed` | `background: var(--rmrs-gray); &::before { content: "●"; color: #F44336; }` |
| Hero Image | `:load` | Fade in animation |

### Dividers
None in this section.

---

## Section 3: Search & Quick Actions

### Structure Overview
```
[SECTION: Search Section] .rmrs-search-section
└── [CONTAINER: Search Inner] flex-column
    ├── [CONTAINER: Top Row] flex-row → wrap on mobile
    │   ├── [CONTAINER: I'm Here To]
    │   │   ├── [TEXT: Label]
    │   │   └── [CONTAINER: Buttons] flex-row
    │   │       ├── [BUTTON: Recycle]
    │   │       ├── [BUTTON: Request Pickup]
    │   │       ├── [BUTTON: Learn About Recycling]
    │   │       └── [BUTTON: Get Involved]
    │   └── [CONTAINER: Depot Status]
    │       └── [DEPOT STATUS WIDGET]
    ├── [DIVIDER: Horizontal Line]
    ├── [CONTAINER: Search Row] flex-column
    │   ├── [TEXT: "What can I Recycle?"]
    │   ├── [TEXT: Subtitle]
    │   └── [CONTAINER: Search Box] flex-row
    │       ├── [RECYCLING SEARCH WIDGET]
    │       └── [BUTTON: Search]
    ├── [DIVIDER: Horizontal Line]
    └── [CONTAINER: Help Row] flex-row → stack on mobile
        ├── [CONTAINER: A-Z Guide]
        │   └── [BUTTON: Browse Complete A-Z Guide]
        ├── [TEXT: "or"]
        └── [CONTAINER: Hotline]
            └── [TEXT + LINK: Call Recycling Hotline]
```

### Elementor Configuration

#### Section Settings
| Property | Value | Type |
|----------|-------|------|
| Tag | `section` | Local |
| Width | Full Width | Local |
| Content Width | Boxed (1200px) | Local |
| Background | White | Local |
| Padding | 60px 0 | Local |

#### Top Row Container
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Row | Row | Column |
| Justify | Space Between | Space Between | Center |
| Align | Center | Center | Stretch |
| Gap | 40px | 24px | 20px |
| Padding | 0 40px 30px | 0 24px 24px | 0 16px 20px |

#### Quick Action Buttons Container
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Row | Row | Column |
| Wrap | NoWrap | Wrap | NoWrap |
| Gap | 12px | 10px | 8px |

#### Search Row Container
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Column | Column | Column |
| Align | Center | Center | Stretch |
| Gap | 16px | 14px | 12px |
| Padding | 30px 40px | 24px 24px | 20px 16px |

#### Search Box Container
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Row | Row | Column |
| Width | 100% | 100% | 100% |
| Max Width | 700px | 600px | 100% |
| Gap | 0 | 0 | 12px |

### CSS Classes

| Element | Class | Purpose | Type |
|---------|-------|---------|------|
| Section | `.rmrs-search-section` | Section wrapper | Custom |
| Section | `.rmrs-section--white` | White bg | Custom |
| Container | `.rmrs-quick-actions` | Button group | Custom |
| Button | `.rmrs-quick-action` | Individual action btn | Custom |
| Button | `.rmrs-quick-action--active` | Selected state | Custom |
| Container | `.rmrs-search-box` | Search wrapper | Custom |
| Input | `.rmrs-search-box__input` | Search input | Custom |
| Button | `.rmrs-search-box__btn` | Search button | Custom |
| Button | `.rmrs-btn-primary` | Primary button | Custom |
| Button | `.rmrs-btn-outline` | Outline button | Custom |
| Link | `.rmrs-link` | Standard link | Custom |
| Link | `.rmrs-link--underline` | Underlined link | Custom |

### States

| Element | State | CSS Changes |
|---------|-------|-------------|
| Quick Action | `:default` | `background: transparent; border: 1px solid var(--rmrs-gray); color: var(--rmrs-gray-dark);` |
| Quick Action | `:hover` | `border-color: var(--rmrs-primary); color: var(--rmrs-primary);` |
| Quick Action | `.active` | `background: var(--rmrs-primary); color: white; border-color: var(--rmrs-primary);` |
| Search Input | `:focus` | `border-color: var(--rmrs-primary); box-shadow: 0 0 0 3px rgba(30,75,142,0.1);` |
| Search Button | `:hover` | `background: var(--rmrs-primary-dark);` |
| A-Z Link | `:hover` | `text-decoration-thickness: 2px;` |

### Dividers

| Position | Style | Type |
|----------|-------|------|
| After Top Row | 1px solid #E0E0E0 | Elementor Divider Widget |
| After Search Row | 1px solid #E0E0E0 | Elementor Divider Widget |

#### Divider Settings
```
Width: 100%
Color: #E0E0E0
Weight: 1px
Gap: 0
Margin: 0
```

---

## Section 4: Services

### Structure Overview
```
[SECTION: Services] .rmrs-services-section
└── [CONTAINER: Services Inner] flex-column
    ├── [CONTAINER: Header] flex-row
    │   ├── [HEADING: "Services"]
    │   └── [BUTTON: View All →]
    └── [CONTAINER: Cards Grid] grid 3-col → 1-col mobile
        ├── [CONTAINER: Card 1] .rmrs-card--service
        │   ├── [IMAGE: Service Image]
        │   └── [CONTAINER: Card Content]
        │       ├── [HEADING: Title]
        │       └── [TEXT: Excerpt]
        ├── [CONTAINER: Card 2]
        └── [CONTAINER: Card 3]
```

### Elementor Configuration

#### Section Settings
| Property | Value | Type |
|----------|-------|------|
| Tag | `section` | Local |
| Width | Full Width | Local |
| Content Width | Boxed (1200px) | Local |
| Background | var(--rmrs-beige) | Custom Class |
| Padding | 80px 0 | Local |

#### Header Container
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Row | Row | Column |
| Justify | Space Between | Space Between | Flex Start |
| Align | Center | Center | Flex Start |
| Gap | 20px | 16px | 12px |
| Margin Bottom | 40px | 32px | 24px |

#### Cards Grid Container
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Display | Grid | Grid | Grid |
| Columns | 3 | 2 | 1 |
| Gap | 30px | 24px | 20px |
| Padding | 0 40px | 0 24px | 0 16px |

#### Individual Card
| Property | Value | Type |
|----------|-------|------|
| Direction | Column | Local |
| Background | White | Local |
| Border Radius | 12px | Local |
| Overflow | Hidden | Local |
| Box Shadow | 0 2px 8px rgba(0,0,0,0.08) | Local |

#### Card Image Container
| Property | Value | Type |
|----------|-------|------|
| Width | 100% | Local |
| Aspect Ratio | 16/10 | Local |
| Overflow | Hidden | Local |

#### Card Content Container
| Property | Value | Type |
|----------|-------|------|
| Padding | 20px | Local |
| Direction | Column | Local |
| Gap | 8px | Local |

### CSS Classes

| Element | Class | Purpose | Type |
|---------|-------|---------|------|
| Section | `.rmrs-services-section` | Section wrapper | Custom |
| Section | `.rmrs-section--beige` | Beige bg | Custom |
| Container | `.rmrs-section__header` | Header row | Custom |
| Heading | `.rmrs-section__title` | Section title | Custom |
| Link | `.rmrs-section__link` | View all link | Custom |
| Container | `.rmrs-cards-grid` | Grid container | Custom |
| Container | `.rmrs-cards-grid--3col` | 3 column grid | Custom |
| Container | `.rmrs-card` | Card base | Custom |
| Container | `.rmrs-card--service` | Service card variant | Custom |
| Container | `.rmrs-card__image` | Image wrapper | Custom |
| Image | `.rmrs-card__img` | Actual image | Custom |
| Container | `.rmrs-card__content` | Content area | Custom |
| Heading | `.rmrs-card__title` | Card title | Custom |
| Text | `.rmrs-card__excerpt` | Card description | Custom |

### States

| Element | State | CSS Changes |
|---------|-------|-------------|
| Card | `:hover` | `box-shadow: 0 8px 24px rgba(0,0,0,0.12); transform: translateY(-4px);` |
| Card Image | `:hover` | `transform: scale(1.05);` (with transition) |
| Card Title | `:hover` | `color: var(--rmrs-primary);` |
| View All Link | `:hover` | `color: var(--rmrs-primary-dark); → arrow moves right` |

### Card Hover Animation (Elementor Motion Effects)
```
Transform: translateY(-4px)
Transition: 0.3s ease
Image Scale: 1.05
Image Transition: 0.5s ease
```

---

## Section 5: Programs

### Structure Overview
```
[SECTION: Programs] .rmrs-programs-section
└── [CONTAINER: Programs Inner] flex-column
    ├── [CONTAINER: Header] flex-row
    │   ├── [HEADING: "Programs"]
    │   └── [BUTTON: View All →]
    └── [CONTAINER: Cards Grid] grid 3-col → 1-col mobile
        ├── [CONTAINER: Card 1] .rmrs-card--program
        │   ├── [IMAGE: Program Image]
        │   └── [CONTAINER: Overlay]
        │       └── [HEADING: Title]
        ├── [CONTAINER: Card 2]
        └── [CONTAINER: Card 3]
```

### Elementor Configuration

#### Section Settings
| Property | Value | Type |
|----------|-------|------|
| Tag | `section` | Local |
| Width | Full Width | Local |
| Content Width | Boxed (1200px) | Local |
| Background | White | Local |
| Padding | 80px 0 | Local |

#### Cards Grid Container
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Display | Grid | Grid | Flex |
| Columns | 3 | 2 | - |
| Direction | - | - | Column |
| Gap | 30px | 24px | 20px |

#### Individual Program Card
| Property | Value | Type |
|----------|-------|------|
| Position | Relative | Local |
| Aspect Ratio | 4/3 | Local |
| Border Radius | 12px | Local |
| Overflow | Hidden | Local |

#### Card Overlay Container
| Property | Value | Type |
|----------|-------|------|
| Position | Absolute | Local |
| Bottom | 0 | Local |
| Left | 0 | Local |
| Right | 0 | Local |
| Padding | 20px | Local |
| Background | linear-gradient(transparent, rgba(0,0,0,0.7)) | Local |

### CSS Classes

| Element | Class | Purpose | Type |
|---------|-------|---------|------|
| Section | `.rmrs-programs-section` | Section wrapper | Custom |
| Section | `.rmrs-section--white` | White bg | Custom |
| Container | `.rmrs-card--program` | Program card variant | Custom |
| Container | `.rmrs-card__overlay` | Gradient overlay | Custom |
| Heading | `.rmrs-card__title--overlay` | White title on overlay | Custom |

### States

| Element | State | CSS Changes |
|---------|-------|-------------|
| Card | `:hover` | `transform: scale(1.02);` |
| Card Image | `:hover` | `transform: scale(1.1);` |
| Overlay | `:hover` | `background: linear-gradient(transparent 30%, rgba(0,0,0,0.8));` |
| Title | `:hover` | `transform: translateY(-4px);` |

---

## Section 6: Stats Bar

### Structure Overview
```
[SECTION: Stats] .rmrs-stats-section
└── [CONTAINER: Stats Inner] flex-row → stack on mobile
    ├── [CONTAINER: Content] 55%
    │   ├── [HEADING: "What We've Accomplished Together"]
    │   └── [CONTAINER: Stats Grid] grid 2x2
    │       ├── [CONTAINER: Stat 1]
    │       │   ├── [TEXT: Number] .rmrs-stat-value
    │       │   └── [TEXT: Label] .rmrs-stat-label
    │       ├── [CONTAINER: Stat 2]
    │       ├── [CONTAINER: Stat 3]
    │       └── [CONTAINER: Stat 4]
    └── [CONTAINER: Image] 45%
        └── [IMAGE: Stats Image]
```

### Elementor Configuration

#### Section Settings
| Property | Value | Type |
|----------|-------|------|
| Tag | `section` | Local |
| Width | Full Width | Local |
| Content Width | Boxed (1200px) | Local |
| Background | var(--rmrs-beige) | Custom Class |
| Padding | 80px 0 | Local |

#### Main Container (Stats Inner)
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Row | Row | Column |
| Justify | Space Between | Space Between | Center |
| Align | Center | Center | Center |
| Gap | 60px | 40px | 32px |

#### Content Container (Left)
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Width | 55% | 50% | 100% |
| Direction | Column | Column | Column |
| Gap | 40px | 32px | 24px |

#### Stats Grid
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Display | Grid | Grid | Grid |
| Columns | 2 | 2 | 2 |
| Rows | 2 | 2 | 2 |
| Gap | 32px 48px | 24px 32px | 20px 24px |

#### Individual Stat Container
| Property | Value | Type |
|----------|-------|------|
| Direction | Column | Local |
| Gap | 4px | Local |
| Text Align | Left | Local |

#### Image Container (Right)
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Width | 45% | 50% | 100% |
| Max Width | 500px | 400px | 350px |
| Border Radius | 12px | Local |
| Overflow | Hidden | Local |

### CSS Classes

| Element | Class | Purpose | Type |
|---------|-------|---------|------|
| Section | `.rmrs-stats-section` | Section wrapper | Custom |
| Section | `.rmrs-section--beige` | Beige bg | Custom |
| Container | `.rmrs-stats-bar` | Stats wrapper | Custom |
| Container | `.rmrs-stats-grid` | 2x2 grid | Custom |
| Container | `.rmrs-stat-item` | Individual stat | Custom |
| Text | `.rmrs-stat-value` | Number value | Custom |
| Text | `.rmrs-stat-suffix` | % or unit | Custom |
| Text | `.rmrs-stat-label` | Description | Custom |

### States & Animations

| Element | State/Animation | CSS/JS |
|---------|-----------------|--------|
| Stat Value | `:in-viewport` | Counter animation (JS) |
| Stat Value | Animation | `count-up` from 0 to target |
| Stat Item | `:in-viewport` | `opacity: 0 → 1; transform: translateY(20px) → translateY(0);` |
| Image | `:in-viewport` | Fade in with slight scale |

### Counter Animation Settings
```javascript
// Stats Bar Widget Settings
{
  duration: 2000,
  easing: 'easeOutCubic',
  separator: ',',
  decimal: '.',
  startOnViewport: true,
  viewportOffset: 0.8
}
```

### Stats Data
| Value | Suffix | Label |
|-------|--------|-------|
| 67 | % | Waste Diverted Yearly |
| 42 | | Community Partners |
| 15,200 | | Households Served |
| 89 | % | Community Engagement Rate |

---

## Section 7: News

### Structure Overview
```
[SECTION: News] .rmrs-news-section
└── [CONTAINER: News Inner] flex-column
    ├── [CONTAINER: Header] flex-row
    │   ├── [HEADING: "Read Our Latest News Updates"]
    │   └── [BUTTON: View All →]
    ├── [CONTAINER: Cards Grid] grid 2-col or 3-col → 1-col mobile
    │   ├── [CONTAINER: Card 1] .rmrs-card--news
    │   │   ├── [IMAGE: Featured Image]
    │   │   └── [CONTAINER: Content]
    │   │       ├── [TEXT: Date]
    │   │       ├── [HEADING: Title]
    │   │       ├── [TEXT: Excerpt]
    │   │       └── [BUTTON: Read Article →]
    │   └── [CONTAINER: Card 2]
    └── [CONTAINER: Footer] (mobile only)
        └── [BUTTON: View All News]
```

### Elementor Configuration

#### Section Settings
| Property | Value | Type |
|----------|-------|------|
| Tag | `section` | Local |
| Width | Full Width | Local |
| Content Width | Boxed (1200px) | Local |
| Background | White | Local |
| Padding | 80px 0 | Local |

#### Cards Grid Container
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Display | Grid | Grid | Flex |
| Columns | 2 | 2 | - |
| Direction | - | - | Column |
| Gap | 30px | 24px | 20px |

#### Individual News Card
| Property | Value | Type |
|----------|-------|------|
| Direction | Column | Local |
| Background | White | Local |
| Border | 1px solid #E0E0E0 | Local |
| Border Radius | 12px | Local |
| Overflow | Hidden | Local |

#### Card Image Container
| Property | Value | Type |
|----------|-------|------|
| Width | 100% | Local |
| Aspect Ratio | 16/9 | Local |
| Overflow | Hidden | Local |

#### Card Content Container
| Property | Value | Type |
|----------|-------|------|
| Padding | 24px | Local |
| Direction | Column | Local |
| Gap | 12px | Local |

### CSS Classes

| Element | Class | Purpose | Type |
|---------|-------|---------|------|
| Section | `.rmrs-news-section` | Section wrapper | Custom |
| Container | `.rmrs-cards-grid--2col` | 2 column grid | Custom |
| Container | `.rmrs-card--news` | News card variant | Custom |
| Text | `.rmrs-card__date` | Date meta | Custom |
| Heading | `.rmrs-card__title` | Card title | Custom |
| Text | `.rmrs-card__excerpt` | Card excerpt | Custom |
| Button | `.rmrs-btn-text` | Text button with arrow | Custom |
| Button | `.rmrs-btn-secondary` | Secondary button | Custom |

### States

| Element | State | CSS Changes |
|---------|-------|-------------|
| Card | `:hover` | `border-color: var(--rmrs-primary); box-shadow: 0 4px 16px rgba(0,0,0,0.1);` |
| Card Image | `:hover` | `transform: scale(1.05);` |
| Card Title | `:hover` | `color: var(--rmrs-primary);` |
| Read Article | `:hover` | `color: var(--rmrs-primary-dark); → arrow moves right 4px` |
| View All News | `:hover` | `background: var(--rmrs-gray-light);` |

---

## Section 8: Footer

### Structure Overview
```
[SECTION: Footer] .rmrs-footer
└── [CONTAINER: Footer Inner] flex-column
    ├── [CONTAINER: Main Footer] flex-row → stack on mobile
    │   ├── [CONTAINER: Brand Column] 25%
    │   │   ├── [IMAGE: Logo]
    │   │   ├── [TEXT: Address]
    │   │   ├── [TEXT: Phone]
    │   │   └── [TEXT: Email]
    │   ├── [CONTAINER: Nav Column 1] 15%
    │   │   ├── [HEADING: "About Us"]
    │   │   └── [NAV: Links]
    │   ├── [CONTAINER: Nav Column 2] 15%
    │   │   ├── [HEADING: "At the Depot"]
    │   │   └── [NAV: Links]
    │   ├── [CONTAINER: Nav Column 3] 15%
    │   │   ├── [HEADING: "Events"]
    │   │   └── [NAV: Links]
    │   └── [CONTAINER: Newsletter Column] 30%
    │       ├── [HEADING: "Subscribe to Our Newsletter"]
    │       ├── [FORM: Newsletter]
    │       │   ├── [INPUT: Name]
    │       │   ├── [INPUT: Email]
    │       │   └── [BUTTON: Submit]
    │       └── [CONTAINER: Social Icons]
    ├── [DIVIDER: Horizontal Line]
    └── [CONTAINER: Copyright Row] flex-row
        ├── [TEXT: Copyright]
        └── [TEXT: Privacy Policy Link]
```

### Elementor Configuration

#### Section Settings
| Property | Value | Type |
|----------|-------|------|
| Tag | `footer` | Local |
| Width | Full Width | Local |
| Content Width | Boxed (1200px) | Local |
| Background | var(--rmrs-dark) | Custom Class |
| Padding | 60px 0 20px | Local |

#### Main Footer Container
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Row | Row | Column |
| Justify | Space Between | Space Between | Flex Start |
| Align | Flex Start | Flex Start | Stretch |
| Gap | 40px | 30px | 32px |
| Wrap | NoWrap | Wrap | NoWrap |

#### Brand Column
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Width | 25% | 45% | 100% |
| Direction | Column | Column | Column |
| Gap | 16px | 14px | 12px |

#### Nav Columns
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Width | 15% | 25% | 50% |
| Direction | Column | Column | Column |
| Gap | 12px | 10px | 8px |

#### Newsletter Column
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Width | 30% | 100% | 100% |
| Direction | Column | Column | Column |
| Gap | 16px | 14px | 12px |
| Order | - | Last | Last |

#### Newsletter Form
| Property | Value | Type |
|----------|-------|------|
| Direction | Column | Local |
| Gap | 12px | Local |

#### Copyright Row
| Property | Desktop | Tablet | Mobile |
|----------|---------|--------|--------|
| Direction | Row | Row | Column |
| Justify | Space Between | Space Between | Center |
| Align | Center | Center | Center |
| Gap | 20px | 16px | 8px |
| Padding Top | 20px | 16px | 16px |

### CSS Classes

| Element | Class | Purpose | Type |
|---------|-------|---------|------|
| Section | `.rmrs-footer` | Footer wrapper | Custom |
| Section | `.rmrs-section--dark` | Dark bg | Custom |
| Container | `.rmrs-footer__inner` | Main container | Custom |
| Container | `.rmrs-footer__brand` | Brand column | Custom |
| Image | `.rmrs-footer__logo` | Footer logo | Custom |
| Text | `.rmrs-footer__contact` | Contact info | Custom |
| Container | `.rmrs-footer__nav` | Nav column | Custom |
| Heading | `.rmrs-footer__heading` | Column heading | Custom |
| Nav | `.rmrs-footer__links` | Link list | Custom |
| Link | `.rmrs-footer__link` | Individual link | Custom |
| Container | `.rmrs-newsletter` | Newsletter form | Custom |
| Input | `.rmrs-newsletter__input` | Form inputs | Custom |
| Button | `.rmrs-newsletter__btn` | Submit button | Custom |
| Container | `.rmrs-social-icons` | Social icons | Custom |
| Link | `.rmrs-social-icon` | Individual icon | Custom |
| Container | `.rmrs-footer__copyright` | Copyright row | Custom |
| Text | `.rmrs-copyright-text` | Copyright text | Custom |
| Link | `.rmrs-privacy-link` | Privacy link | Custom |

### States

| Element | State | CSS Changes |
|---------|-------|-------------|
| Footer Link | `:default` | `color: rgba(255,255,255,0.7);` |
| Footer Link | `:hover` | `color: white; padding-left: 4px;` |
| Newsletter Input | `:focus` | `border-color: var(--rmrs-secondary); background: rgba(255,255,255,0.1);` |
| Newsletter Button | `:hover` | `background: var(--rmrs-secondary);` |
| Social Icon | `:hover` | `color: var(--rmrs-secondary); transform: scale(1.1);` |
| Privacy Link | `:hover` | `text-decoration: underline;` |

### Dividers

| Position | Style | Type |
|----------|-------|------|
| Before Copyright | 1px solid rgba(255,255,255,0.1) | Elementor Divider Widget |

---

## Elementor Class Reference Summary

### Section Classes
| Class | Purpose | Sections Used |
|-------|---------|---------------|
| `.rmrs-section--primary` | Blue gradient background | Hero |
| `.rmrs-section--white` | White background | Search, Programs, News |
| `.rmrs-section--beige` | Beige background | Services, Stats |
| `.rmrs-section--dark` | Dark blue background | Footer |

### Card Classes
| Class | Purpose | Sections Used |
|-------|---------|---------------|
| `.rmrs-card` | Base card styles | All card sections |
| `.rmrs-card--service` | Service card variant | Services |
| `.rmrs-card--program` | Program card with overlay | Programs |
| `.rmrs-card--news` | News card with meta | News |
| `.rmrs-card__image` | Image container | All cards |
| `.rmrs-card__content` | Content container | Services, News |
| `.rmrs-card__overlay` | Gradient overlay | Programs |
| `.rmrs-card__title` | Card title | All cards |
| `.rmrs-card__excerpt` | Card description | Services, News |
| `.rmrs-card__date` | Date meta | News |

### Button Classes
| Class | Purpose | Sections Used |
|-------|---------|---------------|
| `.rmrs-btn-primary` | Primary filled button | Search |
| `.rmrs-btn-secondary` | Secondary button | News |
| `.rmrs-btn-outline` | Outline button | Search |
| `.rmrs-btn-cta` | Call-to-action button | Hero |
| `.rmrs-btn-text` | Text button with arrow | News cards |

### Utility Classes
| Class | Purpose |
|-------|---------|
| `.rmrs-text-center` | Center text |
| `.rmrs-text-white` | White text color |
| `.rmrs-mb-sm` | Margin bottom small |
| `.rmrs-mb-md` | Margin bottom medium |
| `.rmrs-mb-lg` | Margin bottom large |
| `.rmrs-hide-mobile` | Hide on mobile |
| `.rmrs-show-mobile` | Show only on mobile |

---

## Local vs Custom Class Decision Guide

### Use Custom CSS Class When:
- Style is reused across multiple elements
- Style defines a component (cards, buttons, sections)
- Style needs to be consistent site-wide
- Style involves complex hover/state changes
- Style uses CSS variables

### Use Elementor Local Styling When:
- One-off spacing adjustments
- Element-specific sizing
- Unique positioning for single element
- Quick responsive overrides
- Elementor motion effects

---

## Implementation Checklist

- [ ] Import CSS variables to theme
- [ ] Create Header template (Theme Builder)
- [ ] Create Footer template (Theme Builder)
- [ ] Build Hero section
- [ ] Build Search & Quick Actions section
- [ ] Build Services section with Loop Grid
- [ ] Build Programs section with Loop Grid
- [ ] Implement Stats Bar widget
- [ ] Build News section with Posts widget
- [ ] Test all hover states
- [ ] Test responsive breakpoints
- [ ] Verify counter animations
- [ ] Test mobile menu
- [ ] Validate all links
