# JOLux Ontology

This repository is used to document the JOLux ontology of the [Fedlex](https://www.fedlex.admin.ch/en) platform of the [Federal Chancellery](https://www.bk.admin.ch/bk/en/home.html).

## Webpage

The webpage of this repository will be built on every commit via [GitHub Actions](https://github.com/swiss/fedlex-jolux/actions) with the help of [Sphinx](https://www.sphinx-doc.org/en/master/) and deployed to https://swiss.github.io/fedlex-jolux

## How to Contribute

Please open [issues](https://github.com/swiss/fedlex-jolux/issues) on this repository or provide [pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) for contributions.

> [!CAUTION]
> 2024-11-22: This is an ongoing project between the Federal Chancellery and the [Institute for Public Sector Transformation](https://www.bfh.ch/en/research/research-areas/public-sector-transformation/) of the [Bern University of Applied Sciences](https://www.bfh.ch/en/). The content is not yet stable. Further updates will follow.

## Local Build Instructions

For building the JOLux ontology documentation locally, follow these instructions:

### Clone the Repository

```bash
git clone https://github.com/swiss/fedlex-jolux.git
cd fedlex-jolux
```

### Set Up the Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
```

### Build the Documentation

```bash
sphinx-build doc _build # build HTML
sphinx-build -b rinoh doc _build/pdf # build PDF
```
