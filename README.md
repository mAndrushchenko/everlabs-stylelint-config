# Everlabs stylelint config
The [``.stylelintrc.yml``](.stylelintrc.yml) includes the list of rules for SCSS that help you avoid errors and enforce conventions in your styles.


## Installation


### 1. Stylelint
```
npm install stylelint --save-dev
```


### 2. CSS and SCSS stylelint configs
```
npm install stylelint-config-standard-scss --save-dev
```


### 3. Stylelint rules order
```
npm install stylelint-config-rational-order --save-dev
```


### 4. Also need to install ``postcss``
```
npm install postcss --save-dev
```
This library is needed to read custom rules


### 5. Copy file [``.stylelintrc.yml``](.stylelintrc.yml) and paste it to the root folder in the project


### 6. Now need to enable linter in the IDE


#### For JetBrains (Webstorm, Rubymine)
Open **File/settings**. In search input type **stylelint**. Then check **Enable**:

![jet_brains_step_1](assets/jetbrains_step_1.png)

Click on 3 dots and select``node-modules/stylelint``. Than click on **Apply** and **OK**:

![jet_brains_step_1](assets/jetbrains_step_2.png)

Now linter should working.


#### For Visual Code
First need to install plugins **Prettier** and **Stylelint**:

![jet_brains_step_1](assets/vs_step_1.png)

Open **file/preferences/settings**. Then turn on the JSON mode for the settings (as on screen below)

![jet_brains_step_1](assets/vs_step_2.png)

