<p>
<a href="https://github.com/lime7/www/blob/master/gulpfile.pdf">
<h1 align="center">Моя Front-End сборка 2.0</h1>
</a> 
Сборка осуществляется <a href="http://gulpjs.com/">gulp</a>.

<br/>
<br/>
<strong> Gulp</strong> - <i>инструмент сборки веб-приложения, позволяющий автоматизировать повторяющиеся задачи, такие как сборка и минификация CSS- и JS-файлов, запуск тестов, перезагрузка браузера и т.д.</i>
</p>

<strong>Используемые мной возможности:</strong>

 - Создание исходных файлов
 - Компиляция jade и sass файлов
 - Вывод wiredep-ом стилей и скриптов из Bower
 - Build стилей и скриптов
 - Компиляция js и css
 - Минификация js и css
 - Сжатие изображений
 - Кэширование скриптов и стилей
 - Запуск сервера
 - Live перезагрузка и очистка
 - Работа с svg

-----------------------------------------------------------------------------
<h3>Инструменты:</h3>
<p>
- <a href="https://nodejs.org/en/">NODE.JS</a>.  
<i>Download for windows. </i>
<br/>
-  <a href="https://git-scm.com/">GIT</a>.
<i>Download for windows.  1. ... *2. Run for win. 3. ...</i>
<br/>
- <a href="http://rubyinstaller.org/">RubyInstaller</a>.  
<i>Download for windows. </i>
<br/>
- <a href="https://conemu.github.io/">ConeMu терминал</a>.  
</p>

-----------------------------------------------------------------------------
<h3>Технологии:</h3>

-  <a href="http://jsman.ru/jade/">JADE</a> - препроцессор HTML и шаблонизатор.

-  <a href="http://sass-scss.ru/">SASS</a> - CSS препроцессор.

-  <a href="https://www.npmjs.com/">npm</a> - пакетный менеджер node.js.

-  <a href="https://bower.io/">Bower</a> - пакетный менеджер для web.

<i>Менеджеры пакетов упрощают установку и обновление зависимостей проекта, то есть сторонних библиотек, которые он использует: jQuery, др.</i>

<i>Главное отличие npm и Bower — подход к установке зависимостей пакетов. </i>

<i> npm устанавливает зависимости для каждого пакета отдельно, в итоге получается большое дерево пакетов (node_modules/grunt/node_modules/glob/node_modules/…), где может быть несколько версий одного и того же пакета. </i>

<i>В Бовере каждый пакет устанавливается один раз (jQuery всегда будет в папке bower_components/jquery, сколько бы пакетов от него не зависело) и в случае конфликта зависимостей, Бовер просто не станет устанавливать пакет, не совместимый с уже установленными.</i>

-----------------------------------------------------------------------------

##СОЗДАНИЕ ИСХОДНИКОВ:


```
mkdir www
cd !$
mkdir app/{css,js} –p
cd app
touch index.jade js/{main.js,plugins.js}
cd ..
ls
```
<em> ```!$``` - переход во вновь созданную директорию.</em> </br>
<em>Ключ ```-p ``` - создание самой директории ```app```.</em></br>
<em>Переход в директорию -   ```cd app```.</em></br>
<em>Переход на уровень выше -   ```cd ..```.</em></br>
<em>Просмотр файлов -   ```ls```.</em></br>
<em>Просмотр скрытых файлов и с точкой -   ```ls -a```.</em></br>
<em>Полностью удалить директорию -   ```rm -r app```.</em></br>


----------


##ФАЙЛЫ ЗАВИСИМОСТЕЙ :

