elisp-lint
==========

Basic linting for Emacs Lisp

[![MELPA Stable](https://stable.melpa.org/packages/elisp-lint-badge.svg)](https://stable.melpa.org/#/elisp-lint)
[![MELPA](https://melpa.org/packages/elisp-lint-badge.svg)](https://melpa.org/#/elisp-lint)
[![Build Status](https://travis-ci.org/gonewest818/elisp-lint.png?branch=master)](https://travis-ci.org/gonewest818/elisp-lint)
[![CircleCI](https://img.shields.io/circleci/project/github/gonewest818/elisp-lint.svg)](https://circleci.com/gh/gonewest818/elisp-lint)
[![codecov](https://codecov.io/gh/gonewest818/elisp-lint/branch/master/graph/badge.svg)](https://codecov.io/gh/gonewest818/elisp-lint)

This is a tool for finding certain problems in Emacs Lisp files. Use it on the command line like this:

    emacs -Q --batch -l elisp-lint.el -f elisp-lint-files-batch *.el

You can disable individual checks by passing flags on the command line:

    emacs -Q --batch -l elisp-lint.el -f elisp-lint-files-batch --no-indent *.el

You can use file variables or `.dir-locals.el` to disable checks completely, and
also to configure certain checks as described below.

    ((emacs-lisp-mode . ((fill-column . 80)
                         (indent-tabs-mode . nil)
                         (elisp-lint-ignored-validators . ("byte-compile"))
                         (elisp-lint-indent-specs . ((describe . 1)
                                                     (it . 1))))))

Validators
----------

### byte-compile ###

Byte-compiles the file with all warnings enabled.

### checkdoc ###

Runs checkdoc on the file to enforce standards in documentation.

### fill-column ###

Verifies that no line exceeds the number of columns in `fill-column`.

### indent ###

Verifies that each line is indented according to `emacs-lisp-mode`. Where macros
are defined with special `indent` metadata, use the `elisp-lint-indent-specs` alist
to specify each symbol's required indent.

### indent-character ###

Verifies the indentation is consistently tabs or spaces, according to the value
of `indent-tabs-mode`.

### package-format ###

Calls `package-buffer-info` to validate some file metadata.

### trailing-whitespace ###

Verifies the buffer has no lines with trailing whitespace.

Configuration
-------------

Use a file variable or `.dir-locals.el` to override the variables mentioned
above.

Changelog
---------

* Version 0.3 (MELPA)
   - Emacs 23 support is deprecated
* Version 0.2.0 (MELPA Stable - Feb 2018)
   - Project transferred to new maintainer
   - Whitespace check permits page-delimiter (^L)
   - Indentation check prints the diff to console
   - User can specify indent specs to tell the checker about macros
   - Added checkdoc (available only Emacs 25 and newer)
   - Cleared up the console output for easier reading in CI
   - Expand Travis CI test matrix to include Emacs 25 and 26
* Version 0.1.0 (2015)
   - Basic linting functionality implemented

Credits
-------

The initial development of `elisp-lint` is Copyright 2013-2015 Nikolaj
Schumacher. This project was transferred to Neil Okamoto in 2018.

Updates and ongoing development are Copyright 2018 Neil Okamoto and contributors.

Contributing
------------

Pull requests are welcome!
