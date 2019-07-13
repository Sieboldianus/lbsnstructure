![version](https://lbsn.vgiscience.org/concept/version.svg) ![pypi version](https://lbsn.vgiscience.org/concept/pypi.svg) ![pipeline](https://lbsn.vgiscience.org/concept/pipeline.svg)

## LBSNSTRUCTURE

A common language independent and cross-network social-media datascheme. There are several motivations for prividing a common LBSN interchange data structure. Firstly, the GDPR directly requests Social Media Network operators to allow users to transfer accounts and data inbetween services.
While there are attempts by Google, Facebook etc. (see data-transfer-project), it is not currently possible. With this structure concept, we follow an independent road. A primary goal is to systematically characterize LBSN data aspects in a common scheme that enables privacy-by-design for connected software, transfer scripts and database design.

## Description

This is the first version of a common, standardized conceptual data model for analyzing, comparing and relating information of different location based social networks (LBSN). With the structure, we focus on three important directions that are of importance to the whole Priority Program:

- Adaption: Case Studies for application of this structure and exemplary visualizations
- Guides: Theoretic description and guidelines of concept and technical implementation
- Tools: Developing example base functions and algorithms for information retrieval and inter-linkage of data entities

One example output is a common interactive interface based on [Metabase](https://github.com/metabase/metabase), a framework that allows analysts to interactively explore and visualize data based on live connections to multiple types of databases.
Here's one visualization from our Heidelberg Example dataset, which shows all other places visited by people who went to the "Hörnchen" bar at least once. This could be an entry point for analysts to study the spatial frequentation behaviour of a specific user type in Heidelberg (e.g. "Hörnchen Visitors"), for example.

<iframe    src="https://metabase.vgiscience.org/public/question/13ed0a1e-71e3-4505-bff2-2892d831d896"    frameborder="0"    width="800"    height="600"    allowtransparency></iframe>

Furthermore, we decided to describe our common lbsn structure with the platform and language independent [Proto Buffers](https://developers.google.com/protocol-buffers/). [These files](https://gitlab.vgiscience.de/lbsn/concept) can be used to compile and implement our proposed structure in any language such as Python, Java or C++.

## License

* MIT License

## Authors

* Alexander Dunkel (TU Dresden)
* Marc Löchner (TU Dresden)
* Filip Krumpe (FMI Universität Stuttgart)