# Catch&ndash;doctest&ndash;lest feature comparison
Tabularised feature comparison between Catch, doctest and lest C++ test frameworks.

[Skip to the feature comparison](#table).

Note 1: This is an initial draft, it is incomplete and likely contains errors.  
Note 2: Catch-2 is not yet released.

Ideas, additions, corrections, signaling omissions, etc. welcome! 

<!--
**Some history**

- [Kevlin Henney on Rethinking Unit Testing in C++](http://accu.org/index.php/accu_branches/accu_london/accu_london_may_2010)  ([Video](http://skillsmatter.com/podcast/agile-testing/kevlin-henney-rethinking-unit-testing-in-c-plus-plus)).
- December 2010 - Catch (blog)
  - [The Ultimate C++ Unit Test Framework](http://www.levelofindirection.com/journal/2010/5/21/the-ultimate-c-unit-test-framework.html)
  - [Unit Testing in C++ and Objective-C just got easier](http://www.levelofindirection.com/journal/2010/12/28/unit-testing-in-c-and-objective-c-just-got-easier.html) 
- June 2013 - lest
- May 2014 - doctest

<p style="height:5em;"></style>
-->
<a id="table"></a>

Feature                           | [doctest](#DOT)| [Catch-1](#CA1)| [Catch-2](#CA2)| [lest](#LST)| Notes |
----------------------------------|:------:|:------:|:------:|:-------|-------|
**C++ standard related**          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
C++ standard                      | C++98  | C++98  | C++11  | C++11  | &nbsp;|
Can work without exceptions       |&#10003;| -      | -      | -      | reduced functionality |
Requires RTTI                     | -      | ?      | ?      | -      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Fields of use**                 | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Desktop                           |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Embedded (tiny)                   | ?      | ?      | ?      | ?      | &nbsp;|
Embedded (largish)                | ?      | ?      | ?      |&#10003;| &nbsp;|
Operating System                  | ?      | ?      | ?      |&#10003;| lest: IncludeOS |
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Test organisation**             | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Suites of tests                   |&#10003;| -      | -      | -      | &nbsp;|
Fixtures (sections)               |&#10003;|&#10003;|&#10003;|&#10003;| doctest: sub case |
Fixtures (class-based)            |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Templated tests                   |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Parameterised tests               | -      | -      | -      | -      | &nbsp;|
Auto-registration of tests        |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Tabularised tests                 | -      | -      | -      |&#10003;| array of lambdas |
Allow tests accompany code        |&#10003;| -      | -      | -      | &nbsp;|
Allow tests in header files       |&#10003;| -      | -      | -      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Assertions**                    | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
BDD style scenarios               |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Assert expressions                |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Assert exceptions                 |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Assert abortion (death)           | -      | -      | -      | -      | &nbsp;|
Assert assertions (death)         | -      | -      | -      | -      | &nbsp;|
Floating point comparison, approx |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Floating point comparison, ulp    | -      | -      | -      | -      | see [stf](#ULP)|
Hamcrest matchers                 | ?      |[limited](#C1M)|[limited](#C1M)|[hamlest](#HLM)| &nbsp;|
Expression decomposition          |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Macros with and without prefix    |&#10003;|&#10003;|&#10003;|&#10003;| CATCH_CHECK(), CHECK()|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Other test facilities**         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Mocking support                   | -      | -      | -      | -      | via 3rd party |
Logging facility                  |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Logging levels                    | -      | -      | -      | -      | &nbsp;|
Checkpoints                       | -      | -      | -      | -      | see [Boost.Test](#BTC) |
Test data generators              | -      |&#10003;|&#10003;| -      | &nbsp;|
Property-based testing            | -      | -      | -      | -      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**API / seams**                   | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Reporting user-defined types      |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Reporter API                      | -      |&#10003;|&#10003;| -      | &nbsp;|
Event listeners                   | -      |&#10003;|&#10003;| -      | &nbsp;|
Run-time context                  |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Reporting formats**             | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Console, multi-line               |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Console, single-line (compact)    | -      |&#10003;|&#10003;|&#10003;| similar to compiler error |
JUnit                             | -      |&#10003;|&#10003;| -      | result at end|
XML                               | -      |&#10003;|&#10003;| -      | streaming|
TeamCity                          | -      |&#10003;|&#10003;| -      | &nbsp;|
TAP                               | -      |&#10003;|&#10003;| -      | &nbsp;|
Automake                          | -      |&#10003;|&#10003;| -      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Reporting options**             | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Colourised output (run-time)      |&#10003;|&#10003;|&#10003;| &nbsp; | &nbsp;|
Colourised output (compile-time)  |&#10003;| -      | -      |&#10003;| &nbsp;|
Literal suffix u, l, f            | -      | -      | -      |&#10003;| compile-time |
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Test execution**                | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Concurrent execution of tests     | -      | -      | -      | -      | &nbsp;|
Isolated execution of tests       | -      | -      | -      | -      | &nbsp;|
Limit test execution time         | -      | -      | -      | -      | &nbsp;|
Signal tests without assertions   | -      |&#10003;|&#10003;| -      | &nbsp;|
Supports floating point exceptions| -      | -      | -      | -      | &nbsp;|
Supports Posix signals            |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Supports Windows SEH              |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Compile-time control**          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Omit macros without prefix        |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Omit std::wstring                 | -      | -      | -      |&#10003;| &nbsp;|
Omit std::cout, std::cerr         | -      |&#10003;|&#10003;| -      | &nbsp;|
Specify terminal color system     |&#10003;|&#10003;|&#10003;| -      | none, ansi, win32 |
Specify terminal width            | -      |&#10003;|&#10003;| -      | &nbsp;|
Control handling of POSIX signals |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Control handling of SE on Windows |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Enable leak checking on Windows   | -      |&#10003;|&#10003;| -      | uses CRT Debug Heap|
Enable use of \_\_COUNTER\_\_     | -      |&#10003;|&#10003;| -      | for internal unique names|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Run-time control, commandline** | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Help screen                       |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
List selected suites              |&#10003;| -      | -      | -      | &nbsp;|
List selected tests               |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
List tags of selected tests       | -      |&#10003;|&#10003;|&#10003;| &nbsp;|
Select tests by suite             |&#10003;| -      | -      | -      | &nbsp;|
Select tests by name              |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Select tests by tag               |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Select tests by file              |&#10003;|&#10003;|&#10003;| -      | Catch: via filename as tags |
Select section by name            |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Select supports regexp            |&#10003;| -      | -      |&#10003;| &nbsp;|
Omit assertions expected to throw | -      |&#10003;|&#10003;| -      | &nbsp;|
Count selected tests              | -      | -      | -      |&#10003;| &nbsp;|
Abort at N-th failure             |&#10003;|&#10003;|&#10003;|&#10003;| lest: N is 1 |
Break into debugger               |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Report passing tests              |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Time duration of tests            | -      |&#10003;|&#10003;|&#10003;| &nbsp;|
Control order of tests            |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Repeat tests                      | -      |&#10003;|&#10003;|&#10003;| &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**IDE integration**               | &nbsp; | &nbsp; | &nbsp; | &nbsp; | [[10]](#IDE) |
C++ Builder                       | ?      | ?      | ?      | ?      | &nbsp;|
Clion                             | ?      |&#10003;|&#10003;| ?      | &nbsp;|
Code::Blocks                      | ?      | ?      | ?      | ?      | &nbsp;|
CodeLite                          | ?      | ?      | ?      | ?      | &nbsp;|
Eclipse CDT                       | ?      | ?      | ?      | ?      | &nbsp;|
KDevelop                          | ?      | ?      | ?      | ?      | &nbsp;|
Qt Creator                        | ?      | ?      | ?      | ?      | &nbsp;|
VisualMinGW                       | ?      | ?      | ?      | ?      | &nbsp;|
Visual Studio                     | ?      | ?      | ?      | ?      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Documentation of framework**    | &nbsp; | &nbsp; | &nbsp; | &nbsp; | [[11]](#WGD) |
First contact                     | ?      | ?      | ?      | ?      | new users |
Education                         | ?      | ?      | ?      | ?      | new & existing users |
Support                           | ?      | ?      | ?      | ?      | experienced users |
Troubleshooting                   | ?      | ?      | ?      | ?      | annoyed users |
Internals                         | ?      | ?      | ?      | ?      | fellow developers |
Reference                         | ?      | ?      | ?      | ?      | Everyone|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Testing of framework itself**   | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Distribution of framework**     | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
GitHub single-file download       |&#10003;|&#10003;| -      |&#10003;| from the landing page |
conan                             |&#10003;|&#10003;| -      | -      | &nbsp;|
hunter                            |&#10003;| ?      | -      | -      | &nbsp;|
vpkg                              |&#10003;| ?      | -      | -      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|


References
----------
<a id="CA1"></a>[1] Phils Nash. [Catch-1](https://github.com/philsquared/Catch/). 2010     
<a id="CA2"></a>[2] Phils Nash. [Catch-2](https://github.com/philsquared/Catch/tree/dev-modernize). 2017?    
<a id="DOT"></a>[3] Viktor Kirilov. [doctest](https://github.com/onqtam/doctest/). 2014.  
<a id="LST"></a>[4] Martin Moene. [lest](https://github.com/martinmoene/lest/). 2013.  
<a id="ULP"></a>[5] Joel Falcou. [Design rationale for using ULP with stf](https://github.com/jfalcou/stf/blob/master/doc/rationale.md)  
<a id="BTC"></a>[6] Gennadiy Rozental and Raffi Enficiaud. [Checkpoints in Boost.Test](http://www.boost.org/doc/libs/1_64_0/libs/test/doc/html/boost_test/test_output/test_tools_support_for_logging/checkpoints.html).  
<a id="C1M"></a>[7] [Matchers in Catch-1](https://github.com/philsquared/Catch/blob/master/docs/matchers.md).  
<a id="C2M"></a>[8] [Matchers in Catch-2](https://github.com/philsquared/Catch/blob/master/docs/matchers.md).  
<a id="HLM"></a>[9] [Matchers in lest: hamlest](https://github.com/martinmoene/hamlest).  
<a id="IDE"></a>[10] Wikipedia. [List of C++ IDEs](https://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B).  
<a id="WGD"></a>[11] [Jacob Kaplan-Moss. Writing great documentation](https://www.slideshare.net/jacobian/writing-great-documentation-codeconf-2011).  

<p style="height:60em;"></p>
