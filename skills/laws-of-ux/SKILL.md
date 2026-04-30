---
name: Laws of UX
description: "Apply evidence-based UX psychology laws when building web applications and interfaces. Use this skill whenever designing or reviewing UI/UX for web apps, dashboards, landing pages, forms, navigation systems, or any user-facing interface. Also triggers on: 'UX review', 'usability', 'user experience design', 'make this more usable', 'improve UX', 'UX patterns', 'interface design', 'is this good UX', 'accessibility and usability', or any mention of specific UX laws (Fitts's Law, Hick's Law, Jakob's Law, etc.)."
---

# Laws of UX — Web App Design Skill

> **Source:** [lawsofux.com](https://lawsofux.com) by Jon Yablonski · 30 evidence-based psychology laws for UX design

This skill provides actionable guidelines for applying UX psychology laws to **web application development**. Each law includes what it means, how to apply it in code/UI, anti-patterns to avoid, and code-level guidance where relevant.

---

## Quick Reference: Which Law Do I Need?

| User Problem | Apply This Law |
|---|---|
| Users can't find buttons or click wrong things | **Fitts's Law** |
| Too many options paralyzing users | **Hick's Law**, **Choice Overload** |
| Interface feels slow/unresponsive | **Doherty Threshold** |
| Users confused by non-standard patterns | **Jakob's Law** |
| Screen looks cluttered / hard to scan | **Law of Proximity**, **Law of Prägnanz**, **Cognitive Load** |
| Important action not getting noticed | **Von Restorff Effect** |
| Form/input errors frustrating users | **Postel's Law** |
| Users abandoning long flows | **Zeigarnik Effect**, **Goal-Gradient Effect** |
| Feature feels too complex | **Tesler's Law** |
| Users don't remember key info | **Serial Position Effect**, **Miller's Law** |
| Onboarding / first impression weak | **Aesthetic-Usability Effect**, **Peak-End Rule** |
| Related items don't feel connected | **Law of Common Region**, **Law of Similarity**, **Law of Uniform Connectedness** |
| Users skip documentation | **Paradox of the Active User** |

---

## CATEGORY 1: Interaction & Performance

### 1. Fitts's Law
> *The time to acquire a target is a function of the distance to and size of the target.*

**Apply it in web apps:**
- **Touch/click targets must be large enough.** Minimum `44×44px` (iOS HIG) or `48×48px` (Material Design). Never go below `32×32px`.
- **Place primary actions in easy-to-reach areas.** For web: top-left, center-screen, or in fixed position bars at screen edges (targets at edges are effectively infinitely large in one dimension).
- **Put destructive actions far from frequent actions.** Confirmation dialogs should require deliberate movement — this leverages Fitts's Law as a safety mechanism.
- **Group related controls closely** so the user's cursor travel distance between sequential actions is short.

```css
/* ✅ Good: Large, well-spaced touch targets */
.action-button {
  min-width: 44px;
  min-height: 44px;
  padding: 12px 24px;
  margin: 8px; /* spacing between targets */
}

/* ❌ Bad: Tiny, crowded targets */
.tiny-btn {
  height: 20px;
  padding: 2px 6px;
  margin: 2px;
}
```

**Anti-patterns:** Small close buttons on modals (< 16px), densely packed icon toolbars without labels, dropdown menus with tiny hit areas.

---

### 2. Doherty Threshold
> *Productivity soars when a computer and its users interact at a pace (<400ms) that ensures that neither has to wait on the other.*

**Apply it in web apps:**
- **Respond to user input within 400ms.** Visual feedback (hover states, button press, focus rings) must be instantaneous (`< 100ms`).
- **Use optimistic UI updates.** Don't make users wait for server confirmation for local actions (toggle switches, likes, form field validation).
- **Show progress for anything over 1 second.** Spinners, skeleton screens, progress bars.
- **Use perceived performance tricks:**
  - Skeleton screens appear faster than spinners
  - Animated progress bars (even if indeterminate) feel faster than nothing
  - Staggered content reveal keeps attention engaged
  - Purposeful micro-delays can increase perceived value (e.g., a brief animation after payment confirms "something important happened")

```tsx
// ✅ Good: Optimistic update + fallback
function LikeButton({ post }) {
  const [liked, setLiked] = useState(post.isLiked);
  const [loading, setLoading] = useState(false);

  const handleLike = () => {
    // Instant visual feedback (< 100ms)
    setLiked(!liked);
    setLoading(true);
    // Async server sync (user doesn't wait)
    mutateToggleLike(post.id).catch(() => {
      setLiked(liked); // revert on error
    }).finally(() => setLoading(false));
  };

  return <button onClick={handleLike} disabled={loading}>...</button>;
}

// ❌ Bad: Blocking await before any feedback
async function handleLikeBad() {
  setLoading(true);
  await api.toggleLike(post.id); // user waits... :(
  setLiked(!liked);
  setLoading(false);
}
```

**Anti-patterns:** Unresponsive UI during fetches, no loading states, blank screens during route transitions, synchronous blocking operations on main thread.

---

### 3. Hick's Law
> *The time it takes to make a decision increases with the number and complexity of choices.*

**Apply it in web apps:**
- **Progressively disclose options.** Show only what's needed at each step. Wizards, accordions, "Show advanced options" toggles.
- **Highlight recommended/default choices.** Reduce decision fatigue by guiding users.
- **Break complex forms into steps.** A 20-field form → 3 steps of ~7 fields each (see also: Miller's Law).
- **Limit nav items to ~5–7 top-level items.** Use dropdowns or grouping for the rest.

```tsx
// ✅ Good: Progressive disclosure
function SettingsPanel() {
  return (
    <div>
      {/* Always visible: high-priority settings */}
      <Section title="Basic" defaultOpen>
        <Toggle label="Notifications" />
        <Toggle label="Dark mode" />
      </Section>

      {/* Revealed on demand: low-priority settings */}
      <Collapsible title="Advanced">
        <Select label="Cache strategy" options={[...]} />
        <Input label="Custom CORS origin" />
      </Collapsible>
    </div>
  );
}

// ❌ Bad: Wall of choices
function SettingsWall() {
  return (
    <form>
      <h3>Settings</h3>
      {/* 25 fields visible at once — overwhelming */}
      {settings.map(s => <Field {...s} />)}
    </form>
  );
}
```

**Anti-patterns:** Navigation bars with 15+ items, dashboards showing every possible metric at once, multi-select with 50 ungrouped options, pricing pages with no recommended plan highlighted.

---

## CATEGORY 2: Familiarity & Mental Models

### 4. Jakob's Law
> *Users spend most of their time on other sites. This means that users prefer your site to work the same way as all the other sites they already know.*

**Apply it in web apps:**
- **Use conventional UI patterns.** Logo links to home (top-left), cart in top-right, search with magnifying glass icon, hamburger menu on mobile, breadcrumbs for hierarchy.
- **Don't reinvent standard components.** Date pickers, modals, dropdowns, tabs — use familiar patterns unless you have overwhelming reason not to.
- **Match platform conventions.** macOS users expect certain shortcuts/behaviors; Windows users expect others. Web users have shared expectations from Google, GitHub, Twitter, etc.
- **When innovating, provide an off-ramp.** Let users opt into new designs gradually (YouTube's redesign approach).

**Anti-patterns:** Custom scroll behavior, repositioning the submit button to an unusual location, novel navigation paradigms without clear signifiers, non-standard form layouts.

---

### 5. Mental Model
> *A compressed model based on what we think we know about a system and how it works.*

**Apply it in web apps:**
- **Design for existing mental models.** If users think of your app as "like Spotify," leverage that. If they think of it "like a file manager," follow file manager conventions.
- **Bridge gaps with metaphors and onboarding.** When your model is genuinely new, use analogies to connect it to something familiar.
- **Expose system state clearly.** Users build mental models by observing cause-and-effect. Make state changes visible and explainable.
- **Avoid hidden modes.** If double-click does something different than single-click in context, users' mental models will break.

**Anti-patterns:** Hidden features discoverable only by accident, inconsistent behaviors across similar-looking elements, abstract icons without labels.

---

### 6. Paradox of the Active User
> *Users never read manuals but start using the software immediately.*

**Apply it in web apps:**
- **Make zero-onboarding usage possible.** The app should be usable without a tutorial. Default settings should work well.
- **Use contextual help, not documentation walls.** Tooltips, inline hints, placeholder text, and microcopy > PDF manuals.
- **Design for error recovery.** Undo, clear error messages with next steps, forgiving inputs (Postel's Law).
- **Let users learn by doing.** Guided tours that interact with real UI elements (not screenshots), progressive feature reveals tied to usage.

**Anti-patterns:** Mandatory 10-step onboarding before accessing the app, features locked behind "read the docs" gates, error messages that reference manual page numbers.

---

## CATEGORY 3: Perception & Visual Design (Gestalt Principles)

### 7. Law of Proximity
> *Objects that are near each other tend to be grouped together.*

**Apply it in web apps:**
- **Group related form fields with whitespace, not lines.** A label should be closer to its input than to the next field's label.
- **Use consistent spacing scale.** Define a `gap` system (4px base: 4, 8, 12, 16, 24, 32, 48, 64). Items within a group: small gap. Between groups: larger gap.
- **Navigation items should be closer to each other than to page content.**

```css
/* ✅ Good: Proximity creates groups */
.form-group {
  display: flex;
  flex-direction: column;
  gap: 6px;       /* label ↔ input: tight */
  margin-bottom: 24px; /* between groups: loose */
}

/* ❌ Bad: Everything equally spaced */
.form-bad > * + * {
  margin-top: 16px; /* uniform spacing = no grouping signal */
}
```

---

### 8. Law of Similarity
> *The human eye tends to perceive similar elements as a complete picture, shape, or group.*

**Apply it in web apps:**
- **Use visual consistency to communicate relationship.** Same color/style = same type of thing. All primary buttons look alike; all destructive actions are red; all links are the same blue/underline.
- **Card-based UI relies on similarity.** Cards with identical structure signal "these are items of the same kind."
- **Don't use same styling for different actions.** A "Cancel" button should never look identical to a "Submit" button.

---

### 9. Law of Common Region
> *Elements tend to be perceived into groups if they are sharing an area with a clearly defined boundary.*

**Apply it in web apps:**
- **Use cards, panels, and containers to create regions.** A background color, border, or shadow creates a "region" that groups content.
- **Sidebars, main content, and headers are regions.** Use background contrast to separate them.
- **Forms within cards feel like a single unit.** A multi-step wizard where each step is a card creates clear region boundaries.

```tsx
// ✅ Good: Common region groups related content
<div className="grid grid-cols-3 gap-6">
  <Card className="col-span-2">
    <h3>Analytics Overview</h3>
    <Charts />
  </Card>
  <Card>
    <h3>Quick Actions</h3>
    <ActionList />
  </Card>
</div>
```

---

### 10. Law of Uniform Connectedness
> *Elements that are visually connected are perceived as more related than elements with no connection.*

**Apply it in web apps:**
- **Connector lines beat proximity.** A line between two elements makes them feel more related than two nearby unconnected elements.
- **Use in timelines, workflows, and step indicators.** A connecting line between step nodes shows sequence.
- **Breadcrumb separators, table row borders, and connector lines** all exploit this law.

---

### 11. Law of Prägnanz (Law of Simplicity)
> *People will perceive and interpret ambiguous or complex images as the simplest form possible.*

**Apply it in web apps:**
- **Reduce visual noise.** Every element should earn its place. Ask: "Does this help the user complete their task?"
- **Use simple, recognizable icons.** A trash can icon should look like a trash can, not an abstract geometric composition.
- **Favor standard layouts.** Single-column for reading, grid for browsing, sidebar+main for tools — these are the "simplest interpretations" users will naturally arrive at.
- **Avoid decorative complexity that doesn't serve function.**

---

### 12. Von Restorff Effect (Isolation Effect)
> *When multiple similar objects are present, the one that differs from the rest is most likely to be remembered.*

**Apply it in web apps:**
- **Make CTAs stand out.** The primary action button should be visually distinct from secondary/cancel buttons.
- **Use one accent color for emphasis.** If everything is bold, nothing is bold.
- **Important notifications should break the visual pattern.** Error banners, success confirmations, upgrade prompts — they need to pop out.
- **Exercise restraint.** If everything emphasizes, nothing emphasizes. One standout element per screen maximum.

```css
/* ✅ Good: One standout CTA */
.button-secondary { background: #f0f0f0; color: #333; }
.button-primary   { background: #0066cc; color: white; font-weight: 600; } /* pops */
.button-danger     { background: #dc3545; color: white; } /* used sparingly */

/* ❌ Bad: Everything competes */
.btn-a { background: red; }
.btn-b { background: blue; font-size: 1.2em; }
.btn-c { background: yellow; border: 3px dashed orange; animation: pulse; }
```

**Accessibility note:** Don't rely solely on color for distinction. Combine color with size, weight, shape, position, or text labels. Respect `prefers-reduced-motion`.

---

### 13. Selective Attention
> *The process of focusing our attention only to a subset of stimuli — usually those related to our goals.*

**Apply it in web apps:**
- **Users will ignore anything unrelated to their current goal.** A user trying to check out will miss your newsletter signup banner.
- **Design for the user's goal-state.** What is the user trying to do right now? Remove everything that doesn't serve that goal.
- **Don't put critical info in "banner blindness" zones.** Top-right banners, anything that looks like an ad, generic footers — users tune these out.
- **Contextual relevance beats prominence.** A message placed where the user is looking (inline, in-context) beats a modal that interrupts them.

---

## CATEGORY 4: Memory & Cognition

### 14. Miller's Law
> *The average person can only keep 7 (±2) items in their working memory.*

**Apply it in web apps:**
- **Limit options in any single view to ~5–9 items.** Navigation tabs, filter chips, radio button groups.
- **Chunk information.** Break long numbers (credit card: `XXXX XXXX XXXX XXXX`), group related settings, use headings to create chunks.
- **Don't require users to remember things across pages.** Show context, show previous selections, persist state.
- **Progressive disclosure keeps working memory load low.** Reveal complexity only when needed (Hick's Law overlap).

---

### 15. Cognitive Load
> *The amount of mental resources needed to understand and interact with an interface.*

**Apply it in web apps:**
- **Minimize extraneous load.** Remove decorative elements that don't aid understanding. Avoid gratuitous animations.
- **Manage intrinsic load.** Complex tasks inherently require mental effort — support them with wizards, previews, tooltips, and examples.
- **Reduce germane (processing) load through familiarity.** Use patterns users already know (Jakob's Law) so they don't waste cognitive resources learning your interface.
- **One concept per screen when possible.** Settings pages organized by category, not a flat list of 50 toggles.

```tsx
// ✅ Good: Focused, low cognitive load per step
const steps = [
  { id: 'account',  title: 'Create Account',   fields: ['email', 'password'] },
  { id: 'profile',  title: 'Your Profile',     fields: ['name', 'avatar'] },
  { id: 'prefs',    title: 'Preferences',      fields: ['theme', 'notifications'] },
];

// ❌ Bad: Everything at once — high cognitive overload
function MassiveForm() {
  // 25 fields, 5 sections, conditional logic, all visible...
}
```

---

### 16. Chunking
> *Individual pieces of an information set are broken down and then grouped together in a meaningful whole.*

**Apply it in web apps:**
- **Group navigation items under headings.** "Account", "Billing", "Support" instead of 15 flat links.
- **Format data for scanning.** Phone numbers, dates, addresses — use visual chunking.
- **Card grids chunk content.** 12 blog posts → 3 rows of 4 cards, each card a chunk.
- **Breadcrumb paths are chunks.** `Home > Products > Category > Item` helps users maintain spatial memory.

---

### 17. Working Memory
> *A cognitive system that temporarily holds and manipulates information needed to complete tasks.*

**Apply it in web apps:**
- **Never ask users to recall data from a previous step without showing it.** "Step 3 of 3" should summarize choices from Steps 1 & 2.
- **Persist input values.** If a user navigates away and back, their draft should still be there.
- **Show system state visibly.** Is the save happening? Did it succeed? What's left to do?
- **Multi-step flows need persistent progress indicators.**

---

### 18. Serial Position Effect
> *Users have a propensity to best remember the first and last items in a series.*

**Apply it in web apps:**
- **Put the most important item first and the most important action last.** In a nav menu, the most-used link goes first. In a form, the primary CTA is the final button.
- **Pricing tables: place recommended plan first or last** (or highlight it via Von Restorff).
- **In lists of equal importance, accept that middle items will be remembered least.** Consider if ordering matters for your use case.
- **Onboarding: start strong (first impression matters) and end strong (Peak-End Rule overlap).**

---

## CATEGORY 5: Emotion & Behavior

### 19. Aesthetic-Usability Effect
> *Users often perceive aesthetically pleasing design as design that's more usable.*

**Apply it in web apps:**
- **Invest in visual polish — it's not just cosmetic.** Users forgive minor usability issues in beautiful interfaces.
- **Maintain a cohesive design system.** Consistent typography, color, spacing, and iconography create aesthetic coherence.
- **But beware: beauty can mask usability problems.** During testing, users may rate a pretty-but-broken interface highly. Test functionality separately from aesthetics.
- **First impressions form in ~50ms.** Above-the-fold visual quality sets the tone for the entire interaction.

**Practical checklist:**
- [ ] Consistent type scale (heading/body/caption sizes)
- [ ] Harmonious color palette (use a generator tool)
- [ ] Adequate whitespace (don't fear empty space)
- [ ] Crisp iconography (one icon set, one style)
- [ ] Smooth micro-interactions (hover/focus/press states)
- [ ] Responsive layout that doesn't break at any viewport

---

### 20. Peak-End Rule
> *People judge an experience largely based on how they felt at its peak and at its end.*

**Apply it in web apps:**
- **Design delightful peak moments.** The moment a user completes a key task — celebrate it. Success screens, confetti, meaningful copy.
- **End every flow on a high note.** Checkout complete? Show a warm confirmation with next steps. Form submitted? Acknowledge with personality (Mailchimp's "High Five").
- **Negative peaks linger longer than positive ones.** An error at checkout hurts the brand more than a great product browse helps it. Invest in error recovery.
- **Map your user journey and identify peaks.** Intentionally design the emotional high points and the final impression.

```tsx
// ✅ Good: Strong end state
function CheckoutComplete({ order }) {
  return (
    <SuccessScreen>
      <Confetti /> {/* peak delight */}
      <Heading>Order #{order.id} confirmed!</Heading>
      <p>We'll email you at {order.email} with tracking.</p>
      <CTA href="/orders">View Order Details</CTA> {/* clear next step */}
    </SuccessScreen>
  );
}

// ❌ Bad: Abrupt, cold end
function CheckoutCompleteBad() {
  return <div>Thank you. Order received.</div>; /* dead end */}
}
```

---

### 21. Zeigarnik Effect
> *People remember uncompleted or interrupted tasks better than completed tasks.*

**Apply it in web apps:**
- **Show incomplete progress prominently.** Profile completion: "Your profile is 75% complete." Upload queue: "3 of 8 files remaining."
- **Use partial progress to motivate completion.** Endowed progress effect: start progress bars slightly filled (e.g., sign up gives instant 10% toward profile completion).
- **Save drafts automatically.** Let users leave and come back — the incomplete task creates return motivation.
- **Don't hide in-progress state.** Show saved drafts, abandoned carts, unfinished onboarding as re-entry points.

```tsx
// ✅ Good: Visible progress drives completion
function ProfileCompleteness({ percent }) {
  return (
    <Card>
      <ProgressBar value={percent} />
      <p>Your profile is {percent}% complete</p>
      {percent < 100 && (
        <Link to="/settings/profile">Complete your profile →</Link>
      )}
    </Card>
  );
}
```

---

### 22. Goal-Gradient Effect
> *The tendency to approach a goal increases with proximity to the goal.*

**Apply it in web apps:**
- **Show progress that accelerates perceptually.** As users get closer to goal completion, make progress feel faster (smaller remaining steps, larger progress increments).
- **Loyalty programs use this.** "Only 2 more purchases until Gold!" is more motivating than "10 purchases to reach Gold."
- **Break large goals into milestones.** Instead of one big "complete setup" goal, show: "Step 1 ✓ Step 2 ✓ Step 3 → almost there!"
- **Onboarding completion bars** that fill faster near the end increase finish rates.

---

### 23. Flow
> *The mental state in which a person performing some activity is fully immersed in energized focus, full involvement, and enjoyment.*

**Apply it in web apps:**
- **Match challenge to skill level.** Novices get guided flows; experts get keyboard shortcuts and power-user features.
- **Remove friction from core tasks.** For a writing app: the writing experience should be distraction-free. For a coding IDE: code, run, debug should be seamless.
- **Provide immediate feedback loops.** Every action produces a visible response (Doherty Threshold). This maintains the flow state.
- **Don't interrupt flow with unnecessary modals, upsells, or notifications.** Save non-critical communication for natural breaks.

---

### 24. Cognitive Bias
> *A systematic error of thinking that influences our perception and decision-making.*

**Apply it in web apps:**
- **Design for bias, don't fight it blindly.** Users anchor on the first price they see (anchoring bias). They prefer default options (status quo bias). They follow social proof (bandwagon effect).
- **Use ethical persuasion:**
  - Social proof: "Joined by 10,000+ developers"
  - Scarcity (genuine only): "3 spots left"
  - Anchoring: Show original price crossed out next to sale price
  - Defaults: Pre-select the recommended option
- **Avoid dark patterns.** Fake scarcity, forced continuity, confirmshaming — these exploit bias unethically and destroy trust.

---

### 25. Choice Overload (Paradox of Choice)
> *The tendency for people to get overwhelmed when presented with a large number of options.*

**Apply it in web apps:**
- **Curate, don't catalog.** Present 3–5 options, not 50. Use "See all" for power users who want more.
- **Default to smart recommendations.** "Pick for me" buttons, AI-suggested configurations.
- **Use categorized choice architecture.** 50 options sorted into 5 categories of 10 is easier than 50 flat options.
- **Allow favoriting/comparison for complex decisions.** Don't force immediate choice — let users narrow down over time.

---

## CATEGORY 6: System Design & Robustness

### 26. Tesler's Law (Conservation of Complexity)
> *For any system there is a certain amount of complexity which cannot be reduced.*

**Apply it in web apps:**
- **Complexity must live somewhere — either in the code or in the user's brain.** Your job as a designer/developer is to absorb as much complexity as possible so the user doesn't have to.
- **Smart defaults absorb complexity.** Instead of asking users to configure 10 settings, pick good defaults and let them override if needed.
- **Don't oversimplify to the point of abstraction.** Sometimes a complex problem needs a nuanced solution. Hiding all complexity behind a single "Auto" button that doesn't work well is worse than exposing thoughtful controls.
- **Progressive disclosure is the answer.** Simple surface → advanced options available for those who need them.

**Code-level application:**
```tsx
// ✅ Good: Complexity absorbed by the system
<SmartInput
  type="date"
  label="When?"
  // Handles parsing, timezone, validation, formatting
  // User just picks a date
/>

// ❌ Bad: Complexity dumped on the user
<input
  type="text"
  label="Enter date in ISO 8601 format with timezone offset..."
  pattern="^\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}..."
  placeholder="2024-01-15T14:30:00+00:00"
/>
```

---

### 27. Postel's Law (Robustness Principle)
> *Be liberal in what you accept, and conservative in what you send.*

**Apply it in web apps:**
- **Accept varied user input gracefully.**
  - Phone numbers: accept `(555) 123-4567`, `555.123.4567`, `5551234567`
  - Names: accept unicode, spaces, hyphens, apostrophes
  - Dates: parse multiple formats, normalize internally
  - Search: tolerate typos, fuzzy match
- **Output clean, consistent, valid data.** Normalize before storing. Validate before sending to APIs.
- **Provide forgiving error recovery.** "Did you mean...?" instead of "Invalid input."
- **Graceful degradation.** If a feature fails, the core functionality should still work.

```tsx
// ✅ Good: Liberal input, conservative output
function PhoneInput({ value, onChange }) {
  return (
    <input
      value={value}
      onChange={(e) => {
        // Accept: digits, spaces, dashes, parens, plus
        const raw = e.target.value.replace(/[^\d+\-\s().]/g, '');
        onChange(raw); // store normalized
      }}
      placeholder="(555) 123-4567"
    />
  );
}

// Output always normalized:
function formatForAPI(phone) {
  return phone.replace(/\D/g, ''); // "+1 (555) 123-4567" → "15551234567"
}
```

---

### 28. Occam's Razor
> *Among competing hypotheses that predict equally well, the one with the fewest assumptions should be selected.*

**Apply it in web apps:**
- **Fewer assumptions in UX = simpler explanation for user behavior.** If users aren't clicking a button, the simplest explanation is usually: it doesn't look clickable, it's poorly positioned, or the label is unclear — not "users don't understand our revolutionary paradigm."
- **Prefer the simpler solution given equal outcomes.** Two approaches both work? Choose the one with fewer moving parts, fewer concepts for the user to learn, fewer edge cases.
- **Avoid over-engineering.** Not every screen needs an A/B test. Not every interaction needs an animation. Not every form needs real-time validation.

---

### 29. Parkinson's Law
> *Any task will inflate until all of the available time is spent.*

**Apply it in web apps:**
- **Design for speed.** Auto-save, keyboard shortcuts, templates, bulk operations — reduce time-to-completion.
- **Set implicit deadlines.** Progress bars, step counts ("Step 2 of 4"), estimated completion times create time pressure that focuses users.
- **Remove unnecessary steps.** Every extra field, every extra click, every extra page is an opportunity for Parkinson's inflation.
- **Default-filled forms.** Pre-populate what you can (from user data, context, location).

---

## CATEGORY 7: Accessibility Note

All laws must be applied **alongside accessibility best practices**:

- **Von Restorff Effect:** Don't rely solely on color; combine with size, weight, shape, text
- **Fitts's Law:** Large targets help motor-impaired users too
- **Doherty Threshold:** Reduced motion preference (`prefers-reduced-motion`) for animations
- **Miller's Law / Cognitive Load:** Screen reader users benefit even more from chunking and simplification
- **Postel's Law:** Assistive technology compatibility is part of "liberal in what you accept"

---

## UX Review Checklist (Web Apps)

Run through this when reviewing any UI:

### Interaction
- [ ] Touch targets ≥ 44×44px (Fitts's Law)
- [ ] Feedback within 400ms of user action (Doherty Threshold)
- [ ] Primary actions are easiest to reach (Fitts's Law)

### Choices & Navigation
- [ ] No more than 5–9 items in any single choice set (Miller's Law, Hick's Law)
- [ ] Uses conventional patterns for common interactions (Jakob's Law)
- [ ] Progressive disclosure for complex features (Hick's Law, Tesler's Law)

### Visual Design
- [ ] Related items grouped by proximity (Proximity)
- [ ] Consistent styling indicates relationship (Similarity)
- [ ] Clear container boundaries define regions (Common Region)
- [ ] One primary emphasis per screen (Von Restorff Effect)
- [ ] Clean, minimal visual noise (Prägnanz, Cognitive Load)

### Content & Memory
- [ ] Information chunked into scannable groups (Chunking, Miller's Law)
- [ ] Cross-step state is visible (Working Memory)
- [ ] Important items at start/end of lists (Serial Position)

### Flows & Emotion
- [ ] Delight moments at task completion (Peak-End Rule)
- [ ] Incomplete progress is visible (Zeigarnik Effect)
- [ ] Strong finish to every user flow (Peak-End Rule)
- [ ] Polished, coherent visual design (Aesthetic-Usability)

### Robustness
- [ ] Input accepts varied formats (Postel's Law)
- [ ] Smart defaults reduce complexity (Tesler's Law)
- [ ] Errors are recoverable with clear guidance (Postel's Law, Paradox of Active User)

---

## References

- [lawsofux.com](https://lawsofux.com) — Jon Yablonski's complete collection
- [Nielsen Norman Group (nngroup.com)](https://www.nngroup.com/) — Deep-dive research articles
- *Designing with the Mind in Mind* — Jeff Johnson
- *100 Things Every Designer Needs to Know About People* — Susan Weinschenk
