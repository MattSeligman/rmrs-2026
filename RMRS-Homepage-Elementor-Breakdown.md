# RMRS Homepage - Elementor Section Breakdown

## Objective
Break down the homepage design into discrete Elementor sections, identifying what can use existing widgets/CSS vs. what needs custom elements.

## Reference
- **Design**: `doc-images/homepage-design-1.jpg`
- **Mobile Wireframe**: `doc-images/mobile-wireframe-1.jpg`

---

## Homepage Sections (Top to Bottom)

### Section 1: Header
**Type:** Elementor Theme Builder → Header Template

| Element | Implementation | Existing? |
|---------|---------------|-----------|
| Logo | Image widget | ✅ Native |
| Navigation | Nav Menu widget | ✅ Native |
| Search Icon | Button/Icon widget | ✅ Native |

**CSS Classes:** `.rmrs-nav-link`, `.rmrs-nav-link--dropdown`
**Notes:** Use sticky header. Mobile: hamburger menu with full-screen overlay.

---

### Section 2: Hero
**Type:** Elementor Section with Flexbox Container

| Element | Implementation | Existing? |
|---------|---------------|-----------|
| Blue gradient background | Section background | ✅ Native |
| Headline "Recycling Starts With Knowing What Goes Where" | Heading widget | ✅ Native |
| Subtext | Text Editor widget | ✅ Native |
| CTA Button "Learn More" | Button widget | ✅ Native |
| Hero Image (person with recyclables) | Image widget | ✅ Native |

**CSS Classes:** `.rmrs-section--primary`, `.rmrs-btn-cta`
**Layout:** 2 columns (60/40 split), responsive to stacked on mobile
**Background:** Linear gradient using brand blues

---

### Section 3: Search & Quick Actions
**Type:** Elementor Section (White background)

| Element | Implementation | Existing? |
|---------|---------------|-----------|
| "I'm Here To" dropdown | Custom select or Nav | ⚠️ Needs styling |
| "What can I Recycle?" search | **Recycling Search Widget** | ✅ EXISTS |
| Depot Status badge | **Depot Status Widget** | ✅ EXISTS |
| Quick action links | Inner Section with buttons | ✅ Native |

**CSS Classes:** `.rmrs-search-box`, `.rmrs-depot-status`, `.rmrs-quick-actions`
**Notes:** This is a key conversion section. The Recycling Search widget already handles the search functionality.

---

### Section 4: Services
**Type:** Elementor Section (Beige background)

| Element | Implementation | Existing? |
|---------|---------------|-----------|
| Section title "Services" | Heading widget | ✅ Native |
| 3 Service cards | Posts widget OR Loop Grid | ✅ Native |
| Card images | From `rmrs_service` CPT | ✅ Data exists |
| Card titles & links | Advanced Link widget | ✅ EXISTS |

**CSS Classes:** `.rmrs-section--beige`, `.rmrs-card--service`, `.rmrs-card__image`, `.rmrs-card__title`
**Layout:** 3-column grid, responsive to 1 column on mobile
**Data Source:** `rmrs_service` custom post type

---

### Section 5: Programs
**Type:** Elementor Section (White background)

| Element | Implementation | Existing? |
|---------|---------------|-----------|
| Section title "Programs" | Heading widget | ✅ Native |
| 3 Program cards | Posts widget OR Loop Grid | ✅ Native |
| Card images | From `rmrs_program` CPT | ✅ Data exists |
| Card overlays with titles | CSS overlay styling | ✅ CSS exists |

**CSS Classes:** `.rmrs-section--white`, `.rmrs-card--program`, `.rmrs-card__overlay`
**Layout:** 3-column grid
**Data Source:** `rmrs_program` custom post type

---

### Section 6: Stats Bar
**Type:** Elementor Section (Beige background with image)

| Element | Implementation | Existing? |
|---------|---------------|-----------|
| Title "What We've Accomplished Together" | Heading widget | ✅ Native |
| 4 Statistics with animation | **Stats Bar Widget** | ✅ EXISTS |
| Side image | Image widget | ✅ Native |

**CSS Classes:** `.rmrs-stats-bar`, `.rmrs-stat-item`, `.rmrs-stat-value`, `.rmrs-stat-label`
**Stats:**
- 67% Waste Diverted Yearly
- 42 Community Partners
- 15,200 Households Served
- 89% Community Engagement Rate

**Layout:** 2 columns (stats left, image right), stacked on mobile

---

### Section 7: News
**Type:** Elementor Section (White background)

| Element | Implementation | Existing? |
|---------|---------------|-----------|
| Title "Read Our Latest News Updates" | Heading widget | ✅ Native |
| "View All" link | Advanced Link widget | ✅ EXISTS |
| News cards (2-3) | Posts widget | ✅ Native |
| Card with image, date, title, excerpt | Loop Grid template | ✅ Native (V4) |

