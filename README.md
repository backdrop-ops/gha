# Backdrop GHA

This is currently an experiemental repository to explore the feasibility of
using a shared repo for some basic GitHub Actions that can be used by contrib
module maintainers.

Right now only the simplest implementation is included for PHPCS linting with
no customization.

In the future it may be expanded to include other options such as functional
tests, with minor customizations permitted via inputs when calling the action
or workflow.
