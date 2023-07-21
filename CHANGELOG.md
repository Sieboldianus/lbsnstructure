# Changelog

<!--next-version-placeholder-->

## v3.2.0 (2023-07-21)
### Feature
* Correct namin of eBird Origin, add Tripadvisor origin ([`4decc33`](https://github.com/Sieboldianus/lbsnstructure/commit/4decc3391924bf6bdb17ae3932c3849c74ba7c13))

### Fix
* Improve raming for topic_group attribute ([`462500c`](https://github.com/Sieboldianus/lbsnstructure/commit/462500cfdcddd0ecbc1a62be7b2e85107aedd3cc))

### Documentation
* Fix sample code ([`8fe9a1f`](https://github.com/Sieboldianus/lbsnstructure/commit/8fe9a1f259c69b1330b4cd6aa26ccf3d42e7d1ff))
* Add reference to Github ([`84b47cd`](https://github.com/Sieboldianus/lbsnstructure/commit/84b47cd24965350a1492b7727706276a910858ae))
* Update instructions to generate pyi py.typed files alongside ([`113895c`](https://github.com/Sieboldianus/lbsnstructure/commit/113895c5525d6c8d664317a5f2449577981ae29a))

## v3.1.0 (2023-05-12)
### Feature
* Add Post.post_topic (e.g. posts assigned to photo groups on Flickr or submissions on Reddit assigned to subreddits ([`902241f`](https://github.com/Sieboldianus/lbsnstructure/commit/902241ff7f0b80b9f2bc2875fd36387c918f5c03))
* Add Post.PostType.LINK (e.g. a Link Share on Reddit) ([`57b90c6`](https://github.com/Sieboldianus/lbsnstructure/commit/57b90c69faa484d6440607c0a15e36f1b1f4c5f9))

### Documentation
* Clarify filter attribute for topical.Post ([`a751676`](https://github.com/Sieboldianus/lbsnstructure/commit/a75167672a26afc5681e423c3340230139b0f530))
* Update sample code in Readme.md ([`a236cd7`](https://github.com/Sieboldianus/lbsnstructure/commit/a236cd7f299330dbe50dd3a51bf305072808d850))

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