**CSS Classes:** `.rmrs-card--news`, `.rmrs-card__meta`, `.rmrs-btn-secondary`
**Layout:** 2-3 column grid
**Data Source:** WordPress Posts (News category)

---

### Section 8: Footer
**Type:** Elementor Theme Builder → Footer Template

| Element | Implementation | Existing? |
|---------|---------------|-----------|
| Dark blue background | Section background | ✅ Native |
| Logo | Image widget | ✅ Native |
| Address & contact info | Text/Icon List | ✅ Native |
| Navigation links | Nav Menu widget | ✅ Native |
| Newsletter signup | Form widget | ✅ Native (Pro) |
| Social icons | Social Icons widget | ✅ Native |
| Copyright text | Text widget | ✅ Native |

**CSS Classes:** `.rmrs-newsletter`, `.rmrs-newsletter__input`
**Layout:** 3-4 column grid, stacked on mobile

---

## Summary: What Exists vs. What's Needed

### ✅ Existing Custom Widgets (Ready to Use)
1. **Recycling Search** - For "What can I Recycle?" search box
2. **Depot Status** - For real-time open/closed indicator
3. **Stats Bar** - For animated statistics section
4. **Advanced Link** - For enhanced CTAs and links
5. **Recycling Guide** - For material search with categories
6. **RCBC Recyclepedia** - For external search fallback

### ✅ Existing CSS Classes (Ready to Use)
- Section backgrounds: `.rmrs-section--beige`, `.rmrs-section--white`, `.rmrs-section--primary`
- Cards: `.rmrs-card`, `.rmrs-card--service`, `.rmrs-card--program`, `.rmrs-card--news`
- Buttons: `.rmrs-btn-primary`, `.rmrs-btn-secondary`, `.rmrs-btn-cta`
- Stats: `.rmrs-stats-bar`, `.rmrs-stat-item`, `.rmrs-stat-value`
- Quick actions: `.rmrs-quick-actions`, `.rmrs-quick-action`

### ⚠️ Needs Configuration/Styling
1. **"I'm Here To" dropdown** - Style native select or create nav-based switcher
2. **Card hover effects** - May need Elementor motion effects or custom CSS
3. **Hero gradient** - Configure in section background settings

### 🆕 Consider Creating (Optional)
1. **Quick Actions Widget** - Could bundle the 4 action buttons as a reusable widget
2. **News Card Template** - Loop Grid skin for consistent news card styling

---

## Elementor Implementation Approach

### Option A: Page Templates (Recommended for V4)
Build each section as part of the homepage template using:
- **Flexbox Containers** (V4 native) for responsive layouts
- **Loop Grid** for dynamic content (Services, Programs, News)
- **Custom widgets** where they exist (Stats, Search, Depot Status)

### Option B: Saved Section Templates
Create reusable section templates that can be imported:
- `rmrs-hero-section`
- `rmrs-search-section`
- `rmrs-services-grid`
- `rmrs-programs-grid`
- `rmrs-stats-section`
- `rmrs-news-section`

### Option C: Theme Builder Templates
Use Elementor Pro Theme Builder for:
- Header template (sticky, with mobile menu)
- Footer template
- Single Post template (for news)
- Archive template (for services/programs)

---

## Implementation Order

1. **Header & Footer** (Theme Builder templates)
2. **Hero Section** (native Elementor)
3. **Search & Quick Actions** (uses existing widgets)
4. **Stats Section** (uses Stats Bar widget)
5. **Services Section** (Loop Grid + rmrs_service CPT)
6. **Programs Section** (Loop Grid + rmrs_program CPT)
7. **News Section** (Posts widget or Loop Grid)

---

## Key Files Reference

```
wp/rmrs/includes/elementor/widgets/
├── stats-bar.php          # Animated statistics
├── depot-status.php       # Open/closed indicator
├── recycling-search.php   # Material search box
├── recycling-guide.php    # Full material browser
├── rcbc-recyclepedia.php  # External API search
└── advanced-link.php      # Enhanced link widget

wp/rmrs/assets/css/
├── rmrs-variables.css     # Design tokens
├── rmrs-utilities.css     # Buttons, forms, nav
├── rmrs-components.css    # Cards, stats, modals
└── rmrs-elementor.css     # Elementor overrides
```

---

## Verification

1. Preview homepage at multiple breakpoints (desktop, tablet, mobile)
2. Test all custom widgets render correctly
3. Verify card hover effects work
4. Test Stats Bar counter animation on scroll
5. Verify Depot Status shows correct open/closed state
6. Test Recycling Search returns results
7. Check all links navigate correctly
8. Validate responsive behavior matches mobile wireframe
