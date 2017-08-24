[![NPM version](http://img.shields.io/npm/v/wct-headless.svg?style=flat-square)](https://npmjs.org/package/wct-headless)

Headless Chrome browser support for [web-component-tester](https://github.com/Polymer/web-component-tester).

wct-headless plugin is derived from [wct-local](https://github.com/Polymer/wct-local) for headless Chrome support.

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
- `chromeOptions` to specify command line arguments (ChromeDriver's `chromeOptions.args`) to Chrome browser. Default is `[ "start-maximized", "headless", "disable-gpu" ]`
```javascript
{
  "plugins": {
    "local": {
      "disabled": true
    },
    "headless": {
      "browsers": [
        "chrome"
      ],
      "chromeOptions": [
        "window-size=1920,1080",
        "headless",
        "disable-gpu"
      ]
    }
  }
}
```
- "chrome failed to maximize" error is always shown whether or not `"start-maximized"` option is set
- `"windows-size=width,height"` option is effective regardless of `"start-maximized"` option
- `"no-sandbox"` option is required to let `wct-headless` run in a docker container without privilege
```javascript
{
  "plugins": {
    "local": {
      "disabled": true
    },
    "headless": {
      "browsers": [
        "chrome"
      ],
      "chromeOptions": [
        "window-size=1920,1080",
        "headless",
        "disable-gpu",
        "no-sandbox"
      ]
    }
  }
}
```
- `wct-headless` is compatible with my fork [@t2ym/web-component-tester](https://www.npmjs.com/package/@t2ym/web-component-tester) for [wct-istanbul](https://www.npmjs.com/package/wct-istanbul) as well.