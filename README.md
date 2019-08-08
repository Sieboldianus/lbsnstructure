![php](https://lbsn.vgiscience.org/concept/version.svg) ![pipeline](https://lbsn.vgiscience.org/concept/pipeline.svg) ![php](https://lbsn.vgiscience.org/concept/php-version.svg) ![python](https://lbsn.vgiscience.org/concept/python-version.svg)

## LBSNSTRUCTURE

A common language independent and cross-network social-media datascheme.

**Important:** In order to encapsulate and share code across different package managers (pypi, composer), we make use of _git_ _submodules_. To clone this super-repository, including all its example-folders, use:

```bash
git clone --recursive
```

## Description

This is the first version of a common, standardized conceptual data model for analyzing, comparing and relating information of different location based social networks (LBSN). With the structure, we focus on three important directions that are of importance to the whole Priority Program:

- Adaption: Case Studies for application of this structure and exemplary visualizations
- Guides: Theoretic description and guidelines of concept and technical implementation
- Tools: Developing example base functions and algorithms for information retrieval and inter-linkage of data entities

We decided to describe our common lbsn structure with the platform and language independent [Proto Buffers](https://developers.google.com/protocol-buffers/). [These files](https://gitlab.vgiscience.de/lbsn/concept) can be used to compile and implement our proposed structure in any language such as Python, Java or C++.

## Docs

The full documentation is available at [lbsn.vgiscience.org/concept/docs/](https://lbsn.vgiscience.org/concept/docs/).

## Quick Start

To compile ProtoBuffers structure in your language, get the [current release for your OS](https://developers.google.com/protocol-buffers/docs/downloads), clone this repository (or download [Structure.proto](lbsnstructure/Structure.proto)) and execute (Python example):

```bash
protoc --python_out=examples/python lbsnstructure/lbsnstructure.proto
protoc --python_out=examples/python google/protobuf/timestamp.proto
```

Replace `--python` with your language of choice, e.g. for php:  

```bash
protoc --php_out=examples/php/ lbsnstructure/lbsnstructure.proto
protoc --php_out=examples/php/ google/protobuf/timestamp.proto
```

If successful, you will see a file generated in output directory in your language, e.g. `lbsnstructure/lbsnstructure_pb2.py` ([Note](https://developers.google.com/protocol-buffers/docs/reference/python-generated) that currently both proto2 and proto3 append "_pb2.py" to generated filenames). 

This file can be imported to your tool.

E.g. for python:

```python
from lbsnstructure.lbsnstructure_pb2.py import lbsnOrigin, CompositeKey, lbsnCountry
```

Have a look at the [python compiled example repository](https://gitlab.vgiscience.de/lbsn/lbsnstructure-python) and the [Jupyter Notebook](https://gitlab.vgiscience.de/lbsn/lbsnstructure-python/blob/master/StructureTest.ipynb) for a brief guide on using the structure in Python.

## Semantic release

We make use of automatic versioning using semantic-release workflow.
To auto-increase version based on commits, use:

```bash
semantic-release publish
```

## Changelog

see [CHANGELOG](CHANGELOG)