# Modal, Bottom Sheet or Popover: How to Choose an Overlay (With Real UI Examples)

## SEO Metadata

| Field | Value |
|---|---|
| **Article title** | Modal, Bottom Sheet or Popover: How to Choose an Overlay (With Real UI Examples) |
| **Meta title** (55 chars) | Modal Animation vs Bottom Sheet: Pick the Right Overlay |
| **Meta description** (134 chars) | Compare modal animation, bottom sheets, popovers and drawers with real UI examples, and learn why heavier overlays need clearer exits. |
| **Slug** | /blog/overlay-ui |
| **Canonical URL** | https://www.ripplix.com/blog/overlay-ui |
| **Focus keyword** | modal animation |
| **Primary keyword** | modal animation |
| **Secondary keywords** | bottom sheet animation, popover animation, pop up animation, overlay animation, drawer animation, side panel animation |
| **Related keywords** | modal animation css, ui modal, animated modal, modal open animation, bottom sheet ui animation, animated bottom sheet, popover ui animation, animated popover, dropdown menu animation, pop up ui animation, animated pop up, overlay ui animation, animated overlay, drawer ui animation, animated drawer, side panel ui animation, animated side panel, accordion expand animation, card animation, slide up animation, modal vs bottom sheet, bottom sheet vs dialog, react native modal animation, framer motion modal animation |
| **Search intent** | Informational, with a comparison and decision angle. The reader is a designer or front-end developer choosing between overlay types and wants to see how each one actually moves before building it. |
| **Article category** | Interaction Design / UI Patterns |
| **Collection family** | Components: operating the UI |

---

## Keyword Research Summary

**Tools used:** Ubersuggest (US, locId 2840) for volume, SEO difficulty and intent. KeywordTool.io guest access for autocomplete suggestions, questions and prepositions. Guest access returns keyword text only, so terms sourced there are marked as suggested rather than measured.

### Researched (with data)

| Keyword | Volume (US/mo) | SEO difficulty | Notes |
|---|---|---|---|
| modal animation | 30 | 41 | Primary. Intent is informational. Outline listed 20/mo KD 23; Ubersuggest US now shows 30/mo KD 41, so difficulty is higher than the brief assumed. |
| bottom sheet animation | 50 | 27 | Highest volume and lowest difficulty in the whole cluster. Mixed informational and transactional intent. The brief asked to validate this term; it validates well and is the best secondary bet. |
| overlay animation | 70 | 40 | **Caution.** Volume is real but the SERP intent is video editing, not UI. Suggestions returned stream overlay animation, CapCut overlay animation, Twitch overlay animation, facial overlay animation. Do not optimise the Overlay section for this term in isolation. Use overlay ui animation instead. |
| react native modal animation | 30 | 30 | Implementation long-tail, informational. |
| framer motion modal animation | 10 | 5 | Very low difficulty. Good long-tail entry point. |
| figma drawer animation | 10 | 13 | Design-tool long-tail for the drawer section. |
| shopify cart drawer animation | 0 | 4 | Near zero volume, listed only to show the drawer term is thin. |

### Researched (suggestions, no volume on guest access)

Comparison intent, which matches this article's angle directly: modal vs bottom sheet, bottom sheet vs modal, bottom sheet vs dialog, sheet vs modal, ios modal vs bottom sheet, persistent bottom sheet vs modal bottom sheet, react native bottom sheet vs modal.

Question intent, usable as FAQ seeds: what is modal animation, what is a bottom sheet, why modal is bad, why avoid modals, are modals accessible, are modal windows accessible, are modals bad.

### Conclusions that shaped the article

1. The brief's note was right. This is a low-demand cluster in raw volume. The value is not head-term ranking, it is topical coverage plus the comparison angle, which has real suggestion volume ("modal vs bottom sheet", "bottom sheet vs dialog"). That is why the article is built as a ranked comparison with a weight table, not as seven unconnected definitions.
2. "overlay animation" is contaminated by video-editing intent. The Overlay section uses "overlay ui animation", "scrim" and "fullscreen layer" language so it does not chase the wrong SERP.
3. Accessibility questions ("are modals accessible", "why avoid modals") show up strongly in autocomplete, so focus trapping, escape to close and reduced motion are covered in the body and in the FAQ rather than being left out.
4. Framework long-tails (React Native, Framer Motion, Compose, Flutter) have very low difficulty. Worth separate articles later rather than stuffing into this one.
5. "drawer animation" and "side panel animation" returned no standalone US volume. They stay as section-level secondaries, not as campaign targets. This answers the brief's request to validate the drawer terms: bottom sheet validates, drawer does not.

### Not used

Rejected as irrelevant despite volume: stream overlay animation, Twitch overlay animation, CapCut overlay animation, text overlay animation, facial overlay animation, HUD overlay animation, modal sheets vs cotton, insulated cookie sheet vs regular. All are different industries or fabric and bedding queries that share the words only.

