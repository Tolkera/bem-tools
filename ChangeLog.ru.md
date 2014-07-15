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
- Исправили запуск `bem create level`без прототипа (--level opt)
- LibraryNode: создаются ведущие директории перед checkout
- bemdecl.js: пробегает по всем полям, а не только  `mix` и `content`

0.6.15 (stable)
---------------

- API: в `getBuildResultChunk()` должен был передаваться суффикс источника, а не цели, что и было исправлено. Рекомендуем проверить технологии modules на возможность поломки.

0.6.14 (stable)
---------------

- bem: Исправлен баг в `bem create level`, который не позволял использовать прототип уровня из модуля, установленного в папке `node_modules` на уровне project 
- bem: Выбрасывается ошибка, когда нет возможности выполнить технологию с помощью имени, указанного в свойстве `baseTechName` в модуле технологии

0.6.13 (stable)
---------------

- tech/v2: `transformBuildDecl()` переписан и используется в `buildByDecl()`
- level scanner: используются корректные суффиксы для папок, представляющих блоки с mod и val
- level scanner: не игнорируются папки типа `block/elem/elem.tech` и `block/mod/mod.tech` 
- deps.js v2: валидация не проходит, если измененная дата declaration позже, чем deps.js

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

Чтобы отключить предупреждения о депрекации указанных выше команд, выставьте значение `false` для `util.deprecate.silence` или значение `1` для переменной окружения `BEM_NO_DEPRECATION`.

0.6.9 (stable)
--------------

