# Catch&ndash;lest feature comparison
Tabularised feature comparison between Catch, lest and possibly other C++ test frameworks.

Note: This is an initial draft, it is incomplete and likely contains errors.

Feature                          | Catch  | lest   | Notes |
---------------------------------|:------:|:------:|:------|
Assert expressions               |&#10003;|&#10003;| &nbsp;|
Assert exceptions                |&#10003;|&#10003;| &nbsp;|
Assert abortion (death)          | -      | -      | &nbsp;|
Assert assertions (death)        | -      | -      | &nbsp;|
Expression decomposition         |&#10003;|&#10003;| &nbsp;|
Literal suffix u, l, f           | -      |&#10003;| &nbsp;|
Colourised output                |&#10003;|&#10003;| &nbsp;|
BDD style scenarios              |&#10003;|&#10003;| &nbsp;|
Fixtures (sections)              |&#10003;|&#10003;| &nbsp;|
Fixtures (class-based)           |&#10003;| -      | &nbsp;|
Floating point comparison, approx|&#10003;|&#10003;| &nbsp;|
Floating point comparison, ulp   | -      | -      | &nbsp;|
Test selection (include/omit)    |&#10003;|&#10003;| &nbsp;|
Test selection (regexp)          | -      |&#10003;| &nbsp;|
Section selection (include)      |&#10003;| -      | &nbsp;|
Help screen                      |&#10003;|&#10003;| &nbsp;|
Abort at first failure           |&#10003;|&#10003;| &nbsp;|
Count selected tests             |&#10003;|&#10003;| &nbsp;|
List tags of selected tests      |&#10003;|&#10003;| &nbsp;|
List selected tests              |&#10003;|&#10003;| &nbsp;|
Report passing tests             |&#10003;|&#10003;| &nbsp;|
Time duration of tests           |&#10003;|&#10003;| &nbsp;|
Control order of tests           |&#10003;|&#10003;| &nbsp;|
Repeat tests                     |&#10003;|&#10003;| &nbsp;|
Auto registration of tests       |&#10003;|&#10003;| &nbsp;|
Modules of tests                 |&#10003;|&#10003;| &nbsp;|
&nbsp;                           |&nbsp;  |&nbsp;  | &nbsp;|
Suites of tests                  | -      | -      | &nbsp;|
Parameterised tests              | -      | -      | &nbsp;|
Templated tests                  | -      | -      | &nbsp;|
Test data generators             |&#10003;| -      | &nbsp;|
Hamcrest matchers                |[limited](https://github.com/philsquared/Catch/blob/master/docs/matchers.md)|[hamlest](https://github.com/martinmoene/hamlest)| &nbsp;|
Logging facility                 |&#10003;| -      | &nbsp;|
Break into debugger              |&#10003;| -      | &nbsp;|
Concurrent execution of tests    | -      | -      | &nbsp;|
Shielded execution of tests      | -      | -      | &nbsp;|

