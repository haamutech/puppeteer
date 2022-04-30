# puppeteer

This repository builds puppeteer Docker image that is based on Alpine Linux. Alpine Linux makes it possible to get puppeteer to run on ARM devices. [Please see the documentation about the actual package](https://github.com/puppeteer/puppeteer).

## Quick start

Below is a small snippet that you can use as a starting point.

```js
const puppeteer = require('puppeteer');

async function main(argv) {
   if (argv.length < 2) {
      console.log(`Usage ${argv[0]} ${argv[1]} [url]`);
      return 1;
   }

   // Start the browser in headless mode.
   const browser = await puppeteer.launch({
      headless: true,
      executablePath: process.env.CHROME_BIN || null,
      args: ['--no-sandbox', '--headless', '--disable-gpu', '--disable-dev-shm-usage']
   });

   // Open a new page.
   const page = await browser.newPage();

   // Navigate to url.
   await page.goto(argv[1]);

   // TODO: Do something with the page.

   // Close the browser.
   await browser.close();

   return 0;
}

main(process.argv).then(process.exit);
```
