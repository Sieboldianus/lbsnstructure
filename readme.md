## Proto Buffers Standardization of Social Media Data Structures and Cross-Network Interrelationships

This is the first version of a common, standardized conceptual data model for analyzing, comparing and relating information of different location based social networks (LBSN). With the structure, we focus on three important directions that are of importance to the whole Priority Program:

- Adaption: Case Studies for application of this structure and exemplary visualizations
- Guides: Theoretic description and guidelines of concept and technical implementation
- Tools: Developing example base functions and algorithms for information retrieval and inter-linkage of data entities

One example output is a common interactive interface based on [Metabase](https://github.com/metabase/metabase), a framework that allows analysts to interactively explore and visualize data based on live connections to multiple types of databases.
Here's one visualization from our Heidelberg Example dataset, which shows all other places visited by people who went to the "Hörnchen" bar at least once. This could be an entry point for analysts to study the spatial frequentation behaviour of a specific user type in Heidelberg (e.g. "Hörnchen Visitors"), for example.

<iframe    src="https://metabase.vgiscience.org/public/question/13ed0a1e-71e3-4505-bff2-2892d831d896"    frameborder="0"    width="800"    height="600"    allowtransparency></iframe>

Furthermore, we decided to describe our common lbsn structure with the platform and language independent [Proto Buffers](https://developers.google.com/protocol-buffers/). [These files](https://gitlab.vgiscience.de/lbsn/concept) can be used to compile and implement our proposed structure in any language such as Python, Java or C++.

[Filip](https://gitlab.vgiscience.de/Filip) demonstrated how to implement a [Mapping Algorithms](https://gitlab.vgiscience.de/Filip/point_location) for relating two different sources for enriching information: OSM Polygons to Twitter, Instagram or Facebook Places. Such algorithms are the key to relating information coming from different datasources, which helps us to get a better overall understanding of relationships.

Finally, [Nida](https://gitlab.vgiscience.de/nida.cilasun) provided a specific Case Study for applying our structure. As a result, her Topic Modeling visualizations originally developed on Twitter data could be directly applied and tested with other data, in this case to the Heidelberg example datasets from Flickr and Instagram. This gives analysts the ability to test and compare suitability of algorithms across different networks and datasets.

The background technical infrastructure was administered by [Marc](https://gitlab.vgiscience.de/ml), who integrated Proto Buffers with Git, which further links to our PostgreSQL database. Interactive online interfaces such as [https://pgadmin.vgiscience.org/](pgadmin.vgiscience.org) or [https://metabase.vgiscience.org/](metabase.vgiscience.org) can be used by anyone with individual connections to private databases.

## Quick Start

To compile ProtoBuffers structure in your language, get the [current release for your OS](https://developers.google.com/protocol-buffers/docs/downloads), clone this repository (or download [Structure.proto](lbsnstructure/Structure.proto)) and execute (Python example):

`protoc --python_out=examples/python lbsnstructure/Structure.proto` 
`protoc --python_out=examples/python lbsnstructure/external/timestamp.proto`

Replace `--python` with your language of choice. 

If successful, you will see a file generated in output directory in your language, e.g. `lbsnstructure/Structure_pb2.py` ([Note](https://developers.google.com/protocol-buffers/docs/reference/python-generated) that currently both proto2 and proto3 append "_pb2.py" to generated filenames). 
This file can be imported to your tool (for python, `from lbsnstructure.Structure_pb2 import Origin, CompositeKey, Country` .

Have a look at the [Jupyter Notebook](examples/python/StructureTest.ipynb) for a brief Guide of using the structure in Python.