Detecting polygon self-intersection in Javascript
============================================
An implementation of the O((n + k) log n) Bentley–Ottmann sweep-line algorithm for detecting crossings in a set of line segments (originally forked from Simon Tokumine's iteration of `sweepline`). The aim was to make something to rapidly detect self-intersecting polygons for client side validation before serialization and storage. However, this implementation can be used for server-side validations (except it being more a statement of intent than actual production ready code).

* Note: This fork does not contain any client side or browser examples - this entirely server-side validation of floor plan data and geometries.


Development
===========
* node.js 6.9.1
* mocha
* chai

Notable Changes to Implementation
==============================================
1. ECMAScript classes that provide a much simpler and clearer syntax to create objects and deal with inheritance.
2. Point: refactor the `isLeftofSegment` of Class `Point` as a static method.
3. Polygon: fix implicit global variables; rename `simple_polygon` to `isSimplePolygon`; refactor the logic according to the rest of the classes.
4. RedBlackTree: fix the implicit global variables in Kevin Lindsey's implementation.
5. Sweepline: Rename to Bentley-Ottman; improvements to SweepLine and SweepLine segment logic; refactor the logic according to the new constructor patterns.
6. EventQueue: add the `next` method; refactor the logic according to the new constructor pattern.
7. Updates to the test specification for floor plan data.


Reference Implementation
==============================================
This is the implementation of the Bentley–Ottmann sweep-line algorithm with an AVL tree: http://geomalgorithms.com/a09-_avl_code.html#SweepLineClass.


In use is a variant with a Red-Black tree in lieu of the AVL tree. It has some adjustments and modified methods (for example - no rotateLeft and rotateRight methods).


Tests
======
To run tests, please ensure that you have `node.js`, `mocha`, `chai` and `npm` installed:

$ npm test

Note that this implementation currently doesn't validate polygons that share the same start and end vertex.


License
========
This project is in the worldwide [public domain](LICENSE.md). 

> This project is in the public domain within the United States, and copyright and related rights in the work worldwide are waived through the [CC0 1.0 Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/).