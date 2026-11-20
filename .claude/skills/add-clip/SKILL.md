---
name: add-clip
description: Add one of Hunter's published stories to the Clips section of index.html from a link, copying the headline, outlet and date exactly as published, then push it live. Use when Hunter runs /add-clip with a story URL or asks to add a clip.
argument-hint: <link to story>
---

# Add a clip

Story link: $ARGUMENTS

If no link was given, ask Hunter for one and stop.

## 1. Open the link

Open the link with WebFetch (or the web-fetch agent if WebFetch isn't available). From the published page, copy:

- **Headline**: the story's headline exactly as it appears on the page, character for character. That means the same capitalization, punctuation and quote marks. Use the visible headline on the page. Don't use the browser tab title or the share title, which often add the outlet's name or differ from the real headline.
- **Outlet**: the publication's name as it writes it (for example "The Washington Sun").
- **Date**: the publication date exactly as the page shows it. If the page shows both a published and an updated date, use the published date.

Rules:

- Never rewrite, shorten, summarize, fix or add to the headline. Don't add a summary or subheadline either.
- If the page doesn't open, is behind a paywall or login, or blocks the request, ask Hunter for the headline, outlet and date. Do the same if you can't find one of the three. **Never guess or fill in from memory.** Once Hunter answers, use their words exactly.
- If the byline doesn't include Hunter Riggall, show Hunter what you found and ask before adding it.
- If the link is already in the Clips list, tell Hunter and don't add it again.

## 2. Add it to index.html

Clips live in `<ul class="clip-list">` inside `<section id="clips">`, newest first. Insert the new clip directly below the `<!-- CLIPS: newest first ... -->` comment, so it's at the top of the list. If its date is older than clips already listed, put it in date order instead and tell Hunter you did.

Use exactly this markup (indented 8 spaces like the comment):

```html
        <li class="clip">
          <p class="clip-outlet">OUTLET</p>
          <h3 class="clip-headline"><a href="URL">HEADLINE</a></h3>
          <p class="clip-date">DATE</p>
        </li>
```

- Escape HTML special characters in the text: `&` → `&amp;`, `<` → `&lt;`, `>` → `&gt;`, and `"` → `&quot;` inside the `href`. Keep curly quotes, apostrophes and dashes exactly as published.
- Use the link Hunter gave, minus tracking parameters such as `utm_*`. If the page redirected to a different canonical URL, use the canonical one.
- Don't change anything else on the page.

## 3. Push it live

Follow CLAUDE.md: commit straight to `main` with a message like `Add clip: <headline>` and push to `origin main`.

## 4. Tell Hunter

In plain words, tell Hunter exactly what you added: the headline, outlet and date as they now appear on the site, plus the link. Say whether you copied them from the page or used what Hunter told you. Remind Hunter that the live site can take a minute or two to update.
