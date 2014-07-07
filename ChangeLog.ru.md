История изменений
=================

0.8.0 (stable)
--------------
- Обновили версию borschik до [1.0.1](https://github.com/bem/borschik/blob/master/CHANGELOG.ru.md#101).
- Обновили npm-зависимости.
- Добавили технологию scss (`v2/sass`).
- Добавили технологию bemjson.js (`v2/bemjson.js`).

0.7.9 (stable)
--------------
- Добавили технологию stylus (`v2/styl`).
- Возможность устанавливать опции `--no-colors` и `--verbosity`
через переменные окружения `BEM_MAKE_NO_COLORS` и `BEM_MAKE_VERBOSITY` соответственно.

0.7.8 (stable)
--------------
— bem create: Добавили возможность создавать сущности с переданным содержанием.
- npm: Обновили COA до 0.4.0, cli-table до 0.3.0.

0.7.7 (stable)
--------------
- Добавили технологии roole и less.

0.7.6 (stable)
--------------
- Правильно обрабатывается reject без указании причины в promise в модулях технологий
- Добавлена проверка, чтобы у технологий бандлов не было общих суффиксов
- Кэшированные данные сохраняются только в случае успешной сборки

0.7.5 (stable)
--------------
- npm: borschik обновлен до 0.4.27.

0.7.4 (stable)
--------------
- Исправлена ошибка, связанная с переходом с underscore на lodash.
- Откатили: передача результата Tech#getTechPath() в качестве аргумента forceTech bem-create. Это изменение ломало технологию уровеня level-proto.
- Тесты: технология level-proto включена в bem make suite

0.7.3 (stable)
--------------
- Fix "bem create" as worcker invocation
- Результат Tech#getTechPath() передается в качестве аргумента forceTech bem-create

0.7.2 (stable)
--------------
- bem server: исправили проблему с кодировкой файлов, содержащих нелатинские символы

0.7.1 (stable)
--------------
- Исправили исключение в  `bem build`

0.7.0 (stable)
--------------
- Сканнер уровней больше не падает на символьных ссылках
- Технология CSS правильно генерирует классы для модификаторов без значений ([#425](http://github.com/bem/bem-tools/issues/425))
- Показывается предупреждение, когда уровень не существует или не содержит директорию .bem. ([#418](http://github.com/bem/bem-tools/issues/418))
- Возможность указывать несколько элементов в свойствах элемента в файлах `deps.js` ([#401](http://github.com/bem/bem-tools/issues/401)):

  ```javascript
  ({
    shouldDeps: { block: 'bla', elem: ['e1', 'e2', 'e3'] }
  })
  ```

  Равнозначно:

  ```javascript
  ({
    shouldDeps: [
        { block: 'bla', elem: 'e1' },
        { block: 'bla', elem: 'e2' },
        { block: 'bla', elem: 'e3' }
  })
  ```
- Краткая форма для указывания зависимостей по технологиям одного и того же блока ([#413](http://github.com/bem/bem-tools/issues/413)):

  ```javascript
  { block: 'b',  tech: 'js', mustDeps: { tech: 'bemhtml' }  }
  ```

  равнозначно:

  ```javascript
  { block: 'b',  tech: 'js', mustDeps: { block: 'b', tech: 'bemhtml' }  }
  ```

- команду для сборки `bem bench` можно изменить в скрипте `bem-bench-build` в файле `package.json` проекта
- GitLibraryNode указывает git dir напрямую командами git ([#355](http://github.com/bem/bem-tools/issues/355))
- Технология base выбирается в соответствии с `API_VER` дочернего элемента. Если у базовых и дочерних технологий разные `API_VER`, выбрасывается ошибка ([#416](http://github.com/bem/bem-tools/issues/416))
- Добавлена возможность писать технологию module как функцию ([#363](http://github.com/bem/bem-tools/issues/363)):

  ```javascript
  module.exports = function(BEM) {
      return {
          //tech mixin
      };
  }
  ```

- Добавлена возможность писать конфиги для уровня как функцию ([#364](http://github.com/bem/bem-tools/issues/364)):

  ```javascript
  module.exports = function(BEM) {
      return {
          //level mixin
      };
  }
  ```

- свойство `baseLevelName`  можно использовать в конфиге уровня, чтобы указать уровень `simple` или уровень
  `project` по имени  ([#367](http://github.com/bem/bem-tools/issues/367))
- сканнер уровня simple не игнорирует директории с именами типа name.tech
- deps: возможность объявить зависимость без прямого включения сущности ([#459](http://github.com/bem/bem-tools/issues/459)):

  ```javascript
  {
      block: "some-block",
      mustDeps: [
        {block: "other-block", include: false}
      ]
  }

  ```

  В данном случае  `other-block` не будет автоматически включен в пакет `some-block`. Но если пакету требуется и `some-block`, и `other-block`, `other-block` всегда будет включен перед `some-block`.
- опция `--no-colors` позволяет отключить цвета в терминале
- в предупреждение технологии `v1` добавлена ссылка на инструкции по миграции
- библиотеки `q-fs` и `q-http` заменены на `q-io`
- библиотека `underscore` заменена на `lodash` ([#94](http://github.com/bem/bem-tools/issues/94))
- можно собирать бенчмарки на нескольких уровнях переопределения


0.6.16 (stable)
---------------

- Обновили csso в зависимостях borschik до версии 1.3.8
- deps.js: Исправлена проверка валидности кэша уровней
- Предупреждение при использовании модуля технологии v1, а не при его создании
- GitLibraryNode: добавили параметр origin для кастомизации удаленного имени
- Обновили зависимость borschik до 0.3.5
- Независимое от версии решение для CP#fork (Node.js 0.6+)
- Добавили имя технологии и путь к предупреждению о депрекации V1 
- Исправили запуск  `bem create level`без прототипа (--level opt)
- LibraryNode: создаются ведущие директории перед checkout
- bemdecl.js: пробегает по всем полям, а не только  `mix` и `content`

0.6.15 (stable)
---------------

- API: в `getBuildResultChunk()` должен был передаваться суффикс источника, а не цели, что и было исправлено. Рекомендуем проверить технологии modules на возможность поломки.

0.6.14 (stable)
---------------

- bem: Исправлен баг в `bem create level`, который не позволял использовать прототип уровня из модуля, установленного в папке `node_modules` на уровне project 
- bem: Выбрасывать ошибку, когда нет возможности выполнить технологию с помощью имени, указанного в свойстве `baseTechName` в модуле технологии

0.6.13 (stable)
---------------

- tech/v2: `transformBuildDecl()` переписан и используется в `buildByDecl()`
- level scanner: используются корректные суффиксы для папок, представляющих блоки с mod и val
- level scanner: не игнорируются папки типа `block/elem/elem.tech` и `block/mod/mod.tech` 
- deps.js v2: валидация не проходит, если измененная дата declaration позже, чем  deps.js

0.6.12 (stable)
---------------

- bem: Добавлена технология `level-proto`, которая создает уровни на основе прототипов в `.bem/levels/*.js` на уровне project

  Пример использования (`.bem/level.js`):

  ```js
  exports.getTechs = function() {
      return {
          'docs':   'level-proto', // will create levels <name>.blocks/ with proto in .bem/levels/docs.js
          'blocks': 'level-proto'  // will create levels <name>.blocks/ with proto in .bem/levels/blocks.js
      };
  };
  ```

- bem: Исправлен баг в `bem create level`, который не позволял создавать уровень без прототипа
- bem make: Исправлен баг в `BemCreateNode`, который вызывал ошибку во время использовании одной технологии на разных именах (например, `level-proto`)
- bem make: `require()` в конфигах `.bem/make.js` теперь ведет себя более корректно (попробуйте указать любую зависимость  проекта из `.bem/make.js`)
- bem make: свойство `level` в `BlockNode` сейчас инициализируется при первом доступе, что помогает спавиться с созданием уровней во время сборки `bem make`
- API: Из модуля `bem` экспортируются `logger` и `template` 
- API: Добавлен статический метод `Node.create()` для упрощения создания нод, см. пример

  ```js
  var opts = {
          // node options
      },
      node = registry
          .getNodeClass('BemCreateNode')
          .create(opts);
  ```

0.6.11 (stable)
---------------

- tech v2: Исправлено кэширование. Две технологии с одним целевым именем не переписывают кэш метаданных друг друга
- bem make: Прекращено использование команд {block,mod,val} в процессе make

0.6.10 (stable)
---------------

- API: Рекомендуется использовать API технологии V2  вместо V1
- API: Больше не используется API `LegacyTech` 
- API: Больше не используются команды `bem create block`, `bem create elem` и `bem create mod`, используйте команду `bem create` с опциями

Чтобы отключить предупреждения о депрекации вышеуказанных команд, выставьте значние `false` для `util.deprecate.silence`.
или выставьте значение `1` переменной окружения `BEM_NO_DEPRECATION`.

0.6.9 (stable)
--------------

- bem bench: Добавлена возможность тестирования шаблонов [bh](https://github.com/enb-make/bh) и сравнивать их с bemhtml

  You should run `bem bench -t bh [...other opts...]` to launch `bh` tests only or just `bem bench`
  to run both if they exist.

  См. подробности в документации

0.6.8 (stable)
--------------

- deps.js: Корректные уникальные элементы в `forEach` в случае зависимостей от технологий

0.6.7 (stable)
--------------

- level: Добавлена поддержка `opts.noCache` в `level.createLevel()`для создания новых уровней без задействования кэша 
- API: Возможность указывать исходные технологии для `BundlesLevelNode` (через `getBundleSourceTechs()`)
- code: Исправлены предупреждения от jshint

0.6.6 (stable)
--------------

- package: Перешли с более поздней версии q 0.9.6  на более раннюю 0.9.5, так 0.9.6 некорректно работала на node 0.10
- level: Показывать предупреждение, когда не удается загрузить технологию во время сканирования уровней
- level: Исправлен сканнер уровней для поиска block.tech dir внутри mods
- API: Исправлен `util.isFileP()` и помечен как более неиспользуемый

0.6.5 (stable)
--------------

- API: Добавлен хелпер `util.bemParseKey()`, чтобы парсить ключ сущности BEM key в объект сущности BEM.
  (исправляет ошибку выполнения `bem bench`)

0.6.4 (stable)
--------------

- fixed bugs in new level scanner (see BEM-467)

0.6.3 (unstable)
----------------

- bem bench: Run `npm install` before `bem make` after revision export

0.6.2 (unstable)
----------------

- bem bench: Disable verbose mode for `rsync` to stop output buffer overflow
- bem bench: Disable double error output on `rsync`

0.6.1 (unstable)
----------------

- bem: Add `bem bench` command see [docs](https://github.com/bem/bem-tools/blob/master/docs/bem-bench/bem-bench.ru.md)
  (in russian) for more info

- bem: Add ability to create level prototypes (js files) using `bem create level` command. See example:

  ```
  bem create level -l simple .bem/levels/docs.js
  ```

- bem: Add `project` tech and `project` level prototype:

  This command will create `my` project:

  ```
  bem create -b my -T project
  ```

  ```
  my/
  ├── .bem/
  |   ├── levels/
  |   |   ├── blocks.js
  |   |   ├── bundles.js
  |   |   ├── docs.js
  |   |   ├── examples.js
  |   |   └── tech-docs.js
  |   ├── techs/
  |   └── level.js
  └── node_modules/
      ├── .bin/
      |   └── bem -> symplink/to/globally/installed/bem (executable)
      └── bem/ -> symplink/to/globally/installed/bem (module)
  ```

- bem: Add `docs` tech and `docs` level prototype.

  This command will create new level based on `docs`:

  ```
  bem create level -l docs docs
  ```

  ```
  docs/
  └── .bem/
      └── level.js
    ```

  This command will create `docs` tech for block `button`:

  ```
  bem create -b button -T docs
  ```

  ```
  button/
  ├── button.docs/
  |   └── .bem/
  |       └── level.js
  └── ...
  ```

- bem: Add `tech-docs` tech and `tech-docs` level prototype.

- API: Introduce `util.findLevel(path, [types])` function

0.6.0 (unstable)
----------------

- new techs API is implemented (see lib/tech/v2.js). It operates with real file paths instead of prefixes.
This makes build avoid redundant operations and makes it work faster.
- as the part of new API new level introspection is implemented. In default implementation it just scans dirs/files
and checks their validity to being BEM entity using simple string operations (see scan* methods in lib/level.js).

0.5.33 (stable)
---------------

- package: q updated to 0.8.12
- package: borschik updated to 0.3.1
- package: xjst updated to 0.4.13
- package: ometajs updated to 3.2.4
- package: preferglobal set to false

0.5.32 (stable)
---------------

- bem: Fix `bem create level` on Node 0.10.x (Closes #372)
- bem make: Create parent directory for `SymlinkLibraryNode` if it doesn't exists (Closes #342)

0.5.31 (stable)
---------------

- bem: Add additional techs and levels from abandoned introspect branch
- API: Add mkdrip wrapper to util.js
- bem: ie.css tech should pass absolute path for its chunks
- bem make: Fix for "Coud not call for method of undefined" when using nodes from API

0.5.30 (stable)
---------------

- bem make: Add ability to customize build rules more flexibly by providing Arch.createCustomNode() method
- bem make: Add match*() methods to `simple` level prototype, add tests (Closes #282)

0.5.29 (stable)
---------------

- bem make: don't update git library form upstream when working copy state satisfies to configured one. git update commands chain altered (no git reset for now) (Closes #335)

0.5.27 (stable)
---------------

- bem make: fixed to work on node 0.10 (Closes #357)
- bem make: some performance boost achieved (#250)

0.5.26 (stable)
---------------

- bem make: Magic nodes doesn't link the nodes it creates with parent magic nodes (Closes #306)
- deps.js: don't swallow parsing errors (Closes #353)

0.5.25 (stable)
---------------

- bem server: windows fixes

0.5.24 (stable)
---------------

- bem server: Add error handling for server.listen() (Closes #315)
- bem server: Fix server message about serving address to have real host name it is listening on (Closes #334)
- bem server: Add socket-only option to make bem server listen only unix socket (Closes #316)
- bem server: Add a check for specified tcp port value to be a number
- bem make: Fix recursion error when build target name contain trailing slash (Closes #252)
- bem make: Use tech.getSuffixes() in MetaNode to build dependencies list (Closes #320)
- bem make: Git library checkout fixed to work with commit hashes (close #302)
- bem make: Git library branch parameter is added to specify branch name. Use treeish parameter to specify commit or tag.
- ie6.css tech: Don't include bundle.css

0.5.21 (stable)
---------------

- Update `borschik` to `0.2.3`

0.5.20 (stable)
---------------

- bem make: Fixed `npmPackages` check in `LibraryNode` (Closes #300)
- bem make: Install production dependencies in `LibraryNode` by default (Closes #310)
- Update `csso` to `1.3.5`
- Update `q` to `0.8.10`

0.5.19 (stable)
---------------

- Freeze dependencies using `npm shrinkwrap` to fix problems with `q 0.8.10` release

0.5.18 (stable)
---------------

- Dummy release

0.5.17 (stable)
---------------

- bem: Make content read of deps.js files of block to be synchronous to gain some speed boost (PR #261)
- bem make: Provide a more convenient way to configure the list of bundles and blocks levels to build (Closes #260)
- bem make: Change signature of `getLevels()` method of `BundleNode` to `getLevels(tech)` to add ability
  to configure the list of levels more precisely
- docs: Small JSDoc improvements in `BundleNode` class
- docs: Correct links in README (@banzalik)

0.5.16 (stable)
---------------

- bem: Require errors in .bem/level.js were masked (Closes #223)
- bem: Add `.git` to ignorable paths during introspection
- bem: Skip `blocks/` level directory during introspection in `nested` level
- bem: Introduce `bem decl intersect` command (Closes #219)
- bem make: Install library dependencies after checkout (Closes #224)
- bem make: Do not install dependencies when `npmPackages = false` (Closes #229)
- bem make: Ability to configure list of techs to optimize, see `BundleNode.getOptimizerTechs()` (Closes #231)
- bem make: `Rename bemhtml.js` tech to `bemhtml`, fix this in your `.bem/make.js` files
- bem make: Use non interactive mode for `svn` commands in `SvnLibraryNode` (Closes #221)
- bem make: Store `*.meta.js` files in `<project-root>/.bem/cache/` directory (Closes #232)
- bem make: Fixed bug in the inspector preventing it to work properly in FF (Closes #240)
- docs: Translate into english chapter about level.js (Closes #38)
- docs: Updated english docs in installation topic (@fliptheweb, #225)
- docs: Add `CONTRIBUTING.md`
- docs: Add `LICENSE` (we use MIT)
- API: Expose `__filename` and `__dirname` vars in `.bem/make.js` files
- API: Add `util.exec()` promised function to execute commands
- API: Remove `relative()` function from `lib/path.js` in favor of that in node 0.6+ (Closes #226)
- API: Refactor introspection logic (Pull #237)
  - Add `createIntrospector()` method to `Level` class to create custom introspectors (see jsdoc)
  - Refactor `getDeclByIntrospection()` to use `createIntrospector()`
  - Add `getItemsByIntrospection()` method to `Level` class, that returns array of BEM entities in techs
- API: Refactor `LevelNode` (Pull #238)
  - Lazy level object creation
  - Use `getItemsByIntrospection()` to collect BEM items to build
  - Unify actualization of blocks and elems in `BundleLevelNode`
- tests: Cover introspection logic
- tests: Cover `deps.intersect()` and `deps.subtract()`
- tests: Cover building of bundles-as-elements
- package: Support node 0.8.x (Closes #220)

0.5.15 (stable)
---------------

- bem: Add `;` after each include in js-based techs (`js` and `js-i`) (Closes #210)
- bem make: Bugfix: Use `Q.when()` to call base `alterArch()` method in `BundlesLevelNode` (Closes #216)
- docs: Add russian and english docs for `bem make` / `bem server` feature
- docs: Add more info on `--chdir`, `-C` option on `bem create *` commands (See #204)
- docs: Add `BEM.create()` docs: russian and english (Closes #192)
- docs: Document API changes in `BEM.build()` (Closes #193)
- docs: Document extensions in tech modules API (Closes #194)
- docs: Add russian docs for `.bem/level.js` config (See #38)
- API: Implement `include()` in `.bem/make.js` files (Closes #209)
- package: Depends on `csso ~1.2.17` (some critical bug fixes)

0.5.14 (unstable)
-----------------

- bem: Get rid of `Q` deprecation warnings (Closes #200)
- bem make: Node of type `MergedBundle` depends on all nodes of type `BundleNode` on the same level (Closes #206)
- package: Depend on `q ~0.8.8` and `apw ~0.3.6`

0.5.13 (unstable)
-----------------

- bem make: Create directory `.bem/snapshots` if it doesn't exist before writting a snapshot (Closes #201)
- bem make: Implement `clean()` method of `BemCreateNode`
- bem make: `getLevels()` method of `BundleNode` fixed to avoid putting undefined level into the resulting
  array (Closes #203)
- API: Add `getLevelPath()` helper method to `BlockNode` and `LevelNode` classes (Closes #190)

0.5.12 (unstable)
-----------------

- bem make: Forward errors from `borschik` with prefix `borschik: ` in `BorschikNode`
- bem make: Store output file name in `this.output` property to use later in the logs in `BorschikNode`
- package: Depends on `borschik ~0.0.11`

0.5.11 (unstable)
-----------------

- bem: Implement various strategies for mass IO operations in `Tech.filterPrefixes()` and `BemBuildNode.isValid()` (Closes #167)
- bem: Fix referencing techs by name
- bem: Allow use of `module.exports = ...` in files read by `util.readDecl()`
- bem: `util.getBemTechPath()` returns full tech path now, with extension
- bem: Add `-T` option as an alias for `-t`, `--tech` for `bem build` command
- bem: Add `--output-level` and `--block`, `--elem`, `--mod`, `--val` options for `bem build` command to build BEM
  entities on bundle levels
- bem: Allow using `require()` in decl-like files (Closes #172)
- bem: Add inspector server feature to `bem make` and `bem server` commands
- bem: Do not create new class from `LegacyTech` and legacy tech module content mixin in `getTechClass()` (potential bug fix)
- bem: Bugfix: `bem decl subtract` creates empty `*.deps.js` file (Closes #170)
- deps.js tech: Fix serializing of empty deps
- deps.js tech: Fix twice expansion of deps (Closes #163)
- bem make: Allow build triggering using final file names in case when tech produces many files (Closes #172)
- bem make: When `BEM_IO_STRATEGY === 'callback'` and `meta` was empty promise would never resolve
- bem make: Add merged bundle support
- bem server: Listen on file socket on `--socket` option, configure socket path using `--socket-path` option
  and socket permissions using `--socket-mode` option (Closes #166)
- docs: Document API changes in `BEM.create.block()`, `BEM.create.elem()` and `BEM.create.mod()` of version 0.5.x (Closes #161)
- docs: Declare dependency on NodeJS 0.6+
- API: Add third `level` optional argument to `getTechClass()` function of `tech` method
- API: Add third `level` optional argument to `createTech()` function of `tech` method
- API: Add `getCreateSuffixes()` and `getBuildSuffixes()` to `Tech` class to let build system to deal with techs like
  `bemhtml` more correct
- API: Add `util.removePath(path)` function to remove file and dir paths, but not recursively
- API: Add `util.readJsonJs(path)` function to read and eval JSON-JS files
- API: Add `util.symbolicLink(link, target, force)` function
- API: Add `util.lpad()` alias to `util.pad()`, add `util.rsplit(string, sep, maxsplit)` function
- API: Add `getContext()` method to `LegacyTech` class as a proxy to `this.techObj.getContext()`
- API: Add `getBuildResultChunk()` method to `LegacyTech` class as a proxy to `this.techObj.outFile()`
- API: Wait for `opts.declaration` to load before call to `this.techObj.build()` in `LegacyTech` class
- tests: Add tests for serializing empty deps in `deps.js tech`
- tests: Use `bem-bl` as git submodule for tests data (Closes #176)
- tests: Add tests that additionally build `i18n` and `i18n.js` techs for bundles
- tests: Add tests for merged bundle build
- tests: Add tests for `getTechClass()` function of `tech` module
- package: Add `dom-js` dependency for i18n tests (Closes #172)
- package: Add `clean` target to `GNUmakefile`
- package: Depend on `coverjs >= 0.0.7-aplha` (Closes #191)

0.5.10 (unstable)
-----------------

- bem: Use synchronous file existence check in `filterPrefixes()` instance method in `Tech` class
- bem: Fix bug with `--chdir` option for `bem create level` command (Closes #151)
- deps.js tech: More precisely report problems in blocks `*.deps.js` files
- deps.js tech: Read every block `*.deps.js` file only once
- bem make: Checks for target dir to exist before executing `svn info` in `SvnLibraryNode` (Closes #154)
- bem make: Output collected logs in case of fail in `Node` (Closes #155)
- bem make: Fix exception during build of `*.meta.js` files in `BemBuildMetaNode` (Closes #153)
- bem make: Sync mtime checks in `isValid()` instance method of `BemBuildNode` class (Closes #157)
- API: Add `util.readDecl()` promised function
- tests: Add legacy `Makefile` "tests" for `bem decl merge` command
- package: Depend on `coa ~0.3.5`
- package: Depend on `apw ~0.3.4`

0.5.9 (unstable)
----------------

- bem make: Build minimized versions of `*.bemhtml.js` files
- bem make: Check for svn revision in `SvnLibraryNode.isValid()`

0.5.8 (unstable)
----------------

- bem make: `SvnLibraryNode` extends `ScmLibraryNode`

0.5.7 (unstable)
----------------

- More fixes on running of `bem make` and `bem server` not in project root
- bem: Output full stack traces on error
- bem: Lazy tech paths resolving in `Level` class
- bem: `bem create *` commands display error when there are no techs specified in command line options
  and `defaultTechs` in level config is empty
- bem: Add convenient `bem create` command to create all type of BEM entities
- bem server: Convert russian lang messages to english
- bem server: Fix wrong links in directory listings
- bem server: Strip query string part before accessing a file
- bem make: Do not checkout `bem-bl` by default
- bem make: Fix `LibraryNode`
- bem make: Extend context of `.bem/make.js` using `global`
- bem make: Conditional build of bundle files based on existance of `*.bemjson.js` and `*.bemdecl.js` on the file system
- bem make: Resolve tech module paths using level object in `BundleNode`
- bem make: Use `Level.createTech()` instead of `Level.getTech()` to construct tech objects for `BemBuildNode`
- bem make: Depend nodes of `BemBuildNode` class only on existing blocks files to increase performance
- bem make: Run nodes of `BemBuildNode` class forked by default to increase performance
- bem make: Add more logging to `BundleNode`
- bem make: Add support for `csso` processing of `*.css` files for production builds in `BorschikNode`
- bem make: Add support for `uglifyjs` processing of `*.js` files for production builds in `BorschikNode`
- bem make: Rename `repo` param to `url` in `ScmLibraryNode` and its derivatives
- bem make: Fix cleaning of obsolete dependencies in `BemBuildNode`
- bem make: Huge internal refactoring on `BundleNode`
- bem make: Rename `getCreateDependencies()` instance method to `getDependencies()` in `BemBuildNode` class
- bem make: Rename `getCreateDependencies()` instance method to `getDependencies()` in `BemCreateNode` class
- bem make: Add `setFileNode()` and  `setBemCreateNode()` instance methods to `BundleNode` class
- logging: Log node versions on `debug` verbosity
- logging: Log profiling info of `bem make`
- logging: Add more `debug` verbosity logging to `BundleNode`
- docs: Add jsdoc for `Level` class
- docs: Update jsdoc for `Tech` class
- docs: Add docs for `bem create elem` and `bem create mod`
- docs: Add docs for `bem create`
- docs: Fix jsdoc for `setBemBuildNode()` instance method of `BundleNode` class
- docs: Add jsdoc for `Node`, `FileNode`, `MagicNode`, `ScmLibraryNode`
- API: Export `util` module as `require('bem').util`
- API: Add `matchAny()` instance method to `Level` class
- API: Add instance methods-shortcuts to `Level` class: `getPath()`, `getPathByObj()`, `getRelPathByObj()`
- tests: Add tests for bem make
- tests: Rewrite all tests to `mocha`
- package: Add `xjst 0.2.21` to dependency list
- package: Add `ometajs ~2.1.10` to dependency list
- package: Bump `q` dependency version to `~0.8.5`
- package: Bump `apw` dependency version to `~0.3.2`
- package: Bump `borschik` dependency version to `~0.0.10`

0.5.6 (unstable)
----------------

- docs: Draft of russian docs for `bem make` / `bem server`
- API: Add `resolvePaths(paths)` and `resolvePath(path)` methods to `Level` class
- bem make: Add more logging to `BorschikNode`
- bem make: Use `js-i` tech in `BundleNode` to build bundles `*.js` files by default
- package: Bump `borschik` dependency to `~0.0.9`

0.5.5 (unstable)
----------------

- Require node 0.6.x
- deps.js tech: Fix bug with building of `deps.js` files introduced in 0.5.2
- Fix running of `bem make` and `bem server` not in project root
- logging: Add `flog()` shorthand function to output formatted log as a replacement for `console.log`
- logging: Log version number of `bem-tools` on `bem make` and `bem server`
- bem server: Show http link on server start
- bem server: Fix current directory output in directory listing
- bem make: Tune verbosity level for build messages
- bem make: Log targets to build on build start
- bem make: Fix validity checks in `LibraryNode` and `BemBuildNode`
- bem make: Move validity cheks from `FileNode` to `GeneratedFileNode`
- bem make: Fix `clean()` of `BemBuildMetaNode`
- bem make: Store relative paths in `*.meta.js` files
- API: Add `require('bem').version`
- API: Add `require('bem/lib/util').writeFileIfDiffers(path, content, force)`

0.5.4 (unstable)
----------------

- package: Bump `apw` dependency version to `~0.3.0`

0.5.3 (unstable)
----------------

- deps.js tech: Support `deps.js` format as a declaration for `bem build`

0.5.2 (unstable)
----------------

- Add `--verbosity` option to `bem make` and `bem server` commands
- bem make: Add a lot of colorfull logging
- bem make: A lot of internal refactorings
- bem make: Fix dependency bug with building `_*.ie.css` files
- bem make: Fix child process handling in `BorschikNode` and `BemBuildNode`
- API: Add winston as logging engine

0.5.1 (unstalbe)
----------------

- bem make: Quick fix removing testing code

0.5.0 (unstable)
----------------

- bem make / server feature introduction
