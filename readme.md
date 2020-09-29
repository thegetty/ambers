This is the repository for “Ancient Carved Ambers in the J. Paul Getty Museum,” by Faya Causey. This digital book was first published January 10, 2012, by the J. Paul Getty Museum. On November 26, 2019, it was moved to a new publishing platform and new paperback and ebook editions were released. It is now available online at [http://www.getty.edu/publications/ambers/](http://www.getty.edu/publications/ambers/) and may be downloaded free of charge in multiple formats.

## About the Book

This catalogue presents a group of remarkable amber carvings from the J. Paul Getty Museum’s collection—the second largest body of this material in the United States and one of the most important in the world. The fifty-six Etruscan, Greek, and Italic carved ambers date from around 650 to 300 B.C.

Offering a full description of each piece, including typology, style, chronology, provenance, condition, and iconography, the catalogue is preceded by a general introduction to ancient amber. Through exquisite visual examples and vivid excerpts from classical texts, this book examines the myths and legends woven around amber—its employment in magic and medicine, its transport and carving, and its incorporation into jewelry, amulets, and other objects of prestige.

## Using this Repository

This is one in series of multiformat publications using [Quire](http://www.getty.edu/publications/digital/platforms-tools.html), Getty’s new publishing framework. Quire is currently in private beta, with the goal of it being released as free and open source software in the future. In the meantime, users are encouraged to request access at http://bit.ly/quire-beta. This repository can also be run locally to build the online site (but not the PDF or ebook formats) with [Hugo](https://gohugo.io/), the [static site generator](https://www.smashingmagazine.com/2015/11/modern-static-website-generators-next-big-thing/) at the core of Quire.

We are dedicated to maintaining this publication for years to come at the permanent URL, [http://www.getty.edu/publications/amberss/](http://www.getty.edu/publications/ambers/), and in its various formats and incarnations. For any updates to the book, we will be following something between an app and traditional book publication model. Updates will only be made in regulated chunks as formal revisions and new editions and will always be thoroughly documented here in the repository, as well as in the revision history included with each of the book’s many formats.

The primary content pieces of the book can be found in the `data` and `content` directories. The master branch represents the current, published edition at all times, and the revisions branch, when present, will show changes currently under consideration. We invite you to submit suggestions or corrections via pull request on the revisions branch, by posting an issue, or by emailing us at [pubsinfo@getty.edu](mailto:pubsinfo@getty.edu).

## Development Notes

This project was last built with the following software versions:

- Quire 0.18.0
- Node 12.18.3 / npm 6.14.6
- Hugo 0.72
- PrinceXML 13.5
- Pandoc 2.10.1

While the core Quire Starter Theme was used, a number of customizations were made for this publication:

- Add a contents page type to show all object entries, even from other sections
- Customize cover design to match other JPGM collection catalogues
- Add shortcodes for pop-up abbreviations and abbreviations table
- Add shortcodes for pop-up object images, which show thumbnail of image and provide a link to the entry page for that object
- Use the `url` attribute in page yaml to match publication URLs of this version with that of the original 2012 version of the catalogue

Within the theme itself, changes were made to the `source/css/variables.scss` and `source/css/print.scss` files. Outside of the theme, customizations can be found in the project’s `layouts` directory, and in `static/css/custom.css`.

### Images Submodule

Many of figure images for *Mummy Portraits* are licensed from third parties for use exclusively in this publication. As such, they are kept in a separate, private repository, https://github.com/thegetty/ambers-images/, which is linked to this main publication repository as a submodule in `static/img/figures/`. When cloning this repo for further development, you’ll permissions for the private repository and will need to clone recursively in order to clone both the main repo and the submodule.

```
git clone --recursive https://github.com/thegetty/ambers.git
```

### Original 2012 Edition

The first, 2012 edition of this publication was built by the museum and hosted at http://museumcatalogues.getty.edu/amber/. When the 2019 edition was launched, the other was taken down and archived with Getty’s institutional archives. A version may also be through the Internet Archive at https://web.archive.org/web/20191001140216/http://museumcatalogues.getty.edu/amber/.

## License

© 2019 J. Paul Getty Trust

Except where otherwise noted, this work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/). Figures 3, 9–17, 22–24, 28, 32, 33, 36, 38, 40, 51, and 54 are reproduced with the permission of the rights holders acknowledged in captions and are expressly excluded from the CC BY license covering the rest of this publication. These images may not be reproduced, copied, transmitted, or manipulated without consent from the owners, who reserve all rights.
