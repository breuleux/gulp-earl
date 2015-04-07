
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

This might be a bit confusing: `earl-gulp` exports macros to neatly
define gulp tasks in Earl Grey, whereas `gulp-earl` (this package) is
to compile `.eg` files.

    require-macros:
       earl-gulp -> task

    require:
       gulp-earl as earl

    task earl:
       chain gulp:
          @src("./src/**/*.eg")
          @pipe(earl())
          @pipe(gulp.dest("./build/"))

