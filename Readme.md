# PORK - Python tags parser for Word files

*Pork* is a template engine which parses annotated text file and renders native Word .docx file - similar to Markdown -> HTML processing.

# Tags supported by **Pork**

## Blocks:
- title
- subtitle
- header 1 to 6
- paragraph
- macro
- TOC heading
- quote
- ordered and unordered list
- table
- page break
- image
## Inlines:
- highlighted text
- styled text (bold, italics, underline, strike, subscript, superscript)


------

# Block tags

Block tags starts at the very beginning of line. Block ends when running cursors meets empty line. (with the exception of ordered and unordered lists, which are just line-based).


| Syntax              | Meaning           | Proxy to                                   |
|:------------------- |:------------------|:-------------------------------------------|
|`+++ Text`           | Title _Text_      | `add_paragraph('Text',style='Title')`      |
|`++++++ Text`        | Subtitle _Text_   | `add_paragraph('Text',style='Subtitle)`    |
|`# Text` .. `######` | Header _Text_     | `add_heading('Text',level=(amount of #))`  |
|`block of text....`  | Regular paragraph. Treated as a whole block till the empty line. | `add_paragraph('block of text....')`        |
|`^text ...`         | Macro style.      | `add_paragraph('text ....',style='macro')`   |
|`@TOC`               | Table of contents heading. Creates placeholder that needs manual `F9` to fill the data | `add_paragraph('Table of contents', style='TOC Heading')`|      
|`q' Text`            | Quote `Text`      | `add_paragraph('Text',style='Quote')`|
|`1. Text`, `2. Text`, `3. Text` | Ordered list item `Text`. Number means indentation level | `add_paragraph('Text', style='List Number')`,`add_paragraph('Text, style='List Number 1')`,`add_paragraph('Text, style='List Number 2')` |
|`* Text`, `** Text`, `*** Text` | Bulleted list item `Text`. Amount of `*` character means indentation level | `add_paragraph('Text', style='List Bullet')`,`add_paragraph('Text, style='List Bullet 1')`,`add_paragraph('Text, style='List Bullet 2')`|
|`\| text \| text \| ...\| `| Table | |
|`--`                 | Page break        |  `doc.add_page_break()` |
|`!image` , `!image!x!y` | Image with optional `x` and `y` size in cm | `doc.add_picture('image')`, `doc.add_picture('image',width=Cm(x),height=Cm(y)` |
 
## Inlines

Inlines can occur inside a block of text (paragraph)
_(tbd...)_
