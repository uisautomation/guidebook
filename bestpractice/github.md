# Best practice for GitHub

This section discusses best practice for using the GitHub website. Best practice
for using git itself is in [another section](bestpractice/git).

## Repository naming

See the [corresponding subsection](bestpractice/hierarchy.md#repository-naming) in
the product/component hierarchy section.

## Repository setup

When creating a new repository, follow the following checklist:

* [ ] The repository is named ``{product}-{component}``.
* [ ] The "admins" team has been given admin permissions.
* [ ] The "developers" team has been given write permissions.
* [ ] The "droids" team has been given read or write permissions as appropriate.
* [ ] The ``master`` branch is protected:
  * [ ] Pull requests require reviews.
  * [ ] Status checks must pass.
  * [ ] Include administrators in the restrictions.
