# @snowdog/vuepress-plugin-pdf-export
Vuepress plugin for exporting site as PDF

## Features
- Exports whole Vuepress based page as a single PDF file
- Applies styles to hide UI elements like navigation or sidebar
- Doesn't other languages like Java to run
- Designed to work well in headless environments like CI runners

## Config options
- `theme` - theme name (default `@vuepress/default`)
- `sorter` - function for changing pages order (default `false`)
- `outputFileName` - name of output file (default `site.pdf`)
- `puppeteerLaunchOptions` - [Puppeteer launch options object](https://github.com/puppeteer/puppeteer/blob/v2.1.1/docs/api.md#puppeteerlaunchoptions) (default `{}`)
- `pageOptions` - [Puppeteer page formatting options object](https://github.com/puppeteer/puppeteer/blob/v2.1.1/docs/api.md#pagepdfoptions) (default `{}`)

### Usage

Using this plugin:

``` js
// in .vuepress/config.js
module.exports = {
  plugins: ['@snowdog/vuepress-plugin-pdf-export']
}
```

Then run:

``` bash
vuepress export [path/to/your/docs]
```

### Tips
To run this plugin on Gitlab CI you may want to run Chrome with `no-sandbox` flag. [Details](https://github.com/puppeteer/puppeteer/blob/master/docs/troubleshooting.md#setting-up-chrome-linux-sandbox)

```js
module.exports = {
  plugins: [
    ['@snowdog/vuepress-plugin-pdf-export', {
      // to pass puppeteer launch options
      puppeteerLaunchOptions: {
        args: ['--no-sandbox', '--disable-setuid-sandbox']
      },
      // to pass puppeteer page options
      pageOptions: {
        margin: {
          top: '1cm',
          bottom: '1cm',
          left: '1cm',
          right: '1cm'
        }
      }
    }]
  ]
}
```
