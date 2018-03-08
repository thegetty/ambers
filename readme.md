## Ancient Carved Ambers Catalogue Quire conversion

Existing XML files from the current version of the catalogue (information copied from Roger Howard's Technical Overview):

- `bib.xml`  -  bibliographic entries and abbreviations in Docbook
- `cat.xml`  -  catalogue entries (objects), including their essays and footnotes in Docbook
- `essay.xml`  -  the conservation “technical essay” in a simple XML format, including footnotes and tables.
- `groups.xml`  -  the catalogue entry groups, group-object mappings, and essays and footnotes where present in a simple XML format.
- `images.xml`  -  all images/figures in the catalogue, mapped to the section(s) in which they are used, including captions and other details, in a simple XML format
- `index.xml`  -  catalogue entry index terms in a simple XML format
- `intro.xml`  -  the catalogue introduction in Docbook
- `objs.xml`  - object-specific data
- `tables.xml`  - technical essay tables

Pandoc was used to convert the above files to Markdown, though the conversion was only partially effective with files with XML Docbook schema (relevant data, formatting, and tags were often missing) and did not work with `images.xml`, `groups.xml`, and `index.xml`. Conversion to YAML format was not possible through Pandoc.

After the conversion, the contents from each file have been structured according to Quire's content model.

New files and folders have been renamed to be consistent with current catalogue url paths.

**"About" pages are not xml files** The contents of these pages were in html files at `srv/www/catalogues.getty.edu/catalogues/amber/templates/`

`amber_about.html`

`amber_about_authors.html`

`amber_credits.html`

`amber_rights.html`

`amber_rights_illustrations.html`

Part of this information is now in `publication.yml`but additional markdown pages have been created.

## Publication sections and elements

### 1. Introduction

A single file, `intro.xml`, contained all sections of the introduction.
The 18 sections are now 18 different Markdown files inside the `intro` folder, files are named as numbers according to the introduction urls. Section essays are formatted in Markdown, titles have been added to the YAML block. Type of page is "essay".
In the intro folder the file `intro.md` is the section head of the introduction.  


### 2. Catalogue entries (Objects)

Similar to `intro.xml`, all 57 catalogue entries were grouped inside a single file (`cat.xml`). The information contained in `objs.xml` was a duplicated of objects tombstone info in `cat.xml`.

Created 57 Markdown files, one for each object inside the `objects` folder. Objects metadata is now contained in the YAML block, the essays have been converted to Markdown (bibliography shortcode used).

Conversion of the objects metadata XML tags included in the YAML block:

- Object title:

XML tag example: `<title>Catalogue</title> <part id="p01"> <title>Pendant: <emphasis role="italic">Female Holding a Child (Kourotrophos)</emphasis></title>`

YAML block values: `number`, `title` and `subtitle`

- Group title:

XML tag example: `<title><emphasis role="italic">Orientalizing Group</emphasis></title>`

YAML block value: `group_name`

- Origin (object):

XML tag example: `<para>Etruscan</para>`

YAML block value: `origin`

- Date (object):

XML tag example: `<para>600-550 B.C.</para>`

YAML block value: `date`

- Dimensions(object):

XML tag example: `<para>Height: 130 mm; width: 45 mm; depth: 18 mm</para> <para>Diameter of suspension holes: 2.5 mm</para> <para>Weight: 55.2 g</para>`

YAML block value: `dimensions`

- Accession number (object):

XML tag example: `<para>77.AO.84</para>`

YAML block value: `accession_number`

- A link to the object in the museum collection catalogue is not available in the current version of the catalogue. An identification number, `dor_id`, has been added to the YAML block to facilitate the linking.

Quire doesn't require the following XML tags from catalogue entries:

``<part id="">``

``<chapter id="">``

``<abstract id="">``

``<section id="" role="">``


*Issues:*

*- Objects are cited in the essay (using a link with the accession_number). In the current catalogue there's an object pop up page that gives you basic info–probably sourced by `objs.xml`.*

### 3. Groups

A folder called groups has been created inside the objects folder. Once again, a single xml file (`groups.xml`) had all the contents. 10 group files have been created to reorganize the content. Some groups have essays formatted in Markdown with links to objects and footnotes, but other groups have no essay.

Each YAML block contains:
- Title of the group
- Objects of the group
- A "group" type has been created to display the objects in the group

XML data `group id="1"` is not used, instead this id number is used as filename.

### 4. Terms

This file (originally `index.xml`) listed terms grouping objects according subjects and themes, offered an alternative navigation to the catalogue groups. These terms are displayed with *related objects* at the bottom page menu in each object page.

The word "index" cannot be used to name files due to Hugo incompatibilities, instead the name given to the file containing the terms is `terms.yml`.

For each term, the info available in `index.xml` is: `<index id=" " parent=" " artifacts=" " title=" " order=" "/>`
From these, only `title` and `artifacts` are included in the YAML file.

### 5. Technical essay

The contents of the technical essay were split in two files `essay.xml` and `tables.xml`. Markdown formatted tables have been added to `essay.md`, so a single file has all contents.  
Other than the title, subtitle, and page *type*, the YAML block includes the essay authors (originally didn't appear in the xml file).
The essay is formatted in Markdown, it uses figures and footnotes shortcodes, tables callouts are anchor links.

### 6. Figures

The data from `images.xml` has been converted into YAML.

XML tags converted to YAML:
- `xmlid=""` to `id`
- `src=""` to `src`
- `<caption> </caption>` to `caption`

Not translated/used XML tags/data:
`<image spin=""`
`type="entry/intro/techessay"`
`version="1"`
`order="4"`

*To do's:*
*- `alt text` to be added later*
*- Images of the objects and image tiles*

### 7. References

Bibliographical data and abbreviations from `bib.xml` are structured according to the format of `references.yml`. At the moment, abbreviations are not included in `references.yml` and are being kept on a separate YAML file.

Bibliography
XML tags converted to YAML:
- `biblioentry id` to `sort_as:`
- `abbrev` to `short:`
- `bibliosource` to `full:`

In bibliographic entries of chapters of a book or volumes/issues of a journal the `bibliosource` field had link to the book/journal instead of the full reference. This link has been replaced with the full reference.

Abbreviations
XML tags converted to YAML:
- `biblioentry id` to `sort_as:`
- `abbrev` to `short:`
- `titleabbrev` to `full:`
