# Activity Sass mixins for your needs

Take what you need!

## This repository has some Sass-Mixins for you

- button
- image
- layout
- text
- scrollbar
- iphoneXHack

## General Usage

- install

```javascript
/* .npmrc */
@tiyafe:registry=https://npm.lizhifm.com/

/* .shell */
npm install --save-dev @tiyafe/awesome-mixins
```

- config

  - 方式一：react-app-rewired

    ```javascript
    /* config-overrides.js */

    //cdn文件地址要和package.json的name相同，如果是多頁面的情況下除了name還要加上頁面的文件夾名稱
    const { override, adjustStyleLoaders } = require("customize-cra");
    const packInfo = require("./package.json");

    webpack: override(
      adjustStyleLoaders(({ use: [, css, postcss, resolve, processor] }) => {
        // pre-processor
        if (processor && processor.loader.includes("sass-loader")) {
          processor.options.prependData = `
            @import "@tiyafe/awesome-mixins";
            $_cdnImagePath: "http://fepublicty.tiyalive.com/tiya/activities/${packInfo.name}";
            `;
        }
      })
    );
    ```

  - 方式二：craco

  ````javascript

      /* craco.config.js */

      //cdn文件地址要和package.json的name相同，如果是多頁面的情況下除了name還要加上頁面的文件夾名稱
      const packInfo = require("./package.json");
      module.exports ={
          style:{
              sass: {
                loaderOptions: {
                    additionalData: `
                    @import "@tiyafe/awesome-mixins";
                    $_cdnImagePath: "http://fepublicty.tiyalive.com/tiya/activities/${packInfo.name}";
                    `,
                },
            }
          }
      }
      ```
  ````

in your project's root directory to install the mixins repository. After that you can require the mixins file within your project.
