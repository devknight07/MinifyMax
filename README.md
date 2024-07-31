# Minify CSS and JS Files

This tutorial will show you how to set up and run minification for CSS and JS using `terser` and `cssnano` with `postcss`.

## Prerequisites

Make sure you have `npm` installed on your machine.

## Installation

1. Install the required packages:

   ```bash
   npm install terser cssnano postcss postcss-cli
   ```
2. Create a `postcss.config.js` file in the root of your project with the following content:

    ```bash
    import cssnano from 'cssnano';
    export default {
      plugins: [
        cssnano({
          preset: 'default',
        }),
      ],
    };
    ```
    
3. Ensure that your `package.json` file includes "type" : "module":
    
    ```bash
    {
        "type": "module"
    }
    ```
4. Update your `package.json` scripts section to include the minification commands:

    >Adjust the paths and file names according to your project's structure.
    
    ```bash
    {
      "scripts": {
        "minify:css": "npx postcss public/css/style.css -o public/css/style.min.css",
        "minify:js": "npx terser public/js/script.js -o public/js/script.min.js",
        "minify": "npm run minify:css && npm run minify:js"
      }
    }
    ```
5. To minify your CSS and JS files, run the following command:

    ```bash
    npm run minify
    ```

