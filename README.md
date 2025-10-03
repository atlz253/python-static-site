# Пример статической сайта, сгенерированного при помощи Pelican

## Генерация шаблона и автоматическое развертывание на GH Actions

1. Был установлен python с (официального сайта)(https://www.python.org/)
2. Был установлен venv по (инструкции)[https://virtualenv.pypa.io/en/latest/installation.html]
3. Был создан каталог для проекта
4. Был установлен Pelican и markdown: `pip install "pelican[markdown]"`
5. Был сгенерирован стартовый проект при помощи команды `pelican-quickstart`
6. В директории `content` был создан файл со статьей `hello-world.md`
7. Была разработана конфигурация (`.github/workflows/pelican.yml`) CI/CD пайплайна для генерации и публикации статической сайта на платформе GitHub Pages
8. Был инициализирован git репозиторий и опубликован на платформе GitHub
9. В настройках репозитория GitHub было разрешено редактирование репозитория при помощи GitHub Actions: `Settings -> Actions -> General -> Workflow permissions -> Read and write permissions`
10. Был включен Pages для репозитория: `Settings -> Pages -> Branch -> gh-pages`
11. Была перезапущена последняя проваленная задача GitHub Actions, после успешного завершения был проверен доступ к сайту
12. В файле конфигурации `pelicanconf.py` был задан базовый URL сайта (`SITEURL`) для корректной работы стилей

## Подключение собственной темы

1. Из [репозитория тем Pelican](https://github.com/getpelican/pelican-themes) перенесли шаблон темы `simple-bootstrap` в проект
2. В `pelicanconf.py` в константе `THEME` указали путь до директории с темой `simple-bootstrap`
3. Для изменения темы достаточно изменять файлы в директории шаблона темы
4. При помощи команды `pelican content -o output -s pelicanconf.py --autoreload --listen` был запущен сервер для проверки изменений

## Минификация HTML

1. Установлен пакет с закрепленной версией `pip install minify-html~=0.15.0` из-за несовместимости пакета `pelican-htmlmin` с более новыми версиями
2. Был установлен `pelican-htmlmin`: `pip install pelican-htmlmin`
3. В `pelicanconf.py` была добавлена константа `PLUGINS = ['minify']`
4. Была проверена сборка проекта при помощи `make publish`

## PostCSS

1. Был инициализирован `package.json`: `npm init -y`
2. Был установлен PostCSS: `npm install --save-dev postcss postcss-cli autoprefixer cssnano`
3. В файле `postcss.config.js` подключены установленные плагины
4. В `package.json` был добавлен скрипт сборки при помощи PostCSS: `"build-css": "postcss themes/ваша_тема/static/css/input.css -o output/static/css/main.min.css"`
5. В `Makefile` был модифицирован скрипт `publish` для вызова `npm` скрипта
6. Обновлен `.github/workflows/pelican.yml` для установки npm зависимостей
