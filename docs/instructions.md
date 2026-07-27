# How to write instructions

Instructions can be written in [Markdown](https://commonmark.org/help/) (we use
[Marked](https://marked.js.org/) for parsing, so you can
[try the demo to validate your Markdown](https://marked.js.org/demo/)), HTML,
or plain text.

### Markdown
To use our Markdown renderer, simply name your files with a .md extension.
Markdown can also contain arbitrary HTML, so you can add additional
customizations not possible through standard markdown. We use Markdown for most
of our packs since it's simpler to write than HTML but still has support for
better styling, linking, etc., than plain text.

### HTML
To use our HTML renderer, simply name your files with a .html extension.

### Plain Text
To use our plain text renderer, simply name your files with a .txt extension.
We do render the text monospaced, so various ASCII art is fair game!
```
  |\_/|
 / @ @ \
( > º < )
 `>>x<<´
 /  O  \
```
Be sure to wrap long lines, since we don't do that for you.

### Multiple files
We support having multiple files. They will be served with the names you create,
minus extensions. (e.g. to access index.md, either refer to `/` or to `/index`,
but not to `/index.html`. To reference [another file](./index), simply add a link
to `./<filename>`. 

We do _not_ currently support nested directories of files in the documentation
folder.

### Link placeholders
You may want to include links to other pages from your instructions document,
but hardcoding them doesn't work great if you want to use the same pack on
different instances running at different domains / IPs.
We support embedding link placeholders that will be replaced with links to
the corresponding pages under the accessed domain name / IP address.
Currently, the supported placeholders are:
- DTANM_LINK_INSTRUCTIONS: `/instructions/index`
- DTANM_LINK_PROGRAM: `/program`
- DTANM_LINK_MY_SCORE: `/teams/me`
- DTANM_LINK_TEAMS: `/teams`
- DTANM_LINK_ATTACKS: `/attacks`
- DTANM_LINK_STATS: `/stats`
- DTANM_LINK_ADMIN: `/admin`

Placeholder replacement uses jinja2 and looks like:
```
{{DTANM_LINK_INSTRUCTIONS}}
```

This would produce `http://76.65.84.69/instructions/index` if accessed through
a DTANM instance at `76.65.84.69`

Formatting can be disabled by setting `ENABLE_INST_FORMATTING = False`,
it's enabled by default on v4.0 packs. On v3.0 packs it's ignored and assumed
False.
