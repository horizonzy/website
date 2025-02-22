# etcd.io

The [etcd.io][] website, built using [Hugo][] and hosted on [Netlify][].

## Build prerequisites

To build and serve the site, you'll need the latest [LTS release][] of **Node**.
Like Netlify, we use **[nvm][]**, the Node Version Manager, to install and
manage Node versions:

```console
$ nvm install --lts
```

## Setup

 1. Clone or download a copy of this repo.
 2. From a terminal window, change to the cloned or unzipped repo directory.
 3. Get NPM packages and git submodules, including the the [Docsy][] theme:
    ```console
    $ npm install 
    ```

## Build or serve the site

To locally serve the site at [localhost:8888][], run the following command:

```console
$ npm run serve
```

To build and check links, run these commands:

```console
$ npm run build
$ npm run ci-check-links
```

> **Note**: If you have `htmltest` in our path, you can run the `check-links`
> script instead.

You can also locally serve using [Docker](https://docker.com):

```console
$ make docker-serve
```

## Contributing

We welcome issues and PRs! For details, see [Contributing][].

If you submit a PR, Netlify will automatically create a [deploy preview][] so
that you can view your changes. Once merged, Netlify automcatically deploys to
the production site [etcd.io][].

## Releasing a new version of the etcd documentation

> **IMPORTANT**: this section is out-of-date, see issue [#406][].

Follow these steps to add documentation for a newly released version of etcd, vX.Y:

* Recursively copy [content/docs/next](content/docs/next) into
  `content/docs/vX.Y`, where `vX.Y` is the newly released version of etcd. For example:

    ```bash
    cp -r content/docs/next content/docs/v3.5
    ```

* In the `_index.md` file at the root of the new directory, update the frontmatter
  to reflect the new version:
  ```
  ---
  title: etcd version X.Y
  weight: 1000
  cascade:
    version: vX.Y
  ---
  ```
* Add the version to the `params.versions.all` array in the
  [config.toml](config.toml) configuration file.
* If the version is meant to be the latest version of etcd, change the
  `params.versions.latest` parameter to the desired new version.
* Submit a pull request with the changes.

[#406]: https://github.com/etcd-io/website/issues/406
[Contributing]: https://etcd.io/community/#contributing
[deploy preview]: https://www.netlify.com/blog/2016/07/20/introducing-deploy-previews-in-netlify/
[Docsy]: https://www.docsy.dev
[etcd.io]: https://etcd.io
[Hugo]: https://gohugo.io
[localhost:8888]: http://localhost:8888
[LTS release]: https://nodejs.org/en/about/releases/
[Netlify]: https://netlify.com
[nvm]: https://github.com/nvm-sh/nvm/blob/master/README.md#installing-and-updating
