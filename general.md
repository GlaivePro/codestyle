# General rules

These are the rules that are applicable to everything.

## Encoding

Use UTF-8 without BOM.

Use `\n` for line breaks.

## Lines

Every line including the final one must end with a `\n`.

Do not leave trailing whitespace at the end of the line unless required.

Try to limit the line length to 80 columns, especially for prose like comments
or markdown files. Assume that people will read your files on 80-character
terminals.

## Indentation

Use either tabs or 4 spaces. If you prefer any other indentation size, use tabs
and configure your editor to display tabs as 3 or 8 or 11 or whatever spaces.

## .editorconfig

Include [this file](.editorconfig) on every project. Use an editorconfig 
plugin for your editor or IDE. It will take care of the conerncs described
in this document.

The `indent_size = 4` rule is paramount as it fixes how GitHub displays the tab
character.
