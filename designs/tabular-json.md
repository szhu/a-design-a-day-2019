# Tabular JSON

## Background

CSV files are simple, but (1) they only support text cells and (2) their format is notoriously not universal.

XLS, XLSX, and ODS support a ton of features, but they are (1) not universal and (2) definitely not simple. In particular, they allow the user to save visual formatting (color, bold, etc.), which not everyone needs.

How about a spreadsheet file format that stores only rich data but no formatting?

## Idea

*Tabular JSON* is a file format that allows you to store complex data types within a table. It is literally pieces of JSON in a CSV/TSV container. The preferred file extension is `.tabjson`, but files can have the extension `.json.csv`/`.json.tsv` if need be.

A standard container format should be chosen so that programs that open Tabular JSON files do not have to do any guesswork about how the document is formatted. This makes it unlikely to open files in the wrong encoding, and simplifies implementation.

Here are two possibilities for the container format:

- Container format proposal 1 (CSV):

  - Files are UTF8 and begin with the byte-order mark.
  - Rows are `\n`-separated; columns are comma-separated.
  - Commas and quote characters are quoted using Excel conventions -- quotes around the entire cell, double up the character to produce a literal one.
  
  Benefits of this format:

  - When named `.json.csv`, the file can be opened by default with every spreadsheet program in existence today!
  - Unicode characters can be typed literally into the document. Also, allowing any character in cells allows objects to be pretty-printed into each cell. These traits make cells more readable when opened in a traditional spreadsheet program.

- Container format proposal 2 (TSV):

  - Files are ASCII-only. This means that all non-ASCII characters in strings must be backslash-escaped.
  - Rows are `\n`-separated; columns are `\t`-separated.
  - Cells must not contain literal `\n` or `\t` characters. This means that we can't save pretty-printed objects (since literal newlines would be required), and it means all `\n` and `\t` characters in strings must be backslash-escaped.
  
  Benefits of this format:
  
  - When named `.json.tsv`, the file can be opened by default with most spreadsheet programs, and all spreadsheet programs should be able to be able to open them using advanced open options. It will always open in the right encoding, since it is only ASCII.
  - No quoting convention is required because literal `\n` and `\t` characters can't appear in cells. This makes the file extremely `cut`- and `sed`-friendly and could makes files easier to index.
  - Disallowing newlines in cells puts the onus on the editor to provide pretty-printing, which leads to a better separation of content and presentation.

Once the container format is established, the rest of the implementation is simple -- each cell is simply JSON. That means that, for example, all string cells must begin and end in quotes. No empty cells are allowed -- they must be `null`. (If space efficiency is a concern, a standard compression format can be defined in the future.)

Example file:

```json
{"header":true},"animal","otherNames","weightInPounds","isDangerous"
{"header":false},"Grizzly bear",["Brown bear"],400,true
{"header":false},"Panda",["Giant panda", "Panda bear"],200,false
{"header":false},"Polar bear",[],500,true
```

Here's what it looks like opened up in a traditional spreadsheet program:

<table>
<tr><td>{"header":true}<td>"animal"<td>"otherNames"<td>"weightInPounds"<td>"isDangerous"
<tr><td>{"header":false}<td>"Grizzly bear"<td>["Brown bear"]<td>400<td>true
<tr><td>{"header":false}<td>"Panda"<td>["Giant panda", "Panda bear"]<td>200<td>false
<tr><td>{"header":false}<td>"Polar bear"<td>[]<td>500<td>true
</table>

This is where the Tabular JSON spec ends. Applications can use Tabular JSON as a pure data storage format, or can add extra functionality by defining schemas in a similar way as [JSON schemas](https://json-schema.org/).
