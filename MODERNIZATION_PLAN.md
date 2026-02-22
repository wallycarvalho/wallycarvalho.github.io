# MODERNIZATION PLAN: Hackers Y2K Retro-Modern Landing Page

## Design Direction & Visual Philosophy

### Core Aesthetic
- **Inspiration:** Hackers (1995) film aesthetic + minimalist modern design
- **Visual Foundation:** Light, clean backgrounds (whites, light grays) with strategic neon accents
- **Feel:** High-tech minimalism, slightly retro but contemporary
- **Key Attributes:**
  - Geometric precision (grid-based, clean lines)
  - High contrast (dark text on light, neon highlights)
  - Subtle tech undertones (no heavy sci-fi clichés)
  - Photography-forward (custom images as background elements)
  - Scannable content hierarchy (users can quickly find info)

---

## 1. COLOR PALETTE SPECIFICATION

### Primary Palette
```
Background:           #FFFFFF (Pure white, or #F8F8F8 for subtle warmth)
Primary Text:         #000000 or #1A1A1A (Near black)
Secondary Text:       #4A4A4A (Medium gray)
Dividers/Borders:     #E0E0E0 (Light gray)
```

### Neon Accent Colors (Hackers Inspired)
```
Neon Green:          #00FF41 (Matrix-style green)
Neon Magenta:        #FF006E (Hot pink/magenta)
Neon Cyan:           #00D9FF (Electric blue)
Neon Yellow:         #FFFF00 (Bright yellow - use sparingly)
Neon Purple:         #B700FF (Electric purple)
```

### Neutral/Dark Accents
```
Dark Accent:         #1A1A2E (Dark navy, for depth)
Muted Blue:          #0F3460 (Subtle tech color)
```

### Usage Guidelines
- **Neon colors:** Reserved for:
  - Links & hover states
  - Key CTAs (buttons)
  - Section accents/borders
  - Icon highlights
  - Highlight text (sparingly)
- **Avoid:** Neon as primary text color (reduces readability)
- **Contrast ratio:** All neon accents must meet WCAG AA standards when used with backgrounds

