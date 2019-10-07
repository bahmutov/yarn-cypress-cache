# yarn-cypress-cache [![Build Status](https://travis-ci.org/bahmutov/yarn-cypress-cache.svg?branch=master)](https://travis-ci.org/bahmutov/yarn-cypress-cache)
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
```

## More info

- Travis caching documentation page https://docs.travis-ci.com/user/caching/