Now need to add (don't replace) to the ``settings.json`` next rules:
```json
{
  "stylelint.enable": true,
  "stylelint.validate": [
    "css",
    "scss"
  ],
  "css.validate": false,
  "scss.validate": false,
  "[scss]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```
Don't forget to save file and then linter should works.


### 7. Add script to ``package.json``

```json
{
  "scripts": {
    "lint-css": "npx stylelint '[YOUR_PATH]/**/*.scss' --fix"
  }
}
```

Replace ``[YOUR_PATH]`` to path from your root folder of the project to folder where you store styles. If you don't need autofix, delete ``--fix``.


### 8. Lets test!
For start testing your project, run the command below:
```
npm run lint-css
```


## Customisation


You can extend [``.stylelintrc.yml``](.stylelintrc.yml) file by adding other rules. For example your project has SCSS files that should not be linted. You can add this files to the list:

```yaml
ignoreFiles: [
  # Exclude all min.scss files
  "**/*.min.scss",

  # Exclude vendors
  "**/vendors/**/*.scss",
  
  # Your files
  "**/example_file.scss"
]
```

Also you can disable or enable some rules that doesn't fit to your project:

```yaml
rules:
  color-named: null
  # other rules...
```

The list of rules:
- [CSS](https://stylelint.io/user-guide/rules/list)
- [SCSS](https://github.com/stylelint-scss/stylelint-scss#list-of-rules)
- [Rules order](https://github.com/hudochenkov/stylelint-order)
- [Example config with order rules](https://github.com/maxdenaro/maxgraph-youtube-source/blob/master/stylelint/.stylelintrc)

 For disabling specific line write ``/* stylelint-disable-next-line [RULE_NAME] */``:
```scss
.list-item {
  /* stylelint-disable-next-line color-named */
  color: green;
}
```
More about ignoring rules in the files you can find [here](https://stylelint.io/user-guide/ignore-code/)


## Extends


Everlabs config extends:
- [stylelint-config-standard-scss](https://github.com/stylelint-scss/stylelint-config-standard-scss)
- [stylelint-config-rational-order](https://github.com/constverum/stylelint-config-rational-order)

The ``stylelint-config-standard-scss`` in turn under hood extends others:
- [stylelint-config-recommended](https://stylelint.io/user-guide/rules/list/#avoid-errors)
- [stylelint-config-standard](https://github.com/stylelint/stylelint-config-standard/blob/main/index.js)
- [stylelint-config-recommended-scss](https://github.com/stylelint-scss/stylelint-config-recommended-scss)


## Rules
- [alpha-value-notation](#alpha-value-notation) (autofixable)
- [at-rule-empty-line-before](#at-rule-empty-line-before) (autofixable)
- [at-rule-name-case](#at-rule-name-case) (autofixable)
- [at-rule-name-space-after](#at-rule-name-space-after) (autofixable)
- [at-rule-no-vendor-prefix](#at-rule-no-vendor-prefix) (autofixable)
- [at-rule-semicolon-newline-after](#at-rule-semicolon-newline-after) (autofixable)
- [block-closing-brace-empty-line-before](#block-closing-brace-empty-line-before) (autofixable)
- [block-closing-brace-newline-after](#block-closing-brace-newline-after) (autofixable)
- [block-closing-brace-newline-before](#block-closing-brace-newline-before) (autofixable)
- [block-closing-brace-space-before](#block-closing-brace-space-before) (autofixable)
- [block-opening-brace-newline-after](#block-opening-brace-newline-after) (autofixable)
- [block-opening-brace-space-after](#block-opening-brace-space-after) (autofixable)
- [block-opening-brace-space-before](#block-opening-brace-space-before) (autofixable)
- [color-hex-case](#color-hex-case) (autofixable)
- [color-hex-length](#color-hex-length) (autofixable)
- [comment-empty-line-before](#comment-empty-line-before) (autofixable)
- [comment-whitespace-inside](#comment-whitespace-inside) (autofixable)
- [custom-property-empty-line-before](#custom-property-empty-line-before) (autofixable)
- [custom-media-pattern](#custom-media-pattern)
- [custom-property-pattern](#custom-property-pattern)
- [declaration-bang-space-before](#declaration-bang-space-after) (autofixable)
- [declaration-block-semicolon-newline-after](#declaration-block-semicolon-newline-after) (autofixable)
- [declaration-block-semicolon-space-after](#declaration-block-semicolon-space-after) (autofixable)
- [declaration-block-semicolon-space-before](#declaration-block-semicolon-space-before) (autofixable)
- [declaration-block-single-line-max-declarations](#declaration-block-single-line-max-declarations)


## Examples


### [alpha-value-notation](https://stylelint.io/user-guide/rules/list/alpha-value-notation/#percentage)

#### Config:
```yaml
'alpha-value-notation': [
  'percentage',
  {
    exceptProperties: ['opacity'],
  },
]
```

#### Example:

```scss
// bad
a { opacity: 0.5 }

a { color: rgb(0 0 0 / 0.5) }

// good
a { opacity: 50% }

a { color: rgb(0 0 0 / 50%) }
```


### [at-rule-empty-line-before](https://stylelint.io/user-guide/rules/list/at-rule-empty-line-before#always)

#### Config:
```yaml
'at-rule-empty-line-before': [
  'always',
  {
    except: ['blockless-after-same-name-blockless', 'first-nested'],
    ignore: ['after-comment'],
  },
],
```

#### Example:

```scss
// bad
a {} @media {}

a {}
@media {}

// good
a {}

@media {}
```


### [at-rule-name-case](https://stylelint.io/user-guide/rules/list/at-rule-name-case#lower)

#### Config:
```yaml
'at-rule-name-case': 'lower'
```

#### Example:

```scss
// bad
@Media (min-width: 50em) {}

@MEDIA (min-width: 50em) {}

// good
@media (min-width: 50em) {}
```


### [at-rule-name-space-after](https://stylelint.io/user-guide/rules/list/at-rule-name-space-after/#always-single-line)

#### Config:
```yaml
'at-rule-name-space-after': 'always-single-line'
```

#### Example:

```scss
// bad
@media(min-width: 700px) {}

@media  (min-width: 700px) {}

// good
@media (min-width: 700px) {}
```


### [at-rule-no-vendor-prefix](https://stylelint.io/user-guide/rules/list/at-rule-no-vendor-prefix#true)

#### Config:
```yaml
'at-rule-no-vendor-prefix': true
```

#### Example:

```scss
// bad
@-webkit-keyframes anim { 0% { top: 0; } }

@-ms-viewport { orientation: landscape; }

// good
@keyframes anim { 0% { top: 0; } }

@viewport { orientation: landscape; }
```


### [at-rule-semicolon-newline-after](https://stylelint.io/user-guide/rules/list/at-rule-semicolon-newline-after#always)

#### Config:
```yaml
'at-rule-semicolon-newline-after': 'always',
```

#### Example:

```scss
// bad
@import url("x.css"); @import url("y.css");

@import url("x.css"); a {}

// good
@import url("x.css");
@import url("y.css");

@import url("x.css"); /* end-of-line comment */
a {}

@import url("x.css");

a {}
```


### [block-closing-brace-empty-line-before](https://stylelint.io/user-guide/rules/list/block-closing-brace-empty-line-before#never)

#### Config:
```yaml
'block-closing-brace-empty-line-before': 'never'
```

#### Example:

```scss
// bad
a {
  color: pink;

}

// good
a {
  color: pink;
}
```


### [block-closing-brace-newline-after](https://stylelint.io/user-guide/rules/list/block-closing-brace-newline-after#always)

#### Config:
```yaml
'block-closing-brace-newline-after': 'always'
```

#### Example:

```scss
// bad
a { color: pink; }b { color: red; }

a { color: pink;
} b { color: red; }

// good
a { color: pink; }
b { color: red; }
```


### [block-closing-brace-newline-before](https://stylelint.io/user-guide/rules/list/block-closing-brace-newline-before/#always-multi-line)

#### Config:
```yaml
'block-closing-brace-newline-before': 'always-multi-line'
```

#### Example:

```scss
// bad
a {
  color: pink;}

// good
a { color: pink; }

a {
  color: pink;
}
```


### [block-closing-brace-space-before](https://stylelint.io/user-guide/rules/list/block-closing-brace-space-before#always-single-line)

#### Config:
```yaml
'block-closing-brace-space-before': 'always-single-line'
```

#### Example:

```scss
// bad
a { color: pink;}

// good
a { color: pink; }
```


### [block-opening-brace-newline-after](https://stylelint.io/user-guide/rules/list/block-opening-brace-newline-after#always-multi-line)

#### Config:
```yaml
'block-opening-brace-newline-after': 'always-multi-line'
```

#### Example:

```scss
// bad
a{color: pink;
}

// good
a { color: pink; }
```


### [block-opening-brace-space-after](https://stylelint.io/user-guide/rules/list/block-opening-brace-space-after#always-single-line)

#### Config:
```yaml
'block-opening-brace-space-after': 'always-single-line'
```

#### Example:

```scss
// bad
a {color: pink; }

// good
a { color: pink; }
```


### [block-opening-brace-space-before](https://stylelint.io/user-guide/rules/list/block-opening-brace-space-before#always)

#### Config:
```yaml
'block-opening-brace-space-before': 'always'
```

#### Example:

```scss
// bad
a{ color: pink; }

// good
a { color: pink; }
```


### [color-hex-case](https://stylelint.io/user-guide/rules/list/color-hex-case#lower)

#### Config:
```yaml
'color-hex-case': 'lower'
```

#### Example:

```scss
// bad
a { color: #FFF; }

// good
a { color: #000; }

a { color: #fff; }
```


### [color-hex-length](https://stylelint.io/user-guide/rules/list/color-hex-length#short)

#### Config:
```yaml
'color-hex-length': 'short'
```

#### Example:

```scss
// bad
a { color: #ffffff; }

a { color: #ffffffaa; }

// good
a { color: #fff; }

a { color: #fffa; }

a { color: #a4a4a4; }
```


### [comment-empty-line-before](https://stylelint.io/user-guide/rules/list/comment-empty-line-before#always)

#### Config:
```yaml
'comment-empty-line-before': [
  'always',
  {
    except: ['first-nested'],
    ignore: ['stylelint-commands'],
  },
]
```

#### Example:

```scss
// bad
a {}
/* comment */

// good
a {}

/* comment */

a {} /* comment */
```


### [comment-whitespace-inside](https://stylelint.io/user-guide/rules/list/comment-whitespace-inside#always)

#### Config:
```yaml
'comment-whitespace-inside': 'always'
```

#### Example:

```scss
// bad
/*comment*/

/*comment */

/** comment**/

// good
/* comment */

/** comment **/
```


### [custom-property-empty-line-before](https://stylelint.io/user-guide/rules/list/custom-property-empty-line-before#always)

#### Config:
```yaml
'custom-property-empty-line-before': [
  'always',
  {
    except: ['after-custom-property', 'first-nested'],
    ignore: ['after-comment', 'inside-single-line-block'],
  },
]
```

#### Example:

```scss
// bad
a {
  top: 10px;
  --foo: pink;
  --bar: red;
}

// good
a {
  top: 10px;

  --foo: pink;
  --bar: red;
}
```


### [custom-media-pattern](https://stylelint.io/user-guide/rules/list/custom-media-pattern)

#### Config:
```yaml
'custom-media-pattern': [
  '^([a-z][a-z0-9]*)(-[a-z0-9]+)*$',
  {
    message: 'Expected custom media query name to be kebab-case',
  },
]
```

#### Example:

```scss
// bad
@custom-media fooBar (min-width: 30em);

@custom-media foo_bar (min-width: 30em);


// good
@custom-media foo-bar (min-width: 30em);
```


### [custom-property-pattern](https://stylelint.io/user-guide/rules/list/custom-property-pattern/)

#### Config:
```yaml
'custom-property-pattern': [
  '^([a-z][a-z0-9]*)(-[a-z0-9]+)*$',
  {
    message: 'Expected custom property name to be kebab-case',
  },
],
```

#### Example:

```scss
// bad
:root { --foo_bar: 0; }

// good
:root { --foo-bar: 0; }
```


### [declaration-bang-space-after](https://stylelint.io/user-guide/rules/list/declaration-bang-space-after#never)

#### Config:
```yaml
'declaration-bang-space-after': 'never'
```

#### Example:

```scss
// bad
a { color: pink ! important; }

a { color: pink! important; }

// good
a { color: pink !important; }
```


### [declaration-bang-space-before](https://stylelint.io/user-guide/rules/list/declaration-bang-space-before#always)

#### Config:
```yaml
'declaration-bang-space-before': 'always'
```

#### Example:

```scss
// bad
a { color: pink!important; }

a { color: pink  ! important; }

// good
a { color: pink !important; }
```


### [declaration-block-semicolon-newline-after](https://stylelint.io/user-guide/rules/list/declaration-block-semicolon-newline-after#always-multi-line)

#### Config:
```yaml
'declaration-block-semicolon-newline-after': 'always-multi-line'
```

#### Example:

```scss
// bad
a {
  color: pink; top: 0;
}

// good
a { color: pink; }

a { color: pink; top: 0; }

a {
  color: pink;
  top: 0;
}
```


### [declaration-block-semicolon-space-after](https://stylelint.io/user-guide/rules/list/declaration-block-semicolon-space-after#always-single-line)

#### Config:
```yaml
'declaration-block-semicolon-space-after': 'always-single-line'
```

#### Example:

```scss
// bad
a { color: pink;top: 0; }

// good
a { color: pink; top: 0; }

a {
  color: pink;
  top: 0;
}
```


### [declaration-block-semicolon-space-before](https://stylelint.io/user-guide/rules/list/declaration-block-semicolon-space-before#never)

#### Config:
```yaml
'declaration-block-semicolon-space-before': 'never'
```

#### Example:

```scss
// bad
a { color: pink ; }

a { color: pink ; top: 0 ; }

// good
a { color: pink; }

a { color: pink; top: 0; }
```


### [declaration-block-single-line-max-declarations](https://stylelint.io/user-guide/rules/list/declaration-block-semicolon-space-before#never)

#### Config:
```yaml
'declaration-block-single-line-max-declarations': 1
```

#### Example:

```scss
// bad
a { color: pink; top: 3px; }

a,
b { color: pink; top: 3px; }

// good
a { color: pink; }

a,
b { color: pink; }

a {
  color: pink;
  top: 3px;
}
```



# END_OF_THE_FILE