### Dark Mode Consideration (Future)
- Invert: Light backgrounds → #1A1A2E, Dark text → #FFFFFF
- Neon colors remain the same (they'll pop on dark)
- Secondary text: #B0B0B0

---

## 2. TYPOGRAPHY SYSTEM

### Font Pairing
```
Headings (H1-H6):      'Poppins' or 'Inter' (modern geometric sans-serif)
                       Weights: 700 (bold), 600 (semi-bold)
                       Style: Clean, minimal, geometric feel
                       
Body Text:             'Inter' or 'Roboto' (current, works well)
                       Weights: 400 (regular), 500 (medium)
                       Line-height: 1.6+ (for readability)
                       
Code/Technical:        'JetBrains Mono' or 'Courier Prime' (optional, if needed)
                       Only for inline code or technical snippets
```

### Sizing Hierarchy (Refined)
```
H1 (Hero/Page Title):  3.5rem - 4.5rem (responsive)
H2 (Section Title):    2.25rem - 2.75rem
H3 (Subsection):       1.75rem - 2rem
H4:                    1.5rem
Body (p):              1rem (16px base)
Small/Caption:         0.875rem - 0.9375rem
Code/Monospace:        0.875rem
```

### Typography Improvements
- **Tighter letter-spacing** on headings (0.5px to -1px) for modern look
- **Increased line-height** on body (1.7–1.8) for better readability
- **Font weight variation:** Use 600/700 for hierarchy instead of just color
- **Monospace restraint:** Only use for actual code, not text
- **Anti-aliasing:** `-webkit-font-smoothing: antialiased` for cleaner rendering

---

## 3. LAYOUT & GRID APPROACH

### Grid Foundation
- **Base Grid Unit:** 8px / 4px (consistent spacing system)
- **Layout Mode:** CSS Grid (primary) + Flexbox (components)
- **Subtle Grid Overlay:** Optional thin grid lines at `#F0F0F0` for underlying structure (can be toggled on/off with CSS variable)

### Spacing System
```
Nano:     0.5rem (8px)
Micro:    1rem (16px)
Small:    1.5rem (24px)
Medium:   2rem (32px)
Large:    3rem (48px)
XL:       4rem (64px)
2XL:      5rem (80px)
```

### Container & Max-Width
- **Content max-width:** Keep 930px (current) or increase to 1000px
- **Full-bleed sections:** Allow background imagery to extend edge-to-edge
- **Padding on sides:** 1.5rem (mobile), 2rem (tablet), 3rem (desktop)

### Layout Variations for Landing Page
1. **Hero Section:** Full-width, asymmetric layout (text left, profile photo right)
2. **Content Sections:** 2-column grid with alternating layouts (text left/right)
3. **Project/News Cards:** 3-column grid (desktop), responsive down
4. **Full-bleed backgrounds:** Photography sections with overlay text

---

## 4. COMPONENT MODERNIZATION SPECS

### 4.1 Hero Section
**Current State:** Name + subtitle + profile photo (right-aligned)

**Modernized Approach:**
- **Layout:** Asymmetric split (left: text, right: photo/visual)
- **Text content:**
  - Name as large H1 (Poppins, 4rem+)
  - Role/subtitle as H2 or large paragraph
  - Brief 2-3 line bio in secondary text
  - Optional: Subtle CTA button ("View Work" or "Get in Touch")
- **Visual element:**
  - Profile photo with subtle geometric border (thin neon accent line)
  - Alternative: Hero image with gradient overlay
  - Aspect ratio: 1:1 or 4:5 (portrait-friendly)
- **Spacing:** 
  - Text section: 2-3rem from left edge
  - Photo section: 2-3rem from right edge
  - Vertical alignment: Center or slight top-bias
  - Gap between text/photo: 3-4rem

**Design Details:**
- Thin neon border accent (1-2px) on profile photo or text container
- Subtle drop shadow on photo: `0 4px 12px rgba(0,0,0,0.1)`
- Background: Pure white or very subtle texture
- No aggressive animations; simple fade-in on page load

### 4.2 Navigation Bar
**Keep mostly as-is**, but modernize:
- **Font:** Update to Poppins for consistency
- **Color:** Black text on white (or add subtle neon underline on active/hover)
- **Accent:** Single neon line under active nav item
- **Dark mode toggle:** Subtle icon, neon highlight on hover
- **Spacing:** Increase padding slightly (0.75rem vertical)
- **Logo/Branding:** Use your name or custom mark (geometric if possible)

### 4.3 Profile/Bio Section
**Current:** Floated image + text

**Modernized:**
- **Layout:** Flex or grid for better control
- **Typography:** H2 for name, cleaner hierarchy
- **Content info:** Use monospace sparingly (only email, not contact block)
- **Visual:** 
  - Image border: Thin neon line (1-2px) - maybe cyan or magenta
  - Box padding: Increase to 1.5rem
  - Background: Subtle light gray (#F8F8F8) or white with border

### 4.4 Content Cards (News, Posts, Projects)
**Current:** Tables or simple lists

**Modernized Options:**
1. **Grid Card Layout:**
   - Title, date/meta, excerpt in clean card
   - Neon accent border on left or top
   - Hover: Subtle lift effect (2-3px), slight shadow increase
   - Background: White card with 1px border (#E0E0E0)

2. **Timeline Option:**
   - For news: Vertical timeline with dots
   - Neon-colored dots/connectors
   - Text right-aligned or alternating left/right

3. **List with Accent:**
   - Keep table-like structure
   - Add thin neon left border to highlight rows
   - Hover: Subtle background highlight (#F8F8F8)

### 4.5 Section Dividers & Accents
**Add visual interest:**
- Thin horizontal lines (1px, #E0E0E0) between sections
- Optional: Short neon accent lines (2-4rem wide) as section headers
- Negative space: Increase spacing between major sections (4-6rem)

### 4.6 Buttons & Interactive Elements
**Design:**
- **Style:** Minimal rectangular or slightly rounded (4px border-radius)
- **Background:** Transparent with neon border OR solid neon with white text
- **Padding:** 0.75rem 1.5rem (generous)
- **Hover:** 
  - Neon glow effect (subtle box-shadow with neon color)
  - Text color change (if not filled)
  - No aggressive movement
- **Font:** Poppins, 500 weight

**States:**
```css
Button Normal:  border: 2px solid #00FF41; color: #000; background: transparent;
Button Hover:   border: 2px solid #00FF41; color: #00FF41; box-shadow: 0 0 8px rgba(0, 255, 65, 0.3);
Button Active:  background: #00FF41; color: #000;
```

### 4.7 Images & Photography
**Integration:**
- Full-bleed image sections with text overlay
- Subtle gradient overlay (dark-to-transparent) for readability
- Image corners: No border-radius (stay sharp/geometric)
- Lazy loading: Keep enabled for performance
- WebP conversion: Maintain current setup

---

## 5. MICRO-INTERACTIONS & ANIMATIONS

### Guiding Principle
**Subtle, purposeful, and performance-optimized. No aggressive animations.**

### Recommended Interactions

1. **Link Hover:**
```css
a { color: #000; transition: color 0.2s ease; }
a:hover { color: #00FF41; }
```

2. **Button Hover:**
```css
button {
  border: 2px solid #00FF41;
  box-shadow: 0 0 0 transparent;
  transition: box-shadow 0.2s ease, color 0.2s ease;
}
button:hover {
  box-shadow: 0 0 8px rgba(0, 255, 65, 0.3);
}
```

3. **Card Hover:**
```css
.card {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
}
```

4. **Fade-In on Scroll:**
   - Subtle fade-in (opacity: 0 → 1) as elements enter viewport
   - Duration: 0.6–0.8s
   - Use `Intersection Observer API` (performant)
   - No parallax or aggressive transforms

5. **Section Accent Animations:**
   - Thin neon line "draws" from left to right on section header
   - Duration: 0.8s on page load
   - Creates sense of polish without being distracting

6. **Underline Animations:**
   - Nav links: Underline animates from left-to-right on hover
   - Duration: 0.3s

### CSS Transitions to Use
- `transition: all 0.2s ease;` for most hover effects
- `transition: opacity 0.6s ease;` for fade-ins
- Avoid `transition: all` with long durations (use specific properties)

### Motion Preferences
- Respect `prefers-reduced-motion: reduce` media query
- For users with motion sensitivity: Remove/simplify all animations

---

## 6. TECH STACK DECISIONS

### Keep (No Changes)
- **Jekyll** as static site generator
- **Bootstrap 5** for grid/utility classes
- **SCSS** for styling
- **Liquid** for templating
- **MDB** for component enhancements (optional, can reduce)

### Potential Enhancements (Optional)
1. **Add new CSS utility library:** Consider `Tailwind CSS` if you want more control, but **recommend sticking with Bootstrap** to minimize changes
2. **Animation library:** Use vanilla CSS + `Intersection Observer` (no new dependencies)
3. **Font loading:** Use Google Fonts (current approach is fine) but optimize with `font-display: swap`

### New CSS Features to Leverage
- **CSS Grid:** For layout (already used somewhat, increase usage)
- **CSS Custom Properties:** Expand for neon color themes (already in place)
- **CSS Variables for spacing:** Create `--spacing-sm`, `--spacing-md`, etc.

### No New Dependencies Needed
- Pure CSS animations
- Vanilla JS for interactions (Intersection Observer, etc.)
- Keep current build pipeline as-is

---

## 7. PHASED IMPLEMENTATION ROADMAP

### **Phase 1: Foundation (Days 1-2)**
**Goal:** Set up color palette and typography system

Tasks:
1. Create new SCSS file: `_sass/_modernized-variables.scss`
   - Define neon color variables
   - Define new spacing system (8px base grid)
   - Define typography sizes and weights

2. Update `_sass/_themes.scss`
   - Add neon colors to light/dark mode CSS variables
   - Keep existing variables, add new `--color-neon-*` variables

3. Test typography
   - Import `Poppins` font (if not already available)
   - Update `_sass/_base.scss` for new font sizes and line-heights
   - Verify readability and hierarchy

**Deliverable:** New color palette + typography active on all pages (foundation ready)

---

### **Phase 2: Hero Section Redesign (Days 2-3)**
**Goal:** Modernize landing page hero

Tasks:
1. Update `_layouts/about.liquid`
   - Redesign hero section structure (asymmetric layout)
   - Add neon accent border to profile image
   - Refine text spacing and hierarchy

2. Create new SCSS partial: `_sass/_hero.scss`
   - Style hero section with new layout
   - Add subtle drop shadow and border effects
   - Responsive design (stack on mobile)

3. Optional: Add hero background
   - Full-bleed background image (placeholder for your photos)
   - Gradient overlay for text readability

**Deliverable:** Modern hero section with Hackers aesthetic

---

### **Phase 3: Component Modernization (Days 3-4)**
**Goal:** Update cards, buttons, and content sections

Tasks:
1. Update card components (`_includes/projects.liquid`, etc.)
   - Add neon accent borders
   - Improve hover states
   - Refine spacing

2. Create button styles: `_sass/_buttons.scss`
   - Design minimal neon-bordered buttons
   - Hover/active states
   - Optional: secondary button variants

3. Update content sections (news, posts, projects)
   - Card grid layout
   - Neon accent lines
   - Responsive design

4. Add section dividers and accents
   - Thin separator lines
   - Optional neon header accents

**Deliverable:** Cohesive component library with modern, retro aesthetic

---

### **Phase 4: Micro-Interactions (Days 4-5)**
**Goal:** Add subtle animations and interactions

Tasks:
1. Implement fade-in animations
   - `Intersection Observer` setup
   - Fade-in SCSS transitions
   - Apply to cards, sections

2. Add hover effects
   - Link hover colors (neon)
   - Button hover glows
   - Card lift on hover
   - Nav underlines

3. Add scroll animations (optional)
   - Section accent line "draw" effect
   - Subtle parallax for images (minimal, respect prefers-reduced-motion)

4. Test performance
   - Ensure animations are smooth (60fps)
   - Check accessibility (motion preferences)

**Deliverable:** Smooth, polished interactions across landing page

---

### **Phase 5: Navigation & Header Modernization (Days 5-6)**
**Goal:** Refresh nav bar with Hackers aesthetic

Tasks:
1. Update `_includes/header.liquid`
   - Use Poppins font
   - Add neon accent underline for active nav items
   - Refine spacing and contrast

2. Enhance dark mode toggle
   - Neon highlight on hover
   - Better icon design

3. Test responsive nav
   - Mobile menu still functional
   - Proper spacing at all breakpoints

**Deliverable:** Modern, consistent navigation

---

### **Phase 6: Cross-Page Consistency (Days 6-7)**
**Goal:** Apply modernizations to other pages (blog, projects, CV)

Tasks:
1. Apply hero/section styles to other layouts
   - Blog posts
   - Project pages
   - CV page

2. Ensure consistency
   - Same typography system
   - Same color palette
   - Same spacing rules

3. Test all pages
   - Responsive design
   - Color contrast
   - Animations

**Deliverable:** Cohesive design across entire site

---

### **Phase 7: Photography Integration (Days 7-8)**
**Goal:** Integrate your custom images

Tasks:
1. Prepare image placeholders
   - Set up full-bleed sections ready for your photos
   - Define image aspect ratios and sizing

2. Once you provide images:
   - Optimize for web (WebP conversion, responsive sizes)
   - Add gradient overlays if needed
   - Test on various devices

3. Refine based on actual photos
   - Adjust colors/accents to complement imagery
   - Update section backgrounds if needed

**Deliverable:** Photography-forward landing page with custom images

---

### **Phase 8: Testing & Refinement (Days 8-9)**
**Goal:** QA and final polish

Tasks:
1. Cross-browser testing
   - Chrome, Safari, Firefox (desktop and mobile)
   - Verify neon colors render correctly

2. Performance audit
   - Lighthouse score check
   - Animation performance (no jank)
   - Image optimization

3. Accessibility check
   - Color contrast ratios (WCAG AA minimum)
   - Motion preferences respected
   - Keyboard navigation works

4. User testing
   - Ask for feedback on hero, colors, animations
   - Iterate based on feedback

5. Final refinements
   - Tweak spacing, colors, animations based on testing
   - Prepare for launch

**Deliverable:** Production-ready modernized landing page

---

## 8. FILE STRUCTURE & MODIFICATIONS OVERVIEW

### New Files to Create
```
_sass/
├── _modernized-variables.scss    (Colors, spacing, typography vars)
├── _hero.scss                    (Hero section styles)
├── _buttons.scss                 (Button component styles)
└── _interactions.scss            (Animations and transitions)

assets/js/
├── intersection-observer.js       (Fade-in animations on scroll)
└── animations.js                 (Additional interaction JS, if needed)
```

### Files to Modify
```
_sass/
├── _variables.scss               (Add neon color definitions)
├── _themes.scss                  (Add CSS variables for neon)
└── _base.scss                    (Update typography sizes, line-heights)

_includes/
├── header.liquid                 (Nav styling updates)
└── projects.liquid, news.liquid  (Card component updates)

_layouts/
└── about.liquid                  (Hero section redesign)

assets/css/
└── main.scss                     (Import new SASS files)
```

### Configuration (No Changes Needed)
```
_config.yml                       (Keep as-is, unless you want to adjust colors)
```

---

## 9. COLOR PALETTE REFERENCE CARD

```css
/* Light Mode (Default) */
--bg-primary:     #FFFFFF;
--bg-secondary:   #F8F8F8;
--text-primary:   #000000;
--text-secondary: #4A4A4A;
--border-light:   #E0E0E0;
--accent-dark:    #1A1A2E;

/* Neon Accents */
--neon-green:     #00FF41;  /* Primary accent */
--neon-magenta:   #FF006E;  /* Secondary accent */
--neon-cyan:      #00D9FF;  /* Tertiary accent */
--neon-yellow:    #FFFF00;  /* Highlight (use sparingly) */
--neon-purple:    #B700FF;  /* Alternative accent */

/* Dark Mode (Future) */
--bg-primary-dark:     #1A1A2E;
--bg-secondary-dark:   #0F3460;
--text-primary-dark:   #FFFFFF;
--text-secondary-dark: #B0B0B0;
```

---

## 10. NEXT STEPS & DECISION POINTS

### Before Implementation, Confirm:

1. **Neon Color Choice:** Should primary accent be neon green (#00FF41) or magenta (#FF006E)?
   - Recommendation: Start with green (Hackers iconic)
   
2. **Hero Layout:** Confirm asymmetric layout (text left, photo right)?
   - Alternative: Split screen 50/50 or text-first?

3. **Font Choice:** Is Poppins the right choice for headings?
   - Alternatives: Inter, Space Mono, DM Sans?

4. **Grid Overlay:** Include subtle grid background pattern?
   - Yes/No/Experiment first?

5. **Neon Usage Intensity:** How prominent should neon be?
   - Subtle (only links/accents) vs. More prominent (section headers)?

6. **Photography Placeholder:** Ready to provide images, or should I design with generic placeholders first?

---

## SUMMARY TABLE

| Aspect | Current | Modernized | Priority |
|--------|---------|-----------|----------|
| **Colors** | Purple/Cyan | Neon accents on white | High |
| **Typography** | Roboto | Poppins + Roboto | High |
| **Hero** | Name + photo | Asymmetric layout | High |
| **Cards** | Tables | Grid + neon borders | Medium |
| **Animations** | Minimal | Subtle fade-in + hover | Medium |
| **Nav** | Functional | Modern with neon accents | Low |
| **Images** | Current approach | Full-bleed sections | Medium |
| **Tech Stack** | Jekyll + Bootstrap | Same + new SCSS | Low |

---

## STATUS

**Current Phase:** Planning Complete ✅  
**Ready for Implementation:** Pending confirmation of 6 decision points above  
**Start Date:** Ready to begin Phase 1 upon confirmation
