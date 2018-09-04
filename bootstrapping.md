# Bootstrapping

This section has some general guidance on how you can get started developing
applications for us. We assume a working knowledge of git and Unix-like
operating systems.

?> UIS members may gain such a knowledge through our [LinkedIn
Learning](https://www.linkedin.com/learning/) organisational account.

## GitHub account

The majority of our products are developed on GitHub. When you join the DevOps
team you will be asked for your GitHub account name. You may wisht to use a
personal account or create one named after your crsid.

### Add a SSH public key

The git version control system works best when used in combination with SSH. You
will want to [associate a SSH key with your
account](https://github.com/settings/keys).

?> For more information, see the [GitHub documentation on
SSH](https://help.github.com/articles/connecting-to-github-with-ssh/).

### Configure GitHub

GitHub has a notification system which can be used to notify you over email when
things of interest happen. Having notifications enabled is useful to keep you in
the loop as any changes you make are reviewed, commented on and, eventually,
merged. You can [configure
notifications](https://github.com/settings/notifications) in the GitHub
settings.

## Clone product repositories

The usual naming convention for repositories is ``{product}-{component}``. For
example, the web application for the Media Platform is at
[uisautomation/media-webapp](https://github.com/uisautomation/media-webapp).

?> Having your repository cloned to a matching ``{product}/{component}``
directory is considered [best
practice](bestpractice/hierarchy.md#filesystem-layout).

If you install [hub](https://hub.github.com/), you can clone a local repository
and create your own fork:

```bash
$ cd ~/repos  # or, wherever you keep your clones repositories
$ mkdir media && cd media
$ hub clone uisautomation/media-webapp webapp && cd webapp
$ hub fork  # creates a fork and adds a new remote
```

## Configure CircleCI for your fork

Most of our products use [CircleCI](https://circleci.com/) for continuous
integration and development. You can set up CircleCI integration for your fork
by visiting https://circleci.com/gh/{username}/{repository} in your browser and
clicking the "Follow Project" button.

For example, to configure [bb9e](https://github.com/bb9e)'s fork of
[iar-backend](https://github.com/uisautomation/iar-backend), visit
https://circleci.com/gh/bb9e/iar-backend.

## Read the documentation

The README file in a repository will contain any special information about
getting started with a project. For example, you may need to obtain and
configure some product-specific credentials. This file may also contain any
CircleCI specific configuration you require for your fork.

?> From the repository root directory, you can open the corresponding GitHub
repository web page and read the README file using the command
``hub browse``.

## Webapps

This section is specific to getting started developing our webapps.

For webapps, we have settled on a solution for local development based on
[docker-compose](https://docs.docker.com/compose/). This allows for a consistent
development environment even if an individual Developer's machine varies.

### Configure Codecov for your fork

Many of our products use [Codecov](https://codecov.io/) for code coverage
checking. You can set up Codecov integration for your fork
by visiting https://codecov.io/gh/{username}/{repository} in your browser.

For example, to configure [bb9e](https://github.com/bb9e)'s fork of
[iar-backend](https://github.com/uisautomation/iar-backend), visit
https://codecov.io/gh/bb9e/iar-backend.

### Install Docker and docker-compose

Make sure that the latest version of [docker](https://www.docker.com/) and
docker-compose are installed on your machine. Using docker-compose allows us to
run tests and develop within an environment very close to that we deploy in.

### Run tests

Tests for the webapp can be run inside a container using the ``./tox.sh`` script
present in many of our webapps. Generally this will check that the documentation
builds, run code style checks and run the test suite. A code coverage summary
will be shown after the tests run.

### Start a development server

A development server can be started with ``./compose.sh development up``. The
web application is then usually available at http://localhost:8000/.

For applications making use of React to render the frontend, we usually have
automatically generated
[styleguidist](https://github.com/styleguidist/react-styleguidist) documentation
for React components at http://localhost:6060/.

For applications which send email, we usually have a
[MailHog](https://github.com/mailhog/MailHog) instance running at
http://localhost:8025.

## Deployment

!> This section is likely to change significantly.

We deploy applications using configuration in a ``{product}-deploy`` repository
on GitHub. Usually these repositories are private. See the ``README`` in any one
repository for an overview of how deployment happens for that product.
