# Contributing to EDGES

> Note: these guidelines are based in large part on the excellent guidelines in https://github.com/RadioAstronomySoftwareGroup/pyuvdata/CONTRIBUTING.md

Thank you for considering contributing to EDGES! 

[Edges-collab](https://github.com/edges-collab) is a Github organisation hosting a set of open-source 
software applicable to the [EDGES](http://loco.lab.asu.edu/edges/) experiment.
While members of the collaboration are active collaborators on the experiment, the tools provided
here may sometimes find wider applicability in the community, and are intended to make the analysis
pipeline of EDGES open and reproducible both within and without the central collaboration.

These guidelines are intended as a semi-exhaustive reference for central collaboration members, as well
as an overview of the guidelines for the extended community who wish to contribute to the development
of any of the tools provided by edges-collab.

There are many ways to contribute, including writing tutorials, improving the documentation, submitting bug 
reports and feature requests or writing code which can be incorporated into the repositories. 
Following the guidelines and patterns suggested below helps us maintain a high quality code base and review 
your contributions faster.

Please note we have a [code of conduct](CODE_OF_CONDUCT.md), please follow it in all your interactions with the project.

## Instructions for the Community (or first-timers!)

### How to report a bug
First check the issues to see if your bug already exists. Feel free to comment on the existing issue to provide 
more context or just to note that it is affecting you as well. If your bug is not in the issue list, make a new issue.

When making an issue, try to provide as much context as possible including:

1. What version of python and the code are you using?
2. What operating system are you using?
3. What did you do?
4. What did you expect to see?
5. What did you see instead?
6. Any code to reproduce the bug (as minimal an example as possible)

If you're really inspired, you can make a pull request (PR) adding a test that fails because of the bug. 
This is likely to lead to the bug being fixed more quickly.

### How to suggest a feature or enhancement
First check the issues to see if your feature request already exists. Feel free to comment on the existing 
issue to provide more context or just to note that you would like to see the feature implemented as well. 
If your feature request is not in the issue list, make a new issue.

When making a feature request, try to provide as much context as possible. Feel free to include suggestions 
for implementations.

### Guidelines for contributing to the code

* Create issues for any major changes and enhancements that you wish to make. Discuss things transparently and 
  get community feedback.
* Keep pull requests as small as possible. Ideally each pull request should implement ONE feature or bugfix. 
  If you want to add or fix more than one thing, submit more than one pull request.
* Do not commit changes to files that are irrelevant to your feature or bugfix.
* Be aware that the pull request review process is not immediate, and is generally proportional to the size of the 
  pull request.
* Be welcoming to newcomers and encourage diverse new contributors from all backgrounds. 
  See our [Code of Conduct](../CODE_OF_CONDUCT.md).
* Any code changes _must_ be made on a new branch (or Github fork) and submitted as a PR to be merged to the 
  master branch. 

#### Your First Contribution

Contributing for the first time can seem daunting, but we value contributions from our user community and we will 
do our best to help you through the process. Here’s some advice to help make your work more useful and rewarding.

* Use issue labels to guide you
  - Unsure where to begin contributing? You can start by looking through issues labeled `good first issue` and 
    `help wanted` issues.

* Start small
  - It’s easier to get feedback on a little issue or pull request than on a big one.

* If you’re going to take on a big change, make sure that your idea has support first
  - This means getting someone else to confirm that a bug is real before you fix the issue, and ensuring that 
    there’s consensus on a proposed feature before you work to implement it. Use the issue log to start 
    conversations about major changes and enhancements.

* Be bold! Leave feedback!
  - Sometimes it can be scary to make new issues or comment on existing issues or pull requests, but contributions 
    from the wider community are what ensure that the EDGES collaboration code serves the whole community as well as possible.

* Be rigorous
  - Our requirements on code style, testing and documentation are important. If you have questions about them or 
    difficulty meeting them, please ask for help, we will do our best to support you. Your contributions will be 
    reviewed and integrated much more quickly if your pull request meets the requirements.

If you are new to the GitHub or the pull request process you can start by taking a look at these tutorials:
http://makeapullrequest.com/ and http://www.firsttimersonly.com/. If you have more questions, feel free to ask for 
help, everyone is a beginner at first and all of us are still learning!

#### Getting started

1. Create your own fork of the code (or, if you are a member, create a branch)
2. Do the changes in your fork
3. If you like the change and think the project could use it:
  - If you're fixing a bug, include a new test that breaks as a result of the bug (if possible)
  - Ensure that all your new code is covered by tests and that the existing tests pass. 
  - Ensure that your code meets the style guidelines (not all of our codes are Python, but those that are will comply with PEP8).
  - Ensure that you fully document any new features.

#### Code review process

The core team looks at pull requests on a regular basis and tries to provide feedback as quickly as possible. 
Larger pull requests generally require more time for review and may require discussion among the core team.


## Instructions for Members
In this section we provide a set of guidelines for members on the various standards we adopt in edges-collab
concerning coding style and best practices. Some of these are very general, and some are specific to 
certain languages. These standards are to enable better collaboration and simplicity of understanding
the various codes that are used to provide the EDGES results. Poor coding standards leads to obfuscation
of intent, and ultimately may let errors slip through. 

On the other hand, adherance to standards can sometimes feel like a chore, and may negatively impact productivity
at first. Nevertheless, at least in Python, a great ecosystem of tooling has emerged around these standards
that allows them usually to be quite painless to adhere to.

### Repos
Repos should *always* contain (the following can be replaced by relevant `.rst` files if useful/necessary):
* A `LICENSE.md`: if the code is open-source, we recommend using the MIT license, which can be chosen when creating a 
  new repo. 
* If the specific standards of the particular repo go beyond those outlined in this document, the repo should contain a 
  `CONTRIBUTING.md` file, which _references this document_.
* A single sub-directory which houses the main installable code (typically, for Python projects, this will be the 
  project name)
* A `CHANGELOG.md`: this should detail the changes implemented for each released version of the code. 
  See below for a template.
* A `README.md`: this should briefly describe the purpose of the repo, its main features, how to install it, and how
  to use it in the most basic way. If possible, it should contain badges at the top which quickly show
  the status of the code (tests passing, coverage, docs etc.).
* An `AUTHORS.md`: this should contain the primary authors, and a list of every contributor to the code.

Managing repos/projects:
* We treat individual repositories as self-contained parts of the overall project that are loosely coupled
  with other parts of the pipeline. This enables them to be potentially used outside the project, where
  applicable. This means that each repo should have sets of files that are naturally kept together, not a loose
  bundle of random scripts.
* Any code that is ever to be called by another library/application should follow the versioning rules at 
  https://semver.org. This enables exact version pinning for any downstream libraries/applications. 
  In _python_, versioning is made a little easier by using the `bump2version` package. 
* In practice, version bumps should be handled in PRs. In general, individual PRs will not increase the version,
  but specific version-bump PRs will. These should take note of all PRs merged between this and the last
  version-bump PR, ensure that the changelog is up-to-date, and decide on whether the bump is a MAJOR, MINOR
  or PATCH update based on this changelog. 


### Coding Standards
#### Testing
* All repos should be _continuously tested_: this means that every time the code is changed (via PR/git commit),
  all unit tests are re-run. 
* Continuous testing (called continuous integration, or CI) can be done with travis.org, circle-ci.org or Azure pipelines.
  At this point, we recommend travis.org as it is the service that we have most experience with.
* If using _Python_, use the `pytest` testing framework. 
* Tests should ideally cover more than 90% of the codebase. In _python_, this can be checked using `coverage`, 
  and https://coveralls.io. When your repo has gotten past the initial development stage and has become "stable",
  90% coverage can be _enforced_ in the CI setup.
  
#### Code Format
* All code should be formatted to respect a given strict style. This makes it easier to catch errors, and reduces
  the number of pure formatting changes between different collaborators, as there is one definite "way" to do it 
  (even if that way is not necessarily the best).
* Ensuring proper coding style should be done in two ways: (1) encouraging each user to use pre-commit hooks, and 
  (2) requiring code-style checks to pass on the CI.
* [Pre-Commit](https://github.com/pre-commit/pre-commit) is a python library that _works for any language_ and 
  sets up pre-defined ways that any git commit must check that the code has the correct style, per-user.
  This cannot be enforced, but it makes it much easier per-user to get things right. Installation of the package
  can be encouraged in the README or via package development requirements files (in python).
* In _python_, we _highly recommend_ using a combination of `black` and `flake8`, both for pre-commit and 
  in the CI. `black` _automatically_ reformats code to look a certain way, which makes it very easy. `flake8`
  has a number of checks for docstrings, cyclomatic complexity and other code smells which can catch problems
  before they become problems.
  
#### Preferred Libraries
There are a number of preferred libraries, for Python codes, that we recommend using:
* `numpy`: for any manipulation of array data
* `click`: for creating command-line interfaces (much better than the in-built arg/opt-parse!)
* `tqdm`: for progress-bar functionality
* `attrs`: for small data-like classes
* `ctypes` or `cffi`: for wrapping C code. The former should be used for small interfaces, the latter for larger ones.
* `sphinx`: for automatic API documentation

#### Documentation
* All projects should _at least_ have a README, as defined above. 
* Any CLI defined within a project should have a standard unix-like help interface (whether a C or Python project).
* Code should be well-commented as to the coder's intent
* Python projects should have an abundance of docstrings, formatted in `numpydoc` style.
* If a _python_ project is more widely applicable, it should also have Sphinx documentation in a `docs/` directory,
  which should also be hosted on readthedocs.org.
* Python projects should have one or more Jupyter notebook _examples_ that show how to use the code and some 
  interesting use-cases. These can be automatically hosted on readthedocs.org as well, using `nbsphinx`.

#### Github
A number of guidelines on how to do various things on Github:
* Repos should, after an initial period of rapid development, be set to protect the master branch (this can be
  done in Settings/Branches). This enables master to _never_ be written to directly, and can require tests
  to pass and positive reviews to be submitted before merging. This is a very good way to protect the code.
* As stated in the guidelines above, try to use the issues capability to the fullest extent. Instead of emailing
  each other about issues with codes (or questions etc.), instead make a formal issue which can then be tasked
  out to relevant people and gets formally tracked. This also helps the community know what is going on, and is
  great for posterity.


### File templates
#### Changelog
Each new version should have the following format::

    ## vMAJOR.MINOR.PATCH [Date]
    Optional short statement describing the overall release.
    
    ### Features
    * new feature
    
    ### Enhancements
    * new enhancement, thanks to @thisperson!
    
    ### Bugfixes
    * Fixed this problem [issue #57]
    
Any section (Features/Enhancements/Bugfixes) that has no entries can be left out. Any changes/fixes that 
make the code backwards-incompatible should be marked as such (eg. by **backwards-incompatible** after the point).



