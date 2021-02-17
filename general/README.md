# General

Style and best practices that apply to all languages and frameworks.

In addition to the general guidelines below, we also have the following more
detailed, language/framework-specific style guides:

- [HTML](../html)
- [CSS](../css)
- [Sass](../sass)
- [JavaScript](../javascript)
- [PHP](../php)
- [.NET](../net)
- [EPiServer](../episerver)

## Formatting

- Break long lines after 80 characters.
- Delete trailing whitespace.
- Don't include spaces after `(`, `[` or before `]`, `)`.
- Don't misspell.
- Don't vertically align tokens on consecutive lines.
- If you break up a hash, keep the elements on their own lines and closing curly
  brace on its own line.
- Indent continued lines two spaces.
- Indent private methods equal to public methods.
- Use 2 space indentation (no tabs).
- Use an empty line between methods.
- Use empty lines around multi-line blocks.
- Use spaces around operators, except for unary operators, such as `!`.
- Use spaces after commas, after colons and semicolons, around `{` and before
  `}`.
- Use [Unix-style line endings][newline explanation] (`\n`).
- Use [uppercase for SQL key words and lowercase for SQL identifiers].

[uppercase for sql key words and lowercase for sql identifiers]: http://www.postgresql.org/docs/9.2/static/sql-syntax-lexical.html#SQL-SYNTAX-IDENTIFIERS
[newline explanation]: http://unix.stackexchange.com/questions/23903/should-i-end-my-text-script-files-with-a-newline

## Naming

- Avoid abbreviations.
- Avoid object types in names (`userArray`, `emailMethod` `CalculatorClass`, `ReportModule`).
- Prefer naming classes after domain concepts rather than patterns they
  implement (e.g. `Guest` vs `NullUser`, `CachedRequest` vs `RequestDecorator`).
- Name the enumeration parameter the singular of the collection.
- Name variables, methods, and classes to reveal intent.
- Treat acronyms as words in names (`XmlHttpRequest` not `XMLHTTPRequest`),
  even if the acronym is the entire name (`class Html` not `class HTML`).

## Organization

- Order methods so that caller methods are earlier in the file than the methods
  they call.
- Order methods so that methods are as close as possible to other methods they
  call.

## IDE/Text Editor

- Use linting plugins avaialable for your editor to make sure you're not violating any of our code style guides
  - Add/enable ESLint for JavaScript linting
  - Add/enable Stylelint for Sass/SCSS linting

MTM specific code style linting configuration files can be found into each relevant language style directory.
