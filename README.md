[![NPM version](http://img.shields.io/npm/v/wct-headless.svg?style=flat-square)](https://npmjs.org/package/wct-headless)

Headless Chrome browser support for [web-component-tester](https://github.com/Polymer/web-component-tester).

wct-headless plugin is the same as [wct-local](https://github.com/Polymer/wct-local) except for headless Chrome support.

### Notes:
- The "local" plugin has to be explicitly disabled as it is automatically enabled by default.
- Option #1: Disable the "local" plugin with `--skip-plugin=local` option
```sh
    wct --skip-plugin=local
```
- Option #2: Disable the "local" plugin in wct.conf.json
```javascript
    {
      "plugins": {
        "local": {
          "disabled": true
        },
        "headless": {
          "browsers": [
            "chrome"
          ]
        }
      }
    }
```
- Firefox is NOT headless even in the "headless" plugin.
- Global wct needs global wct-headless installation.
```sh
    npm install -g web-component-tester
    npm install -g wct-headless
```
- Local wct (./node_modules/.bin/wct) needs local wct-headless installation.
```sh
    npm install --save-dev web-component-tester
    npm install --save-dev wct-headless
```
- `wct-headless` is compatible with my fork [@t2ym/web-component-tester](https://www.npmjs.com/package/@t2ym/web-component-tester) for [wct-istanbul](https://www.npmjs.com/package/wct-istanbul) as well.