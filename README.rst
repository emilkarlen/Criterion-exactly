===============================================================================
Some tests of Criterion using Exactly
===============================================================================

An implementation of the tests in *Exactly*, corresponding to the tests
implemented in *Cram* in the official repository.

- Criterion_
- Exactly_
- Cram_


Organisation
===============================================================================

Test root directory
-------------------------------------------------------------------------------

``c.suite``
   Suite file for the tests of the C library.

``cxx.suite``
   Suite file for the tests of the C++ library.

``exactly.suite``
   Suite file for all tests - C and C++.


A sub suite corresponding to each Cram file (``.t``)
-------------------------------------------------------------------------------

Each Cram test file (``.t``) is implemented as an Exactly sub suite,
located in its own subdirectory.

Each such sub suite has a common structure:

``c``
   Directory representing a sub suite for the tests of the C library.

``cxx``
   Directory representing a sub suite for the tests of the C++ library.

``c.suite``
   Suite file for the tests of the C library.

``cxx.suite``
   Suite file for the tests of the C++ library.

``exactly.suite``
   Suite file for all tests - C and C++.

A Cram test file contains multiple test cases,
and each such test case is represented by a single Exactly test case file
(``.case``).


Execution
===============================================================================

Executing a suite via its suite file ``NAME.suite``::

  > exactly suite NAME.suite

Executing a case via its case file ``NAME.case``::

  > exactly NAME.case

Executing the *action to check* of a test case file ``NAME.case``::

  > exactly --act NAME.case

This will ignore assertions and output exit-code, stdout and stderr
of the program run in ``[act]``.


Evaluation
===============================================================================

  
Status
-------------------------------------------------------------------------------

Only tested on Linux (Debian).


Pros
-------------------------------------------------------------------------------

- More detailed tests, and test of more props:
  - exit code
  - stdout
  - stderr
- Ability to run each test case independently.
- Execpted output text can be put in sepate file.
- Resue of resources
  - Common output in external files that can be reused.
  - Replacement of name-of-sourc-file in expected output
    means that the same expected output can be used for
    both C and C++.
- No dependency on a shell.
- Test setup is handled by the test tool.

  The Cram tests depends on setup (environment variables)
  handled by the build tool (``meson``).


Cons
-------------------------------------------------------------------------------

- Problem - replace refs (see ``asserts/c/fail-messages.case``).

  Cram's feature for checking text (mixing constants and reg-exps)
  is nice and could be added Exactly.
- Challenging to organise and run via ``meson``.
- Exactly cannot check prerequesites.

  These has to be implemented via the build system (``meson``).
- Exactly is more complex - may take more time to learn.

.. _Criterion: https://github.com/Snaipe/Criterion
.. _Exactly: https://github.com/emilkarlen/exactly
.. _Cram: https://github.com/brodie/cram

