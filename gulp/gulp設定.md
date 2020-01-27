# エラー集
## 1月27日TypeError: imagemin.jpegtran is not a function」というエラー
- 解決策
gulpfile.js
`imagemin.jpegtran()`
を
`imagemin.mozjpeg()`
に変更して解決（アップデートによる変更？）
## Error: Invalid built-in order 'alphabetically' provided. Available built-in orders are: alphabetical,concentric-css,smacss
`.pipe( postcss([ cssdeclsort({ order: 'alphabetically' }) ]) )//プロパティをソートし直す(アルファベット順)`
ここを
`.pipe( postcss([ cssdeclsort({ order: 'alphabetical' }) ]) )//プロパティをソートし直す(アルファベット順)`
に訂正
# gulp導入
- npm init -y
- npm install -D gulp
- 各プラグインインストール
```
npm install gulp-sass gulp-plumber gulp-notify gulp-sass-glob browser-sync gulp-postcss autoprefixer css-declaration-sorter gulp-imagemin imagemin-pngquant imagemin-mozjpeg gulp-ejs gulp-rename gulp-uglify gulp-pug  --save-dev
```
## タスクコマンド一覧
**npx gulp**
**npx images**
**npx js**

## gulp.jsの設定
```js
const
  gulp = require('gulp');
  sass = require('gulp-sass'); //Sassコンパイル
  plumber = require('gulp-plumber'); //エラー時の強制終了を防止
  notify = require('gulp-notify'); //エラー発生時にデスクトップ通知する
  sassGlob = require('gulp-sass-glob'); //@importの記述を簡潔にする
  browserSync = require( 'browser-sync' ); //ブラウザ反映
  postcss = require('gulp-postcss'); //autoprefixerとセット
  autoprefixer = require('autoprefixer'); //ベンダープレフィックス付与
  cssdeclsort = require('css-declaration-sorter'); //css並べ替え
  imagemin = require('gulp-imagemin');
  pngquant = require('imagemin-pngquant');
  mozjpeg = require('imagemin-mozjpeg');
  ejs = require("gulp-ejs");
  rename = require("gulp-rename"); //.ejsの拡張子を変更
  uglify = require('gulp-uglify')
  pug = require('gulp-pug');

const
  pugOptions = {
    pretty: true,
  }
  paths = {
    src: {
      pug: [
        "src/pug/*.pug",
        "!src/pug/_*.pug",
      ],
      html: [
        "src/html/*.html",
      ],
      sass: [
        "src/sass/**/*.scss",
        "src/sass/**/*.sass",
        "!src/sass/**/_*.scss",
        "!src/sass/**/_*.sass",
      ],
      js: [
        "src/js/*.js",
      ],
    },
    dest: {
      html: "dist/",
      css: "dist/css",
      img: "dist/img",
      js: "dist/js",
    }
  }

//pugの設定
gulp.task('pug', function() {
  return gulp
  .src( paths.src.pug )
  .pipe( plumber({ errorHandler: notify.onError("Error: <%= error.message %>") }) )//エラーチェック
  .pipe(pug(pugOptions))
  .pipe(gulp.dest(paths.dest.html))
})

//jsの圧縮設定
gulp.task("js", function() {
  return gulp
    .src( paths.src.js )
    .pipe(uglify())
    .pipe(rename({
          extname: '.min.js'
    }))
    .pipe(gulp.dest(paths.dest.js));
});

// htmlをdistにコピー
//gulp.task('html', function() {
//  return gulp
//  .src( paths.src.html )
//  .pipe( gulp.dest(paths.dest.html))
//})


// scssのコンパイル
gulp.task('sass', function() {
return gulp
.src( paths.src.sass )
.pipe( plumber({ errorHandler: notify.onError("Error: <%= error.message %>") }) )//エラーチェック
.pipe( sassGlob() )//importの読み込みを簡潔にする
.pipe( sass({
  outputStyle: 'expanded' //expanded, nested, campact, compressedから選択
}) )
.pipe( postcss([ autoprefixer(
{
// ☆IEは11以上、Androidは4.4以上
// その他は最新2バージョンで必要なベンダープレフィックスを付与する
"overridebrowserslist": ["last 2 versions", "ie >= 11", "Android >= 4"],
cascade: false}
) ]) )
.pipe( postcss([ cssdeclsort({ order: 'alphabetically' }) ]) )//プロパティをソートし直す(アルファベット順)
.pipe(gulp.dest(paths.dest.css));//コンパイル後の出力先
});

// 保存時のリロード
gulp.task( 'browser-sync', function(done) {
browserSync.init({

//ローカル開発
server: {
baseDir: "dist/",
index: "index.html",
head: "head.html",
}
});
done();
});

gulp.task( 'bs-reload', function(done) {
browserSync.reload();
done();
});

//gulp.task("ejs", (done) => {
//gulp
//.src(["ejs/**/*.ejs", "!" + "ejs/**/_*.ejs"])
//.pipe( plumber({ errorHandler: notify.onError("Error: <%= error.message %>") }) )//エラーチェック
//.pipe(rename({extname: ".html"})) //拡張子をhtmlに
//.pipe(gulp.dest("./")); //出力先
//done();
//});

//圧縮率の定義
var imageminOption = [
pngquant({ quality: [.7, .85], }),
mozjpeg({ quality: 85 }),
imagemin.gifsicle({
  interlaced: false,
  optimizationLevel: 1,
  colors: 256
}),
imagemin.jpegtran(),
imagemin.optipng(),
imagemin.svgo()
];
// 画像の圧縮
// $ gulp imageminで./src/img/base/フォルダ内の画像を圧縮し./src/img/フォルダへ
// .gifが入っているとエラーが出る
gulp.task('images', function () {
return gulp
.src('./src/img/base/*.{png,jpg,gif,svg}')
.pipe(imagemin(imageminOption))
.pipe(gulp.dest(paths.dest.img));
});

// 監視
gulp.task( 'watch', function(done) {
//gulp.watch( './src/html/*.html', gulp.task('html') );//htmlが更新されたらgulp htmlを実行
//gulp.watch( './src/html/*.html', gulp.task('bs-reload') );//htmlが更新されたらbs-relaodを実行
gulp.watch( './src/pug/*.pug', gulp.task('pug'));//pugが更新されたらgulp pugを実行
gulp.watch( './src/pug/*.pug', gulp.task('bs-reload'));//pugが更新されたらbs-relaodを実行
gulp.watch( './src/sass/**/*.sass', gulp.task('sass') ); //sassが更新されたらgulp sassを実行
gulp.watch( './src/sass/**/*.sass', gulp.task('bs-reload')); //sassが更新されたらbs-reloadを実行
gulp.watch( './src/sass/**/*.scss', gulp.task('sass') );
gulp.watch( './src/sass/**/*.scss', gulp.task('bs-reload'));
gulp.watch( './src/js/*.js', gulp.task('js') ); //jsが更新されたらgulp jsを実行
gulp.watch( './src/js/*.js', gulp.task('bs-reload') ); //jsが更新されたらbs-relaodを実行
//gulp.watch('./ejs/**/*.ejs',gulp.task('ejs') ) ; //ejsが更新されたらgulp-ejsを実行
//gulp.watch('./ejs/**/*.ejs',gulp.task('bs-reload') ) ; //ejsが更新されたらbs-reloadを実行
});

// default
gulp.task('default', gulp.series(gulp.parallel('browser-sync', 'watch')));

// build
gulp.task( 'build', gulp.series(gulp.parallel('pug','sass','js','images')));
```

### 断層
- app
    - dist
      - css
        - main
        - reset.css
        - style.css
      - img
      - js
      - index.html
    - node_modules
    - src
      - img
        - base
      - js
      - pug
        - index.pug
      - sass
        - layout
        - main
        - reset.sass
        - style.sass
    - .gitignore
    - package-lock.json
    - package.json
    - README.md

