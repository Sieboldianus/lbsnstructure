![version](https://lbsn.vgiscience.org/concept/version.svg) ![pypi version](https://lbsn.vgiscience.org/concept/pypi.svg) ![pipeline](https://lbsn.vgiscience.org/concept/pipeline.svg)

## LBSNSTRUCTURE

A common language independent and cross-network social-media datascheme.

## Description

This is the first version of a common, standardized conceptual data model for analyzing, comparing and relating information of different location based social networks (LBSN). With the structure, we focus on three important directions that are of importance to the whole Priority Program:

- Adaption: Case Studies for application of this structure and exemplary visualizations
- Guides: Theoretic description and guidelines of concept and technical implementation
- Tools: Developing example base functions and algorithms for information retrieval and inter-linkage of data entities

One example output is a common interactive interface based on [Metabase](https://github.com/metabase/metabase), a framework that allows analysts to interactively explore and visualize data based on live connections to multiple types of databases.
Here's one visualization from our Heidelberg Example dataset, which shows all other places visited by people who went to the "Hörnchen" bar at least once. This could be an entry point for analysts to study the spatial frequentation behaviour of a specific user type in Heidelberg (e.g. "Hörnchen Visitors"), for example.

<iframe    src="https://metabase.vgiscience.org/public/question/13ed0a1e-71e3-4505-bff2-2892d831d896"    frameborder="0"    width="800"    height="600"    allowtransparency></iframe>

Furthermore, we decided to describe our common lbsn structure with the platform and language independent [Proto Buffers](https://developers.google.com/protocol-buffers/). [These files](https://gitlab.vgiscience.de/lbsn/concept) can be used to compile and implement our proposed structure in any language such as Python, Java or C++.

## Docs

The full Documentation is available at [lbsn.vgiscience.org/concept/docs/](https://lbsn.vgiscience.org/concept/docs/).

## Quick Start

To compile ProtoBuffers structure in your language, get the [current release for your OS](https://developers.google.com/protocol-buffers/docs/downloads), clone this repository (or download [Structure.proto](lbsnstructure/Structure.proto)) and execute (Python example):

`protoc --python_out=examples/python lbsnstructure/lbsnstructure.proto`  
`protoc --python_out=examples/python google/timestamp.proto`  

Replace `--python` with your language of choice. 

If successful, you will see a file generated in output directory in your language, e.g. `lbsnstructure/lbsnstructure_pb2.py` ([Note](https://developers.google.com/protocol-buffers/docs/reference/python-generated) that currently both proto2 and proto3 append "_pb2.py" to generated filenames). 
This file can be imported to your tool (for python, `from lbsnstructure.lbsnstructure_pb2.py import Origin, CompositeKey, Country` .

Have a look at the [python compiled example repository](https://gitlab.vgiscience.de/lbsn/lbsnstructure-python) and the [Jupyter Notebook](https://gitlab.vgiscience.de/lbsn/lbsnstructure-python/blob/master/StructureTest.ipynb) for a brief guide on using the structure in Python.

## Changelog

see [CHANGELOG](CHANGELOG)