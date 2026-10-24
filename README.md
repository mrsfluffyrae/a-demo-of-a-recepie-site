# Hearth & Spoon: semantic recipe site

A hand-written, multi-page recipe site: HTML5 only, no CSS frameworks, no JavaScript. `style.css` is a small stylesheet for legibility only.

## Structure

```
site/
  index.html
  contact.html
  style.css
  README.md
  images/            SVG illustrations used by the recipe pages
  recipes/
    shakshuka.html
    coconut-curry.html
    banana-oat-pancakes.html
```

## How the requirements are met

| Requirement | How |
| --- | --- |
| Semantic elements | Every page uses `header`, `nav`, `main`, `footer`. Recipes are `article`s with `section`s for ingredients, method and nutrition. |
| One `h1`, logical order | The site name in the header is a `p`, so each page has exactly one `h1` in `main`. Headings go h1, h2, h3 with no skipped levels. |
| Lists | Ingredients use `ul`. Method steps use `ol`. The curry splits its long list into three groups under `h3` headings. |
| Accessible form | Every control has a `label` linked by `for`/`id`. Input types are `text`, `email`, `tel`, `radio`, `checkbox`, plus a `select` and `textarea`. Groups use `fieldset`/`legend`. Hints are linked with `aria-describedby`. |
| Alt text and table | Every `img` has descriptive `alt`. Each recipe has a nutrition `table` with `caption`, `thead`, `th scope="col"` and `th scope="row"`. |
| Consistent navigation | The same `nav` appears on every page with `aria-current="page"` on the current link. A skip link comes first on every page. |
| Stretch goal | Recipe pages carry schema.org `Recipe` microdata (name, description, image, times, yield, ingredients, instructions). |

## Edge cases

- **Many ingredients:** the curry page groups 16 ingredients under three `h3` headings so the list stays scannable.
- **Long title in navigation:** nav labels are short, and the `ul` uses `flex-wrap`, so links wrap onto a new line instead of overflowing. The long curry title appears only in the `h1`, which uses `overflow-wrap: anywhere`.
- **Empty form submission:** `required`, `type="email"` and `minlength` make the browser block an empty submit and move focus to the first invalid field, with no JavaScript. The server must validate again, because browser checks can be bypassed.

## Form action

The form posts to a placeholder URL (`https://example.com/contact-submit`). Replace it with a real form endpoint before publishing.

## Validation

Validate each page at https://validator.w3.org/ (use "Validate by File Upload"), or run the validator locally:

```
java -jar vnu.jar site/*.html site/recipes/*.html
```

Pages to check: `index.html`, `contact.html`, and the three files in `recipes/`.

Keyboard test: press Tab from the top of each page. Focus should visit the skip link, then the nav links, then (on the contact page) each field in visual order, ending on the submit button.
# a-demo-of-a-recepie-site
