There appears to be some conflict between [`node-source-map-support`](https://github.com/evanw/node-source-map-support) and [`minifyify`](https://github.com/ben-ng/minifyify). `app.js` contains the simplest usage of `node-source-map-support`:

    require('source-map-support');
    console.log('Success!');

Compile it both with and without `minifyify` by running `npm run build` (precompiled versions are in the `dist` folder).

Then you can test it by running `npm test` or opening the two .html files in your browser and looking at the console. The version without minifyify works, but the version with minifyify results in an error:

    Error: Cannot find module './base64-vlq'
        at Function.Module._resolveFilename (module.js:325:15)
        at Function.Module._load (module.js:276:25)
        at Module.require (module.js:353:17)
        at require (internal/module.js:12:17)
        at s (/home/jdscheff/projects/minifyify-node-source-map-support-bug/dist/app-with-minifyify.js:1:176)
        at /home/jdscheff/projects/minifyify-node-source-map-support-bug/dist/app-with-minifyify.js:1:367
        at l (/home/jdscheff/projects/minifyify-node-source-map-support-bug/dist/app-with-minifyify.js:31:1675)
        at o (/home/jdscheff/projects/minifyify-node-source-map-support-bug/dist/app-with-minifyify.js:31:1181)
        at Object.<anonymous> (/home/jdscheff/projects/minifyify-node-source-map-support-bug/dist/app-with-minifyify.js:26:280)
        at u (/home/jdscheff/projects/minifyify-node-source-map-support-bug/dist/app-with-minifyify.js:31:815)