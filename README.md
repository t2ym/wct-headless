[![NPM version](http://img.shields.io/npm/v/wct-headless.svg?style=flat-square)](https://npmjs.org/package/wct-headless)

Headless Chrome and Firefox browser support for [web-component-tester](https://github.com/Polymer/web-component-tester).

wct-headless plugin is derived from [wct-local](https://github.com/Polymer/wct-local) for headless Chrome 59+ & Firefox 55+ support.

### Notes:
- The "local" plugin has to be explicitly disabled as it is automatically enabled by default.
- Option #1: Disable the "local" plugin with `--skip-plugin=local` option
```sh
    wct --skip-plugin=local
```
- Option #2: Disable the "local" plugin in wct.conf.json
```json
    {
      "plugins": {
        "local": {
          "disabled": true
        },
        "headless": {
          "browsers": [
            "chrome",
            "firefox"
          ]
        }
      }
    }
```
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
- Firefox 55 only on Linux supports `--headless` option, while Firefox 56+ (released version) on Windows and macOS will do.
- `browsersOptions` to specify command line arguments (ChromeDriver's `chromeOptions.args` and GeckoDriver's `moz:firefoxOptions.args`) to Chrome and Firefox browsers, respectively. Default is `{ "chrome": [ "start-maximized", "headless", "disable-gpu" ], "firefox": [ "--headless" ] }`
```json
{
  "plugins": {
    "local": {
      "disabled": true
    },
    "headless": {
      "browsers": [
        "chrome",
        "firefox"
      ],
      "browsersOptions": {
        "chrome": [
          "window-size=1920,1080",
          "headless",
          "disable-gpu"
        ],
        "firefox": [
          "--headless"
        ]
      }
    }
  }
}
```
- Chrome's `"no-sandbox"` option is required to let `wct-headless` run in a docker container without privilege
```json
{
  "plugins": {
    "local": {
      "disabled": true
    },
    "headless": {
      "browsers": [
        "chrome"
      ],
      "browsersOptions": {
        "chrome": [
          "window-size=1920,1080",
          "headless",
          "disable-gpu",
          "no-sandbox"
        ]
      }
    }
  }
}
```
- Chrome browser's User-Agent header containing `HeadlessChrome/...` can unexpectedly invoke on-the-fly ES5 transpilation by `polyserve`, which is the web server for `web-component-tester`
  - Option #1: `wct --compile=never` to avoid ES5 transpilation
  - Option #2: Add `"--user-agent='Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.108 Safari/537.36'"` (or an appropriate User-Agent for Chrome) option to `plugins` -> `headless` -> `browsersOptions` -> `chrome` in `wct.conf.json`
```json
{
  "plugins": {
    "local": {
      "disabled": true
    },
    "headless": {
      "browsers": [
        "chrome"
      ],
      "browsersOptions": {
        "chrome": [
          "window-size=1920,1080",
          "headless",
          "disable-gpu",
          "user-agent='Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.108 Safari/537.36'"
        ]
      }
    }
  }
}
```
- `wct-headless` is compatible with my fork [@t2ym/web-component-tester](https://www.npmjs.com/package/@t2ym/web-component-tester) for [wct-istanbul](https://www.npmjs.com/package/wct-istanbul) as well.