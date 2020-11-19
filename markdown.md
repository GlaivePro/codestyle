# Markdown style guidelines

## General

Follow the [general guidelines](general.md).

Assume that your files will not only be read by computers and parsed to HTML
but also read by people on their IDEs, editors and even `cat`ed on consoles.
Strive to make them readable as-is.

> An example to this rule ar ordered lists if they are long. Feel free to use
> `1.` for every item for ease of maintenance.

## Code samples

Use backtick syntax to delimit code samples and include language specification
if applicable. Use three backticks as the default.

````md
```md
An inline code sample: `this`.
```
````

The spacing is optional and should follow the text flow. If the sample block is
a part of a sentence, feel free to not include empty lines around it:
````md
You can write titles like this:
```md
# A title

````

## Syntax

Apart from code samples, use any flavour of syntax, but strive to be consistent
within a project. You should have a good reason if you are mixing multiple 
options of syntax. This project uses:

- Dashes `-` for itemizations;
- Asterisks for `*emphasis*`, `**strong**`;
- Atx-style headers `# Title`, `## Subtitle`.

## Titles

Use proper outline as you would in HTML — have a single `#` at the top, put
sections in `##` etc.

Include an empty line before any title, except at the beginning of a document.

## Emphasis

Try to emphasize keywords. When in doubt and unsure which one to use, fall 
back to single asterisks as the `*default emphasis*`.

Other than that you are free to use any emphasis you wish — bold, italics, 
quotes or even the code backticks. If your keyword is also a link, no need 
for another emphasis.
