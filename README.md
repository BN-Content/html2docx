# html3docx
A fork of https://github.com/johnjor/html2docx, which itself is a fork of https://github.com/pqzx/html2docx.  This version will focus on support of right-to-left languages.

Consider it a replacement to either [html3docx](https://pypi.org/project/html3docx/) or [htmldocx](https://pypi.org/project/htmldocx/); it should work in place of either of them as-is.

Dependencies: `python-docx` & `bs4`

### To install

We have not listed this work on PyPI.

### Improvements

- Parameterized `language`, `is_rtl`, `bidi`, and `east_asia` as part of initial call.
- Added `set_paragraph_direction` and `set_run_language` and added calls wherever paragraphs and runs were instantiated.
- Tested locally to verify. Have verified Arabic; YMMV on other languages (mostly depending on Word's support, I'd guess)

## Original README

### Usage

Add strings of html to an existing docx.Document object

```
from docx import Document
from htmldocx import HtmlToDocx

document = Document()
new_parser = HtmlToDocx()
# do stuff to document

html = '<h1>Hello world</h1>'
new_parser.add_html_to_document(html, document)

# do more stuff to document
document.save('your_file_name')
```

Convert files directly

```
from htmldocx import HtmlToDocx

new_parser = HtmlToDocx()
new_parser.parse_html_file(input_html_file_path, output_docx_file_path)
```

Convert files from a string

```
from htmldocx import HtmlToDocx

new_parser = HtmlToDocx()
docx = new_parser.parse_html_string(input_html_file_string)
```

Change table styles

Tables are not styled by default. Use the `table_style` attribute on the parser to set a table
style. The style is used for all tables.

```
from htmldocx import HtmlToDocx

new_parser = HtmlToDocx()
new_parser.table_style = 'Light Shading Accent 4'
```

To add borders to tables, use the `TableGrid` style:

```
new_parser.table_style = 'TableGrid'
```

Default table styles can be found
here: https://python-docx.readthedocs.io/en/latest/user/styles-understanding.html#table-styles-in-default-template

Change default paragraph style

No style is applied to the paragraphs by default. Use the `paragraph_style` attribute on the parser
to set a default paragraph style. The style is used for all paragraphs. If additional styling (
color, background color, alignment...) is defined in the HTML, it will be applied after the
paragraph style.

```
from htmldocx import HtmlToDocx

new_parser = HtmlToDocx()
new_parser.paragraph_style = 'Quote'
```

Default paragraph styles can be found
here: https://python-docx.readthedocs.io/en/latest/user/styles-understanding.html#paragraph-styles-in-default-template
