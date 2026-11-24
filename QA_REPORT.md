# Проверка доработки AVF Repair v2

Ветка: feature/engineering-repair-spec. Production не обновлялся; merge в main не выполнялся.

## Выполненные проверки

- Сборка: 17 статических страниц, включая 7 услуг и 6 проектов.
- node --check src/app.js: успешно.
- scripts/check.mjs: 560 локальных ссылок, якорей и ресурсов; 40 JSON-LD блоков; уникальные Title и Description для всех 17 страниц; по одному H1; отсутствие повторяющихся id; alt и размеры изображений; целостность sitemap; отсутствие пустых контактных ссылок.
- git diff --check: без ошибок.
- В браузере проверены главная, шаблон услуги (зенитные фонари), шаблон проекта (Переделкино), портфолио и контакты на ширинах 375, 390, 768, 1024, 1440, 1920 px: 30 сочетаний, горизонтального переполнения нет. Это проверка пяти шаблонов, а не всех страниц на каждом размере.
- Мобильное меню: открытие и закрытие Escape.
- Форма: пустая отправка показывает ошибки; заполненная форма с согласием переходит в demo-ready и сообщает, что ничего не отправлено. Повторно проверено после защиты от параллельных отправок.
- Реальный локальный PNG выбран через file chooser: предпросмотр появился; удаление вернуло количество фото к нулю.
- Сравнение: ArrowRight изменил долю «после» с 50 до 51 процента.
- Фильтр «Металлоконструкции»: показано 2 из 6 объектов.
- UTM source=qa и campaign=spec сохранены при переходе с главной на услугу; canonical остаётся чистым production URL без UTM.
- Console error в проверенных сценариях: 0.
- Сохранены снимки review/home-desktop.jpg и review/home-mobile.jpg.

## Реализовано, но требует внешней проверки

- Сетевые состояния sending/success/error подготовлены для endpoint. Настоящий endpoint отсутствует, поэтому реальная доставка не тестировалась и form_success не имитируется.
- Drag-and-drop использует тот же обработчик, что выбор файлов. Проверка загрузки выполнена через chooser; жест перетаскивания и реальные iOS/Android устройства отдельно не тестировались.
- Ограничения формата/размера/количества и декодирование изображений реализованы. Полная матрица повреждённых/больших файлов не прогонялась.
- Метрика и GA4 не подключены: идентификаторы пустые. Нужна проверка приёма событий в реальных кабинетах после согласования запуска.
- Lighthouse не запускался: CLI в окружении не установлен. Performance 90+, Accessibility 90+, Best Practices 90+, SEO 95+ остаются целями, а не полученными оценками.
- Скриншоты, семантические проверки и клавиатурные сценарии не заменяют полный аудит доступности скринридером.

## Ограничения готовности контента

Фотографии услуг, реальных результатов, производств и команды заменены явно обозначенными схемами. Кейсы — страницы с подтверждёнными названиями/направлениями и пометками о недостающих деталях. Условия гарантии, контактные и юридические данные не выдумывались. Без этих материалов сайт готов к ревью, но не к запуску рекламы и реальному сбору заявок. Полный список — CONTENT_TODO.md.

## Публикация

Только после отдельного подтверждения пользователя по последнему пункту ТЗ. Инструкция запуска и публикации — README.md. GitHub Pages продолжает показывать предыдущую main.

## Изменённые файлы

```text
A	ARCHITECTURE.md
A	CONTENT_TODO.md
A	QA_REPORT.md
M	README.md
M	docs/app.js
A	docs/assets/after.svg
A	docs/assets/architecture.svg
A	docs/assets/before.svg
A	docs/assets/favicon.svg
A	docs/assets/glass.svg
A	docs/assets/metal.svg
A	docs/assets/og.png
A	docs/assets/production.svg
A	docs/assets/stone.svg
A	docs/assets/team.svg
A	docs/config.js
M	docs/contacts.html
M	docs/index.html
M	docs/portfolio.html
D	docs/portfolio.js
A	docs/privacy.html
A	docs/projects/fok-nekrasovka.html
A	docs/projects/peredelkino-flyugarki.html
A	docs/projects/peredelkino-kamen.html
A	docs/projects/sambo-boks.html
A	docs/projects/sbercity-flyugarki.html
A	docs/projects/uspenskaya-ograzhdeniya.html
A	docs/robots.txt
A	docs/services/gidrofobizatsiya.html
A	docs/services/parapetnye-kryshki.html
A	docs/services/remont-ograzhdeniy.html
A	docs/services/restavratsiya-kamnya.html
A	docs/services/ruchki-antipanika.html
A	docs/services/zamena-steklopaketov.html
A	docs/services/zenitnye-fonari.html
A	docs/sitemap.xml
M	docs/style.css
A	review/home-desktop.jpg
A	review/home-mobile.jpg
A	scripts/build.mjs
A	scripts/check.mjs
A	scripts/og.mjs
A	scripts/serve.mjs
A	src/app.js
A	src/architecture.svg
A	src/config.mjs
A	src/data.mjs
A	src/style.css
```
