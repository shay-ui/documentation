OpenSAFELY is a rapidly changing platform and the user documentation should be updated frequently to keep pace. 
If you are an OpenSAFELY user and want to contribute corrections, clarifications, or new materials to the documentation, 
please do! You can either:

* Suggest improvements in an [issue](https://github.com/opensafely/documentation/issues).
* Clone [the repo](https://github.com/opensafely/documentation) locally, make edits on a new branch, then create a pull request for it.
* [Edit directly on GitHub](https://github.com/opensafely/documentation/tree/main/docs) ([instructions](https://docs.github.com/en/github/managing-files-in-a-repository/editing-files-in-your-repository)), making sure to "Create a new branch for this commit and start a pull request".

Do not commit changes directly to the main branch.

## Making changes to the study definition variables

Edit the docstrings in the [`patients.py` file in the `cohort-extractor` repository](https://github.com/opensafely-core/cohort-extractor/blob/master/cohortextractor/patients.py).

!!! note "Variable docstrings follow the [Google style guide](https://google.github.io/styleguide/pyguide.html#383-functions-and-methods)."

If you don't have write access, you can fork the cohort-extractor repo, make a change, and submit a pull request.
Editing directly in GitHub will take you through these steps automatically.
At least one commit in the pull request should be named using the prefix `fix: ` or `feature: `. For example `fix: typo in age_as_of docstring`. 
This ensures that a new version of `cohortextractor` is released and can be imported by the documentation via GitHub actions.
Then add a reference to your new variable in the [variables page](study-def-variables.md).

Additionally, the
[`requirements.prod.txt`](https://github.com/opensafely/documentation/blob/main/requirements.prod.txt)
file in the [documentation
repo](https://github.com/opensafely/documentation) itself has to be
updated to match the new incremented version of `cohortextractor`. See
the [documentation repository's
README](https://github.com/opensafely/documentation#building-locally-and-testing)
that details the use of `pip-compile` for this.

---8<-- 'includes/glossary.md'

## Making changes to the data definition examples
You will need to check out the [documentation repo](https://github.com/opensafely/documentation) so you can run the example generating toolchain.

Edit the python modules in the `databuilder/snippets` directory.

Each example is bounded by snex markers which define the filename they will produce.
For example, a block starting with `:snippet data-definition` will create the file `examples/src-data-definition.md`.

!!! note "All example filenames are prefixed with `src-`"

Once you've edited an example (or created a new one) you can run `just databuilder/extract` to update the markdown files in `examples`.

Examples are included in the markdown files using the [pymdown snippet notation](https://facelessuser.github.io/pymdown-extensions/extensions/snippets/#snippets-notation).

Make sure you commit both the changes to the `examples` and `databuilder/snippets` directories.

If you are updating multiple examples it might be easier to the extraction step happen each time you change the python modules, you can do this with `just databuilder/watch-examples`.