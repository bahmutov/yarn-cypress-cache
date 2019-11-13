# yarn-cypress-cache [![Build Status](https://travis-ci.org/bahmutov/yarn-cypress-cache.svg?branch=master)](https://travis-ci.org/bahmutov/yarn-cypress-cache) [![renovate-app badge][renovate-badge]][renovate-app]
> Example caching Cypress on Travis when using Yarn

See [.travis.yml](.travis.yml) file.

## Notes

```shell
$ yarn -v
1.17.3
$ yarn add -D cypress
info Direct dependencies
└─ cypress@3.4.1
```

Check where Cypress binary was downloaded and cached (Mac)

```shell
$ yarn cypress cache path
/Users/gleb/Library/Caches/Cypress
```

You can also see what binary versions are cached in that folder

```shell
$ yarn cypress cache list
3.4.0 3.4.1
```

## Tip

Cypress installs its NPM package, then runs its `postinstall` hook that downloads Cypress binary. If the hooks is skipped for some reason, the binary will be missing. You can safely run install yourself - if there is binary already present, it will finish quickly.

```yaml
install:
  # install dependencies
  - yarn install --frozen-lockfile
  # just in case the install script skipped Cypress post-install hook for some reason
  # call install ourselves. If there is binary already installed, it will quickly finish.
  # By overriding the install step we make sure the NPM modules AND the Cypress binary
  # are installed before the cache is saved
  - yarn cypress install
  # good idea to verify the binary so its status is saved in the cache as well
  - yarn cypress verify
script:
  - yarn cypress run
```

Example running `cypress install` command:

```shell
$ yarn cypress install

Cypress 3.4.1 is installed in /Users/gleb/Library/Caches/Cypress/3.4.1

Skipping installation:

  Pass the --force option if you'd like to reinstall anyway.
```

## More info

- Travis caching documentation page [https://docs.travis-ci.com/user/caching/](https://docs.travis-ci.com/user/job-lifecycle/)

[renovate-badge]: https://img.shields.io/badge/renovate-app-blue.svg
[renovate-app]: https://renovateapp.com/
