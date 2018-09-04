# Product/component hierarchy

Each *product* which we develop is usually composed of multiple *components*.
For example, a web application may have a public repository containing the
source for the application and a private deployment repository which contains
scripts and configuration to deploy the web application on our infrastructure.

## Repository naming

Name a new Github repository using the form ``{product}-{component}``. For
example, the web application for the Media Platform is at
[uisautomation/media-webapp](https://github.com/uisautomation/media-webapp).

## Filesystem layout

Divide your repositories into a ``{product}/{component}`` hierarchy. Single-repo
products should be cloned into a separate ``devops`` directory.  For example, if
you store your cloned repositories in the ``~/repos`` directory and are working
on the IAR, Media Platform, this guidebook and our boilerplate application, your
repositories will be cloned as follows:

```
~/repos
├── devops
│   ├── django-boilerplate
│   └── guidebook
├── iar
│   ├── backend
│   ├── deploy
│   └── frontend
└── media
    ├── deploy
    └── webapp
```
