# Catch&ndash;doctest&ndash;lest feature comparison
Tabularised feature comparison between Catch, doctest and lest C++ test frameworks.

Note: This is an initial draft, it is incomplete and likely contains errors.

Feature                          | [doctest](https://github.com/onqtam/doctest/)| [Catch-1](https://github.com/philsquared/Catch/)| [Catch-2](https://github.com/philsquared/Catch/tree/dev-modernize)| [lest](https://github.com/martinmoene/lest/)| Notes |
---------------------------------|:------:|:------:|:------:|:-------|-------|
**C++ standard related**         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
C++ standard                     | C++98  | C++98  | C++11  | C++11  | &nbsp;|
Can work without exceptions      |&#10003;| -      | -      | -      | &nbsp;|
Requires RTTI                    | -      | ?      | ?      | ?      | &nbsp;|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Test organisation**            | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Suites of tests                  |&#10003;| -      | -      | -      | &nbsp;|
Fixtures (sections)              |&#10003;|&#10003;|&#10003;|&#10003;| doctest: sub case |
Fixtures (class-based)           |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Templated tests                  |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Parameterised tests              | -      | -      | -      | -      | &nbsp;|
Auto-registration of tests       |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Tabularised tests                | -      | -      | -      |&#10003;| array of lambdas |
Allow tests accompany code       |&#10003;| -      | -      | -      | &nbsp;|
Allow tests in header files      |&#10003;| -      | -      | -      | &nbsp;|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Assertions**                   | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
BDD style scenarios              |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Assert expressions               |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Assert exceptions                |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Assert abortion (death)          | -      | -      | -      | -      | &nbsp;|
Assert assertions (death)        | -      | -      | -      | -      | &nbsp;|
Floating point comparison, approx|&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Floating point comparison, ulp   | -      | -      | -      | -      | &nbsp;|
Hamcrest matchers                | ?      |[limited](https://github.com/philsquared/Catch/blob/master/docs/matchers.md)|[limited](https://github.com/philsquared/Catch/blob/master/docs/matchers.md)|[hamlest](https://github.com/martinmoene/hamlest)| &nbsp;|
Expression decomposition         |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Macros with and without prefix   |&#10003;|&#10003;|&#10003;|&#10003;| CATCH_CHECK(), CHECK()|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Other test facilities**        | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Mocking support                  | -      | -      | -      | -      | via 3rd party |
Logging facility                 |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Test data generators             | -      |&#10003;|&#10003;| -      | &nbsp;|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**API / seams**                  | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Reporting user-defined types     |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Reporter API                     | -      |&#10003;|&#10003;| -      | &nbsp;|
Event listeners                  | -      |&#10003;|&#10003;| -      | &nbsp;|
Run-time context                 |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Reporting formats**            | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Console, multi-line              |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Console, single-line (compact)   | -      |&#10003;|&#10003;|&#10003;| &nbsp;|
JUnit                            | -      |&#10003;|&#10003;| -      | result at end|
XML                              | -      |&#10003;|&#10003;| -      | streaming|
TeamCity                         | -      |&#10003;|&#10003;| -      | &nbsp;|
TAP                              | -      |&#10003;|&#10003;| -      | &nbsp;|
Automake                         | -      |&#10003;|&#10003;| -      | &nbsp;|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Reporting options**            | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Colourised output (run-time)     |&#10003;|&#10003;|&#10003;| &nbsp; | &nbsp;|
Colourised output (compile-time) |&#10003;| -      | -      |&#10003;| &nbsp;|
Literal suffix u, l, f           | -      | -      | -      |&#10003;| compile-time |
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Test execution**               | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Concurrent execution of tests    | -      | -      | -      | -      | &nbsp;|
Shielded execution of tests      | -      | -      | -      | -      | &nbsp;|
Supports Posix signals           |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Supports Windows SEH             |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Compile-time control**         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Omit macros without prefix       |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Omit std::wstring                | -      | -      | -      |&#10003;| &nbsp;|
Omit std::cout, std::cerr        | -      |&#10003;|&#10003;| -      | &nbsp;|
Specify terminal color system    |&#10003;|&#10003;|&#10003;| -      | none, ansi, win32 |
Specify terminal width           | -      |&#10003;|&#10003;| -      | &nbsp;|
Control handling of POSIX signals|&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Control handling of SE on Windows|&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Enable leak checking on Windows  | -      |&#10003;|&#10003;| -      | uses CRT Debug Heap|
Enable use of \_\_COUNTER\_\_    | -      |&#10003;|&#10003;| -      | for internal unique names|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Run-time control, commandline**| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
Help screen                      |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
List selected suites             |&#10003;| -      | -      | -      | &nbsp;|
List selected tests              |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
List tags of selected tests      | -      |&#10003;|&#10003;|&#10003;| &nbsp;|
Select tests by suite            |&#10003;| -      | -      | -      | &nbsp;|
Select tests by name             |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Select tests by tag              |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Select tests by file             |&#10003;|&#10003;|&#10003;| -      | Catch: via filename as tags |
Select section by name           |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Select supports regexp           |&#10003;| -      | -      |&#10003;| &nbsp;|
Omit assertions expected to throw| -      |&#10003;|&#10003;| -      | &nbsp;|
Count selected tests             | -      |&#10003;|&#10003;|&#10003;| &nbsp;|
Abort at N-th failure            |&#10003;|&#10003;|&#10003;|&#10003;| lest: N is 1 |
Break into debugger              |&#10003;|&#10003;|&#10003;| -      | &nbsp;|
Report passing tests             |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Time duration of tests           | -      |&#10003;|&#10003;|&#10003;| &nbsp;|
Control order of tests           |&#10003;|&#10003;|&#10003;|&#10003;| &nbsp;|
Repeat tests                     | -      |&#10003;|&#10003;|&#10003;| &nbsp;|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**IDE integration**              | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
  Visual Studio output window    |&#10003;| ?      | ?      | -      | &nbsp;|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
**Testing of framework itself**  | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|
  &nbsp;                         | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp;|

