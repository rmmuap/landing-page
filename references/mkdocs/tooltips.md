---
icon: material/tooltip-plus
---

# Tooltips

Technical documentation often incurs the usage of many acronyms, which may
need additional explanation, especially for new user of your project. For these
matters, Material for MkDocs uses a combination of Markdown extensions to
enable site-wide glossaries.

Tooltips will be rendered for the following elements:

- __Content__ – elements with a `title`, permalinks and code copy button
- __Header__ – home button, header title, color palette switch and repository link
- __Navigation__ – links that are shortened with ellipsis, i.e. `...`

## Usage

### Adding tooltips

The [Markdown syntax] allows to specify a `title` for each link, which will
render as a beautiful tooltip when [improved tooltips] are enabled. Add a
tooltip to a link with the following lines:

``` markdown
[Hover me](https://example.com "I'm a tooltip!")
```

<div class="result" markdown>

[Hover me](https://example.com "I'm a tooltip!")

</div>

Tooltips can also be added to link references:

``` markdown
[Hover me][example]

  [example]: https://example.com "I'm a tooltip!"
```

<div class="result" markdown>

[Hover me](https://example.com "I'm a tooltip!")

</div>

For all other elements, a `title` can be added by using the [Attribute Lists]
extension:

``` markdown
:material-information-outline:{ title="Important information" }
```

<div class="result" markdown>

:material-information-outline:{ title="Important information" }

</div>

  [Markdown syntax]: https://daringfireball.net/projects/markdown/syntax#link
  [improved tooltips]: #improved-tooltips

### Adding abbreviations

Abbreviations can be defined by using a special syntax similar to URLs and
[footnotes], starting with a `*` and immediately followed by the term or
acronym to be associated in square brackets:

``` markdown title="Text with abbreviations"
The HTML specification is maintained by the W3C.

*[HTML]: Hyper Text Markup Language
*[W3C]: World Wide Web Consortium
```

<div class="result" markdown>

The HTML specification is maintained by the W3C.

*[HTML]: Hyper Text Markup Language
*[W3C]: World Wide Web Consortium

</div>

  [footnotes]: footnotes.md

### Adding a glossary

The [Snippets] extension can be used to implement a simple glossary by moving
all abbreviations in a dedicated file[^1], and [auto-append] this file to all
pages with the following configuration:

  [^1]:
    It's highly recommended to put the Markdown file containing the
    abbreviations outside of the `docs` folder (here, a folder with the name
    `includes` is used), as MkDocs might otherwise complain about an
    unreferenced file.

=== ":octicons-file-code-16: `includes/abbreviations.md`"

    ```` markdown
    *[HTML]: Hyper Text Markup Language
    *[W3C]: World Wide Web Consortium
    ````

=== ":octicons-file-code-16: `mkdocs.yml`"

    ```` yaml
    markdown_extensions:
      - pymdownx.snippets:
          auto_append:
            - includes/abbreviations.md
    ````

  [auto-append]: https://facelessuser.github.io/pymdown-extensions/extensions/snippets/#auto-append-snippets

