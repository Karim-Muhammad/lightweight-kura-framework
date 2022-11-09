# lightweight-kura-framework

---gulpjs content---
```js
const { src, dest, watch, series } = require("gulp");
const sass = require("gulp-sass")(require("sass"));
const purgecss = require("gulp-purgecss");

function build_styles() {
  return src("scss/**/*.scss")
    .pipe(sass())
    .pipe(dest("css"))
    .pipe(purgecss({ content: ["*.html"] }))
    .pipe(dest("purged/"));
}

function watch_files() {
  watch(["scss/**/*.scss"], build_styles);
  // => /**/ means any subfolder as well if found
}

exports.default = series(build_styles, watch_files);
```