---

## TL;DR

- Seven overlay patterns, one job: put something on top of the page without navigating away.
- Every overlay interrupts. The only real questions are how much of the page it covers and how the user gets back out.
- Ranked by weight: popover is lightest, full modal is heaviest. The heavier the overlay, the more obvious the exit has to be.
- Twenty one real UI recordings from products like HubSpot CRM, Airbnb, Duolingo ABC, Monday, Ideogram AI and Wrike, so you can see the timing instead of guessing it.
- Pick the pattern by reach and weight first, then tune the animation. Motion cannot fix a wrong choice.

---

## Introduction

A modal animation is the most interruptive thing you can add to a screen, and that is exactly why people argue about it. This article covers the full overlay and layer group: seven ways to put something on top of the current page without sending the user somewhere else. Modal, bottom sheet, popover, pop up, overlay, drawer and side panel. Each one is a different amount of interruption, and each one has a different exit.

This is for product designers and front-end developers who are picking a pattern for a real screen. Maybe you need a confirmation before a delete. Maybe you need filters that do not lose the user's scroll position. Maybe you just need a small menu attached to a button. These are not interchangeable choices. A centered dialog on a mobile screen sits far from the thumb. A popover used for something critical gets dismissed by accident. The pattern you choose sets the user's expectation of how serious the thing is.

The useful way to think about this group is weight. Rank the seven from a tooltip-light popover up to a full-screen modal that blocks everything. The heavier the overlay, the more obvious the exit has to be. A popover can close on outside click and nobody complains. A full modal needs a visible close control, an escape key, and usually a backdrop click too. Every example below is a real recording from a shipped product, with the actual interaction tags from the Ripplix library, so you can study the timing and easing instead of inventing them.

---

## 1. Modal

### What a modal is and when to use it

A modal is a centered layer that blocks the page and demands a yes or no. It takes focus, it dims what is behind it, and the user cannot continue until they deal with it. Use it only when the decision truly cannot wait: destructive confirmations, required input before a flow continues, a legal acceptance. If the content is only helpful rather than blocking, you almost certainly want something lighter from this list.

