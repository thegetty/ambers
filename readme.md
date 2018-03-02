## Ancient Carved Ambers Catalogue Quire conversion

Existing XML files (information copied from Roger Howard's Technical Overview):

- `bib.xml`  -  bibliographic entries and abbreviations in Docbook
- `cat.xml`  -  catalogue entries (objects), including their essays and footnotes in Docbook
- `essay.xml`  -  the conservation “technical essay” in a simple XML format, including footnotes and tables.
- `groups.xml`  -  the catalogue entry groups, group-object mappings, and essays and footnotes where present in a simple XML format.
- `images.xml`  -  all images/figures in the catalogue, mapped to the section(s) in which they are used, including captions and other details, in a simple XML format
- `index.xml`  -  catalogue entry index terms in a simple XML format
- `intro.xml`  -  the catalogue introduction in Docbook
- `objs.xml`  - object-specific data
- `tables.xml`  - technical essay tables

Pandoc was used to convert the above files to Markdown, though the conversion was only partially effective with files with XML Docbook schema. Despite the conversion to Markdown, relevant data and tags were often missing.

After the conversion, the contents from each file have been structured according to Quire's content model.

New files and folders have been renamed to be consistent with current catalogue url paths.

**"About" pages are not xml files** The contents of these pages are in html files at srv/www/catalogues.getty.edu/catalogues/amber/templates/

amber_about.html

amber_about_authors.html

amber_credits.html

amber_rights.html

amber_rights_illustrations.html

Part of this information is now in `publication.yml`


### Introduction

A single file, `intro.xml`, contains all sections of the introduction.
The 18 sections are now 18 different Markdown files inside the `intro` folder, files are named as numbers according to the introduction urls. Section essays are formatted in Markdown, titles have been added to the yaml block. Type of page is "essay".
In the intro folder the file `intro.md` is the section head of the introduction.  

*Issue:*
*How to cite a footnote from a different page?*


### Catalogue entries (Objects)

Similar to `intro.xml`, all 57 catalogue entries are grouped inside a single file (`cat.xml`). The information contained in `objs.xml` is a duplicated of objects tombstone info in `cat.xml`.

Created 57 Markdown files, one for each object inside the `objects` folder. Objects metadata is now contained in the yaml block, the essays have been converted to Markdown (bibliography shortcode used).

Objects metadata tags included in the YAML block:

- Group title:

`<title><emphasis role="italic">Orientalizing Group</emphasis></title>`

- Object title:

`<title>Pendant: <emphasis role="italic">Female Holding a Child (Kourotrophos)</emphasis></title>`

- Origin (object):

`<para>Etruscan</para>`

- Year (object):

`<para>600-550 B.C.</para>`

- Dimensions(object):

``<para>Height: 130 mm; width: 45 mm; depth: 18 mm</para>
<para>Diameter of suspension holes: 2.5 mm</para>
<para>Weight: 55.2 g</para>``

- Accession number (object):

`<para>77.AO.84</para>`

Quire doesn't require the following XML tags from catalogue entries:

``<part id="">``

``<chapter id="">``

``<abstract id="">``

``<section id="" role="">``


*Issues:*

*- Objects are cited in the essay (using a link with the accession_number). In the current catalogue there's an object pop up page that gives you basic info–probably sourced by `objs.xml`.*

*- On object metadata, year has been changed to date.*

*- There are no links to the objects in the museum collection catalogue, worth adding?*

*- YAML block for object, use a metadata standard (Dublin Core, etc.)?*

### Groups

A folder called groups has been created inside the objects folder. Once again, a single xml file (`groups.xml`) had all the contents of the groups. 10 group files have been created to reorganize the content.

Each YAML block contains:
- Title of the group
- Objects of the group
- A "Group" type has been created to display the objects in the group

XML data `group id="1"` is not used, instead the filename is a number.

Some groups have essays formatted in Markdown with links to objects and footnotes, but other groups have no essay.

### Terms

This file lists terms grouping objects according subjects and themes, offers an alternative navigation to the catalogue groups. These terms are displayed with *related objects* along with the bibliography and footnotes at the bottom page menu in each object page.

The word "index" cannot be used to name files due to Hugo incompatibilities, instead the name given to the file containing the terms is `terms.yml`.

For each term, the info available in `index.xml` is: `<index id=" " parent=" " artifacts=" " title=" " order=" "/>`
From these, only the *title* and *artifacts* are included in the YAML file.

### Technical essay

The contents of the technical essay were split in two files `essay.xml` and `tables.xml`. Markdown formatted tables have been added to `essay.md`, so a single file has all contents.  
Other than the title, subtitle, and page *type*, the YAML block includes the essay authors (originally didn't appear in the xml file).
The essay is formatted in Markdown and uses figures and footnotes shortcodes.

*Issues:*
*Not sure about the syntax for anchor links to tables. [Is this a good reference?](https://docs.microsoft.com/en-us/vsts/collaborate/Markdown-guidance#anchor-links)*

### Figures

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

### References

Bibliographical data and abbreviations from `bib.xml` are structured according to the YAML format of `references.yml`.

Bibliography
XML tags converted to YAML:
- `biblioentry id` to `sort_as:`
- `abbrev` to `short:`
- `bibliosource` to `full:`

Abbreviations
XML tags converted to YAML:
- `biblioentry id` to `sort_as:`
- `abbrev` to `short:`
- `titleabbrev` to `full:`

*Issues:*
*At the moment, abbreviations are not included in `references.yml` and are being kept on a separate YAML file.*
