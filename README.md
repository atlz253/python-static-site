# Пример статической сайта, сгенерированного при помощи Pelican

## Отчет

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