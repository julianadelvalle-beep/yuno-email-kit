# Yuno Email Kit

On-brand HTML email templates for Yuno marketing (HubSpot-ready) + the shared
brand assets they use, served over CDN so any email client can load them.

## Structure

```
assets/
  patterns/   grid + halftone background patterns (PNG)
  logos/      wordmarks + hero graphic (PNG)
  icons/      Phosphor "light" product icons in indigo (PNG) — one per feature
templates/
  blog-post.html   Blog post email (white + grid frame + soft cards + icons)
```

## Asset hosting (jsDelivr CDN)

Assets are hot-linked from this repo via jsDelivr — no need to upload to HubSpot.
URL pattern (repo must be **public**):

```
https://cdn.jsdelivr.net/gh/__GH_OWNER__/yuno-email-kit@main/assets/<path>
```

The templates reference `__GH_OWNER__`. **After creating the repo, replace it
with your GitHub username** (see Setup below). jsDelivr caches `@main` for up to
7 days; to force-refresh an updated asset, bump to a tag (e.g. `@v1`) or purge
via `https://purge.jsdelivr.net/gh/<owner>/yuno-email-kit@main/...`.

## Setup (one time)

1. Create a **public** repo named `yuno-email-kit` and push this folder.
2. Replace the placeholder in the templates with your GitHub username:
   ```
   grep -rl __GH_OWNER__ templates | xargs sed -i '' 's/__GH_OWNER__/YOUR_GH_USERNAME/g'
   ```
   (on Linux use `sed -i` without the `''`)
3. Commit + push. The jsDelivr URLs are now live.

## Icon library (feature → file)

Phosphor `light`, indigo `#3E4FE0`. Source: the new site's product menu.

| Feature | icon file |
|---|---|
| Payouts | arrows-left-right |
| Integrations | bounding-box |
| Checkout | shopping-cart-simple |
| Reconciliations | swap |
| Subscriptions | calendar-check |
| Stablecoins | currency-circle-dollar |
| Smart routing | tree-structure |
| Analytics & Insights | chart-line |
| Account updater | arrow-clockwise |
| Monitors | bell-ringing |
| NOVA AI | sparkle |
| Agentic commerce | shopping-bag |
| Payments Concierge | magic-wand |
| Risk conditions | shield-check |
| 3DS | lock-simple-open |
| Chargeback management | bank |
| Network tokens | shield-star |
| Vaulting | vault |

## Using `templates/blog-post.html` in HubSpot

1. HubSpot → Marketing → Email → create email → choose "Code your own" / paste HTML.
2. Per post, edit the spots marked `<!== EDIT ==>`: eyebrow (category), title,
   intro, the 3 cards (icon + title + text), and the CTA url.
   - Pick each card's icon from `assets/icons/` to match the topic
     (routing → tree-structure, 3DS → lock-simple-open, architecture → bounding-box…).
3. Subject line + preview text are set in the HubSpot editor.
4. Personalization: `{{ contact.firstname }}` and `{{ site_settings.* }}` resolve
   in HubSpot. The footer uses `{{ unsubscribe_link }}` (CAN-SPAM compliant).

## Brand rules baked in

Geist typeface · indigo `#3E4FE0` + neutrals · brand grid pattern framing ·
Phosphor light icons · single primary CTA + soft secondary demo link ·
8-pt spacing. See the Yuno design system / brandbook for the full spec.
