# SCSS UI Grid

## Install

```
npm install @wide/styles-grid --save
```

## Note

Please, note that more you add helper mixins, more your CSS compiled file will be heavy.  

So add helpers you really need.

## Usage

- [Variables](#variables)
- [container](#container)
- [row](#row)
- [col](#col)

<br />
<br />

## Variables

All those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="variables-grid-prefix"></a>`$grid-prefix`

Prefix for all grid classes.

```scss
$grid-prefix: '' !default;
```

#### <a name="variables-grid-prefix"></a>`$grid-prefix`

Grid gutter length. **Must be a pixel value.**

```scss
$grid-gutter: 15px !default;
```

<br />
<br />

## container

- [Variables](#container-variables)
  - [`$containers`](#container-variables-containers)
  - [`$containers-prefix`](#container-variables-containers-prefix)
- [Mixins](#container-mixins)
  - [`container-helper()`](#container-helper)
  - [`container-helper-with-bp()`](#container-helper-with-bp)
  - [`container()`](#container-container)

<br />

### <a name="container-variables"></a>Variables

All those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="container-variables-containers"></a>`$containers`

Container's breakpoints list.

```scss
$containers: (
    'xs': (
        max-width: 320px
    ),
    'sm': (
        max-width: 540px
    ),
    'md': (
        max-width: 720px
    ),
    'lg': (
        max-width: 960px
    ),
    'xl': (
        max-width: 1140px
    ),
    'xxl': (
        max-width: 1540px
    )
) !default;
```

#### <a name="container-variables-containers-prefix"></a>`$containers-prefix`

Container classes prefix.

```scss
$containers-prefix: $grid-prefix !default;
```

<br />

### <a name="container-mixins"></a>Mixins

#### <a name="container-helper"></a>`container-helper()`

Set all container classes.

```scss
@use '@wide/styles-grid' as grid;

@include grid.container-helper;
```

##### Output
```css
.container,
.container-fluid {
    width: 100%;
    margin-right: auto;
    margin-left: auto;
    padding-right: 0.9375rem;
    padding-left: 0.9375rem;
}
```

#### <a name="container-helper-with-bp"></a>`container-helper-with-bp()`

Set all container classes with breakpoints media queries.

```scss
@use '@wide/styles-grid' as grid;

@include grid.container-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) {
    .container, .container\@xs {
        max-width: 320px;
    }
}
@media (min-width: 36em) {
    .container, .container\@xs, .container\@sm {
        max-width: 540px;
    }
}
@media (min-width: 48em) {
    .container, .container\@xs, .container\@sm, .container\@md {
        max-width: 720px;
    }
}
@media (min-width: 64em) {
    .container, .container\@xs, .container\@sm, .container\@md, .container\@lg {
        max-width: 960px;
    }
}
@media (min-width: 75em) {
    .container, .container\@xs, .container\@sm, .container\@md, .container\@lg, .container\@xl {
        max-width: 1140px;
    }
}
@media (min-width: 100em) {
    .container, .container\@xs, .container\@sm, .container\@md, .container\@lg, .container\@xl, .container\@xxl {
        max-width: 1540px;
    }
}
.container\@xs, .container\@sm, .container\@md, .container\@lg, .container\@xl, .container\@xxl, .container-fluid {
    width: 100%;
    margin-right: auto;
    margin-left: auto;
    padding-right: 0.9375rem;
    padding-left: 0.9375rem;
}
```

#### <a name="container-container"></a>`container()`

Grid `container` entry point  
Combine both [`container-helper`](#container-helper) and [`container-helper-with-bp`](#container-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-grid' as grid;

@include grid.container;
```

###### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `container-helper-with-bp()` | `false` | `true` |

##### Output
See [`container-helper`](#container-helper) and [`container-helper-with-bp`](#container-helper-with-bp) outputs.

<br />
<br />

## row

- [Variables](#row-variables)
  - [`$rows-cols-max-columns`](#row-variables-rows-cols-max-columns)
  - [`$rows-prefix`](#row-variables-rows-prefix)
- [Mixins](#row-mixins)
  - [`row-helper()`](#row-helper)
  - [`row-helper-with-bp()`](#row-helper-with-bp)
  - [`row()`](#row-row)

<br />

### <a name="row-variables"></a>Variables

All those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="row-variables-rows-cols-max-columns"></a>`$rows-cols-max-columns`

Max columns for basic provided `.row-col-{col}@{breakpoint}` classes.

```scss
$rows-cols-max-columns: 6 !default;
```

#### <a name="row-variables-rows-prefix"></a>`$rows-prefix`
Row classes prefix.

```scss
$rows-prefix: $grid-prefix !default;
```

<br />

### <a name="row-mixins"></a>Mixins

#### <a name="row-helper"></a>`row-helper()`

Set row class.

```scss
@use '@wide/styles-grid' as grid;

@include grid.row-helper;
```

##### Output
```css
.row {
    display: flex;
    flex-wrap: wrap;
    margin-right: -0.9375rem;
    margin-left: -0.9375rem;
}
```

#### <a name="row-cols-helper"></a>`row-cols-helper()`

Set all row-cols classes from the [`$rows-cols-max-columns`](#row-variables-rows-cols-max-columns) variable.  
Specify on a parent element (e.g., `.row`) to force immediate children into NN numberof columns.

```scss
@use '@wide/styles-grid' as grid;

@include grid.row-cols-helper;
```

##### Output
```css
.row-cols-1 > *,
.row-cols-1 > .col {
    flex: 0 0 100%;
    max-width: 100%;
}

.row-cols-2 > *,
.row-cols-2 > .col {
    flex: 0 0 50%;
    max-width: 50%;
}

.row-cols-3 > *,
.row-cols-3 > .col {
    flex: 0 0 33.3333333333%;
    max-width: 33.3333333333%;
}

.row-cols-4 > *,
.row-cols-4 > .col {
    flex: 0 0 25%;
    max-width: 25%;
}

.row-cols-5 > *,
.row-cols-5 > .col {
    flex: 0 0 20%;
    max-width: 20%;
}

.row-cols-6 > *,
.row-cols-6 > .col {
    flex: 0 0 16.6666666667%;
    max-width: 16.6666666667%;
}
```

#### <a name="row-cols-helper-with-bp"></a>`row-cols-helper-with-bp()`

Set all row-cols classes with breakpoints media queries.

```scss
@use '@wide/styles-grid' as grid;

@include grid.row-cols-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .row-cols-1\@xs-only > *,
    .row-cols-1\@xs-only > .col {
        flex: 0 0 100%;
        max-width: 100%;
    }

    .row-cols-2\@xs-only > *,
    .row-cols-2\@xs-only > .col {
        flex: 0 0 50%;
        max-width: 50%;
    }

    .row-cols-3\@xs-only > *,
    .row-cols-3\@xs-only > .col {
        flex: 0 0 33.3333333333%;
        max-width: 33.3333333333%;
    }

    .row-cols-4\@xs-only > *,
    .row-cols-4\@xs-only > .col {
        flex: 0 0 25%;
        max-width: 25%;
    }

    .row-cols-5\@xs-only > *,
    .row-cols-5\@xs-only > .col {
        flex: 0 0 20%;
        max-width: 20%;
    }

    .row-cols-6\@xs-only > *,
    .row-cols-6\@xs-only > .col {
        flex: 0 0 16.6666666667%;
        max-width: 16.6666666667%;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .row-cols-1\@sm > *
     * .row-cols-1\@sm > .col
     * .row-cols-2\@sm > *
     * .row-cols-2\@sm > .col
     * .row-cols-3\@sm > *
     * .row-cols-3\@sm > .col
     * .row-cols-4\@sm > *
     * .row-cols-4\@sm > .col
     * .row-cols-5\@sm > *
     * .row-cols-5\@sm > .col
     * .row-cols-6\@sm > *
     * .row-cols-6\@sm > .col
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .row-cols-1\@sm-only > *
     * .row-cols-1\@sm-only > .col
     * .row-cols-2\@sm-only > *
     * .row-cols-2\@sm-only > .col
     * .row-cols-3\@sm-only > *
     * .row-cols-3\@sm-only > .col
     * .row-cols-4\@sm-only > *
     * .row-cols-4\@sm-only > .col
     * .row-cols-5\@sm-only > *
     * .row-cols-5\@sm-only > .col
     * .row-cols-6\@sm-only > *
     * .row-cols-6\@sm-only > .col
     */
}
@media (min-width: 48em) {
    /*
     * .row-cols-1\@md > *
     * .row-cols-1\@md > .col
     * .row-cols-2\@md > *
     * .row-cols-2\@md > .col
     * .row-cols-3\@md > *
     * .row-cols-3\@md > .col
     * .row-cols-4\@md > *
     * .row-cols-4\@md > .col
     * .row-cols-5\@md > *
     * .row-cols-5\@md > .col
     * .row-cols-6\@md > *
     * .row-cols-6\@md > .col
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .row-cols-1\@md-only > *
     * .row-cols-1\@md-only > .col
     * .row-cols-2\@md-only > *
     * .row-cols-2\@md-only > .col
     * .row-cols-3\@md-only > *
     * .row-cols-3\@md-only > .col
     * .row-cols-4\@md-only > *
     * .row-cols-4\@md-only > .col
     * .row-cols-5\@md-only > *
     * .row-cols-5\@md-only > .col
     * .row-cols-6\@md-only > *
     * .row-cols-6\@md-only > .col
     */
}
@media (min-width: 64em) {
    /*
     * .row-cols-1\@lg > *
     * .row-cols-1\@lg > .col
     * .row-cols-2\@lg > *
     * .row-cols-2\@lg > .col
     * .row-cols-3\@lg > *
     * .row-cols-3\@lg > .col
     * .row-cols-4\@lg > *
     * .row-cols-4\@lg > .col
     * .row-cols-5\@lg > *
     * .row-cols-5\@lg > .col
     * .row-cols-6\@lg > *
     * .row-cols-6\@lg > .col
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .row-cols-1\@lg-only > *
     * .row-cols-1\@lg-only > .col
     * .row-cols-2\@lg-only > *
     * .row-cols-2\@lg-only > .col
     * .row-cols-3\@lg-only > *
     * .row-cols-3\@lg-only > .col
     * .row-cols-4\@lg-only > *
     * .row-cols-4\@lg-only > .col
     * .row-cols-5\@lg-only > *
     * .row-cols-5\@lg-only > .col
     * .row-cols-6\@lg-only > *
     * .row-cols-6\@lg-only > .col
     */
}
@media (min-width: 75em) {
    /*
     * .row-cols-1\@xl > *
     * .row-cols-1\@xl > .col
     * .row-cols-2\@xl > *
     * .row-cols-2\@xl > .col
     * .row-cols-3\@xl > *
     * .row-cols-3\@xl > .col
     * .row-cols-4\@xl > *
     * .row-cols-4\@xl > .col
     * .row-cols-5\@xl > *
     * .row-cols-5\@xl > .col
     * .row-cols-6\@xl > *
     * .row-cols-6\@xl > .col
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .row-cols-1\@xl-only > *
     * .row-cols-1\@xl-only > .col
     * .row-cols-2\@xl-only > *
     * .row-cols-2\@xl-only > .col
     * .row-cols-3\@xl-only > *
     * .row-cols-3\@xl-only > .col
     * .row-cols-4\@xl-only > *
     * .row-cols-4\@xl-only > .col
     * .row-cols-5\@xl-only > *
     * .row-cols-5\@xl-only > .col
     * .row-cols-6\@xl-only > *
     * .row-cols-6\@xl-only > .col
     */
}
@media (min-width: 100em) {
    /*
     * .row-cols-1\@xxl > *
     * .row-cols-1\@xxl > .col
     * .row-cols-2\@xxl > *
     * .row-cols-2\@xxl > .col
     * .row-cols-3\@xxl > *
     * .row-cols-3\@xxl > .col
     * .row-cols-4\@xxl > *
     * .row-cols-4\@xxl > .col
     * .row-cols-5\@xxl > *
     * .row-cols-5\@xxl > .col
     * .row-cols-6\@xxl > *
     * .row-cols-6\@xxl > .col
     */
}
@media (min-width: 100em) {
    /*
     * .row-cols-1\@xxl-only > *
     * .row-cols-1\@xxl-only > .col
     * .row-cols-2\@xxl-only > *
     * .row-cols-2\@xxl-only > .col
     * .row-cols-3\@xxl-only > *
     * .row-cols-3\@xxl-only > .col
     * .row-cols-4\@xxl-only > *
     * .row-cols-4\@xxl-only > .col
     * .row-cols-5\@xxl-only > *
     * .row-cols-5\@xxl-only > .col
     * .row-cols-6\@xxl-only > *
     * .row-cols-6\@xxl-only > .col
     */
}
```

#### <a name="row-row"></a>`row()`

Grid `row` entry point  
Combine [`row-helper`](#row-helper), [`row-cols-helper`](#row-cols-helper) and [`row-cols-helper-with-bp`](#row-cols-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-grid' as grid;

@include grid.row;
```

###### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `row-cols-helper-with-bp()` | `false` | `true` |

##### Output
See [`row-helper`](#row-helper), [`row-cols-helper`](#row-cols-helper) and [`row-cols-helper-with-bp`](#row-cols-helper-with-bp) outputs.

<br />
<br />


## col

- [Variables](#col-variables)
  - [`$cols`](#col-variables-cols)
  - [`$cols-prefix`](#col-variables-cols-prefix)
  - [`$offset-prefix`](#col-variables-offset-prefix)
- [Mixins](#col-mixins)
  - [`col-helper()`](#col-helper)
  - [`cols-helper()`](#cols-helper)
  - [`cols-helper-with-bp()`](#cols-helper-with-bp)
  - [`col()`](#col-col)

<br />

### <a name="col-variables"></a>Variables

All those variables could be customized depending on what you need in your `variables.scss` file.  
Here are the default values.

#### <a name="col-variables-cols"></a>`$cols`

Number of columns for basic provided `.col-{col}@{breakpoint}` and `.offset-{col}@{breakpoint}` classes.

```scss
$cols: 12 !default;
```

#### <a name="col-variables-cols-prefix"></a>`$cols-prefix`

Col classes prefix.

```scss
$cols-prefix: $grid-prefix !default;
```

#### <a name="col-variables-offset-prefix"></a>`$offset-prefix`

Offset classes prefix.

```scss
$offset-prefix: $grid-prefix !default;
```

<br />

### <a name="col-mixins"></a>Mixins

#### <a name="col-helper"></a>`col-helper()`

Set col class.

```scss
@use '@wide/styles-grid' as grid;

@include grid.col-helper;
```

##### Output
```css
.col {
    position: relative;
    width: 100%;
    padding-right: 0.9375rem;
    padding-left: 0.9375rem;
    flex-basis: 0;
    flex-grow: 1;
    max-width: 100%;
}
```

#### <a name="cols-helper"></a>`cols-helper()`

Set all cols classes from the [`$cols`](#col-variables-cols) variable.

```scss
@use '@wide/styles-grid' as grid;

@include grid.cols-helper;
```

##### Output
```css
.col-auto {
  position: relative;
  width: 100%;
  padding-right: 0.9375rem;
  padding-left: 0.9375rem;
  flex: 0 0 auto;
  width: auto;
  max-width: 100%;
}

.col-1 {
  position: relative;
  width: 100%;
  padding-right: 0.9375rem;
  padding-left: 0.9375rem;
  flex: 0 0 8.3333333333%;
  max-width: 8.3333333333%;
}

.offset-1 {
  margin-left: 8.3333333333%;
}

/* and so on */

/*
 * .col-2
 * .offset-2
 * .col-3
 * .offset-3
 * .col-4
 * .offset-4
 * .col-5
 * .offset-5
 * .col-6
 * .offset-6
 * .col-7
 * .offset-7
 * .col-8
 * .offset-8
 * .col-9
 * .offset-9
 * .col-10
 * .offset-10
 * .col-11
 * .offset-11
 * .col-12
 */
```

#### <a name="cols-helper-with-bp"></a>`cols-helper-with-bp()`

Set all cols classes from the [`$cols`](#col-variables-cols) variable with breakpoints media queries.

```scss
@use '@wide/styles-grid' as grid;

@include grid.cols-helper-with-bp;
```

##### Output
```css
@media (min-width: 20.375em) and (max-width: 35.99875em) {
    .col-auto\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 auto;
        width: auto;
        max-width: 100%;
    }

    .col-1\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 8.3333333333%;
        max-width: 8.3333333333%;
    }

    .offset-1\@xs-only {
        margin-left: 8.3333333333%;
    }

    .col-2\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 16.6666666667%;
        max-width: 16.6666666667%;
    }

    .offset-2\@xs-only {
        margin-left: 16.6666666667%;
    }

    .col-3\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 25%;
        max-width: 25%;
    }

    .offset-3\@xs-only {
        margin-left: 25%;
    }

    .col-4\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 33.3333333333%;
        max-width: 33.3333333333%;
    }

    .offset-4\@xs-only {
        margin-left: 33.3333333333%;
    }

    .col-5\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 41.6666666667%;
        max-width: 41.6666666667%;
    }

    .offset-5\@xs-only {
        margin-left: 41.6666666667%;
    }

    .col-6\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 50%;
        max-width: 50%;
    }

    .offset-6\@xs-only {
        margin-left: 50%;
    }

    .col-7\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 58.3333333333%;
        max-width: 58.3333333333%;
    }

    .offset-7\@xs-only {
        margin-left: 58.3333333333%;
    }

    .col-8\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 66.6666666667%;
        max-width: 66.6666666667%;
    }

    .offset-8\@xs-only {
        margin-left: 66.6666666667%;
    }

    .col-9\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 75%;
        max-width: 75%;
    }

    .offset-9\@xs-only {
        margin-left: 75%;
    }

    .col-10\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 83.3333333333%;
        max-width: 83.3333333333%;
    }

    .offset-10\@xs-only {
        margin-left: 83.3333333333%;
    }

    .col-11\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 91.6666666667%;
        max-width: 91.6666666667%;
    }

    .offset-11\@xs-only {
        margin-left: 91.6666666667%;
    }

    .col-12\@xs-only {
        position: relative;
        width: 100%;
        padding-right: 0.9375rem;
        padding-left: 0.9375rem;
        flex: 0 0 100%;
        max-width: 100%;
    }
}
/* and so on */
@media (min-width: 36em) {
    /*
     * .col-auto\@sm
     * .col-1\@sm
     * .offset-1\@sm
     * .col-2\@sm
     * .offset-2\@sm
     * .col-3\@sm
     * .offset-3\@sm
     * .col-4\@sm
     * .offset-4\@sm
     * .col-5\@sm
     * .offset-5\@sm
     * .col-6\@sm
     * .offset-6\@sm
     * .col-7\@sm
     * .offset-7\@sm
     * .col-8\@sm
     * .offset-8\@sm
     * .col-9\@sm
     * .offset-9\@sm
     * .col-10\@sm
     * .offset-10\@sm
     * .col-11\@sm
     * .offset-11\@sm
     * .col-12\@sm
     */
}
@media (min-width: 36em) and (max-width: 47.99875em) {
    /*
     * .col-auto\@sm-only
     * .col-1\@sm-only
     * .offset-1\@sm-only
     * .col-2\@sm-only
     * .offset-2\@sm-only
     * .col-3\@sm-only
     * .offset-3\@sm-only
     * .col-4\@sm-only
     * .offset-4\@sm-only
     * .col-5\@sm-only
     * .offset-5\@sm-only
     * .col-6\@sm-only
     * .offset-6\@sm-only
     * .col-7\@sm-only
     * .offset-7\@sm-only
     * .col-8\@sm-only
     * .offset-8\@sm-only
     * .col-9\@sm-only
     * .offset-9\@sm-only
     * .col-10\@sm-only
     * .offset-10\@sm-only
     * .col-11\@sm-only
     * .offset-11\@sm-only
     * .col-12\@sm-only
     */
}
@media (min-width: 48em) {
    /*
     * .col-auto\@md
     * .col-1\@md
     * .offset-1\@md
     * .col-2\@md
     * .offset-2\@md
     * .col-3\@md
     * .offset-3\@md
     * .col-4\@md
     * .offset-4\@md
     * .col-5\@md
     * .offset-5\@md
     * .col-6\@md
     * .offset-6\@md
     * .col-7\@md
     * .offset-7\@md
     * .col-8\@md
     * .offset-8\@md
     * .col-9\@md
     * .offset-9\@md
     * .col-10\@md
     * .offset-10\@md
     * .col-11\@md
     * .offset-11\@md
     * .col-12\@md
     */
}
@media (min-width: 48em) and (max-width: 63.99875em) {
    /*
     * .col-auto\@md-only
     * .col-1\@md-only
     * .offset-1\@md-only
     * .col-2\@md-only
     * .offset-2\@md-only
     * .col-3\@md-only
     * .offset-3\@md-only
     * .col-4\@md-only
     * .offset-4\@md-only
     * .col-5\@md-only
     * .offset-5\@md-only
     * .col-6\@md-only
     * .offset-6\@md-only
     * .col-7\@md-only
     * .offset-7\@md-only
     * .col-8\@md-only
     * .offset-8\@md-only
     * .col-9\@md-only
     * .offset-9\@md-only
     * .col-10\@md-only
     * .offset-10\@md-only
     * .col-11\@md-only
     * .offset-11\@md-only
     * .col-12\@md-only
     */
}
@media (min-width: 64em) {
    /*
     * .col-auto\@lg
     * .col-1\@lg
     * .offset-1\@lg
     * .col-2\@lg
     * .offset-2\@lg
     * .col-3\@lg
     * .offset-3\@lg
     * .col-4\@lg
     * .offset-4\@lg
     * .col-5\@lg
     * .offset-5\@lg
     * .col-6\@lg
     * .offset-6\@lg
     * .col-7\@lg
     * .offset-7\@lg
     * .col-8\@lg
     * .offset-8\@lg
     * .col-9\@lg
     * .offset-9\@lg
     * .col-10\@lg
     * .offset-10\@lg
     * .col-11\@lg
     * .offset-11\@lg
     * .col-12\@lg
     */
}
@media (min-width: 64em) and (max-width: 74.99875em) {
    /*
     * .col-auto\@lg-only
     * .col-1\@lg-only
     * .offset-1\@lg-only
     * .col-2\@lg-only
     * .offset-2\@lg-only
     * .col-3\@lg-only
     * .offset-3\@lg-only
     * .col-4\@lg-only
     * .offset-4\@lg-only
     * .col-5\@lg-only
     * .offset-5\@lg-only
     * .col-6\@lg-only
     * .offset-6\@lg-only
     * .col-7\@lg-only
     * .offset-7\@lg-only
     * .col-8\@lg-only
     * .offset-8\@lg-only
     * .col-9\@lg-only
     * .offset-9\@lg-only
     * .col-10\@lg-only
     * .offset-10\@lg-only
     * .col-11\@lg-only
     * .offset-11\@lg-only
     * .col-12\@lg-only
     */
}
@media (min-width: 75em) {
    /*
     * .col-auto\@xl
     * .col-1\@xl
     * .offset-1\@xl
     * .col-2\@xl
     * .offset-2\@xl
     * .col-3\@xl
     * .offset-3\@xl
     * .col-4\@xl
     * .offset-4\@xl
     * .col-5\@xl
     * .offset-5\@xl
     * .col-6\@xl
     * .offset-6\@xl
     * .col-7\@xl
     * .offset-7\@xl
     * .col-8\@xl
     * .offset-8\@xl
     * .col-9\@xl
     * .offset-9\@xl
     * .col-10\@xl
     * .offset-10\@xl
     * .col-11\@xl
     * .offset-11\@xl
     * .col-12\@xl
     */
}
@media (min-width: 75em) and (max-width: 99.99875em) {
    /*
     * .col-auto\@xl-only
     * .col-1\@xl-only
     * .offset-1\@xl-only
     * .col-2\@xl-only
     * .offset-2\@xl-only
     * .col-3\@xl-only
     * .offset-3\@xl-only
     * .col-4\@xl-only
     * .offset-4\@xl-only
     * .col-5\@xl-only
     * .offset-5\@xl-only
     * .col-6\@xl-only
     * .offset-6\@xl-only
     * .col-7\@xl-only
     * .offset-7\@xl-only
     * .col-8\@xl-only
     * .offset-8\@xl-only
     * .col-9\@xl-only
     * .offset-9\@xl-only
     * .col-10\@xl-only
     * .offset-10\@xl-only
     * .col-11\@xl-only
     * .offset-11\@xl-only
     * .col-12\@xl-only
     */
}
@media (min-width: 100em) {
    /*
     * .col-auto\@xxl
     * .col-1\@xxl
     * .offset-1\@xxl
     * .col-2\@xxl
     * .offset-2\@xxl
     * .col-3\@xxl
     * .offset-3\@xxl
     * .col-4\@xxl
     * .offset-4\@xxl
     * .col-5\@xxl
     * .offset-5\@xxl
     * .col-6\@xxl
     * .offset-6\@xxl
     * .col-7\@xxl
     * .offset-7\@xxl
     * .col-8\@xxl
     * .offset-8\@xxl
     * .col-9\@xxl
     * .offset-9\@xxl
     * .col-10\@xxl
     * .offset-10\@xxl
     * .col-11\@xxl
     * .offset-11\@xxl
     * .col-12\@xxl
     */
}
@media (min-width: 100em) {
    /*
     * .col-auto\@xxl-only
     * .col-1\@xxl-only
     * .offset-1\@xxl-only
     * .col-2\@xxl-only
     * .offset-2\@xxl-only
     * .col-3\@xxl-only
     * .offset-3\@xxl-only
     * .col-4\@xxl-only
     * .offset-4\@xxl-only
     * .col-5\@xxl-only
     * .offset-5\@xxl-only
     * .col-6\@xxl-only
     * .offset-6\@xxl-only
     * .col-7\@xxl-only
     * .offset-7\@xxl-only
     * .col-8\@xxl-only
     * .offset-8\@xxl-only
     * .col-9\@xxl-only
     * .offset-9\@xxl-only
     * .col-10\@xxl-only
     * .offset-10\@xxl-only
     * .col-11\@xxl-only
     * .offset-11\@xxl-only
     * .col-12\@xxl-only
     */
}
```

#### <a name="col-col"></a>`col()`

Grid `col` entry point  
Combine [`col-helper`](#col-helper), [`cols-helper`](#cols-helper) and [`cols-helper-with-bp`](#cols-helper-with-bp) helpers in one helper.

```scss
@use '@wide/styles-grid' as grid;

@include grid.col;
```

###### Parameters
| Type | Description | Mandatory | Default |
|---|---|---|---|
| `Boolean` | Use `cols-helper-with-bp()` | `false` | `true` |

##### Output
See [`col-helper`](#col-helper), [`cols-helper`](#cols-helper) and [`cols-helper-with-bp`](#cols-helper-with-bp) outputs.

<br />
<br />

## Authors

- **Aymeric Assier** - [github.com/myeti](https://github.com/myeti)
- **Julien Martins Da Costa** - [github.com/jdacosta](https://github.com/jdacosta)

<br />

### Contributors

- **Sébastien Robillard** - [github.com/robiseb](https://github.com/robiseb)

<br />
<br />

## Resources 
- [Bootstrap](https://github.com/twbs/bootstrap)

<br />
<br />

## License

This project is licensed under the MIT License - see the [licence](licence) file for details