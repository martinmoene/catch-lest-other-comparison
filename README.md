# Catch&ndash;doctest&ndash;lest feature comparison
Tabularised feature comparison between Catch, doctest and lest C++ test frameworks.

[Skip to the feature comparison](#table).

Note 1: This is an initial draft, it is incomplete and likely contains errors.  
Note 2: Catch-2 is not yet released.

Ideas, additions, corrections, signaling omissions, etc. welcome! 

---

**The frameworks in this comparison share the following properties:**

- The frameworks are available as single-file header-only library.
- Test cases are described by a string, they are not identified by a function name.
- There is a single assertion macro for expressions.   
Expressions are decomposed and original expression code can be shown alongside the values they represent.
- Fixtures can be created inside a test case. They are called sections or sub cases.

**Advent of Catch**&emsp;Expression-decomposing assertions and function-level fixtures (sections) were introduced by Kevlin Henney in his talk *Rethinking Unit Testing in C++* at ACCU London in May 2010 [[1]](#KH1). At that time, Phil Nash was working on a testing framework called *YACUTS* (Yet Another C++ Unit Test System) that would bring similar capabilities, be it a little more intrusively [[2]](#PN1). Kevlin's talk inspired Phil to develop ***Catch*** [[3]](#PN2).

**Kevlin's emphasis on simplicity** in testing and the desire to understand how expression decomposition works inspired Martin Moene to write ***lest*** [[4]](#MM1). The code of *lest* is intentionally kept small, so that it should be fairly easy to gain insight in how things work.

**Accompanying test code with the code to test** was one of the drivers for Viktor Kirilov to write ***doctest*** [[5]](#VK1). Others are to enable using *doctest* with many different compilers and to shine in compile-time and run-time performance.

<p>&nbsp;</p>

<a id="table"></a>

Feature                           | [doctest](#DOT)| [Catch-1](#CA1)| [Catch-2](#CA2)| [lest](#LST)| Notes |
----------------------------------|:------:|:------:|:------:|:-------|-------|
**License**                       | MIT    |BSL-1.0 | &nbsp; |BSL-1.0 | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
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
Type-parameterised tests          |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Value-parameterised tests         | -      | -      | -      | -      | &nbsp;|
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
Expression decomposition          |&#10003;|&#10003;|&#10003;|&#10003;| see [[2]](#PN1) |
Floating point comparison, approx |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Floating point comparison, ulp    | -      | -      | -      | -      | see stf [[10]](#ULP)|
Hamcrest matchers                 | ?      |[limited](#C1M)|[limited](#C1M)|[hamlest](#HLM)| &nbsp;|
Macros with and without prefix    |&#10003;|&#10003;|&#10003;|&#10003;| CATCH_CHECK(), CHECK()|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Other test facilities**         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Mocking support                   | -      | -      | -      | -      | via 3rd party |
Logging facility                  |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Logging levels                    | -      | -      | -      | -      | &nbsp;|
Checkpoints                       | -      | -      | -      | -      | see Boost.Test [[11]](#BTC) |
Test data generators              | -      |&#10003;|&#10003;| -      | &nbsp;|
Property-based testing            | -      | -      | -      | -      | &nbsp;|
Obtain name of current test       | ?      | ?      | ?      | ?      | &nbsp;|
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
Improve compilation speed         |&#10003;|&#10003;|&#10003;|-       | reduced functionality |
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
**Code-related**                  | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Compile-time performance          | ?      | ?      | ?      | ?      | &nbsp;|
Run-time performance              | ?      | ?      | ?      | ?      | &nbsp;|
Can provide canned main()         |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Only depends on C++ std library   |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Single-file header-only           |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Size, LOC                         | 4,500  | 9,100  | ?      | 1,000  | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Platforms**                     | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Cygwin                            | ?      | ?      | ?      | ?      | &nbsp;|
macOS                             |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Unix/Linux                        |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Windows                           |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**IDE integration**               | &nbsp; | &nbsp; | &nbsp; | &nbsp; | see [[15]](#IDE) |
C++ Builder                       | ?      | ?      | ?      | ?      | &nbsp;|
Clion                             | ?      |&#10003;|&#10003;| ?      | &nbsp;|
Code::Blocks                      | ?      | ?      | ?      | ?      | &nbsp;|
CodeLite                          | ?      | ?      | ?      | ?      | &nbsp;|
Eclipse CDT                       | ?      | ?      | ?      | ?      | &nbsp;|
KDevelop                          | ?      | ?      | ?      | ?      | &nbsp;|
Qt Creator                        | ?      | ?      | ?      | ?      | &nbsp;|
Visual-MinGW                      | ?      | ?      | ?      | ?      | &nbsp;|
Visual Studio                     | ?      | ?      | ?      | ?      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Documentation of framework**    | &nbsp; | &nbsp; | &nbsp; | &nbsp; | see [[16]](#WGD) |
First contact                     | ?      | ?      | ?      | ?      | new users |
Education                         | ?      | ?      | ?      | ?      | new & existing users |
Support                           | ?      | ?      | ?      | ?      | experienced users |
Troubleshooting                   | ?      | ?      | ?      | ?      | annoyed users |
Internals                         | ?      | ?      | ?      | ?      | fellow developers |
Reference                         | ?      | ?      | ?      | ?      | everyone|
Try it online                     |&#10003;| -      | -      |&#10003;| &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Testing of framework itself**   | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Distribution of framework**     | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
GitHub single-file download       |&#10003;|&#10003;| -      |&#10003;| from the landing page |
conan                             |&#10003;|&#10003;| -      | -      | &nbsp;|
hunter                            |&#10003;| ?      | -      | -      | &nbsp;|
vcpkg                             |&#10003;|&#10003;| -      | -      | &nbsp;|
  &nbsp;                          | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|


References
----------

<a id="KH1"></a>[1] Kevlin Henney. [Rethinking Unit Testing in C++](http://accu.org/index.php/accu_branches/accu_london/accu_london_may_2010) ([Video](http://skillsmatter.com/podcast/agile-testing/kevlin-henney-rethinking-unit-testing-in-c-plus-plus)). Skills Matter, May 2010.  
<a id="PN1"></a>[2] Phil Nash. [The Ultimate C++ Unit Test Framework](http://www.levelofindirection.com/journal/2010/5/21/the-ultimate-c-unit-test-framework.html). Blog, May 2010.  
<a id="PN2"></a>[3] Phil Nash. [Unit Testing in C++ and Objective-C just got easier](http://www.levelofindirection.com/journal/2010/12/28/unit-testing-in-c-and-objective-c-just-got-easier.html). Blog announcement, December 2010.  
<a id="MM1"></a>[4] Martin Moene. [lest errors escape testing](). Blog announcement, June 2013.  
<a id="VK1"></a>[5] Viktor Kirilov. [doctest – the Lightest C++ Unit Testing Framework](https://accu.org/index.php/journals/2343). Announcement in Overload 137, February 2017.  
<a id="CA1"></a>[6] Phils Nash. [Catch-1 on GitHub](https://github.com/philsquared/Catch/). 2010.  
<a id="CA2"></a>[7] Phils Nash. [Catch-2 on GitHub](https://github.com/philsquared/Catch/tree/dev-modernize). 2017?  
<a id="DOT"></a>[8] Viktor Kirilov. [doctest on GitHub](https://github.com/onqtam/doctest/). 2014.  
<a id="LST"></a>[9] Martin Moene. [lest on GitHub](https://github.com/martinmoene/lest/). 2013.  
<a id="ULP"></a>[10] Joel Falcou. [Design rationale for using ULP with stf](https://github.com/jfalcou/stf/blob/master/doc/rationale.md).  
<a id="BTC"></a>[11] Gennadiy Rozental and Raffi Enficiaud. [Checkpoints in Boost.Test](http://www.boost.org/doc/libs/1_64_0/libs/test/doc/html/boost_test/test_output/test_tools_support_for_logging/checkpoints.html).  
<a id="C1M"></a>[12] [Matchers in Catch-1](https://github.com/philsquared/Catch/blob/master/docs/matchers.md).  
<a id="C2M"></a>[13] [Matchers in Catch-2](https://github.com/philsquared/Catch/blob/master/docs/matchers.md).  
<a id="HLM"></a>[14] [Matchers in lest: hamlest](https://github.com/martinmoene/hamlest).  
<a id="IDE"></a>[15] Wikipedia. [List of C++ IDEs](https://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B).  
<a id="WGD"></a>[16] Jacob Kaplan-Moss. [Writing great documentation](https://www.slideshare.net/jacobian/writing-great-documentation-codeconf-2011).  

<p style="height:60em;"></p>
