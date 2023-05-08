# Changelog

<!--next-version-placeholder-->

## v3.0.0 (2023-05-08)
### Fix
* Add lbsnstructure namespace ([`a8105c9`](https://github.com/Sieboldianus/lbsnstructure/commit/a8105c990e9007fb8737cad261e3459df3eb24ad))
* Import for protoc_gen_doc ([`9fc01b3`](https://github.com/Sieboldianus/lbsnstructure/commit/9fc01b341e0a0f480522775f801be8544799f03d))

### Breaking
* This update requires all import to be updated ([`a8105c9`](https://github.com/Sieboldianus/lbsnstructure/commit/a8105c990e9007fb8737cad261e3459df3eb24ad))

e.g. for Python:

from
```
from lbsnstructure import lbsnstructure_pb2 as lbsn
```

to
```
import lbsnstructure as lbsn
```

### Documentation
* Update php instructions in Readme ([`71cc3cd`](https://github.com/Sieboldianus/lbsnstructure/commit/71cc3cd3931fe170ae171d14f6ba2018241560dd))
* Update commands to relfect new namespace; add linebreaks ([`ec4652c`](https://github.com/Sieboldianus/lbsnstructure/commit/ec4652cd35a5bedfa49b2f8df2a1f54794fd328c))

## v2.0.2 - v2.0.5(2023-04-12)

- CI releases

## v2.0.1 (2023-04-12)
### Fix
* Semantic release ([`a359ab7`](https://github.com/Sieboldianus/lbsnstructure/commit/a359ab782ff12a9ca024f0f43ddddd0e57fed463))

## v2.0.0 (2023-04-12)
### Documentation
* Merge changelog files ([`d956e39`](https://github.com/Sieboldianus/lbsnstructure/commit/d956e39fdb07cf9cf6b75cb47a412b50ba91b90a))

## v1.4.0 (2023-04-12)
### Feature
* Add additional example Origin Networks ([`ce6920c`](https://github.com/Sieboldianus/lbsnstructure/commit/ce6920c416005ff998f0e9e1e77abc58b3c76063))

### Fix
* Relative import in proto files ([`248094b`](https://github.com/Sieboldianus/lbsnstructure/commit/248094b944323bd885bcfdb93739efc381f321bb))

### Documentation
* Update meaning for topical/thematic ([`c09996a`](https://github.com/Sieboldianus/lbsnstructure/commit/c09996aef572ea8a531963d34377f5e7d1665a5a))
* Update link to lbsn docs ([`8894a9f`](https://github.com/Sieboldianus/lbsnstructure/commit/8894a9fe260bd67dafcc6e36c408500f4dbfff81))
* Fix links to lbsn docs ([`124faf5`](https://github.com/Sieboldianus/lbsnstructure/commit/124faf534f74caf0d333a3e9584e56f0751ab7e9))
* Move docs to external repo ([`0f2fa8c`](https://github.com/Sieboldianus/lbsnstructure/commit/0f2fa8c9ee02ed2a05d5ef96c38e86337554f696))
* Add comments and split proto into 4 facets ([`819f388`](https://github.com/Sieboldianus/lbsnstructure/commit/819f388187b7bbd40678cd951ed94c3c3feb6994))

## v0.1.61
### Feature
* Extended structure for additional place attributes

## v0.1.5
### Feature
* Initial Structure
* Python Compilation and Example Jupyter Notebook
* Readme: Overview & Motivation