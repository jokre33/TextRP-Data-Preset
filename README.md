Either use the character cards provided with the preset OR one of `C1`, `C2`, `C3`. They are exact copies of the card versions in case you want to work on an existing card instead of providing the existing character sheet in a different way.
In that case move the `"Tool Prompt ({{char}})"` prompt between `(Context)` and `(End of Context)`.

---

**Explanation of the modules:**

**1) ERP Info** Explicitly enables the integration of `NSFW/ERP Info` into your sheets. *Gemini* sometimes excludes ERP specific info without it.

**2)** Controls how much *Gemini* should do on its own:
*   `2.1) Autonomy: Full` Gives full control over everything not explicitly stated by you to *Gemini*. This includes integration of info from `3.x` modules and suggested info from module `8`.
*   `2.2) Autonomy: Partial` Gives partial control over formatting, structure, etc to *Gemini*. Larger scale changes and integration for `3.x` and `8` changes will be suggested and need approval.
*   `2.3) Autonomy: Suggestions only` All post first pass changes will be suggested instead of directly implemented, including minor wording/grammatical changes.
*   `2.4) Autonomy: None (FPP only)` Completely disables autonomous changes and suggestions apart from the first pass processing of input. (Disables `3.x` and `8` unless explicitly directed by you)

**3)** Controls the level of information that should be taken from `Lore Books` and integrated into the sheet.
*   `3.1) CI: None` Assumes the `Lore Book` will be active when the sheet is used and does not directly integrate any information, instead only referencing it.
*   `3.2) CI: Minimal` Assumes the `Lore Book` will NOT be active when the sheet is used. It integrates the minimum information needed for the sheet to make sense.
*   `3.3) CI: Broad` Same as `3.2`, but integrates a broader context. Be careful when using this, it may add bloat you need to manually cull.

**4)** Pretty self explanatory. Do you want to see only changed sections of the sheet or the full thing with every response?
*   `4.1) Always Full Output` **WARNING:** This may quickly balloon `token count`.
*   `4.2) Only Changed Sections` Nothing much to say.

**5)** Controls output formatting:
*   `5.1) Markdown` Standard `markdown` formatting. *Gemini* is pretty good at creating and reading info using this, so it's the default.
*   `5.2) JSON (Readable)` `JSON` format, might offer more information density, but in my experience it tends to have higher `token count` than `5.1`.
*   `5.3) JSON (Single Line)` `JSON` format, condensed to a single line. Because people on `chub.ai` go nuts if they see a single unnecessary whitespace in character cards lol.
*   `5.4) XML` `XML` format. Offers more explicit structuring than `Markdown` while retaining more human readability than `JSON`.

**6) Web Search** Tells *Gemini* to use its `websearch` capabilities. You need to enable web search in the settings above as well.

**7) Cull Speculative Language** Tries to make *Gemini* actively trim speculative language (because it loves to use it). Doesn't 100% get rid of it, but helps, especially over multiple responses.

**8) Enable Suggestions** Enables suggestions for additional information, points out missing info, etc in your sheet. Probably breaks if you enable `2.4`.