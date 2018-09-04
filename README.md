# DevOps Guidebook

This repository contains the source for the UIS [DevOps
Guidebook](https://uisautomation.github.io/guidebook).

## Developing locally

The guidebook uses [docsify](https://docsify.js.org/) to render the guidbook
from markdown striaght in the browser. As such there is no render step. One
simply clones the repo and starts a local webserver. If you have the
[hub](https://github.com/github/hub) utility installed:

```console
$ hub clone uisautomation/guidebook
$ python3 -m http.server 8000
```

The documentation is now available at http://localhost:8000/.
