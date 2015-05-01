
gulp-earl
=========

gulp plugin for [Earl Grey](http://breuleux.github.io/earl-grey/)

Usage
-----

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