The motion does real work here. A modal that appears instantly feels like a system error. A modal that scales up from about 0.95 with a short fade, usually in the 150 to 250 millisecond range, reads as a deliberate layer arriving. The backdrop fade should run with it, not after it. For a [modal animation](https://www.ripplix.com/interaction/modal-ui-animations) the exit matters as much as the entrance, because a slow dismiss makes the whole product feel heavy. Most teams build this with a transform and opacity pair so the browser can keep it on the compositor, which is why a typical modal animation css implementation animates `transform: scale()` and `opacity` rather than width, height or top. On the accessibility side, a ui modal needs focus trapping, a labelled dialog role, and escape to close. An animated modal that nobody can escape from with a keyboard is not finished.

Designers commonly reach for modals in CRMs, dashboards, settings screens and checkout flows. The pattern is strongest when the decision is short. The moment your modal starts holding a multi step form, it is usually a sign the content deserves its own page or a side panel.

### Video examples

**Action Modal Dialog (HubSpot CRM)**

A web app modal from HubSpot CRM, in the business software category. The recorded interaction combines a modal with expand, flip and loading states, so the dialog does not just appear, it grows into place and then shows its own in dialog loading while the CRM fetches content. This is a good reference for a modal open animation where the layer arrives before its data does, which is the normal case in any real back office tool.

https://www.ripplix.com/library/popup-hubspot-crm-business

**Agency Modal Overlay (Visual Domain)**

A website modal from Visual Domain, a creative agency site. The tags here are the textbook set: tap, fade, overlay and scale. A tap triggers the layer, the backdrop overlay fades in, and the dialog scales to full size. If you only study one modal animation to learn the baseline timing, use this one. It shows the scrim and the panel moving as a pair, which is the detail most hand built modals get wrong.

https://www.ripplix.com/library/popup-visual-domain-agency

**Ai Assistant Modal Flow (Fabulous)**

A mobile app flow from Fabulous, in the wellness category. This one sits on the border between popover and modal, and the library tags say so: popover, tap, glow, modal, AI assistant, text animation and loading. The AI coach layer opens on tap, holds a glow treatment while it thinks, then animates its text in. Useful as a modal open animation example for anything AI driven, where the layer has to communicate waiting without blocking the user's sense of progress.

https://www.ripplix.com/library/popover-text-animation-fabulous-wellness-mobile-app

---

## 2. Bottom Sheet

### What a bottom sheet is and when to use it

A bottom sheet is a panel that rises from the bottom edge of the screen. It exists because of hands. On a phone, a centered modal puts its buttons in the middle of the display, far from the thumb, while a sheet puts them exactly where the thumb already is. That is the whole argument, and it is a good one. Use a sheet for mobile confirmations, option pickers, share menus, filters and anything the user will tap more than once.

A bottom sheet animation is a slide on the Y axis, and the easing is what sells it. A sheet that slides up with a decelerating curve feels like it is settling into place. A linear slide feels mechanical. Many sheets also support drag, which means you are not only animating an entrance, you are handing the sheet's position over to the user's finger and then deciding what happens on release: snap open, snap to a half height detent, or dismiss. That velocity based snap is where most bottom sheet ui animation work actually goes. A good [bottom sheet animation](https://www.ripplix.com/interaction/bottom-sheet-ui-animations) keeps the drag handle visible, because the handle is what tells the user the panel is draggable at all.

On weight, a sheet is lighter than a modal but heavier than a popover. It usually keeps a dimmed overlay behind it, and because it covers the bottom of the screen, the exit needs to be either the handle, a swipe down, or a clear close. An animated bottom sheet with no swipe down and no visible close is a trap.

### Video examples

**Bottom Sheet Animation (Asana)**

A mobile app sheet from Asana, in the business category. The interaction set is bottom sheet, toggle, drag and flip, which makes it the clearest drag reference in this group. The sheet holds toggles the user flips in place, and the sheet itself can be dragged rather than only tapped open. Study this one for how a sheet keeps its content interactive while the panel is still under the user's finger.

https://www.ripplix.com/library/bottom-sheet-toggle-asana-business-mobile-app

**Bottom Sheet Announcement (Airbnb)**

A mobile app sheet from Airbnb, in travel. Tagged as bottom sheet, loop, tap, modal and confirmation. This is the announcement use case: the sheet carries a looping piece of motion as its hero content, then a confirmation action to dismiss. It is a good example of a bottom sheet animation doing a modal's job, with one decision and one clear way out, but placed where the thumb can reach it.

https://www.ripplix.com/library/bottom-sheet-loop-airbnb-travel-mobile-app-555039

**Bottom Sheet Card Slider (Headspace)**

A mobile app sheet from Headspace, in healthcare. Tagged bottom sheet, carousel, slide up and swipe. Here the sheet slides up and then becomes a horizontal surface: cards inside it are swiped sideways. Two gesture axes on one panel is harder than it looks, because vertical drag for the sheet and horizontal swipe for the carousel have to be told apart cleanly. Worth copying if you are building any animated bottom sheet that holds a carousel.

https://www.ripplix.com/library/bottom-sheet-headspace-health-and-wellness

---

## 3. Popover

### What a popover is and when to use it

A popover is a small layer tied to the element that opened it. It is anchored, which is the defining property: its position is computed from the trigger, and it flips or shifts when it would otherwise run off the viewport edge. Use it for contextual actions, account menus, filter controls, date pickers and small bits of secondary information. Do not use it for anything the user must not miss, because a popover's exit is usually an outside click, and outside clicks happen by accident all the time.

A popover animation should be fast and should come from somewhere. Scale from the trigger's corner, origin set to the anchor side, 120 to 180 milliseconds, light fade. If the motion is slow, the popover feels like a modal and the user waits for it. Because popovers behave like menus in practice, a lot of the search demand sits under dropdown menu animation rather than under the popover term itself, and the implementation concerns are the same: anchoring, collision flipping, keyboard navigation between items, and an escape path. A well built [popover animation](https://www.ripplix.com/interaction/popover-ui-animations) also respects reduced motion, dropping to a plain opacity change.

In weight terms this is the lightest real overlay in the group. It usually has no scrim at all, which is correct: the page behind it is not inert, it is just waiting. That is why a popover ui animation needs almost no ceremony, and why adding a dark backdrop to one makes it feel wrong immediately.

### Video examples

**Action Menu Popover (Atoms)**

A mobile app popover from Atoms, in productivity tools. Tagged popover, tap, overlay, morph and scale. The morph tag is the interesting part: the trigger does not just spawn a separate panel, it transforms into the action menu. If you want a dropdown menu animation that feels connected to its button rather than dropped on top of it, this is the technique, and it is much more convincing on mobile where the trigger and the menu are close together.

https://www.ripplix.com/library/popover-atoms-productivity-tools-mobile-app

**Auth Popover Menu (Expedia)**

A web app popover from Expedia, in transportation. Tagged popover, tap, button and show or hide. This is the plain, correct version of the pattern: a header button opens an account menu, the menu hides on dismiss, no scrim, no drama. Use it as the reference for a dropdown menu animation on a dense commercial header, where the popover has to open fast because it is competing with search and booking controls around it.

https://www.ripplix.com/library/pop-over-expedia-travel-and-tourism

**Date Range Popover Calendar (Monday)**

A web app popover from Monday, in productivity tools. Tagged popover, drag, calendar and select. This is a popover that holds a real interactive widget, not just a list of links. The user drags across a calendar to select a range inside the anchored layer. It shows the main constraint of the pattern: once a popover contains a drag interaction, your outside click dismissal has to be careful not to fire mid drag. A good example of a dropdown menu animation pattern stretched to its useful limit.

https://www.ripplix.com/library/popover-monday-productivity

---

## 4. Pop up

### What a pop up is and when to use it

Pop up is the catch all name for an interruption the user did not ask for. The user did not tap anything, or they tapped something small and got something large. Because the layer is unrequested, the motion's whole job is to make it feel less like an ambush. In practice teams use the label for a wide mix: select sheets, confirmation layers, promotional offers, contextual action sheets.

A pop up animation should be slightly slower and softer than a popover, with a short fade on the scrim before the panel finishes arriving. That tiny lead on the backdrop is what prepares the eye. Appearing with a hard snap and a bounce reads as aggressive, which is a real conversion problem for anything promotional. A [pop up animation](https://www.ripplix.com/interaction/pop-up-ui-animations) also needs the most obvious exit in this whole group, because the user has no mental model of why the layer is there. One close control, hit area large enough for a thumb, plus backdrop dismiss.

One honest note on vocabulary. On mobile, most things called pop ups are built as bottom sheets, and the three recordings below show exactly that: all three are bottom edge panels. So if you are choosing an implementation, search for the sheet mechanics, and keep pop up as the name you use with stakeholders rather than the name you use in code. An animated pop up on mobile is usually a sheet wearing a different label.

### Video examples

**Calculator Palette Drawer (Acute Calculator)**

A mobile app pop up from Acute Calculator, in utilities. Tagged pop up, slide up, toggle, show or hide, slide and drawer. A control palette slides up from the bottom edge and can be toggled away again. This is a bottom sheet animation in structure, used for tool switching rather than for a decision, which is a nice reminder that a bottom edge panel does not have to carry a yes or no.

https://www.ripplix.com/library/pop-up-acute-calculator-utilities-mobile-app

**Confirmation Bottom Sheet (Duolingo ABC)**

A mobile app pop up from Duolingo ABC, in education. Tagged select, pop up, tap, bottom sheet, overlay, slide up and confirmation. This is the clearest confirmation example in the group: a selection triggers a sheet, the scrim dims the lesson behind it, and the user confirms. Because the audience is children, the motion is unusually generous, which is worth studying as a bottom sheet animation tuned for a specific user group rather than for speed.

https://www.ripplix.com/library/select-pop-up-duolingo-abc-education-mobile-app

**Contextual Action Sheet (Craft)**

A mobile app pop up from Craft, in productivity tools. Tagged dropdown, pop up, tap, text animation, bottom sheet, slide up and show or hide. Here a dropdown style trigger produces a bottom sheet of contextual actions, with the sheet's text animating in rather than appearing flat. Good reference for a bottom sheet animation inside a document editor, where the action list changes depending on what is selected.

https://www.ripplix.com/library/dropdown-pop-up-craft-productivity-tools-mobile-app

---

## 5. Overlay

### What an overlay is and when to use it

In this group, overlay means the layer that sits over the content rather than the panel itself. Most often that is the darkened scrim behind a modal or a sheet. Its fade is what tells the eye that the page underneath is temporarily inert. Get the scrim wrong and the whole interaction feels broken even when the panel is perfect.

Three practical rules. First, the scrim and the panel should animate together, with the scrim leading by a few frames at most. Second, keep it subtle: somewhere around 40 to 60 percent black is usually enough, and a blur behind it can replace some of that darkness. Third, the scrim is a dismissal surface for light overlays and must not be one for destructive confirmations. Beyond the scrim, overlay also covers full screen layers that cover the page without being a dialog: a fullscreen navigation menu, a loading state over a canvas, a heads up layer in a game. A good [overlay animation](https://www.ripplix.com/interaction/overlay-ui-animations) is mostly opacity work, which is cheap to render, so an overlay ui animation is one of the few places you can be generous with duration without hurting performance.

Where designers use it: behind every pattern above, plus as a standalone layer in media apps, AR interfaces and agency sites where a fullscreen menu replaces the page for a moment. An animated overlay is also the standard way to block input during a slow action without moving the user off the screen.

### Video examples

**Ar Scope Reticle Overlay (Aim XR)**

An AR and VR overlay from Aim XR, in the game category. Tagged overlay, image, 3D, morph, card and parallax. This is the heads up display version of the pattern: a reticle and card layer sits over a live 3D view, morphing and parallaxing against the scene behind it instead of dimming it. A useful card animation reference too, because the floating card has to stay readable over moving content, which is a contrast problem a flat scrim never has to solve.

https://www.ripplix.com/library/overlay-aim-xr-game-vrmp4

**Action Loading Blur Overlay (Dream.ai)**

A web app overlay from Dream.ai, in AI. Tagged tap, overlay, filter, blur and loading. A tap starts a generation, and a blurred overlay covers the canvas while the model works. This is the best example here of a scrim doing more than dimming: the blur communicates that the content underneath is still there but not ready. Use it as a template for any overlay animation that has to cover an unpredictable wait.

https://www.ripplix.com/library/loader-dreamai-ai-web-appmp4

**Agency Fullscreen Menu Overlay (Reform Collective)**

A website overlay from Reform Collective, a creative agency. Tagged menu, hover, hero, reveal and overlay. Here the overlay is the navigation: a fullscreen layer reveals over the hero, with hover states inside it. Note that this one is a reveal rather than an accordion style expand, so treat it as the fullscreen menu reference in this group. It shows why heavy overlays need an unmissable close, since there is no page edge left to click.

https://www.ripplix.com/library/menu-hover-reform-collective-agency

---

## 6. Drawer

### What a drawer is and when to use it

A drawer slides in from a side edge and holds navigation, filters, history or details without leaving the current screen. It is the right answer when the content is a companion to what is on screen rather than a replacement for it. Mobile navigation drawers, cart drawers, filter drawers and history panels in AI tools are all the same pattern.

A drawer animation is a slide on the X axis plus a scrim, and the main decision is whether the drawer overlays the content or pushes it. Overlaying is simpler and faster. Pushing reflows the layout, which costs more and can feel laggy on a long page. For a [drawer animation](https://www.ripplix.com/interaction/drawer-ui-animations) built in CSS, animate `transform: translateX()` rather than `left` or `width`, keep it in the 200 to 300 millisecond range, and give the exit a slightly shorter duration than the entrance so dismissal feels responsive. Edge swipe support is a nice addition on mobile but needs care, because it competes with browser back gestures.

On weight, a drawer sits between a sheet and a modal. It covers a significant part of the screen, so it needs a scrim and a clear close, but it does not demand a decision, so backdrop dismiss is usually fine. A drawer ui animation that collapses to a narrow rail instead of disappearing completely is often the better choice in desktop tools, because the rail keeps the control discoverable. That is the point where an animated drawer starts turning into a side panel.

### Video examples

**Canvas History Drawer (Ideogram AI)**

A web app drawer from Ideogram AI, in AI. Tagged drawer, tap, list, expand and story. A tap opens a history list beside the canvas, expanding into place rather than appearing all at once. This is the companion content case: the user needs their previous generations visible without losing the canvas, so the expand animation keeps both contexts alive at the same time.

https://www.ripplix.com/library/drawer-ideogram-ai-ai-web-appmp4

**Collapsible Side Drawer (SeaArt AI)**

A web app drawer from SeaArt AI, in AI. Tagged drawer, expand, collapse, tap, reveal and accordion. The accordion tag is accurate here: the drawer's sections expand and collapse inside the panel, so you get two levels of motion, the drawer itself and the groups within it. A strong accordion expand animation reference, and the clearest example of a drawer that collapses rather than closes.

https://www.ripplix.com/library/drawer-expand-collapse-seaart-ai-ai-web-appmp4

**Header Search Drawer (Populous)**

A website drawer from Populous, in the enterprise category. Tagged search, dropdown, hover, button, tap, overlay, drawer and collapse. A header search expands into a drawer with an overlay behind it, then collapses back. Worth studying for the hover to tap sequence: the control signals on hover before it commits on tap, which makes the expand animation feel predictable on a corporate site where the search is not the main action.

https://www.ripplix.com/library/search-dropdown-button-hover-populous-corporatemp4

---

## 7. Side Panel

### What a side panel is and when to use it

A side panel is docked to one side of the layout and expands or collapses in place, rather than floating over the content. That is the real difference from a drawer: a panel is part of the layout, so it has no scrim, nothing behind it goes inert, and the user can keep working while it is open. Use it for detail views in dashboards, task details beside a kanban board, properties panels, inspectors and persistent navigation in desktop apps.

A side panel animation is mostly a width or transform change plus a content reflow, and the reflow is the hard part. When the panel opens, the main content gets narrower, and if your grid snaps while the panel is still sliding, the whole thing looks broken. Common fixes: animate the panel and the content area with the same duration and easing, avoid animating `width` where you can use a transform and a fixed track instead, and fade the panel's inner content in slightly after the panel geometry has settled. For a [side panel animation](https://www.ripplix.com/interaction/side-panel-ui-animations) in a data heavy tool, also remember that virtualized lists inside the panel may need to recalculate after the transition ends, not during it.

This is the lightest heavy pattern in the group, in the sense that it takes a lot of space but interrupts very little. Because it does not block anything, the exit can be a simple collapse toggle. A side panel ui animation that remembers its collapsed state between sessions is usually what users expect, and an animated side panel that collapses to an icon rail keeps the feature visible without spending the width.

### Video examples

**Collapsible Side Panel (Wrike)**

A web app side panel from Wrike, in business software. Tagged side panel, tap, reveal, expand, accordion and toggle. A toggle expands the panel and the groups inside it behave like an accordion. This is the accordion expand animation case inside a docked panel: two nested levels of expand and collapse, which means your durations have to be different or the motion reads as one confused movement.

https://www.ripplix.com/library/side-panel-wrike-business-5714

**Kanban Side Panel Reveal (Wrike)**

A second web app recording from Wrike, also in business software, but a different interaction. Tagged side panel, tap, reveal, card, select and collapse. Here selecting a card on a kanban board reveals its detail panel at the side, and collapsing returns the board to full width. This is the pattern most project tools converge on, and it is the best argument for side panels over modals: the board stays visible, so the user keeps their place.

https://www.ripplix.com/library/side-panel-wrike-business

**Slide Over Side Panel (Chase)**

A web app side panel from Chase, in fintech. Tagged side panel, tap, fade, button, overlay and confirmation. Note the overlay tag: this one slides over the content with a scrim and ends in a confirmation, so it behaves closer to a drawer than to a docked panel. That is a reasonable choice in banking, where the panel is carrying a decision and the product wants the rest of the screen to go quiet first.

https://www.ripplix.com/library/side-sheet-drawer-chase-fintech

---

## How to choose: a quick ranking by weight

Use this order when you are stuck. Lightest first.

1. **Popover.** Anchored, no scrim, outside click closes it. Contextual actions only.
2. **Side panel.** Large but docked, no scrim, nothing blocked. Details and inspectors.
3. **Drawer.** Slides over from an edge with a scrim. Navigation, filters, history.
4. **Bottom sheet.** Mobile first, thumb reachable, draggable. Options and confirmations.
5. **Pop up.** Unrequested, so it needs the softest entrance and the clearest close.
6. **Overlay.** The scrim or fullscreen layer itself. Carries the weight of whatever is on top of it.
7. **Modal.** Centered, blocking, focus trapped. Only for decisions that cannot wait.

The rule that ties the list together: the heavier the overlay, the more obvious the exit has to be. If you cannot describe the exit in one sentence, the pattern is too heavy for the job.

---

## FAQ

**What is a modal animation?**

A modal animation is the motion a blocking dialog uses to arrive and leave. Usually it is a short scale and fade on the dialog paired with an opacity fade on the backdrop behind it, in the 150 to 250 millisecond range. The purpose is to show the user that a new layer has taken over the page, instead of having content appear with no explanation.

**When should I use a bottom sheet instead of a modal?**

Use a bottom sheet on mobile, especially when the user has to tap something more than once. A centered modal puts its controls in the middle of the screen, away from the thumb, while a sheet puts them at the bottom edge where the hand already is. Keep the modal for desktop, and for mobile cases where you genuinely want to block everything.

**What is the difference between a popover and a modal?**

A popover is anchored to the element that opened it and does not block the page, so it closes on an outside click. A modal is centered, blocks the page, traps focus and needs a deliberate dismissal. The practical test is whether the user is allowed to ignore the layer. If yes, use a popover animation. If no, use a modal.

**Is a drawer the same thing as a side panel?**

No. A drawer slides over the content with a scrim behind it and is meant to be closed. A side panel is docked into the layout, has no scrim, and expands or collapses in place while the user keeps working. Some products blur the line, and the Chase recording above is a good example of a side panel that behaves like a drawer because it is carrying a decision.

**What should I animate for better overlay performance?**

Stick to `transform` and `opacity` wherever you can. Animating `width`, `height`, `top` or `left` forces layout work on every frame, which is what makes a drawer animation or a side panel animation feel sticky on long pages. Also respect `prefers-reduced-motion` by falling back to a plain fade, and keep exit durations a little shorter than entrances so dismissal feels fast.

**Can I rebuild these interactions with AI coding tools?**

Yes, and that is what the library is built for. Each Ripplix animation page gives you a prompt you can paste into Cursor, Lovable, v0, Bolt or Replit to rebuild the interaction, typically around 80 to 90 percent accurate to the original recording. You still need to check accessibility yourself: focus trapping, escape to close and reduced motion are rarely handled well by a generated component on the first pass.

---

## Conclusion

Overlays are not seven interchangeable components, they are seven different amounts of interruption. Choose by reach and weight first: does this content belong next to the page, over one edge of it, or in front of all of it? Then make the exit match the weight you chose. A modal animation earns its interruption only when the decision truly cannot wait, and a popover stays useful only as long as it stays easy to dismiss by accident without any cost.

The fastest way to get the timing right is to watch patterns that already ship. The twenty one recordings above come from real products across web apps, mobile apps, websites and even an AR interface, so the motion in them has already survived real users. Browse the overlay and layer collections in the Ripplix animation library, find the one closest to your case, then copy the AI prompt and rebuild it in Cursor, Lovable, v0, Bolt or Replit. Start from something that works instead of guessing an easing curve.

---

## Internal Linking Suggestions

*For the CMS editor. Not part of the article narrative.*

### Already included in the article (inline anchors, one each)

| Anchor text | Destination | Section |
|---|---|---|
| modal animation | https://www.ripplix.com/interaction/modal-ui-animations | 1. Modal |
| bottom sheet animation | https://www.ripplix.com/interaction/bottom-sheet-ui-animations | 2. Bottom Sheet |
| popover animation | https://www.ripplix.com/interaction/popover-ui-animations | 3. Popover |
| pop up animation | https://www.ripplix.com/interaction/pop-up-ui-animations | 4. Pop up |
| overlay animation | https://www.ripplix.com/interaction/overlay-ui-animations | 5. Overlay |
| drawer animation | https://www.ripplix.com/interaction/drawer-ui-animations | 6. Drawer |
| side panel animation | https://www.ripplix.com/interaction/side-panel-ui-animations | 7. Side Panel |

Plus 21 library item links, one per video example, in pack order.

### Primary collection link

The seven interaction hubs above are the collection targets for this article. The modal hub (https://www.ripplix.com/interaction/modal-ui-animations) should carry the primary link weight, since modal animation is the focus keyword.

### Suggested sibling collections (not yet in the article)

Verified against the Ripplix interaction vocabulary. Add in a related links block, not inline.

| Collection | URL | Why it is related |
|---|---|---|
| Dropdown | https://www.ripplix.com/interaction/dropdown-ui-animations | Popover and pop up recordings in this pack carry dropdown tags; captures the dropdown menu animation demand. |
| Accordion | https://www.ripplix.com/interaction/accordion-ui-animations | The SeaArt AI drawer and Wrike side panel both use accordion expand behaviour inside the panel. |
| Menu | https://www.ripplix.com/interaction/menu-ui-animations | The Reform Collective fullscreen overlay is a menu pattern; natural next step for navigation overlays. |

Optional fourth, if the related block allows it: Collapse (https://www.ripplix.com/interaction/collapse-ui-animations), which pairs directly with the drawer and side panel sections.

---

## JSON-LD

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Article",
      "@id": "https://www.ripplix.com/blog/overlay-ui#article",
      "headline": "Modal, Bottom Sheet or Popover: How to Choose an Overlay (With Real UI Examples)",
      "name": "Modal, Bottom Sheet or Popover: How to Choose an Overlay (With Real UI Examples)",
      "description": "Compare modal animation, bottom sheets, popovers and drawers with real UI examples, and learn why heavier overlays need clearer exits.",
      "url": "https://www.ripplix.com/blog/overlay-ui",
      "mainEntityOfPage": {
        "@type": "WebPage",
        "@id": "https://www.ripplix.com/blog/overlay-ui"
      },
      "articleSection": "Interaction Design / UI Patterns",
      "keywords": [
        "modal animation",
        "bottom sheet animation",
        "popover animation",
        "pop up animation",
        "overlay animation",
        "drawer animation",
        "side panel animation",
        "dropdown menu animation",
        "accordion expand animation"
      ],
      "about": [
        { "@type": "Thing", "name": "Modal animation" },
        { "@type": "Thing", "name": "Bottom sheet animation" },
        { "@type": "Thing", "name": "Popover animation" },
        { "@type": "Thing", "name": "Overlay animation" },
        { "@type": "Thing", "name": "Drawer animation" },
        { "@type": "Thing", "name": "Side panel animation" }
      ],
      "isPartOf": {
        "@type": "Blog",
        "@id": "https://www.ripplix.com/blog",
        "name": "Ripplix Blog"
      }
    },
    {
      "@type": "BreadcrumbList",
      "@id": "https://www.ripplix.com/blog/overlay-ui#breadcrumb",
      "itemListElement": [
        {
          "@type": "ListItem",
          "position": 1,
          "name": "Home",
          "item": "https://www.ripplix.com/"
        },
        {
          "@type": "ListItem",
          "position": 2,
          "name": "Blog",
          "item": "https://www.ripplix.com/blog"
        },
        {
          "@type": "ListItem",
          "position": 3,
          "name": "Modal, Bottom Sheet or Popover: How to Choose an Overlay",
          "item": "https://www.ripplix.com/blog/overlay-ui"
        }
      ]
    }
  ]
}
```


---

## Final QA Checklist

### Content validation

| Check | Status | Note |
|---|---|---|
| Every pack item has its own section | PASS | 7 sections: Modal, Bottom Sheet, Popover, Pop up, Overlay, Drawer, Side Panel. |
| Items follow original pack order | PASS | Order preserved exactly as in the content pack. |
| Every video matched against all_animations.json | PASS | All 21 slugs resolved to a record. 0 missing, 0 duplicate URLs. |
| Every video description reflects its actual interaction | PASS | Written from the matched record's title, product, platform, industry and interaction tags. |
| Duplicate URLs handled honestly | PASS (N/A) | No duplicates in this pack. The two Wrike recordings are different slugs and different tag sets, and the article says so explicitly. |
| No unsupported products, platforms or features introduced | PASS | Product names corrected to the verified records where the outline used placeholders. See flags below. |
| FAQ contains 4 to 6 questions | PASS | 6 questions. |

### SEO validation

| Check | Status | Note |
|---|---|---|
| Article title short and intent-focused | PASS | States the comparison and the decision. |
| Meta title 60 characters or fewer | PASS | 55 characters. |
| Meta description 155 characters or fewer | PASS | 134 characters. |
| Both metadata fields contain the primary keyword | PASS | "Modal Animation" in the meta title, "modal animation" in the meta description. |
| Primary keyword in the introduction | PASS | First sentence of the introduction. |
| Secondary and long-tail keywords included | PASS | All six secondary hero keywords plus accessibility, performance and comparison long-tails. |
| Internal links use correct URLs | PASS | All 7 interaction hubs and all 21 library URLs taken verbatim from the pack. |
| Each required anchor appears exactly once | PASS | Verified: 1 inline link per interaction hub. |

### Structure validation

| Check | Status | Note |
|---|---|---|
| TL;DR contains 3 to 5 lines | PASS | 5 lines. |
| Introduction contains 2 to 3 short paragraphs | PASS | 3 paragraphs. |
| All item sections included | PASS | 7 of 7. |
| FAQ visible in article body | PASS | Rendered as body content, not schema only. |
| Conclusion contains 2 short paragraphs | PASS | 2 paragraphs. |
| Conclusion repeats primary keyword exactly once | PASS | Verified by count: 1. |
| Conclusion includes the Cursor, Lovable, v0, Bolt, Replit CTA | PASS | Final sentence of the second paragraph. |
| Internal Linking Suggestions section included | PASS | Separated into "already included" and "suggested". |
| JSON-LD contains Article and BreadcrumbList only | PASS | Parsed and validated. No FAQPage. |

### Writing validation

| Check | Status | Note |
|---|---|---|
| Plain, simple, founder-style English | PASS | Short sentences, practical framing, no marketing padding. |
| No fancy or unnecessary words | PASS | |
| No keyword stuffing | PASS | Each hero keyword used where it describes the pattern, not repeated for density. |
| No repetitive AI-style content | PASS | The pack's boilerplate "This is a real X UI animation recorded from Y" line was not reused 21 times. Each description is written from that record's own tags. |
| No em dashes anywhere | PASS | Full-output scan for the character returned 0 occurrences. En dashes also 0. |

### Flags for the editor

1. **Product name corrections.** The outline labelled several videos with placeholders that do not match the animation record. Corrected against all_animations.json: "Habit App AI Coach Modal" is Fabulous; "Customize home bottom sheet" is Asana; "Mobile App Travel Bottom Sheet" is Airbnb; "Mobile App Carousel Bottom Sheet" is Headspace; "action-menu-popover.mp4" is Atoms; "Account schedule popover" is Monday; "Mobile App Pop up" is Acute Calculator; "Mobile App Select Pop up" is Duolingo ABC; "Mobile App" (Pop up item, video 3) is Craft; "Web App" (Side Panel item, video 3) is Chase.
2. **One assigned video keyword was not supportable.** The Reform Collective fullscreen menu was assigned "accordion expand animation", but its record tags are Menu, Hover, Hero, Reveal, Overlay. There is no accordion behaviour in it. The description calls it a reveal and says so plainly rather than asserting an accordion.
3. **Assigned video keywords that cross categories were kept where the data supports them.** The three Pop up videos were assigned "bottom sheet animation" and all three records genuinely carry bottom sheet or slide up tags, so that assignment is accurate and is used.
4. **The Aim XR record is an AR and VR platform entry, not a web or mobile overlay.** Its "card animation" keyword is supported by a Card tag on the record, so it is used, but the section notes the platform difference instead of presenting it as a standard web scrim.
5. **Sibling collection URLs were verified** against the live Ripplix interaction vocabulary before being suggested. Dropdown, Accordion, Menu and Collapse all exist with the slugs given.
