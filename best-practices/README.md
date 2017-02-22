Best Practices
==============

A guide for programming well.

General
-------

* These are not to be blindly followed; strive to understand these and ask
  when in doubt.
* Don't duplicate the functionality of a built-in library.
* Don't swallow exceptions or "fail silently."
* Don't write code that guesses at future functionality.
* Exceptions should be exceptional.
* [Keep the code simple].

[Keep the code simple]: http://www.readability.com/~/ko2aqda2

Object-Oriented Design
----------------------

* Avoid global variables.
* Avoid long parameter lists.
* Limit collaborators of an object (entities an object depends on).
* Limit an object's dependencies (entities that depend on an object).
* Prefer composition over inheritance.
* Prefer small methods. Between one and five lines is best.
* Prefer small classes with a single, well-defined responsibility. When a
  class exceeds 100 lines, it may be doing too many things.

Web
---

* Avoid a Flash of Unstyled Text, even when no cache is available.
* Avoid rendering delays caused by synchronous loading.
* Use https instead of http when linking to assets.

Browsers
--------

* Avoid supporting versions of Internet Explorer before IE10.

HTML
----

* Use Jade/Pug template engine for static websites.
* Use `<button>` tags over `<a>` tags for actions.

CSS
---

* Document the project's CSS architecture (the README, component library or style guide are good places to do this), including things such as:
  * Organization of stylesheet directories and Sass partials
  * Selector naming convention
  * Code linting tools and configuration
  * Browser support
* Use Sass.
* Use [Autoprefixer][autoprefixer] to generate vendor prefixes based on the
  project-specific browser support that is needed.
* Prefer `overflow: auto` to `overflow: scroll`, because `scroll` will always
display scrollbars outside of OS X, even when content fits in the container.

[autoprefixer]: https://github.com/postcss/autoprefixer

JavaScript
----------
* Use the latest stable JavaScript syntax with a transpiler, such as [babel].

[babel]: http://babeljs.io/
