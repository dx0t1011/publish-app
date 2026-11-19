# publish-app — сайт для верификации OAuth-приложения

Этот каталог — **готовый публичный репозиторий** для GitHub Pages. Он нужен Google,
чтобы проверить приложение: без публичной домашней страницы и публичной политики
конфиденциальности заявку не принимают.

Ничего секретного здесь нет и быть не должно.

---

## Что внутри

| Файл | Зачем |
|---|---|
| `index.html` | домашняя страница приложения (то, что Google называет Application home page) |
| `privacy.html` | политика конфиденциальности — обязательна для верификации |
| `terms.html` | условия использования — поле «Application terms of service link» |
| `404.html` | простая страница ошибки |
| `.nojekyll` | отключает обработку Jekyll, чтобы файлы отдавались как есть |
| `assets/logo-120.png` | логотип ровно 120×120 — его же грузим в OAuth consent screen |
| `assets/logo-512.png` | крупная версия (для страницы и на будущее) |
| `assets/hero.jpg` | оформление канала на главной |
| `VERIFICATION.md` | поля для заявки: что куда вставлять |

---

## Состояние: уже опубликовано

| Что | Значение |
|---|---|
| Репозиторий | https://github.com/dx0t1011/publish-app (публичный) |
| Главная | https://dx0t1011.github.io/publish-app/ |
| Политика | https://dx0t1011.github.io/publish-app/privacy.html |
| Условия использования | https://dx0t1011.github.io/publish-app/terms.html |
| Pages | ветка `main`, папка `/ (root)`, включён через API |

Обновить сайт после правок:

```bash
cd ~/Desktop/"warm burrow stories"
cp -R site/. /tmp/publish-app-sync/ 2>/dev/null || { mkdir -p /tmp/publish-app-sync && cp -R site/. /tmp/publish-app-sync/; }
cd /tmp/publish-app-sync && git add -A && git commit -m "update site" && git push
```

Проще: правь `site/` в проекте, затем синхронизируй (после первого клона
репозитория достаточно копировать файлы в клон и пушить).

## Почта в контакте

Уже стоит: `bs2accc@gmail.com` в `index.html` и `privacy.html`.
Поменять — правка в этих файлах и `./tools/sync_site.sh`. Проверить:

```bash
python3 tools/check_site.py --url https://dx0t1011.github.io/publish-app/
```

## Если понадобится подтвердить домен

Google Search Console → добавить ресурс `https://dx0t1011.github.io/publish-app/` →
способ «HTML-файл» → положить полученный `googleXXXX.html` в корень этого репозитория →
закоммитить и запушить.

## Мелочи, из-за которых заявки чаще всего отклоняют

1. Название в OAuth consent screen (**Warm Burrow Publisher**) не совпадает с `<title>`
   на главной странице.
2. Политика конфиденциальности недоступна без логина или содержит плейсхолдеры.
3. В политике нет упоминаний YouTube API Services и ссылки на YouTube Terms of Service —
   в этом шаблоне они уже есть, не удаляй.
4. На главной не сказано, что делает приложение (Google читает её буквально).
5. Контакт — только GitHub issues без почты: допустимо, но почта усиливает заявку.
