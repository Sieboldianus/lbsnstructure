![php](https://lbsn.vgiscience.org/structure/protobuf/version.svg) ![pipeline](https://lbsn.vgiscience.org/structure/protobuf/pipeline.svg) ![php](https://lbsn.vgiscience.org/structure/protobuf/php-version.svg) ![python](https://lbsn.vgiscience.org/structure/protobuf/python-version.svg)

## LBSNSTRUCTURE

A common language independent and cross-network social-media datascheme.

**Important:** In order to encapsulate and share code across different package managers 
(pypi, composer), we make use of _git_ _submodules_. To clone this super-repository, 
including all its example-folders, use:

```bash
git clone --recursive
```

On Github, the python compiled repository can be found here:
https://github.com/Sieboldianus/lbsnstructure-python

## Description

This is the first version of a common, standardized conceptual data model for analyzing, 
comparing and relating information of different location based social networks (LBSN). 
With the structure, we focus on three important directions that are of importance 
to the whole Priority Program:

- Adaption: Case Studies for application of this structure and exemplary visualizations

- Guides: Theoretic description and guidelines of concept and technical implementation

- Tools: Developing example base functions and algorithms for information retrieval 
  and inter-linkage of data entities

We decided to describe our common lbsn structure with the platform and language independent 
[Proto Buffers](https://developers.google.com/protocol-buffers/). [These files](https://gitlab.vgiscience.de/lbsn/concept) 
can be used to compile and implement our proposed structure in any language such 
as Python, Java or C++.

## Docs

The full documentation is available at
[lbsn.vgiscience.org/structure/protobuf/docs/](https://lbsn.vgiscience.org/structure/protobuf/docs/).

## Quick Start

```
apt install -y protobuf-compiler
protoc --version # Ensure compiler version is >= 3.19.0.
```

Optionally, [install binary](https://grpc.io/docs/protoc-installation/):
```
PB_REL="https://github.com/protocolbuffers/protobuf/releases"
curl -LO $PB_REL/download/v3.19.0/protoc-3.19.0-linux-x86_64.zip
unzip protoc-3.19.0-linux-x86_64.zip -d $HOME/.local
export PATH="$PATH:$HOME/.local/bin"
```

To compile ProtoBuffers structure in your language, get the 
[current release for your OS](https://developers.google.com/protocol-buffers/docs/downloads), 
clone this repository (or download [Structure.proto](lbsnstructure/Structure.proto)).

Python example:

```bash
protoc --python_out=examples/python lbsnstructure/interlinkage.proto \
    && protoc --python_out=examples/python/src/ lbsnstructure/social.proto \
    && protoc --python_out=examples/python/src/ lbsnstructure/spatial.proto \
    && protoc --python_out=examples/python/src/ lbsnstructure/temporal.proto \
    && protoc --python_out=examples/python/src/ lbsnstructure/topical.proto \
    && protoc --python_out=examples/python/src/ google/protobuf/timestamp.proto \
    && protoc --python_out=examples/python/src/ google/protobuf/duration.proto
```

Replace `--python` with your language of choice, e.g. for php:  

```bash
protoc --php_out=examples/php/ lbsnstructure/interlinkage.proto \
    && protoc --php_out=examples/php lbsnstructure/social.proto \
    && protoc --php_out=examples/php lbsnstructure/spatial.proto \
    && protoc --php_out=examples/php lbsnstructure/temporal.proto \
    && protoc --php_out=examples/php lbsnstructure/topical.proto \
    && protoc --php_out=examples/php/ google/protobuf/timestamp.proto \
    && protoc --php_out=examples/php/ google/protobuf/duration.proto
```

Optionally, install `mypy-protobuf`, to generate type stubs for proto files:
```bash
python3 -m venv mypy-proto_env
source ./mypy-proto_env/bin/activate
pip install mypy-protobuf
protoc --python_out=examples/python lbsnstructure/interlinkage.proto \
    && protoc --python_out=examples/python/src/ --mypy_out=examples/python/src/ lbsnstructure/social.proto \
    && protoc --python_out=examples/python/src/ --mypy_out=examples/python/src/ lbsnstructure/spatial.proto \
    && protoc --python_out=examples/python/src/ --mypy_out=examples/python/src/ lbsnstructure/temporal.proto \
    && protoc --python_out=examples/python/src/ --mypy_out=examples/python/src/ lbsnstructure/topical.proto \
    && protoc --python_out=examples/python/src/ --mypy_out=examples/python/src/ google/protobuf/timestamp.proto \
    && protoc --python_out=examples/python/src/ --mypy_out=examples/python/src/ google/protobuf/duration.proto
```

If successful, you will see a file generated in output directory in your language, e.g. `lbsnstructure/lbsnstructure_pb2.py` ([Note](https://developers.google.com/protocol-buffers/docs/reference/python-generated) that currently both proto2 and proto3 append "_pb2.py" to generated filenames). 

This file can be imported to your tool.

E.g. for python:

```python
import lbsnstructure as lbsn
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