# JOLux Ontology

This repository is used to document the JOLux ontology of the [Fedlex](https://www.fedlex.admin.ch/en) platform of the [Federal Chancellery](https://www.bk.admin.ch/bk/en/home.html).

## How to Contribute

Please open [issues](https://github.com/swiss/fedlex-jolux/issues) on this repository or provide [pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) for contributions.

> [!CAUTION]
> 2026-02-23: This is an ongoing project between the Federal Chancellery and the [Institute for Public Sector Transformation](https://www.bfh.ch/en/research/research-areas/public-sector-transformation/) of the [Bern University of Applied Sciences](https://www.bfh.ch/en/). The content is mainly stable. Some further updates will still follow.

## Maintainers Manual

The following instructions are for maintainers of this repository that may not be familiar with [Sphinx](https://www.sphinx-doc.org/en/master/) and the related tools.

### Change Pages

To change the content of the documentation, the `*.md` files in the `doc` folder can be directly edited.

### Change Figures

All the figures are stored in the `doc/img` folder and can be edited with [draw.io](https://app.diagrams.net/). After editing a figure, export it as PNG and replace the existing file in the `doc/img` folder. PNG was chosen because of the better rendering in the PDF version of the documentation.

> [!TIP]
> Export the figures with a high resolution to ensure good quality in the PDF version.

### Add New Pages

To add a new page to the documentation, create a new `*.md` file in the `doc` folder and add it to the `doc/index.md` file by including a link to it in the appropriate section. The title for the navigation will be taken from the first heading in the new `*.md` file.

Also add an entry for the new page in the `doc/reference.md` file in the section "Concepts".

### Definitions

The idea is, to have the definitions of the classes and properties in the JOLux ontology in the continuous text of the documentation. To add a new definition, add a admonition with the name of the class or property as title and the definition as content directly in the markdown file. For example:

```markdown
:::{admonition} jolux:parliamentDraftId
:class: note
:name: parliamentDraftId
The data property **jolux:parliamentDraftId** is used to connect a [jolux:Draft](#Draft) to the identifier of the parliamentary process that leads to the new legal resource.
:::
```

Afterwards, add this definition to the reference page in the appropriate section (classes, datatype properties, object properties) with a link to the definition in the continuous text. For example:

```markdownmarkdown
## JoLux Datatype Properties

Others:

- [parliamentDraftId](#parliamentDraftId)
```

Use this definition for linking occurences of the class or property in the continuous text. For example:

```markdown
The data property [jolux:parliamentDraftId](#parliamentDraftId) is used in...
```

### Build the Webpage

The webpage of this repository will be automatically built on every commit via [GitHub Actions](https://github.com/swiss/fedlex-jolux/actions) with the help of [Sphinx](https://www.sphinx-doc.org/en/master/) and deployed to https://swiss.github.io/fedlex-jolux

### Local Build Instructions

For building the JOLux ontology documentation locally, follow these instructions:

**Clone the Repository**

```bash
git clone https://github.com/swiss/fedlex-jolux.git
cd fedlex-jolux
```

**Set Up the Virtual Environment**

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
```

**Build the Documentation**

```bash
sphinx-build doc _build # build HTML in the _build folder
sphinx-build -b rinoh doc _build/pdf # build PDF
```
