# Sass

- [Sample](sample.scss)
- [Shared StyleLint configuration](https://github.com/CosAnca/stylelint-config-nucleum)

  - This configuration aligns with our team-wide guides below.

- Use maps and variables to codify and centralize breakpoint values.
- Prefer abstract names such as `sm`, `md`, `lg`, etc. instead of specific devices.
- Nest breakpoints inside of the relevant selector.
- If a component needs a specific breakpoint to work, keep it with the relevant component partial. If other components need the same value, integrate it into the centralized breakpoints map.

## Architecture

Project stylesheets should be structured following closely to the principles of [ITCSS](https://medium.com/@jordankoschei/how-i-shrank-my-css-by-84kb-by-refactoring-with-itcss-2e8dafee123a#.7gdzbrk1m), imported in the following order for greater control over re-usability and specificity:

0. **Settings** - Global configuration and variables.
1. **Tools** - Mixins and functions.
2. **Generic** - High-level styles such as resets and [normalize.css](https://github.com/necolas/normalize.css).
3. **Elements** - Base HTML styling.
4. **Objects** - Common non-cosmetic structural design patterns.
5. **Components** - Specific cosmetic elements of UI.
6. **Utilities** - Helpers and overrides.

## Formatting

- Use the SCSS syntax.
- Use hyphenated BEM style when naming mixins, extends, classes, functions & variables: `span-columns` not `span_columns` or `spanColumns`.
- Use one space between property and value: `width: 20px` not `width:20px`.
- Use a blank line above a selector that has styles.
- Use lowercase hex color codes `#fff`.
- Avoid using shorthand properties for only one value: `background-color: #ff0000;`, not `background: #ff0000;`.
- Use `//` for comments not `/* */`, except for when adding tool related comments that requires CSS style comment.
- Use `// [number]` comments for declarations specific to a bug or to connect with further declared properties.
- Use one space between selector and `{`.
- Use double quotation marks.
- Use only lowercase.
- Don't add a unit specification after `0` values, unless required by a mixin or browser support.
- Use a leading zero in decimal numbers: `0.5` not `.5`.
- Use space around operands: `$variable * 1.5`, not `$variable*1.5`.
- Avoid in-line operations in shorthand declarations (Ex. `padding: $variable * 1.5 variable * 2`).
- Use parentheses around individual operations in shorthand declarations: `padding: ($variable * 1.5) ($variable * 2);`.
- Use double colons for pseudo-elements.
- Use a `%` unit for the amount/weight when using Sass's color functions: `darken($color, 20%)`, not `darken($color, 20)`.
- Use a trailing comma after each item in a map, including the last item.

## Order

- Use [SMACCS](https://smacss.com/book/formatting) style for properties order.
- Place `@includes` at the top of your declaration list.
- Place media queries directly after the declaration list.
- Place concatenated selectors second.
- Place pseudo-states and pseudo-elements third.
- Place nested elements fourth.
- Place nested classes fifth.

## Selectors

- Don't use ID's in selectors.
- Don't use HTML elements in selectors: `.c-example` not `div.c-example`.
- Use meaningful names: `$visual-grid-color` not `$color` or `$vslgrd-clr`.
- Be consistent about naming conventions for classes. For instance, if a project is using BEM, continue using it, and if it's not, do not introduce it.
- Use class names that are as short as possible but as long as necessary.
- Use namespaces in class names relevant to their layer. (Ex. `.o-container` for objects, or `.c-comp` for components).
- Avoid nesting more than 3 selectors deep.
- Avoid using comma delimited selectors.
- Avoid nesting within a media query.

## BEM

- Avoid using the SCSS ampersand shortcut (`&__` or `&--`) when defining elements, it'll make searching the codebase a lot less productive.
- Don't create elements inside elements (e.g. `.c-example__element__element`). Consider creating a new block for the parent element instead.
- Changes in a state shouldn't be dictated by modifiers, and are handled [slightly differently](#states).

## Namespacing

- `o-` signifies that this class is an **Object**, and that it may be used in any number of unrelated contexts to the one you can currently see it in. Making modifications to these types of class could potentially have knock-on effects in a lot of other unrelated places. _(These type of classes are also immutable and should not be reassigned within other declaration blocks)_.
- `c-` signifies that this class is a **Component**. This is a concrete, implementation-specific piece of UI. All of the changes you make to its styles should be detectable in the context you're currently looking at. Modifying on top of these styles should be safe and have no side effects.
- `u-` signifies that this class is a **Utility** class. It has a very specific role (often providing only one declaration) and probably recognize this namespace from libraries and methodologies like SUIT. _(These type of classes are also immutable and should not be reassigned within other declaration blocks)_.
- `t-` signifies that a class is responsible for adding a **Theme** to a view. It lets us know that UI Components' current cosmetic appearance may be due to the presence of a theme.
- `s-` signifies that a class creates a new styling context or **Scope**. Similar to a Theme, but not necessarily cosmetic, these should be used sparingly — they can be open to abuse and lead to poor CSS if not used wisely.
- `is-, has-` signifies that the piece of UI in question is currently styled a certain way because of a **state** or **condition**. This stateful namespace is gorgeous, and comes from SMACSS. It tells us that the DOM currently has a temporary, optional, or short-lived style applied to it due to a certain state being invoked.
- `_` signifies that this class is the worst of the worst — **a hack**! Sometimes, although incredibly rarely, we need to add a class in our markup in order to force something to work. If we do this, we need to let others know that this class is less than ideal, and hopefully temporary (i.e. do not bind onto this). _(These type of classes are also immutable and should not be reassigned within other declaration blocks)_.
- `js-` signifies that this piece of the DOM has some behaviour acting upon it, and that **JavaScript** binds onto it to provide that behaviour. If you’re not a developer working with JavaScript, leave these well alone.
- `qa-` signifies that a **QA** or Test Engineering team is running an automated UI test which needs to find or bind onto these parts of the DOM. Like the JavaScript namespace, this basically just reserves hooks in the DOM for non-CSS purposes.

## States

- As mentioned in the previous section, use `is-` or `has-` to customize a temporary, optional, or short-lived style applied due to a certain state being invoked.

## Extending and Modifying

- Don't use `@extend`.
- Don't directly overwrite a previously defined class. Use a `--modifier` class instead.

## Specificity

- By following the steps above (specifically by using classes and limited nesting) conflicts with specificity shouldn't be a problem.
- If you're struggling to override styles, battling specificity, the safest option is to [chain the selector to itself] (e.g. `.c-example.c-example`).

[chain the selector to itself]: http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/#safely-increasing-specificity

## Organization

- Use [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/) stylesheets structure model.
- Use [Bourbon](https://www.bourbon.io/docs/latest/) for a Sass mixins library.
- Use [Adaptable](https://github.com/CosAnca/adaptable) for a grid framework.
- Use a mobile first approach.
- Use HTML structure for ordering of selectors. Don't just put styles at the bottom of the Sass file.

<details>

#### Code examples

SMACSS declarations order:

```scss
.c-example {
  display: block;
  position: relative;
  width: 100%;
}
```

Comprehensive example of ordering items within a declaration block:

```scss
.c-example {
  @include size(10px);

  display: block;
  margin: $spacing-variable;

  @media (min-width: $screen-variable) {
    padding: $spacing-variable;
  }

  &:focus {
    border-color: $color-variable;
  }

  &::before {
    content: "";
  }

  .c-nested-element {
    margin: $spacing-variable;
  }
}
```

#### Motivation

SMACSS declaration order can be automated and is commonly a feature that can be added to code editors through extensions.

#### Linting

SMACSS declaration ordering can be linted using stylelint.

</details>
