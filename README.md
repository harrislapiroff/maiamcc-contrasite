# Maia's Contradance Site

Made with [Jekyll](https://jekyllrb.com/).

Deployed via [Cloudbuild](./cloudbuild), just push changes to GitHub (no need to `jekyll build`) and it should automatically work.

To preview: `bundle exec jekyll serve`.

## Dance Formatting
Dances loaded into my choreo page and represented in blog posts have the following fields:
- title: str
- author || coauthor: str
- formation: str
- difficulty: str (one of accessible | advanced | expert)
- fave: bool
- comp_notes: str
- choreo_notes: str
- date_written: str (yyyymm)
- blurb: str
- video_link: str
- choreo: dict[section: str --> moves: list[str]]
  - e.g.:
  ```yaml
  a1:
    - long lines forward and back
    - long lines forward and back
  a2:
    - long lines forward and back
    - long lines forward and back
  etc.
  ```
- footnotes: dict[ref: int --> content: str]
  - footnotes origins in the above sections are denoted with `text[^1]`. As long as the text is passed through the `footnoter` Jekyll filter, the reference will be properly rendered, and linked to the footnote with ref=1.

### Tooltips for Dance Choreo
To create a tooltip'd dance link (using [Tippy](https://atomiks.github.io/tippyjs/)):
- make sure that your post/page has a `dances` object in the frontmatter: should be a list of dance objects (as spec'd above)
- include your dance as an element in that `dances` list
- create the link with `{% include custom/dance_tooltip_link.html dance_title='Dance Title Here' %}`. May be used multiple times to reference the same dance.
- if your frontmatter has a `dances` list, Jekyll will automatically include `_includes/custom/dance_tooltip_script.js`, which imports Tippy and registers dance choreo to the corresponding tooltip

## TODO
- [] choreo: mark new dances?
- [] choreo: describe difficulty levels
- [] choreo: filter by difficulty level, favorite, etc.?
- [] choreo: mousing over a footnote highlights the corresponding text
- [] blog: sidebar with recent posts? (look at formatting in partials/sidebar.scss, which currently isn't imported)
- [] blog: collapsible choreo elems (see https://www.w3schools.com/howto/howto_js_collapsible.asp) or tooltips (see https://atomiks.github.io/tippyjs/)
