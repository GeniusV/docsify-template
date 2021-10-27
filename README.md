# Docsify Template


## Develop

```
npm i docsify-cli -g
npm i docsify-tools -g
```

## Init
```bash
docsify init ./doc
```

## Preview
```bash
docsify serve ./doc
```

## Generate Side Bar

```bash
docsify-auto-sidebar -d doc
```

Add copyright to footer
```html
<br/><footer id="mb-footer" style="margin-left: 15px;margin-top: 10px"></footer>
```

## Local Only Mode

By default, docsify need to internet connections to fetch js and css resources. However, by downloading all required asserts to local can avoid this.

Steps:
1. Download all asserts:
```shell
sh download-asserts.sh
```
2. Replace `index.html` with `index_online.html`