- bem bench: Добавлена возможность тестировать шаблонов [bh](https://github.com/enb-make/bh) и сравнивать их с bemhtml

  Вам нужно запустить `bem bench -t bh [...other opts...]` для тестов `bh` или  `bem bench` для запуска обоих команд, если это возможно.

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

- исправлены баги в новом сканере уровней (см. BEM-467)

0.6.3 (unstable)
----------------

- bem bench: Запустите `npm install` перед `bem make` после экспорта ревизии

0.6.2 (unstable)
----------------

- bem bench: Отключить режим verbose для `rsync`, чтобы остановить переполнение буфера
- bem bench: Отключить вывод двойной ошибки на `rsync`

0.6.1 (unstable)
----------------

- bem: Добавлена команда `bem bench`, детали см. в  [docs](https://github.com/bem/bem-tools/blob/master/docs/bem-bench/bem-bench.ru.md)

- bem: Добавлены возможность создавать прототипы уровней (файлы js) с помощью `bem create level`. См. пример

  ```
  bem create level -l simple .bem/levels/docs.js
  ```

- bem: Добавлены технология `project` и  прототип уровня `project`:

  Эта команда создаст проект `my`:

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

- bem: Добавлена технология `docs` и прототип уровня `docs`.

  Эта команда создаст новый уровень на основе `docs`:

  ```
  bem create level -l docs docs
  ```

  ```
  docs/
  └── .bem/
      └── level.js
    ```

  Эта команда создаст технологию `docs` для блока `button`:

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

- bem: Добавлена технология `tech-docs` и прототип уровня `tech-docs`

- API: Появилась функция `util.findLevel(path, [types])`

0.6.0 (unstable)
----------------

- Реализована новая технология API (см. lib/tech/v2.js). Она работает с реальными путями файлов вместо префиксов. Это ускоряет сборку за счет избавления от лишних операций.
- В качестве части нового API была реализована интроспекция новых уровней. По умолчанию директории/файлы просто сканируются на предмет их валидности и соответствия сущности BEM с помощью простых строковых операций (смотри методы scan* в lib/level.js)

0.5.33 (stable)
---------------

- package: q обновлен до 0.8.12
- package: borschik обновлен до 0.3.1
- package: xjst обновлен до 0.4.13
- package: ometajs обновлен 3.2.4
- package: для preferglobal выставлено false

0.5.32 (stable)
---------------

- bem: Исправлен `bem create level` на Node 0.10.x (Closes #372)
- bem make: Создается родительская директория для `SymlinkLibraryNode`, если таковая не существует (закрыт #342)

0.5.31 (stable)
---------------

- bem: Добавлены дополнительные технологии и уровни from abandoned introspect branch
- API: В util.js добавлена обертка для mkdrip
- bem: Технология ie.css должна передавать абсолютные пути 
- bem make: Исправлено "Coud not call for method of undefined" во время использования нод из API

0.5.30 (stable)
---------------

- bem make: Добавлена возможность более гибкой кастомизации правил сборки за счет метода Arch.createCustomNode()
- bem make: Добавлены методы match*() для прототипа уровня `simple`, добавлены тесты (закрыт #282)

0.5.29 (stable)
---------------

- bem make: не обновляйте git library из upstream,  если текущая копия работает. Изменились команды git update (git reset сейчас нет) (Closes #335)

0.5.27 (stable)
---------------

- bem make: исправлено для работы на node 0.10 (закрыт #357)
- bem make: улучшен перформанс (#250)

0.5.26 (stable)
---------------

- bem make: Magic nodes doesn't link the nodes it creates with parent magic nodes (Closes #306)
- deps.js: показываются ошибки парсинга (Closes #353)

0.5.25 (stable)
---------------

- bem server: исправления windows 

0.5.24 (stable)
---------------

- bem server: Добавлен обработка ошибок для server.listen() (закрыт #315)
- bem server: Исправлено сообщение сервера о том, чтобы serving address имел реальное имя хоста, который он "слушает" (закрыт #334)
- bem server: Добавлена опция socket-only, чтобы bem server "слушал" только сокеты unix (закрыт #316)
- bem server: Добавлена проверка на то, чтобы указанное значение port tcp было числом.
- bem make: Исправлена ошибка рекурсии, которая возникала во время построения целевого имени, содержащего завершающий слэш (закрыт #252)
- bem make: Используйте tech.getSuffixes() в MetaNode для построения списка зависимостей (Closes #320)
- bem make: Git library checkout работает с хэшами (close #302)
- bem make: Добавлен параметр Git library branch для того, чтобы указывать имя ветки. Используйте параметр  Use treeish для указани коммита или тэга
- ie6.css tech: не включается bundle.css

0.5.21 (stable)
---------------

- `borschik` обновлен до `0.2.3`

0.5.20 (stable)
---------------

- bem make: Исправлена проверка `npmPackages` в `LibraryNode` (закрыт #300)
- bem make: Установлены дефолтные зависимости продакшна в `LibraryNode` (закрыт #310)
- Обновили `csso` до `1.3.5`
- Обновили `q` до `0.8.10`

0.5.19 (stable)
---------------

- Для исправления проблем с релизом `q 0.8.10` с помощью `npm shrinkwrap` заморожены зависимости  

0.5.18 (stable)
---------------

- Dummy release

0.5.17 (stable)
---------------

- bem: Сделать чтение файлов deps.js блока синхронным для улучшения скорости работы (PR #261)
- bem make: Более удобный способ конфигурации списка бандлов и уровней блоков для сборки (закрыт #260)
- bem make: Изменить подпись метода `getLevels()` в `BundleNode` на `getLevels(tech)` для того, чтобы добавить возможность более точно конфигурировать списки уровней
- docs: Небольшие улучшения JSDoc в классе `BundleNode`
- docs: Корректные ссылки in README (@banzalik)

0.5.16 (stable)
---------------

- bem: Скрыты ошибки require в .bem/level.js (закрыт #223)
- bem: Добавлен `.git` для игнорируемых путей во время интроспекции
- bem: Пропускается директория уровня `blocks/` во время интроспекции в уровне `nested`
- bem: Появилась команда `bem decl intersect` (закрыт #219)
- bem make: После checkout устанавливаются зависимости библиотек (закрыт #224)
- bem make: Не устанавливать зависимости, если `npmPackages = false` (закрыт #229)
- bem make: Возможность сконфигурировать список технологий для оптимизации, см. `BundleNode.getOptimizerTechs()` (закрыт #231)
- bem make: Технология `bemhtml.js` переименована в `bemhtml`, исправьте это в своих файлах `.bem/make.js`
- bem make: Используется неинтерактивный режим для команд `svn` в `SvnLibraryNode` (Closes #221)
- bem make: Файлы `*.meta.js` хранятся в директории `<project-root>/.bem/cache/` (закрыт #232)
- bem make: Исправлен баг в инспекторе, не позволявший корректную работу в FF (закрыт #240)
- docs: Глава о level.js переведена на английский язык (закрыт #38)
- docs: Обновлены англоязычные документы в теме установки (@fliptheweb, #225)
- docs: Добавлен `CONTRIBUTING.md`
- docs: Добавлен `LICENSE` (мы используем MIT)
- API: Expose `__filename` and `__dirname` vars in `.bem/make.js` files
- API: Добавлена функция-promise `util.exec()`для выполнения команд
- API: Убрана функция `relative()` из `lib/path.js` и используется эквивалент из node 0.6+ (Closes #226)
- API: Рефакторинг логики интроспекции (Pull #237)
  - К классу `Level` добавлен метод `createIntrospector()` для создания уникальных интроспекторов (see jsdoc)
  - Отрефакторен `getDeclByIntrospection()` для использования `createIntrospector()`
  - К классу `Level` добавлен метод `getItemsByIntrospection()`, который возвращает массив сущностей BEM в технологиях 
- API: Рефакторинг `LevelNode` (Pull #238)
  - Отложенное создание объектов уровней
  - Используется `getItemsByIntrospection()` для сборки BEM элементов
  - Унифицирована актуализация blocks и elems в `BundleLevelNode`
- tests: Покрыта логика интроспекции
- tests: Покрыты `deps.intersect()` и `deps.subtract()`
- tests: Покрыта сборка bundles-as-elements
- package: Поддержка node 0.8.x (Closes #220)

0.5.15 (stable)
---------------

- bem: Добавлены `;` после каждого include в js технологиях (`js` и `js-i`) (закрыт #210)
- bem make: Багфикс: используется `Q.when()` для вызова базового метода `alterArch()` в `BundlesLevelNode` (закрыт #216)
- docs: Добавлена русскоязычная и англоязычная документация для `bem make` / `bem server`
- docs: Добавлено больше информации об опции `--chdir`, `-C` в командах `bem create *` (см. #204)
- docs: Добавлена англоязычная и русскоязычная документация для `BEM.create()` (закрыт #192)
- docs: Задокументированы изменения API в `BEM.build()` (закрыт #193)
- docs: Задокументированы расширения в API модулей технологий (Closes #194)
- docs: Добавлена русскоязычная документация для конфига `.bem/level.js` (см. #38)
- API: Реализован `include()` в файлах `.bem/make.js` (закрыт #209)
- package: зависимость от `csso ~1.2.17` (некоторые критические багфиксы)

0.5.14 (unstable)
-----------------

- bem: Убраны предупреждения о депрекации `Q` (закрыт #200)
- bem make: Нода типа `MergedBundle` зависит от всех нод типа `BundleNode` на том же уровне (закрыт #206)
- package: Зависимость от `q ~0.8.8` и `apw ~0.3.6`

0.5.13 (unstable)
-----------------

- bem make: Перед слепком создается директория `.bem/snapshots`, если таковая не существует (закрыт #201)
- bem make: Реализован метод `clean()` в `BemCreateNode`
- bem make: Исправлен метод `getLevels()` в `BundleNode`: неопределенный уровень не помещается в конечный массив (закрыт #203)
- API: Добавлен метод-хелпер `getLevelPath()` в классы `BlockNode` и `LevelNode` (закрыт #190)

0.5.12 (unstable)
-----------------

- bem make: Перенаправлять ошибки из `borschik` с префиксом `borschik: ` в `BorschikNode`
- bem make: Хранить выводимое имя файлов output в свойстве `this.output` для дальнейшего использования в логах в `BorschikNode`
- package: Зависимость от `borschik ~0.0.11`

0.5.11 (unstable)
-----------------

- bem: Реализованы различные стратегии для массовых операций IO в `Tech.filterPrefixes()` и `BemBuildNode.isValid()` (закрыт #167)
- bem: Исправлено указание на технологии по имени
- bem: Разрешено использование `module.exports = ...` в файлах, которые читает `util.readDecl()`
- bem: `util.getBemTechPath()` возвращает полный путь с расширением к технологии
- bem: Добавлена опция `-T` в качестве алиаса для `-t`, `--tech` для команды `bem build`
- bem: Добавлены опции `--output-level` and `--block`, `--elem`, `--mod`, `--val` для команды `bem build` для сборки сущностей BEM на уровнях бандлов
- bem: Разрешено использование `require()` в файлах типа decl-like (закрыт #172)
- bem: В команды `bem make` и `bem server` добавлена inspector server feature
- bem: Не создается новый класс из`LegacyTech` и tech module content mixin модуля технологии legacy в `getTechClass()` (исправление потенциального бага)
- bem: Багфикс: `bem decl subtract` создает пустой файл `*.deps.js` (закрыт #170)
- deps.js tech: Исправлена сериализация пустых зависимостей
- deps.js tech: Fix twice expansion of deps (Closes #163)
- bem make: Разрешено начинать сборку используя конечные имена файлов в случае, когда технология производит несколько файлов (закрыт #172)
- bem make: Когда `BEM_IO_STRATEGY === 'callback'` и `meta` было пустым, promise никогда не становился resolve
- bem make: Добавлена поддержка для смердженных бандлов
- bem server: Listen on file socket on `--socket` option, configure socket path using `--socket-path` option
  and socket permissions using `--socket-mode` option (Closes #166)
- docs: Задокументированы изменения API в `BEM.create.block()`, `BEM.create.elem()` и `BEM.create.mod()` в версии 0.5.x (закрыт #161)
- docs: Объявлена зависимость от NodeJS 0.6+
- API: Add third `level` optional argument to `getTechClass()` function of `tech` method
- API: Add third `level` optional argument to `createTech()` function of `tech` method
- API: Добавлены `getCreateSuffixes()` и `getBuildSuffixes()` в класс `Tech`, чтобы позволить системе сборки корректно обрабатывать технологии, такие как `bemhtml`
- API: Добавлена функция `util.removePath(path)`, удаляющая пути к файлам и директориям, но не рекурсивно 
- API: Добавлена функция `util.readJsonJs(path)` для чтения и eval файлов JSON-JS
- API: Добавлена функция `util.symbolicLink(link, target, force)`
- API: Добавлен алиас `util.lpad()` в `util.pad()`, добавлена функция `util.rsplit(string, sep, maxsplit)`
- API: В класс `LegacyTech` добавлен метод `getContext()` в качестве прокси `this.techObj.getContext()`
- API: В класс `LegacyTech` добавлен метод `getBuildResultChunk()` в качестве прокси `this.techObj.outFile()`
- API: Ждать загрузки `opts.declaration` перед вызовом `this.techObj.build()` в классе `LegacyTech` 
- tests: Добавлены тесты для сериализации пустых зависимостей в `deps.js tech`
- tests: Использовать `bem-bl` в качестве суб-модуля git для данных тестов (Closes #176)
- tests: Добавлены тесты, которые дополнительно собирают технологии `i18n` и `i18n.js` для бандлов
- tests: Добавлены тесты для сборки смердженного бандла
- tests: Добавлены тесты для функции `getTechClass()` модуля `tech` module
- package: Добавлена зависимость `dom-js` для тестов i18n (закрыт #172)
- package: Добавлена цель `clean` для `GNUmakefile`
- package: Зависимость от `coverjs >= 0.0.7-aplha` (закрыт #191)

0.5.10 (unstable)
-----------------

- bem: Использовать синхронную проверку существования файлов в instance методе `filterPrefixes()`в классе `Tech`
- bem: Исправлен баг с опцией `--chdir` для команды `bem create level` (закрыт #151)
- deps.js tech: Более точно репортить проблемы в файлах `*.deps.js` блоков
- deps.js tech: Читать файл `*.deps.js` каждого блока только один раз
- bem make: Проверять целевую директорию перед выполнением `svn info` в `SvnLibraryNode` (закрыт #154)
- bem make: Выводить собранные логи в случае фэйла в `Node` (закрыт #155)
- bem make: Исправлено исключение во время сборки файлов `*.meta.js` в `BemBuildMetaNode` (закрыт #153)
- bem make: Синхронизированы проверки mtime в методе `isValid()`класса `BemBuildNode` (закрыт #157)
- API: Добавлена функция-promise `util.readDecl()`
- tests: Add legacy `Makefile` "tests" for `bem decl merge` command
- package: зависимость от `coa ~0.3.5`
- package: зависимость от `apw ~0.3.4`

0.5.9 (unstable)
----------------

- bem make: Собирать минифицированные версии файлов `*.bemhtml.js`
- bem make: Проверять ревизии svn в `SvnLibraryNode.isValid()`

0.5.8 (unstable)
----------------

- bem make: `SvnLibraryNode` extends `ScmLibraryNode`

0.5.7 (unstable)
----------------

- Исправлены баги, возникавшие во время запуска `bem make` и `bem server` не из корня проекта
- bem: Output full stack traces on error
- bem: Lazy tech paths resolving in `Level` class
- bem: Команды `bem create *` выводят ошибку, если не указаны технологии в опциях в командной строке и `defaultTechs`  в конфиге уровня является пустым
- bem: Добавлена команда `bem create` для создания всех типов сущностей BEM
- bem server: Русскоязычные сообщения заменены на англоязычные
- bem server: Исправлены неправильные ссылки в списках директорий
- bem server: Strip query string part before accessing a file
- bem make: Не делать checkout `bem-bl` по умолчанию
- bem make: Исправлен `LibraryNode`
- bem make: Extend context of `.bem/make.js` using `global`
- bem make: Сборка файлов бандла при условии существования `*.bemjson.js` и `*.bemdecl.js` в файловой системе
- bem make: Resolve tech module paths using level object in `BundleNode`
- bem make: Использовать `Level.createTech()` вместо `Level.getTech()` для создания объектов технологий для `BemBuildNode`
- bem make: Устанавливать зависимость нод от класса `BemBuildNode` только для существующих файлов блоков для улучшения перформанса
- bem make: Run nodes of `BemBuildNode` class forked by default to increase performance
- bem make: Добавлено больше логгирования для `BundleNode`
- bem make: `BorschikNode` добавлена поддержка для обработки файлов `*.css` с помощью `csso` для сборки на продакшн 
- bem make: В `BorschikNode` Добавлена поддержка обработки файлов `*.js` с помощью `uglifyjs` для сборки на продакшн
- bem make: Параметр `repo` и производные от него переименован в `url` в `ScmLibraryNode`
- bem make: Исправлено удаление лишних зависимостей в `BemBuildNode`
- bem make: Значительный внутренний рефакторинг `BundleNode`
- bem make: Переименовать instance метод `getCreateDependencies()` в `getDependencies()` в классе `BemBuildNode` 
- bem make: Переименовать instance метод `getCreateDependencies()` в `getDependencies()` в классе `BemCreateNode`
- bem make: Добавлить instance методы `setFileNode()` и  `setBemCreateNode()` в класс `BundleNode`
- logging: Логировать версии node на `debug` verbosity
- logging: Логировать информацию profiling `bem make`
- logging: Добавлено больше логирования `debug` verbosity в `BundleNode`
- docs: Добавлен jsdoc для класса `Level`
- docs: Обновлен jsdoc для класса `Tech`
- docs: Добавлена документация для `bem create elem` и `bem create mod`
- docs: Добавлена документация для `bem create`
- docs: Исправлен jsdoc для  instance метода `setBemBuildNode()` класса `BundleNode`
- docs: Добавлен jsdoc для `Node`, `FileNode`, `MagicNode`, `ScmLibraryNode`
- API: Экспортируется модуль `util` как `require('bem').util`
- API: Добавлен instance метод `matchAny()` в класс `Level`
- API: Add instance methods-shortcuts to `Level` class: `getPath()`, `getPathByObj()`, `getRelPathByObj()`
- tests: Добавлены тесты для bem make
- tests: Переписаны все тесты для `mocha`
- package: В список зависимостей добавлено `xjst 0.2.21`
- package: В список зависимостей добавлено `ometajs ~2.1.10`
- package: Зависимость `q` обновлена до `~0.8.5`
- package: Зависимость `apw` обновлена до версии `~0.3.2`
- package: Зависимость `borschik` обновлена до версии `~0.0.10`

0.5.6 (unstable)
----------------

- docs: Черновик русскоязычной версии документации для `bem make` / `bem server`
- API: Добавлены методы `resolvePaths(paths)` и `resolvePath(path)` для класса `Level`
- bem make: Добавлено больше логгирования для `BorschikNode`
- bem make: В `BundleNode` по дефолту используется технология `js-i` для сборки пакетов файлов `*.js` 
- package: Обновлена зависимость `borschik` до `~0.0.9`

0.5.5 (unstable)
----------------

- Require node 0.6.x
- deps.js tech: Исправлен баг со сборкой файлов `deps.js`, появившихся в 0.5.2
- Исправлен запуск `bem make` и `bem server` не из корня проекта
- logging: Вместо `console.log` добавлена короткая функция `flog()` для вывода отформатированных логов
- logging: Логировать номер версии `bem-tools` в `bem make` и `bem server`
- bem server: Показывать ссылку http на старте сервера
- bem server: Исправлен вывод текущей директории в списке директорий
- bem make: Подправлен уровень verbosity для сообщений сборки
- bem make: Логировать цели сборки на старте сборки
- bem make: Исправлены проверки валидности `LibraryNode` и `BemBuildNode`
- bem make: Проверки валидности перенесены из `FileNode` в `GeneratedFileNode`
- bem make: Исправлен `clean()` `BemBuildMetaNode`
- bem make: Относительные пути хранятся в файлах `*.meta.js`
- API: Добавили `require('bem').version`
- API: Добавили `require('bem/lib/util').writeFileIfDiffers(path, content, force)`

0.5.4 (unstable)
----------------

- package: Обновили версию зависимости `apw` до `~0.3.0`

0.5.3 (unstable)
----------------

- deps.js tech: Поддержка формата `deps.js` в качестве declaration для `bem build`

0.5.2 (unstable)
----------------

- В команды `bem make` и `bem server` добавлена опция `--verbosity`
- bem make: Добавлено разноцветное логгирование
- bem make: Внутренний рефакторинг
- bem make: Поправлен баг с зависимостями во время сборки файлов `_*.ie.css`
- bem make: Fix child process handling in `BorschikNode` and `BemBuildNode`
- API: Добавлен winston в качестве движка дл логирования

0.5.1 (unstalbe)
----------------

- bem make: небольшая правка: убрали тестировочный код

0.5.0 (unstable)
----------------

- bem make / server feature introduction
