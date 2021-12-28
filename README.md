# Docsify Template


## Install

```
npm i docsify-cli -g
```

## Preview
```bash
docsify serve ./doc
```

## Offline Mode

By default, docsify need internet connection to fetch js and css resources. However, by downloading all required asserts to local can avoid this.

Steps:
1. Download all asserts:
```shell
sh download-asserts.sh
```
2. Replace `index.html` with `index_online.html`
