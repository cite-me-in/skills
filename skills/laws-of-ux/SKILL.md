---
name: Laws of UX
description: "Apply evidence-based UX psychology laws when building web applications and interfaces. Use this skill whenever designing or reviewing UI/UX for web apps, dashboards, landing pages, forms, navigation systems, or any user-facing interface. Also triggers on: 'UX review', 'usability', 'user experience design', 'make this more usable', 'improve UX', 'UX patterns', 'interface design', 'is this good UX', 'accessibility and usability', or any mention of specific UX laws (Fitts's Law, Hick's Law, Jakob's Law, etc.)."
---

# Laws of UX — Web App Design Skill

> **Source:** [lawsofux.com](https://lawsofux.com) by Jon Yablonski · 30 evidence-based psychology laws for UX design

---

## How This Skill Works

When activated, follow this workflow — **don't dump all 30 laws**:

### Step 1: Understand Context

Ask (or infer): What is being built or reviewed?

| If they're building... | Start here |
|---|---|
| A **form** (signup, checkout, settings) | Section: Forms & Input |
| A **dashboard** or data-heavy page | Section: Dashboards & Data |
| A **landing page** or marketing page | Section: Landing Pages & Conversion |
| A **mobile** or touch-first app | Section: Mobile & Touch |
| A **navigation** system / information architecture | Section: Navigation & IA |
| Doing a **general UX review** | Run the Prioritized Checklist below |

### Step 2: Select 3–7 Relevant Laws

Use the context table above + the Quick Reference to pick laws that apply. **Ignore the rest.** Loading all 30 laws into every response wastes tokens and overwhelms the user.

### Step 3: Give Specific Feedback

For each selected law:
- Quote the **one-line principle**
- Point to **their actual code/UI** (if available)
- Show a **concrete fix** (code diff, CSS change, layout suggestion)
- Flag **severity**: 🔴 Critical / 🟡 Important / 🔵 Nice-to-have

### Step 4: Call Out Conflicts

If two laws tension against each other (e.g., "make everything big" vs "make one thing stand out"), consult the **[When Laws Conflict](#when-laws-conflict)** section.

### Step 5: Offer Stakeholder Scripts (optional)

If the user needs to defend a decision to a team/PM/client, pull from the **[Stakeholder Communication](#stakeholder-communication)** section.

---

## Context Routing: What You're Building → Which Laws Matter

### Forms & Input (signup, checkout, settings, search)

**Priority order:**

| Priority | Law | Why |
|---|---|---|
| 🔴 Critical | Postel's Law | Accept varied input, normalize internally |
| 🔴 Critical | Hick's Law | Break long forms into steps; limit choices per screen |
| 🔴 Critical | Doherty Threshold | Inline validation < 400ms; optimistic updates |
| 🟡 Important | Miller's Law | ~7 fields per step max |
| 🟡 Important | Tesler's Law | Smart defaults absorb complexity |
| 🟡 Important | Fitts's Law | Touch targets ≥ 44px; adequate spacing |
| 🔵 Nice-to-have | Von Restorff Effect | Primary CTA stands out from secondary actions |
| 🔵 Nice-to-have | Peak-End Rule | Success state is delightful, not abrupt |

**Common form anti-pattern:** A wall of 15+ fields, strict input formatting, no inline validation, identical-looking Submit/Cancel buttons.

---

### Dashboards & Data-Dense Pages

**Priority order:**

| Priority | Law | Why |
|---|---|---|
| 🔴 Critical | Cognitive Load | One concept per screen; remove decorative noise |
| 🔴 Critical | Chunking | Group metrics into cards/sections; use headings |
| 🔴 Critical | Law of Proximity | Related items close together; groups loosely spaced |
| 🟡 Important | Law of Similarity | Same kind of metric = same visual treatment |
| 🟡 Important | Law of Common Region | Cards/panels create clear boundaries |
| 🟡 Important | Miller's Law | ~7 chunks visible at once; paginate/filter rest |
| 🟡 Important | Selective Attention | Users ignore off-goal info; put key metrics in their scan path |
| 🔵 Nice-to-have | Goal-Gradient Effect | Progress bars toward goals/completions |
| 🔵 Nice-to-have | Serial Position Effect | Most important metric first (or last) |

**Common dashboard anti-pattern:** 50 metrics in a flat grid, no grouping, no visual hierarchy, everything competing for attention.

---

### Landing Pages & Conversion Flows

**Priority order:**

| Priority | Law | Why |
|---|---|---|
| 🔴 Critical | Von Restorff Effect | CTA pops; one standout element per screen |
| 🔴 Critical | Jakob's Law | Conventional patterns reduce friction |
| 🟡 Important | Aesthetic-Usability Effect | First impression in ~50ms; polish = perceived quality |
| 🟡 Important | Goal-Gradient Effect | Social proof, progress indicators, urgency |
| 🟡 Important | Peak-End Rule | Strong finish to the conversion flow |
| 🟡 Important | Cognitive Bias (ethical) | Anchoring, social proof, smart defaults |
| 🔵 Nice-to-have | Hick's Law | Remove nav clutter on landing pages |
| 🔵 Nice-to-have | Choice Overload | 1-3 CTAs, not 8 |

**Common landing page anti-pattern:** 5 equally-weighted buttons, generic stock feel, no clear next step, weak end-state.

---

### Mobile & Touch Interfaces

**Priority order:**

| Priority | Law | Why |
|---|---|---|
| 🔴 Critical | Fitts's Law | Thumb zones; 44px minimum targets; edge placement |
| 🔴 Critical | Doherty Threshold | Touch feedback < 100ms; optimistic actions |
| 🔴 Critical | Hick's Law | Reduce choices; progressive disclosure is mandatory on small screens |
| 🟡 Important | Cognitive Load | Screen real estate is precious — every pixel must earn its place |
| 🟡 Important | Law of Proximity | Tight grouping; touch targets must not be accidentally adjacent |
| 🟡 Important | Zeigarnik Effect | Progress visible; multi-step flows show completion % |
| 🔵 Nice-to-have | Aesthetic-Usability | Touch interfaces are intimate — polish matters more |
| 🔵 Nice-to-have | Flow | Minimize interruptions; full-screen modes for focus tasks |

**Common mobile anti-pattern:** Tiny tap targets crammed together, no touch feedback, desktop layout squished onto phone.

---

### Navigation & Information Architecture

**Priority order:**

| Priority | Law | Why |
|---|---|---|
| 🔴 Critical | Jakob's Law | Conventional patterns; users know how nav works already |
| 🔴 Critical | Hick's Law | 5–7 top-level items max; group the rest |
| 🟡 Important | Law of Proximity | Nav items grouped; labels close to their content |
| 🟡 Important | Mental Model | Match user's mental map of where things should live |
| 🟡 Important | Serial Position Effect | Most-used item first; account/profile last |
| 🔵 Nice-to-have | Law of Uniform Connectedness | Breadcrumbs, step indicators show sequence |
| 🔵 Nice-to-have | Selection Attention | Current page/state clearly distinguished |

**Common navigation anti-pattern:** 15+ top-level items, non-standard icons without labels, inconsistent hierarchy.

---

## Quick Reference: All 30 Laws at a Glance

| # | Law | One-Line Summary |
|---|---|---|
| 1 | **Fitts's Law** | Target acquisition time = f(distance, size). Make buttons big and close. |
| 2 | **Doherty Threshold** | Respond < 400ms or lose attention. Optimistic UI, instant feedback. |
| 3 | **Hick's Law** | More choices = slower decisions. Progressive disclosure. |
| 4 | **Jakob's Law** | Users spend most time on other sites. Use conventions they already know. |
| 5 | **Mental Model** | Design for how users *think* your system works, not just how it does. |
| 6 | **Paradox of Active User** | Nobody reads docs. Make it work immediately; help contextually. |
| 7 | **Law of Proximity** | Near items = related items. Spacing creates groups. |
| 8 | **Law of Similarity** | Same look = same kind. Visual consistency signals relationship. |
| 9 | **Law of Common Region** | Shared boundary = shared group. Cards, panels, containers. |
| 10 | **Law of Uniform Connectedness** | Connected elements = related. Lines, breadcrumbs, borders. |
| 11 | **Law of Prägnanz** | People interpret complex things as simply as possible. Reduce noise. |
| 12 | **Von Restorff Effect** | The odd one out gets remembered. One standout element per screen. |
| 13 | **Selective Attention** | Users ignore off-goal content. Design for their current task. |
| 14 | **Miller's Law** | Working memory holds 7±2 items. Limit options per view. |
| 15 | **Cognitive Load** | Mental effort to understand your UI. Minimize extraneous load. |
| 16 | **Chunking** | Break info into meaningful groups. Headings, cards, sections. |
| 17 | **Working Memory** | Temporary task memory. Show state; persist drafts; never hide context. |
| 18 | **Serial Position Effect** | First and last items remembered best. Put important stuff at edges. |
| 19 | **Aesthetic-Usability Effect** | Pretty = feels more usable. Polish isn't optional. |
| 20 | **Peak-End Rule** | Judged by peak emotion + final moment. Design both deliberately. |
| 21 | **Zeigarnik Effect** | Incomplete tasks stick in memory. Show progress; drive completion. |
| 22 | **Goal-Gradient Effect** | Closer to goal = more motivated. Accelerate perceived progress near end. |
| 23 | **Flow** | Immersed focus state. Match challenge to skill; remove friction. |
| 24 | **Cognitive Bias** | Systematic thinking errors. Design for bias ethically; avoid dark patterns. |
| 25 | **Choice Overload** | Too many options = paralysis. Curate; recommend default. |
| 26 | **Tesler's Law** | Complexity can't be eliminated, only moved. Absorb it in code, not UI. |
| 27 | **Postel's Law** | Accept messy input; send clean output. Be liberal in, conservative out. |
| 28 | **Occam's Razor** | Simplest solution wins. Fewer assumptions, fewer concepts to learn. |
| 29 | **Parkinson's Law** | Work expands to fill time. Design for speed; auto-save; shortcuts. |
| 30 | **Working Memory** *(see #17)* | — |

---

## The Laws (Detailed Reference)

> **Read these on-demand** when you've selected relevant laws for the user's context. Don't present them all at once.

---

### CATEGORY 1: Interaction & Performance

## 1. Fitts's Law
> *The time to acquire a target is a function of the distance to and size of the target.*

**Core rules:**
- Touch/click targets **≥ 44×44px** (iOS HIG) or **48×48px** (Material). Never below 32px.
- Place primary actions in **easy-reach areas**: top-left, center-screen, or fixed bars at **screen edges** (edges = effectively infinite target size).
- **Destructive actions far from frequent actions** — leverage Fitts's as safety mechanism.
- Group sequential controls closely to minimize cursor/thumb travel distance.

```css
/* ✅ Good */
.action-button {
  min-width: 44px;
  min-height: 44px;
  padding: 12px 24px;
  margin: 8px;
}

/* ❌ Bad */
.tiny-btn { height: 20px; padding: 2px 6px; margin: 2px; }
```

**Mobile thumb zones:** Bottom-left/right corners for phones (natural grip). Top-center is hardest to reach. Place primary actions in the green zone, destructive in the red (hard-to-reach) zone.

**Anti-patterns:** Close buttons < 16px, dense icon toolbars without labels, dropdowns with tiny hit areas, primary actions in hard-to-reach corners on mobile.

---

## 2. Doherty Threshold
> *Productivity soars when computer and human interact at < 400ms — neither waits on the other.*

**Core rules:**
- **Visual feedback < 100ms** (hover, press, focus states).
- **Optimistic UI updates** — don't block on server for local actions (toggles, likes, checkboxes).
- **Show progress for anything > 1s** — spinners, skeletons, progress bars.
- **Perceived performance tricks:**
  - Skeleton screens appear faster than spinners
  - Animated progress bars feel faster than nothing (even if indeterminate)
  - Staggered content reveal holds attention
  - Micro-delays after payment/signup increase perceived value ("something important happened")

```tsx
// ✅ Good: Instant feedback, async sync
function LikeButton({ post }) {
  const [liked, setLiked] = useState(post.isLiked);
  const handleLike = () => {
    setLiked(!liked);           // < 100ms visual feedback
    mutateToggleLike(post.id)   // async, user doesn't wait
      .catch(() => setLiked(!liked)); // revert on error
  };
  return <button onClick={handleLike}>...</button>;
}

// ❌ Bad: Blocking await, user stares at nothing
async function handleLikeBad() {
  setLoading(true);
  await api.toggleLike(post.id); // 😴
  setLiked(!liked);
}
```

**Anti-patterns:** Unresponsive UI during fetches, blank screen route transitions, synchronous main-thread operations, no loading states anywhere.

---

## 3. Hick's Law
> *Decision time increases with number and complexity of choices.*

**Core rules:**
- **Progressively disclose** — show only what's needed now. Wizards, accordions, "Advanced ▾".
- **Highlight/recommend a default** — reduce decision fatigue by guiding.
- **Break complex forms into steps** — 20 fields → 3 steps of ~7 (see Miller's Law).
- **Nav items: ~5–7 max** at top level. Rest goes in dropdowns or "More".

```tsx
// ✅ Good: Progressive disclosure
<Section title="Basic" defaultOpen>
  <Toggle label="Notifications" />
  <Toggle label="Dark mode" />
</Section>
<Collapsible title="Advanced">
  <Select label="Cache strategy" options={[...]} />
</Collapsible>

// ❌ Bad: Wall of choices — 25 fields at once
{settings.map(s => <Field {...s} />)}
```

**Anti-patterns:** 15+ nav items, dashboards showing every metric, 50-option ungrouped selects, pricing pages with no recommended plan highlighted.

---

### CATEGORY 2: Familiarity & Mental Models

## 4. Jakob's Law
> *Users spend most time on other sites. They prefer yours works like the ones they already know.*

**Core rules:**
- **Conventional patterns:** Logo → home (top-left), cart → top-right, search → 🔍 icon, mobile → hamburger, hierarchy → breadcrumbs.
- **Don't reinvent standard components** — date pickers, modals, dropdowns, tabs. Use familiar versions unless you have overwhelming reason.
- **When innovating, provide an off-ramp** — let users opt-in gradually (YouTube redesign approach).

**The innovation tradeoff:** Novel interaction patterns can differentiate your product but incur training debt. Every non-standard pattern forces users to learn something new. Ask: *Does this innovation give enough value to justify the learning cost?*

**Anti-patterns:** Custom scroll behavior, repositioned submit button, novel navigation without signifiers, non-standard form layouts.

---

## 5. Mental Model
> *A compressed model of what we think we know about a system and how it works.*

**Core rules:**
- **Leverage existing mental models.** "Like Spotify" → use Spotify metaphors. "Like file manager" → use file manager conventions.
- **Bridge gaps with analogies.** Genuinely new concepts? Connect them to something familiar.
- **Expose cause-and-effect visibly.** Users build models by observing. State changes must be observable and explainable.
- **Avoid hidden modes.** Double-click doing something different than single-click in the same context breaks mental models silently.

**How to detect broken mental models:** Watch users hesitate, hover aimlessly, click the wrong thing repeatedly, or say "I thought it would...". These signal a mismatch between their model and your design.

**Anti-patterns:** Hidden features discoverable only by accident, inconsistent behaviors across similar-looking elements, abstract icons without labels, same gesture having different effects in different contexts.

---

## 6. Paradox of the Active User
> *Users never read manuals. They start using the software immediately.*

**Core rules:**
- **Zero-onboarding usage must be possible.** Default settings work well. Core value is accessible without tutorial.
- **Contextual help > documentation walls.** Tooltips, inline hints, placeholder text, microcopy beat PDF manuals.
- **Design for error recovery.** Undo, clear error messages with next steps, forgiving inputs (Postel's Law).
- **Learning by doing.** Guided tours that interact with real UI (not screenshots), progressive feature reveal tied to usage.

**The 10-second test:** Can a new user accomplish something meaningful within 10 seconds of opening your app? If not, the active user paradox will make most people bounce before they ever find your help docs.

**Anti-patterns:** Mandatory 10-step onboarding before app access, features locked behind "read docs" gates, error messages referencing manual page numbers.

---

### CATEGORY 3: Perception & Visual Design (Gestalt Principles)

## 7. Law of Proximity
> *Near objects are perceived as a group.*

**Core rules:**
- **Group with whitespace, not lines.** Label closer to its input than to the next label.
- **Consistent spacing scale.** Base 4px: `4, 8, 12, 16, 24, 32, 48, 64`. Within-group gap < between-group gap.
- **Nav items closer to each other than to page content.**

```css
/* ✅ Good: Proximity creates groups */
.form-group {
  display: flex;
  flex-direction: column;
  gap: 6px;           /* tight within group */
  margin-bottom: 24px; /* loose between groups */
}

/* ❌ Bad: Uniform spacing = no grouping signal */
.form-bad > * + * { margin-top: 16px; }
```

**Practical application:** Form field labels, card titles + content, toolbar icon groups, list items, definition lists. Whenever you see items that belong together, bring them closer and push other things away.

---

## 8. Law of Similarity
> *Similar elements are perceived as a group or whole.*

**Core rules:**
- **Same style = same type.** All primary buttons match. All destructive actions are red. All links share color/underline.
- **Card-based UI exploits this.** Same card structure = "these are items of the same kind."
- **Different actions must look different.** Cancel ≠ Submit visually. Secondary ≠ Primary.

```css
/* ✅ Good: Visual language communicates function */
.btn-primary   { background: #0066cc; color: white; font-weight: 600; }
.btn-secondary { background: #f0f0f0; color: #333; }
.btn-danger    { background: #dc3545; color: white; }
/* Each role has a distinct visual signature */

/* ❌ Bad: Different functions, same appearance */
.btn-submit { background: #0066cc; }
.btn-cancel { background: #0066cc; } /* which one commits? */
```

**Pro tip:** Audit your interface in grayscale. If you can't distinguish action types by size/shape/weight alone, your similarity signaling is over-relying on color (accessibility issue too).

---

## 9. Law of Common Region
> *Elements sharing a bounded area are perceived as a group.*

**Core rules:**
- **Cards, panels, containers = regions.** Background color, border, shadow creates a grouping boundary.
- **Layout regions:** Sidebar, main, header — use background contrast to separate.
- **Wizard steps as cards** = clear boundaries between stages.

```html
<!-- ✅ Good: Regions group related content -->
<div class="grid grid-cols-3 gap-6">
  <div class="card col-span-2">  <!-- region: analytics -->
    <h3>Analytics Overview</h3>
  </div>
  <div class="card">             <!-- region: quick actions -->
    <h3>Quick Actions</h3>
  </div>
</div>
```

**Relationship to proximity:** Common region is stronger than proximity. Items in the same card are seen as grouped even if spaced apart within that card. Items in different cards are seen as separate even if close together.

---

## 10. Law of Uniform Connectedness
> *Visually connected elements are perceived as more related than unconnected ones.*

**Core rules:**
- **Connector lines beat proximity.** A line between two elements makes them feel more related than two unconnected nearby elements.
- **Timelines, workflows, step indicators** — connecting lines show sequence.
- **Breadcrumb separators, table row borders, connector lines** all exploit this.

```html
<!-- ✅ Good: Connector shows relationship -->
<div class="step-indicator">
  <div class="step done">──●──</div>
  <div class="step active">──●──</div>
  <div class="step pending">──○──</div>
</div>

<!-- List items connected by a subtle rule -->
<ul class="connected-list">
  <li>Item A</li>  <!-- border-bottom connects to next -->
  <li>Item B</li>
  <li>Item C</li>
</ul>
```

**Gestalt hierarchy:** Uniform Connectedness > Common Region > Similarity > Proximity. When in doubt, draw a line.

---

## 11. Law of Prägnanz (Simplicity)
> *People interpret ambiguous/complex images as the simplest possible form.*

**Core rules:**
- **Every element earns its place.** Ask: "Does this help the user complete their task right now?"
- **Recognizable icons only.** Trash can looks like trash can, not abstract geometry.
- **Standard layouts.** Single-column for reading, grid for browsing, sidebar+main for tools — these are the simplest interpretations users naturally arrive at.
- **Decorative complexity without function = cognitive tax.**

**The simplicity test:** Can you describe the page structure in one sentence? "It's a [layout type] with [main thing] and [secondary things]." If you need five sentences, there's probably too much going on.

---

## 12. Von Restorff Effect (Isolation Effect)
> *Among similar objects, the different one is remembered best.*

**Core rules:**
- **One standout element per screen maximum.** If everything emphasizes, nothing does.
- **Primary CTA must be visually distinct** from secondary/cancel.
- **Important notifications break the pattern.** Errors, confirmations, upgrades need to pop.
- **Restraint is the skill.** Size, weight, color, position, motion — pick 1-2 dimensions of emphasis. Don't use all of them everywhere.

```css
/* ✅ Good: One element pops */
.button-secondary { background: #f0f0f0; color: #333; }
.button-primary   { background: #0066cc; color: white; font-weight: 600; } /* pops */
.button-danger     { background: #dc3545; color: white; } /* used sparingly */

/* ❌ Bad: Everything competes for attention */
.btn-a { background: red; }
.btn-b { background: blue; font-size: 1.2em; }
.btn-c { background: yellow; border: 3px dashed orange; animation: pulse; }
```

**⚠️ Accessibility:** Never rely on color alone. Combine with size, weight, shape, position, or text labels. Respect `prefers-reduced-motion` for motion-based emphasis.

**⚠️ Ad-blindness risk:** If your "standout" element looks like a banner ad (flashing, contrasting aggressively, placed where ads usually live), users will tune it out via Selective Attention. Emphasis should feel native, not ad-like.

---

## 13. Selective Attention
> *People focus only on stimuli related to their current goal.*

**Core rules:**
- **Users ignore off-goal content.** Checkout user misses newsletter banner. Search user skips promotional carousel.
- **Design for the goal-state.** What is the user trying to do RIGHT NOW? Remove everything that doesn't serve it.
- **Avoid "banner blindness" zones.** Top-right banners, ad-like footers, generic sidebars — users have trained themselves not to see these.
- **In-context beats prominent.** An inline message where the user is looking beats a modal interrupting them.

**Design technique — Goal-State Mapping:**
```
User's likely goal: "Find pricing"
→ Make Pricing link obvious in nav, footer, homepage
→ Don't distract with "Read our blog" popup on the pricing page
→ Remove nav clutter on pricing page (Hick's Law + Selective Attention combo)

User's likely goal: "Submit this form"
→ Remove header nav, footer, sidebar — pure form view
→ Show progress indicator (working memory)
→ One clear CTA (Von Restorff)
→ Validate inline, fast (Doherty + Postel's)
```

**Anti-pattern:** Promotional banners on checkout pages, modals interrupting task flows, critical info in footers/sidebars on task-focused pages.

---

### CATEGORY 4: Memory & Cognition

## 14. Miller's Law
> *Average person holds 7±2 items in working memory.*

**Core rules:**
- **~5–9 items max per view.** Nav tabs, filter chips, radio groups.
- **Chunk to stay within limit.** Credit card: `XXXX XXXX XXXX XXXX`. Phone: `(555) 123-4567`.
- **Never require cross-page recall.** Show context, persist selections, maintain state.
- **Progressive disclosure** keeps working memory load low (overlaps Hick's Law).

**The myth nuance:** Miller's original paper was about one-dimensional stimuli. Real-world "items" are richer, so the practical limit is often closer to **4±1** for complex items (like menu options with labels). Err on the side of fewer.

---

## 15. Cognitive Load
> *Mental resources needed to understand and interact with an interface.*

Three types — know which you're designing for:

| Type | Definition | How to Reduce It |
|---|---|---|
| **Intrinsic** | Effort inherent to the task itself | Support with wizards, previews, tooltips, examples. You can't eliminate it, only support it. |
| **Extraneous** | Effort from how you present it | **This is fixable.** Remove decoration, simplify visuals, avoid gratuitous animation, clean up layout. |
| **Germane** | Effort spent learning/processing | Reduce through familiarity (Jakob's Law). Use known patterns so users spend zero mental resources "figuring out" your UI. |

**One concept per screen** is the golden rule. Settings categorized by topic, not 50 toggles flat.

```tsx
// ✅ Good: Low cognitive load — one concern per step
const steps = [
  { title: 'Account',   fields: ['email', 'password'] },
  { title: 'Profile',   fields: ['name', 'avatar'] },
  { title: 'Preferences', fields: ['theme', 'notifications'] },
];

// ❌ Bad: High cognitive overload — everything at once
// 25 fields, 5 sections, conditional logic, all visible simultaneously
```

---

## 16. Chunking
> *Break information into meaningful groups.*

**Core rules:**
- **Group nav under headings.** "Account", "Billing", "Support" vs 15 flat links.
- **Format data for scanning.** Phones, dates, addresses — visual chunking.
- **Card grids chunk content.** 12 posts → 3 rows × 4 cards. Each card = one chunk.
- **Breadcrumbs are spatial chunks.** `Home > Products > Category > Item`.

**Chunking vs progressive disclosure:** Chunking organizes what's visible. Progressive disclosure controls how much is visible. They work together — show a few chunks, let users expand within each.

**Practical chunk sizes for web:**
- Navigation items per group: 3–7
- Form fields per step: 4–7
- Dashboard cards per row: 2–4
- Table columns visible: 4–8 (rest in detail view)
- List items before paginating: 7–15

---

## 17. Working Memory
> *Cognitive system that temporarily holds/manipulates information for tasks.*

**Core rules:**
- **Never ask users to recall from a previous step without showing it.** "Step 3 of 3" summarizes Steps 1 & 2.
- **Persist values.** Navigate away and back? Draft still there.
- **State visibility.** Is it saving? Did it succeed? What's left?
- **Multi-step flows = persistent progress indicators always.**

**The cost of losing working memory context:** Every time a user forgets a piece of information they needed (what they selected on step 1, what field they were editing, whether they saved), they experience a **micro-friction** that accumulates. Enough micro-frictions = abandonment.

**Implementation checklist:**
- [ ] Auto-save drafts (forms, compose, settings changes)
- [ ] Summarize prior selections at each step
- [ ] Show save status clearly (saved ✓ / saving... / unsaved changes)
- [ ] Restore state on return (browser back, tab switch, refresh)

---

## 18. Serial Position Effect
> *First and last items in a series are remembered best.*

**Core rules:**
- **Most important item first, most important action last.** Nav: most-used link first. Form: primary CTA last.
- **Pricing tables:** recommended plan first or last (or highlight via Von Restorff).
- **Accept middle-item amnesia.** In equal-importance lists, middle items will be remembered least. Reorder if order matters.
- **Onboarding: start strong, end strong.** First impression (Aesthetic-Usability) + final moment (Peak-End Rule).

**Application beyond lists:**
- **Menu items:** Put revenue-driving links first
- **Feature announcements:** Lead with the biggest win
- **Error messages:** Show the most actionable error first (not necessarily the first the backend returned)
- **Testimonials:** strongest quote first or last

---

### CATEGORY 5: Emotion & Behavior

## 19. Aesthetic-Usability Effect
> *Users perceive aesthetically pleasing design as more usable.*

**Core rules:**
- **Visual polish is functional, not cosmetic.** Users forgive minor usability issues in beautiful interfaces.
- **Cohesive design system.** Consistent type, color, spacing, icons = aesthetic coherence.
- **⚠️ Beauty masks usability problems.** Testing: users rate pretty-but-broken interfaces high. Test function separately from form.
- **First impression: ~50ms.** Above-the-fold quality sets the tone for everything after.

**Polish checklist:**
- [ ] Consistent type scale (heading/body/caption)
- [ ] Harmonious color palette
- [ ] Adequate whitespace (empty space is design)
- [ ] Single icon family, single style
- [ ] Micro-interactions (hover/focus/press states)
- [ ] Responsive at every viewport
- [ ] No ragged edges, misaligned elements, or orphaned pixels

**ROI argument for stakeholders:** "Investing in visual quality isn't vanity — the Aesthetic-Usability Effect is well-documented. Users report higher satisfaction and tolerance for issues in polished interfaces. It's a usability multiplier, not a nice-to-have."

---

## 20. Peak-End Rule
> *Experiences are judged by peak intensity + final moment, not the average.*

**Core rules:**
- **Design peak moments.** Task completion = celebrate. Confetti, meaningful copy, satisfying animation.
- **End every flow on a high note.** Checkout → warm confirmation + next steps. Form submitted → personality (Mailchimp "High Five").
- **Negative peaks linger longer than positive.** One checkout error hurts more than great browsing helps. Invest in error recovery.
- **Map your user journey.** Identify emotional peaks (positive and negative). Design them intentionally.

```tsx
// ✅ Good: Strong end state
<SuccessScreen>
  <Confetti />                          {/* peak delight */}
  <Heading>Order #{order.id} confirmed!</Heading>
  <p>We'll email you at {order.email} with tracking.</p>
  <CTA href="/orders">View Order Details</CTA>  {/* clear next step */}
</SuccessScreen>

// ❌ Bad: Dead end
<div>Thank you. Order received.</div>  /* cold, abrupt, no next step */
```

**Common flow endings ranked:**
1. ✅ Delight + clear next step (confetti + "View your order")
2. ✅ Warm confirmation + next step ("You're all set! Here's what happens next")
3. ⚠️ Confirmation only ("Done") — functional but forgettable
4. ❌ Abrupt cutoff (page goes blank, redirects abruptly) — feels broken
5. ❌ Negative peak (error message at end of flow) — worst possible impression

---

## 21. Zeigarnik Effect
> *Uncompleted or interrupted tasks are remembered better than completed ones.*

**Core rules:**
- **Show incomplete progress prominently.** "Your profile is 75% complete." "3 of 8 files remaining."
- **Partial progress motivates completion.** Endowed progress effect: sign up gives instant 10% toward profile completion. Progress bars start slightly filled.
- **Auto-save drafts.** Let users leave and come back — the incomplete task creates return motivation.
- **Never hide in-progress state.** Saved drafts, abandoned carts, unfinished onboarding = re-entry points, not failures.

```tsx
// ✅ Good: Visible incomplete progress drives return
<Card>
  <ProgressBar value={percent} />
  <p>Your profile is {percent}% complete</p>
  {percent < 100 && (
    <Link to="/settings/profile">Complete your profile →</Link>
  )}
</Card>
```

**Ethical consideration:** The Zeigarnik effect is powerful but can be manipulative if overused (gamification dark patterns, artificial urgency). Use it to help users complete genuinely valuable tasks, not to drive addictive looping behavior.

---

## 22. Goal-Gradient Effect
> *Motivation increases as proximity to the goal increases.*

**Core rules:**
- **Accelerate perceived progress near the end.** Smaller remaining steps, larger increments. The last 20% should feel faster than the first 20%.
- **Framing matters.** "Only 2 purchases until Gold!" >> "10 purchases to reach Gold."
- **Large goals → milestones.** "Complete setup" → "Step 1✓ Step 2✓ Step 3 → almost there!"
- **Onboarding bars that fill faster near the end** measurably increase completion rates.

**Implementation techniques:**
- Progress bar with **non-linear easing** (accelerates visually toward 100%)
- **Milestone celebrations** at 25%, 50%, 75% (mini peaks)
- **"Almost there!" messaging** when > 80% complete
- **Remaining count instead of percentage** when close to goal ("2 steps left" > "92% complete")

---

## 23. Flow
> *Immersed state of energized focus, full involvement, enjoyment.*

**Core rules:**
- **Match challenge to skill.** Novices → guided flows. Experts → keyboard shortcuts, power-user features, bulk operations.
- **Remove friction from core tasks.** Writing app → distraction-free writing. IDE → seamless code/run/debug loop.
- **Immediate feedback loops.** Every action → visible response (Doherty Threshold). This maintains flow.
- **Don't interrupt flow.** No unnecessary modals, upsells, notifications during focus tasks. Save non-critical comms for natural breaks.

**Signs of broken flow:** User has to stop and think "where do I click next?", waits for anything, switches context to check something, or gets pulled away by an interruption. Each break risks losing the flow state entirely, and research shows it takes **15-25 minutes** to regain deep flow once broken.

**Flow-friendly design patterns:**
- Keyboard shortcuts for frequent actions (no mouse reach)
- Command palettes (`Cmd+K`) for power users
- Auto-save so Ctrl+S isn't needed
- Distraction-free/fullscreen modes for focus tasks
- Batch operations (select many → act once) vs repetitive individual actions

---

## 24. Cognitive Bias
> *Systematic errors in thinking that influence perception and decisions.*

**Core rules:**
- **Design FOR bias, don't fight it blindly.** Users anchor on first price seen. Prefer defaults. Follow social proof.
- **Ethical persuasion toolkit:**
  - **Anchoring:** Show original price crossed out next to sale price
  - **Social proof:** "Joined by 10,000+ developers" (must be genuine)
  - **Scarcity (genuine only):** "3 spots left" — never fake
  - **Defaults:** Pre-select the recommended option
  - **Authority:** "Recommended by [trusted expert]"
- **Dark patterns to avoid:**
  - Fake scarcity ("Only 2 left!" when there are 500)
  - Forced continuity (free trial auto-bills without clear warning)
  - Confirmshaming ("No, I want to miss out" as cancel option)
  - Roach motel (easy to join, impossible to leave/ delete account)
  - Hidden costs revealed at final checkout step

**The trust equation:** Short-term gains from dark patterns << Long-term value from trusted relationships. Every biased-choice manipulation that deceives users erodes future trust. Design for bias transparently.

---

## 25. Choice Overload (Paradox of Choice)
> *Too many options overwhelm and paralyze.*

**Core rules:**
- **Curate, don't catalog.** 3-5 options presented. "See all" for power users.
- **Smart recommendations.** "Pick for me" buttons, AI-suggested configs.
- **Categorized choice architecture.** 50 options in 5 categories of 10 >> 50 flat options.
- **Defer, don't force.** Favoriting, comparison mode, "decide later" for complex choices.

**The sweet spot:** Research consistently shows that **offering 3-5 options** maximizes conversion satisfaction. Below 3 feels constraining. Above 7 causes measurable decision fatigue. Between 3-5 with a recommended default is optimal for most contexts.

**When you genuinely need many options:**
1. Start with a **recommended/default** pre-selected
2. Let users **narrow down** with filters (not scroll through 50)
3. Offer **comparison mode** for finalists
4. Allow **"decide later"** with saved progress

---

### CATEGORY 6: System Design & Robustness

## 26. Tesler's Law (Conservation of Complexity)
> *Every system has irreducible complexity. It lives either in the code or in the user's brain.*

**Core rules:**
- **Absorb complexity in code, not UI.** Your job: handle the hard stuff so users don't.
- **Smart defaults absorb complexity.** 10 settings to configure? Pick good defaults, let users override.
- **Don't oversimplify to abstraction.** "Auto" button that doesn't work well >> thoughtful exposed controls. Simple surface, advanced available underneath.
- **Progressive disclosure = the answer.** Simple surface → advanced options for those who need them.

```tsx
// ✅ Good: System absorbs complexity
<SmartDateInput
  label="When?"
  // Handles parsing, timezone, validation, formatting
  // User picks a date. That's it.
/>

// ❌ Bad: Complexity dumped on user
<input
  placeholder="2024-01-15T14:30:00+00:00"
  pattern="^\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}..."
  label="Enter date in ISO 8601 format with timezone offset..."
/>
```

**The engineer's tradeoff:** Spending 1 extra week reducing UI complexity saves millions of users 1 extra minute each. Larry Tesler's argument at Xerox PARC. Always err toward absorbing complexity in code.

**Signs complexity is in the wrong place:** Users need to read documentation to use basic features, error messages expose internal concepts (UUIDs, stack traces, database keys), or you hear "why is this so complicated?" about common tasks.

---

## 27. Postel's Law (Robustness Principle)
> *Be liberal in what you accept, conservative in what you send.*

**Core rules:**
- **Accept varied input gracefully:**
  - Phones: `(555) 123-4567`, `555.123.4567`, `5551234567` → all valid
  - Names: unicode, spaces, hyphens, apostrophes → all valid
  - Dates: multiple formats → parse and normalize internally
  - Search: tolerate typos, fuzzy match
- **Output clean, consistent, valid data.** Normalize before storing. Validate before API calls.
- **Forgiving error recovery.** "Did you mean...?" > "Invalid input."
- **Graceful degradation.** Feature fails? Core functionality still works.

```tsx
// ✅ Good: Liberal input, conservative output
function PhoneInput({ value, onChange }) {
  return (
    <input
      value={value}
      onChange={(e) => {
        const raw = e.target.value.replace(/[^\d+\-\s().]/g, '');
        onChange(raw); // store normalized internally
      }}
      placeholder="(555) 123-4567"
      // Accepts any reasonable format. Normalizes to digits-only.
    />
  );
}

// Output: always normalized before sending
function formatForAPI(phone) {
  return phone.replace(/\D/g, ''); // "+1 (555) 123-4567" → "15551234567"
}
```

**Postel's Law is the foundation of forgiving UX.** Combine with Doherty Threshold (fast validation feedback) and Paradox of Active User (no manual needed) for forms that feel intelligent rather than rigid.

---

## 28. Occam's Razor
> *Fewest assumptions wins. Among equally effective solutions, pick the simplest.*

**Core rules for UX:**
- **Simplest explanation for user behavior is usually right.** Button not getting clicks? It doesn't look clickable / poorly positioned / unclear label. NOT "users don't understand our revolutionary paradigm."
- **Fewer moving parts.** Two approaches work equally? Pick the one with fewer concepts to learn, fewer edge cases, fewer interactions.
- **Avoid over-engineering.** Not every screen needs A/B testing. Not every interaction needs animation. Not every form needs real-time validation.

**Occam's questions before adding any feature:**
1. Does this solve a real problem we've observed?
2. Is there a simpler way to solve it?
3. Does this add a new concept for the user to understand?
4. Would removing this break anything?
5. Can we ship without this and add it later?

**The "simplest" trap:** Occam's Razor doesn't mean "oversimplified to the point of uselessness." It means the simplest solution that **actually solves the problem**. Under-simplifying (Tesler's Law violation) pushes complexity to users.

---

## 29. Parkinson's Law
> *Work expands to fill available time.*

**Core rules for UX:**
- **Design for speed.** Auto-save, keyboard shortcuts, templates, bulk ops → reduce time-to-completion.
- **Implicit deadlines.** Progress bars, step counts ("Step 2 of 4"), ETA displays create gentle time pressure.
- **Remove unnecessary steps.** Every extra field, click, or page = opportunity for Parkinson's inflation.
- **Pre-fill everything possible.** User data, context, location, previous choices.

**Parkinson's in product design manifests as:**
- Forms that could be 3 fields but are 10 (because there was space)
- Onboarding that takes 5 minutes because nobody constrained it
- Checkouts with 6 steps because each team added "just one more"
- Settings pages that grew organically without pruning

**Counter-tactics:**
- Set **arbitrary constraints** at design time: "This form must fit on one screen." "Checkout completes in ≤ 3 steps."
- **Time yourself** performing the task. If it takes you 2 minutes (and you built it), it'll take a user 10+.
- **Measure drop-off per step.** Where do users abandon? That step is probably bloated or unnecessary.

---

## When Laws Conflict

Real design involves tradeoffs. Here's how to resolve the most common tensions:

### Fitts's Law vs Von Restorff Effect
**Tension:** Make everything big (Fitts's) vs make only ONE thing stand out (Von Restorff)

**Resolution:** All interactive elements meet minimum size (44px — Fitts's floor), but use **weight/color/position** to make only the primary CTA pop (Von Restorff ceiling). Every button is reachable; only one demands attention.

### Hick's Law vs Postel's Law
**Tension:** Limit visible choices (Hick's) but accept any input format (Postel's)

**Resolution:** Present **few focused options** in the UI (dropdown, toggle, preset buttons) but accept **flexible text input** as fallback. Example: date picker shows calendar (few choices) but also accepts typed dates in any format (liberal input).

### Jakob's Law vs Innovation
**Tension:** Use conventional patterns (Jakob's) vs differentiate your product

**Resolution:** Be **conventional in interaction** (it works like users expect) but **distinctive in personality** (your visual brand, voice, micro-interactions). Users should recognize HOW to use your app instantly (Jakob's) while recognizing it's YOUR app (differentiation). Innovation in interaction should be reserved for places where convention is genuinely broken.

### Aesthetic-Usability vs Peak-End Rule
**Tension:** Invest in overall polish (Aesthetic-Usability) vs invest in peak/end moments (Peak-End)

**Resolution:** Both matter, but they serve different phases. **Aesthetic-Usability sets the baseline** — every screen meets a quality bar. **Peak-End Rule identifies the 2-3 moments** that get extra investment (onboarding complete, first success, checkout confirmation). Budget: 80% of design effort on consistent quality, 20% on peak delight moments.

### Tesler's Law vs Occam's Razor
**Tension:** Absorb complexity in code (Tesler's) vs keep things simple (Occam's)

**Resolution:** These are allies, not enemies. **Occam's tells you WHAT to build** (the simplest solution that works). **Tesler's tells you WHERE the complexity lives** (in your code, not the UI). Simple UI ≠ simple codebase. Often the simplest UI requires the most sophisticated code (smart defaults, fuzzy parsing, predictive input).

### Von Restorff Effect vs Accessibility
**Tension:** Make elements stand out (Von Restorff) vs don't rely solely on color (a11y)

**Resolution:** Multi-dimensional emphasis. Stand out using **size + weight + position + color** (not color alone). A primary button is bigger, bolder, positioned prominently, AND colored differently. This satisfies Von Restorff (it stands out) and WCAG (distinction isn't color-dependent). Win-win.

### Cognitive Bias (persuasion) vs Trust
**Tension:** Use bias to guide choices (Cognitive Bias) vs don't manipulate (trust)

**Resolution:** The line is **transparency**. Using anchoring, social proof, and defaults is ethical when:
- Claims are **genuine** (real social proof, real scarcity)
- The **user benefits** from the guided choice (better fit, less effort)
- The user can **opt out** easily (clear alternative, no confirmshaming)

Cross the line when: claims are fabricated, the guidance serves only your interests, or opting out is hidden/penalized.

---

## Stakeholder Communication

Use these scripts when pushing back on bad UX decisions. Each cites evidence.

### "We need to add more options/features"

> "Right now this screen presents N options. Hick's Law tells us decision time grows logarithmically with the number of choices — we're literally slowing users down with every addition. I'd recommend we either: (a) progressive disclose these under an Advanced section, or (b) pick smart defaults and let power users override them. We can A/B test this, but the research strongly favors fewer choices."

### "Make the button smaller, it looks ugly big"

> "I get the visual concern, but Fitts's Law shows that target acquisition time scales directly with size and inversely with distance. Below 44px, error rates climb sharply — especially on mobile where thumbs are imprecise. We can keep it polished at 44px, or we can track the mis-click rate and revisit. My prediction: smaller button = more support tickets."

### "Users will read the tooltip / help text"

> "The Paradox of the Active User is well-documented — users simply don't read documentation before using software. They start clicking immediately. Whatever they need to know has to be discoverable through the interface itself: inline hints, smart defaults, contextual help. If we're relying on tooltips being read, we're designing for a user who doesn't exist."

### "This looks good enough, let's ship it"

> "The Aesthetic-Usability Effect cuts both ways — research shows users rate prettier interfaces as more usable even when they're not, which means beauty can mask usability problems in testing. I'd suggest we run a quick usability test specifically on task completion (not just subjective ratings) before shipping. What we don't want is a pretty interface that users struggle with."

### "Why spend time on the success/confirmation screen?"

> "The Peak-End Rule shows that people judge experiences primarily by how they felt at the peak and at the end. This confirmation screen IS the end of the flow — it's the lasting impression. A generic 'Thank you' is a wasted opportunity for delight and for guiding next steps. Mailchimp built brand loyalty partly on their 'High Five' screen. It's low effort, high impact."

### "Just let users configure it themselves"

> "Tesler's Law — the Law of Conservation of Complexity. The complexity has to live somewhere. Right now we're pushing it to the user with 'go configure it.' Every setting we expose is cognitive load we're adding. I'd recommend we pick good defaults, absorb the complexity in our code, and only expose configuration for the 10% who actually need it."

### "But [competitor] does it this way"

> "That's actually evidence FOR following Jakob's Law, not against it. Our users spend most of their time on other sites — including our competitor's. They've learned how things work there. We can either leverage that existing mental model (lower learning curve, faster time-to-value) or fight it (novelty cost, potential confusion). What specific advantage does our different approach give the user?"

---

## Prioritized UX Review Checklist

Run through this when reviewing any UI. **Check in severity order — stop at the first critical finding and flag it.**

### 🔴 Critical (Causes errors, abandonment, frustration)

- [ ] **Touch/click targets ≥ 44×44px** (Fitts's Law) — smaller = misclicks, especially mobile
- [ ] **Visual feedback < 400ms** on every interaction (Doherty Threshold) — slower = feels broken
- [ ] **Input accepts varied formats gracefully** (Postel's Law) — rigid input = frustrated users
- [ ] **Errors are recoverable with clear next steps** (Postel's + Active User) — dead ends = abandonment
- [ ] **Uses conventional patterns for core interactions** (Jakob's Law) — novel patterns confuse

### 🟡 Important (Slows users down, reduces completion rates)

- [ ] **No more than 5–7 choices per view** (Miller's + Hick's) — more = decision fatigue
- [ ] **Progressive disclosure for complex features** (Hick's + Tesler's) — wall of options = overwhelmed
- [ ] **Related items grouped by proximity** (Proximity) — scattered = harder to scan
- [ ] **Clear container boundaries define regions** (Common Region) — no boundaries = no structure
- [ ] **One primary emphasis per screen** (Von Restorff) — everything competes = nothing wins
- [ ] **Information chunked into scannable groups** (Chunking + Cognitive Load) — flat = overload
- [ ] **Cross-step state visible; drafts persisted** (Working Memory) — lost context = restart cost
- [ ] **Smart defaults selected** (Tesler's + Cognitive Bias) — blank slate = more work

### 🔵 Nice-to-have (Delight, polish, differentiation)

- [ ] **Delight moment at task completion** (Peak-End Rule) — memorable positive peak
- [ ] **Incomplete progress visible** (Zeigarnik) — drives return and completion
- [ ] **Strong finish to every flow** (Peak-End) — lasting impression
- [ ] **Polished, coherent visual design** (Aesthetic-Usability) — perceived quality boost
- [ ] **Important items at list start/end** (Serial Position) — remembered better
- [ ] **Goal-state optimized** (Selective Attention) — off-goal content minimized
- [ ] **Keyboard shortcuts / power-user features** (Flow) — expert users fly

---

## Accessibility Overlay

All laws have accessibility implications. Here are the key intersections:

| Law | Accessibility Consideration |
|---|---|
| **Fitts's Law** | Large targets help motor-impaired and elderly users. 44px minimum is also an a11y best practice. |
| **Von Restorff** | Never rely on color alone for emphasis. Combine with size, weight, shape, position, text. |
| **Doherty Threshold** | Respect `prefers-reduced-motion`. Replace animations with instant transitions for users who need them. |
| **Miller's / Cognitive Load** | Screen reader users benefit MORE from chunking and simplification than sighted users. Cognitive disabilities magnify extraneous load. |
| **Postel's Law** | Assistive tech compatibility IS "liberal in what you accept." Accept keyboard-only navigation, screen reader input, switch devices. |
| **Hick's Law** | Cognitive accessibility: users with attention disorders are hit hardest by choice overload. Even more reason to limit options. |
| **Color Contrast** (cross-cutting) | All visual laws (Similarity, Von Restorff, Common Region) must meet WCAG AA contrast ratios (4.5:1 normal text, 3:1 large text). |

---

## References

- [lawsofux.com](https://lawsofux.com) — Jon Yablonski's complete collection (primary source)
- [Nielsen Norman Group](https://www.nngroup.com/) — Deep-dive research articles
- *Designing with the Mind in Mind* — Jeff Johnson
- *100 Things Every Designer Needs to Know About People* — Susan Weinschenk
- [W3C WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/) — Accessible pattern implementations
