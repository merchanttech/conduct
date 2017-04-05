# Sass

- [Sample](sample.scss)
- [Default Sass-Lint configuration](.sass-lint.yml)
  - This configuration aligns with our team-wide guides below.

## Architecture

Project stylesheets should be structured following closely to the principles of [ITCSS](https://medium.com/@jordankoschei/how-i-shrank-my-css-by-84kb-by-refactoring-with-itcss-2e8dafee123a#.7gdzbrk1m), imported in the following order for greater control over re-usability and specificity:

0. **Settings** - Global configuration and variables.
0. **Tools** - Mixins and functions.
0. **Generic** - High-level styles such as resets and [normalize.css](https://github.com/necolas/normalize.css).
0. **Elements** - Base HTML styling.
0. **Objects** - Common non-cosmetic structural design patterns.
0. **Components** - Specific cosmetic elements of UI.
0. **Utilities** - Helpers and overrides.

## Formatting

* Use the SCSS syntax.
* Use hyphenated BEM style when naming mixins, extends, classes, functions & variables: `span-columns` not `span_columns` or `spanColumns`.
* Use one space between property and value: `width: 20px` not `width:20px`.
* Use a blank line above a selector that has styles.
* Use lowercase hex color codes `#fff`.
* Avoid using shorthand properties for only one value: `background-color: #ff0000;`, not `background: #ff0000;`
* Use `//` for comments not `/* */`.
* Use one space between selector and `{`.
* Use double quotation marks.
* Use only lowercase.
* Don't add a unit specification after `0` values, unless required by a mixin.
* Use a leading zero in decimal numbers: `0.5` not `.5`
* Use space around operands: `$variable * 1.5`, not `$variable*1.5`
* Avoid in-line operations in shorthand declarations (Ex. `padding: $variable * 1.5 variable * 2`)
* Use parentheses around individual operations in shorthand declarations: `padding: ($variable * 1.5) ($variable * 2);`
* Use double colons for pseudo-elements
* Use a `%` unit for the amount/weight when using Sass's color functions: `darken($color, 20%)`, not `darken($color, 20)`
* Use a trailing comma after each item in a map, including the last item.

## Order

* Use [SMACCS](https://smacss.com/book/formatting) style for properties order.
* Place `@includes` at the top of your declaration list.
* Place media queries directly after the declaration list.
* Place concatenated selectors second.
* Place pseudo-states and pseudo-elements third.
* Place nested elements fourth.
* Place nested classes fifth.

## Selectors

* Don't use ID's in selectors.
* Don't use HTML elements in selectors: `.widget` not `div.widget`
* Use meaningful names: `$visual-grid-color` not `$color` or `$vslgrd-clr`.
* Be consistent about naming conventions for classes. For instance, if a project is using BEM, continue using it, and if it's not, do not introduce it.
* Use class names that are as short as possible but as long as necessary.
* Avoid nesting more than 3 selectors deep.
* Avoid using HTML tags on classes with specific class names like `.featured-articles`.
* Avoid nesting within a media query.

## BEM

* Avoid using the SCSS ampersand shortcut (`&__`) when defining elements, it'll make searching the codebase a lot less productive.
* Don't create elements inside elements (e.g. `.block__element__element`). Consider creating a new block for the parent element instead.
* Changes in a state shouldn't be dictated by modifiers, and are handled [slightly differently](#states).

## Namespacing

* `o-` signifies that this class is an **Object**, and that it may be used in any number of unrelated contexts to the one you can currently see it in. Making modifications to these types of class could potentially have knock-on effects in a lot of other unrelated places.
* `c-` signifies that this class is a **Component**. This is a concrete, implementation-specific piece of UI. All of the changes you make to its styles should be detectable in the context you're currently looking at. Modifying on top of these styles should be safe and have no side effects.
* `u-` signifies that this class is a **Utility** class. It has a very specific role (often providing only one declaration) and probably recognize this namespace from libraries and methodologies like SUIT.
* `t-` signifies that a class is responsible for adding a **Theme** to a view. It lets us know that UI Components' current cosmetic appearance may be due to the presence of a theme.

## States

* Use `is-` or `has-` to customize a temporary, optional, or short-lived style applied due to a certain state being invoked.

## Extending and Modifying

* Don't use `@extend`.
* Don't directly overwrite a previously defined class. Use a `--modifier` class instead.

## Specificity

* By following the steps above (specifically by using classes and limited nesting) conflicts with specificity shouldn't be a problem.
* If you're struggling to override styles, battling specificity, the safest option is to [chain the selector to itself] (e.g. `.c-example.c-example`).

[chain the selector to itself]: http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/#safely-increasing-specificity

## Organization

* Use [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/) stylesheets structure model.
* Use Bourbon for a Sass mixins library.
* Use Neat for a grid framework.
* Use a mobile first approach.
* Use [Normalize](https://github.com/necolas/normalize.css) for browser rendering consistency, rather than a reset.
* Use HTML structure for ordering of selectors. Don't just put styles at the bottom of the Sass file.
* Avoid having files longer than 100 lines.