``` npm init ```       или   ``` touch package.json ``` 
</br>
``` bower init ```   или   ``` touch bower.json ```
</br>
``` touch .bowerrc .gitignore gulpfile.js ```
</br>
- **package.json** - *файл с глобальными настройками проекта, содержит различные метаданные о проекте: имя проекта, версия, описание.*
-  **bower.json** - *хранит зависимости, необходимые для конечного пользователя.*
- **.gitignore** - *cписок ф-ов игнорируемых в GIT*
- **.bowerrc** - *файл настройки [Bower](http://bower.io) с помощью JSON*
- **gulpfile.js** - *файл настроек для сборки проекта и выполнения задач с помощью [Gulp.js](http://gulpjs.com)*

<h3>Минимальное содержимое:</h3>

**package.json:**
```
{ }
```

**bower.json:**
```
{"name" : "test-pj"}
```

**.bowerrc:**
```
{"directory" : "app/bower"}
```

**.gitignore:**
```
node_modules
app/bower
dist
```


-----------------------------------------------------------------------------

**Начальная структура проекта:**

```
► www
┆┈ ► app
┆  ┆┈ ► scss
┆      ┆┈ ► _utilities
┆      ┆  ┆┈ ▷ _variables.scss
┆      ┆  ┆┈ ▷ _mixins.scss
┆      ┆  ┆┈ ▷ _media-queries.scss
┆      ┆  ┆┈ ▷ typography.scss
┆      ┆  ┆┈ ▷ ...
┆      ┆  ╵┈ ▷ _index.scss
┆      ┆
┆      ┆┈ ► base
┆      ┆  ╵┈ ▷ _base.scss
┆      ┆
┆      ┆┈ ► layout
┆      ┆  ┆┈ ▷ _header.scss
┆      ┆  ┆┈ ▷ _footer.scss
┆      ┆  ┆┈ ▷ ...
┆      ┆  ╵┈ ▷ _index.scss
┆      ┆
┆      ┆┈ ► modules
┆      ┆  ┆┈ ▷ _logo.scss
┆      ┆  ┆┈ ▷ _load.scss
┆      ┆  ┆┈ ▷ ...
┆      ┆  ╵┈ ▷ _index.scss
┆      ┆
┆      ┆┈ ► state
┆      ┆  ╵┈ ▷ _animate.scss
┆      ┆
┆      ╵┈ ▷ style.scss
┆       
┆  ┆┈ ► views
┆      ┆┈ ► partials
┆      ┆  ┆┈ ▷ _header.jade
┆      ┆  ┆┈ ▷ _footer.jade
┆      ╵┈ ▷ main.jade
┆
┆  ┆┈ ► js
┆      ┆┈ ▷ main.js
┆      ╵┈ ▷ vendor.js
┆        
┆  ┆┈ ► fonts
┆  ┆┈ ► images
┆  ┆
┆  ╵┈ ▷ index.jade
┆
┆┈ ▷ package.json
┆┈ ▷ bower.json
┆┈ ▷ .bowerrc
┆┈ ▷ .gitignore
╵┈ ▷ gulpfile.js

```

-----------------------------------------------------------------------------

###УСТАНОВКА ПЛАГИНОВ:

**Установка самого gulp:**
```
npm i –g gulp
npm i --save-dev gulp
```
**Локальный dev сервер:**
```
npm i –g browser-sync
npm i --save-dev browser-sync
```

**Наблюдение за изменениями файлов:**
```
npm i gulp-watch
```

**Очистка:**
```
npm i --save-dev gulp-clean
```

**Компиляция ф-ов:**
```
npm i --save-dev gulp-jade
npm i --save-dev gulp-sass
```

**Кэширование файлов:**
```
npm i --save-dev gulp-hash
```

**Замена строк:**
```
npm i gulp-replace-assets
```

**Парсинг\конкатенация js, css, html ф-ов:**
```
npm i --save-dev gulp-useref
npm i --save wiredep
npm i --save-dev gulp-rigger
```

**Удаление не используемых стилей:**
```
npm i --save-dev gulp-uncss
```

**Вендорные префиксы к CSS свойствам:**
```
npm i --save-dev gulp-autoprefixer
```

**Минификация:**
```
npm i --save-dev gulp-uglify
npm i --save-dev gulp-css-minify
npm i --save-dev gulp-imagemin
```

**Bower:**
```
npm i –g bower
npm update –g bower
bower i --save jquery
bower i --save jquery#1.11
bower i bootstrap
bower i --save slick-carousel
bower i --save slick.js
```
----------

**УДАЛЕНИЕ/ДЕИНСТАЛЯЦИЯ:**
```
rm –r node_modules
uninstall browser-sync
npm cache clean ~/
```
----------

<h2>INDEX.JADE</h2>

```
include template/_head
body
    // build:js js/vendor.js
    // bower:js
    // endbower
    // endbuild    
      
    // build:js js/main.js
    script(src='js/main.js')    
    // endbuild
    
```
----------


<h2>GULPFILE.JS</h2>

Используем строгий режим (чтобы не было ошибок):
```
'use strict';
```
Объявляем gulp модули:
``` 
var gulp          = require('gulp'),
	jade          = require('gulp-jade'),	
	sass          = require('gulp-sass'),
	autoprefixer  = require('gulp-autoprefixer'),
	minifyCss     = require('gulp-minify-css'),
	imagemin      = require('gulp-imagemin'),
	uglify        = require('gulp-uglify'),
	uncss         = require('gulp-uncss'),
	useref        = require('gulp-useref'),
	hash          = require('gulp-hash'),
	wiredep       = require('wiredep').stream,
	replaceAssets = require('gulp-replace-assets'),
	watch         = require('gulp-watch'),
	clean         = require('gulp-clean'),
	browserSync   = require('browser-sync'),
	reload        = browserSync.reload;  
```
Прописываем пути:
```
// Пути
var path = {
	app : {          // Исходники
		html   : 'dist/*.html',
		jade   : 'app/*.jade',
		js     : 'app/js/**/*.js',
		sass   : 'app/scss/style.scss',		
		images : 'app/images/**/*.*',
		fonts  : 'app/fonts/**/*.*',
		},
	dist : {         // Релиз
		html   : 'dist/',		
		js     : 'dist/js/',
		css    : 'dist/css/',
		images : 'dist/images/',
		fonts  : 'dist/fonts/'
	},
	watch : {        // Наблюдение
		jade   : 'app/**/*.jade',
		html   : 'dist/**/*.html',
		js     : 'app/js/**/*.js',
		sass   : 'app/scss/**/*.scss',		
		images : 'app/images/**/*.*',
		fonts  : 'app/fonts/**/*.*'
	},
	clean      : './dist' // Чистка
};
```

Настраиваем сервер browsersync:
```
// Настройка сервера
var config = {
	server : {
		'baseDir' : './dist'
	},
	host : 'localhost',
	port : 9000,
	tunel : true
};
```

Компилируем jade в html:
```
// Работа с JADE
gulp.task('jade', function() {	
    gulp.src(path.app.jade)
        .pipe(jade({
        	pretty: '\t',
        }))        
        .pipe(gulp.dest(path.dist.html))
        .pipe(reload({stream : true}));
});
```

Собираем в html все скрипты и стили:
```
// Работа с HTML
gulp.task('html', ['js'], function(){
	var assets = require('./tmp/assets.json');
	gulp.src(path.app.html)
		.pipe(wiredep())
		.pipe(replaceAssets(assets))
        .pipe(useref())	
		.pipe(gulp.dest(path.dist.html))
		.pipe(reload({stream : true}));
});
```

Сжимаем и кэшируем скрипты:
```
// Работа с JS
gulp.task('js', function(){
	return gulp.src(path.app.js)
		.pipe(uglify())
		.pipe(hash())
		.pipe(gulp.dest(path.dist.js))
		.pipe(hash.manifest('assets.json')) 
		.pipe(gulp.dest('tmp'))
		.pipe(reload({stream : true}));
});
```

Компилируем sass в css, сжимаем стили, удаляем не используемые стили gulp-uncss, добавляем автопрефиксы:
```
//Работа с SASS 
gulp.task('sass', function () {
	gulp.src(path.app.sass)
		.pipe(sass({
			includePaths: [
	        	'node_modules/normalize-scss/sass/',
	        	'app/bower/font-awesome-sass/assets/stylesheets/'
	        ],
		}).on('error', sass.logError))
		.pipe(autoprefixer({ browsers: ["> 0%"] }))	
		.pipe(uncss({
		    html: [ 'dist/*.html' ] // html files to check for styles to keep
		}))
		.pipe(minifyCss())
		.pipe(gulp.dest(path.dist.css))
		.pipe(reload({stream : true}));
});
```
Собираем и сжимаем изображения:
```
//Работа с IMAGES 
gulp.task('images', function(){
	gulp.src(path.app.images)
		.pipe(imagemin())
		.pipe(gulp.dest(path.dist.images))
		.pipe(reload({stream : true}));
});
```

Собираем шрифты:
```
//Работа с FONTS 
gulp.task('fonts', function(){
	return gulp.src(path.app.fonts)
		.pipe(gulp.dest(path.dist.fonts))
		.pipe(reload({stream : true}));
});
```
Изменения файлов:
```
// Наблюдение
gulp.task('watch', function () {	
	watch([path.watch.jade], function(event, cb){
		gulp.start('jade');
	});
	watch([path.watch.html], function(event, cb){
		gulp.start('html');
	});
	watch([path.watch.js], function(event, cb){
		gulp.start('js');
	});
	watch([path.watch.sass], function(event, cb){
		gulp.start('sass');
	});
	watch([path.watch.images], function(event, cb){
		gulp.start('images');
	});
	watch([path.watch.fonts], function(event, cb){
		gulp.start('fonts');
	});
});

```
Запуск таска веб сервера с настройками:
```
// Запуск вебсервера
gulp.task('webserver', function(){
	browserSync(config);
});
```

Очиста директории dist:
```
// Чистка
gulp.task('clean', function(cb){
	clean(path.clean, cb);
});
```

Запуск тасков:
```
// Задачи по-умолчанию
gulp.task('default', [	
	'jade',	
	'html',
	'js',
	'sass',
	'images',
	'fonts',
	'webserver',
	'watch'		
]);
```

И **запускаем** всю сборку в консоле одной командой - ```gulp``` .

----------

**Структура проекта:**


```
► www
┆┈ ► app
┆  ┆┈ ► bower
┆  ┆┈ ► ...
┆
┆┈ ► dist
┆  ┆┈ ► css  
┆  ┆  ┆┈ ▷ style.css
┆  ┆  ╵┈ ▷ vendor.css
┆  ┆┈ ► js
┆  ┆  ┆┈ ▷ main.js
┆  ┆  ╵┈ ▷ vendor.js
┆  ┆┈ ► fonts
┆  ┆┈ ► images
┆  ┆
┆  ╵┈ ▷ index.html
┆
┆┈ ► node_modules
┆
┆┈ ▷ package.json
┆┈ ▷ bower.json
┆┈ ▷ .bowerrc
┆┈ ▷ .gitignore
╵┈ ▷ gulpfile.js
```


----------
<h3>Список используемых плагинов:</h3>

- <a href="https://www.browsersync.io/docs/gulp">browser-sync</a>
- <a href="https://www.npmjs.com/package/gulp-watch">gulp-watch</a>
- <a href="https://www.npmjs.com/package/gulp-clean">gulp-clean</a>
-  <a href="https://www.npmjs.com/package/gulp-jade">gulp-jade</a>
-  <a href="https://www.npmjs.com/package/gulp-sass">gulp-sass</a>
- <a href="https://www.npmjs.com/package/gulp-useref">gulp-useref</a>
- <a href="https://www.npmjs.com/package/wiredep">wiredep</a>
- <a href="https://www.npmjs.com/package/gulp-uncss">gulp-uncss</a>
- <a href="https://www.npmjs.com/package/gulp-autoprefixer">gulp-autoprefixer</a>
- <a href="https://www.npmjs.com/package/gulp-minify-css">gulp-minify-css</a>
- <a href="https://www.npmjs.com/package/gulp-uglify">gulp-uglify</a>
- <a href="https://www.npmjs.com/package/gulp-imagemin">gulp-imagemin</a>
- <a href="https://www.npmjs.com/package/gulp-replace-assets">gulp-replace-assets</a>
- <a href="https://www.npmjs.com/package/gulp-hash">gulp-hash</a>
- <a href="https://www.npmjs.com/package/normalize-scss">normalize</a>

----------

<h3>Github:</h3>

```
cd www
git init
git add .
git commit -m "Add all"
git status
```
Создать репозиторий на github.com.
```
git remote https://github.com/NAME/www.git
git push origin master
```

**Дополнение:**

Для наглядного отображения страницы в браузере, а не ее исходного кода, создадим <a href="https://pages.github.com/">gh-pages</a>.
Для этого нужно создать новую ветку - gh-pages и перенести в нее контент для отображения.

```
git branch gh-pages
git checkout gh-pages
```
Перед следующим шагом, я предпочитаю очистить ветку gh-pages от всего содержимого (если таковое имеется).
 
``` git rm file_name ``` - удалить файл,  ```git rm -r dir_name ``` - удалить директорию, ```git rm -rf dir_name ``` - ключ  ```-f  ``` - все равно удалить.

 Далее смержим ветки master и gh-pages и добавим файлы. 
```
git merge master
git push origin gh-pages
```

*Посмотреть список всех коммитов в виде графика:*
```
git log --graph --all --decorate
```

*Вытянуть проект, просмотреть конфликты:*
```
git pull
```

*Закрыть документ*
```
wq!
```

-------------------


## Установка:
```
git clone https://github.com/lime7/www.git
npm i
bower i
gulp
```
-------------------------------------------------------------------------------------------------
<br/>

<a href="https://lime7.github.io/">Посмотреть результат сборки</a>.

-------------------------------------------------------------------------------------------------
<p align="center"> © <a href="http://semenchenkov.github.io/" style="font-weight:bold;">Семенченко</a> 2016</p>
