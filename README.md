
gulp-earl
=========

gulp plugin for [Earl Grey](http://earl-grey.io)

Usage
-----

> `earl([opts])`

### Options

`opts.es5` is a boolean option to change compilation to ES5.  Defaults to false.

`opts.sourceMaps` is a string that specifies how to handle sourcemaps. `.compute` will compute sourcemaps but does not place `sourceMappingURL` within the file. `.inline` does add it.  The default is null.

`opts.runtime` is a string that specifies which runtime to require.  If null, no runtime is used and this removes some boilerplate code.  This defaults to requiring `earlgrey-runtime`.

`opts.parameters` is an object containing flags that you can pass right into your programs to be accessed by macros via `@getopt("flagName")`.  Flags are not limited to booleans and can be any arbitray data. For example (in EG):
```earl-grey
parameters = {
  debug-level = .critical
  test-data = {"Pepperoni", "Cheese", "Sausage", "Peppers"}
  tests = false
}
```

### JavaScript

    var earl = require('gulp-earl');

    gulp.task('earl', function() {
      gulp.src('./src/**/*.eg')
        .pipe(earl({}))
        .pipe(gulp.dest('./build/'))
    });


### Earl Grey (using `earl-gulp`)

`earl-gulp` exports macros to neatly define gulp tasks in Earl Grey,
whereas `gulp-earl` (this package) is to compile `.eg` files. Don't
confuse them (maybe I should just merge them...)

    require-macros:
       earl-gulp -> task

    require:
       gulp-earl as earl

    task earl:
       chain gulp:
          @src("./src/**/*.eg")
          @pipe(earl())
          @pipe(gulp.dest("./build/"))

