# Поля для заявки на верификацию

Копируй отсюда в Google Cloud Console → OAuth consent screen → Verification.
Замени `dx0t1011` на свой ник GitHub и `ПОЧТА` на рабочую почту.

---

## App information (OAuth consent screen)

| Поле | Значение |
|---|---|
| App name | `Warm Burrow Publisher` |
| User support email | `ПОЧТА` |
| App logo | `assets/logo-120.png` (ровно 120×120) |
| Application home page | `https://dx0t1011.github.io/publish-app/` |
| Application privacy policy link | `https://dx0t1011.github.io/publish-app/privacy.html` |
| Application terms of service link | (необязательно, оставить пустым) |
| Authorized domains | `dx0t1011.github.io` |
| Developer contact information | `ПОЧТА` |

## Scopes

```
https://www.googleapis.com/auth/youtube
https://www.googleapis.com/auth/youtube.upload
```

## Scope justification (вставить как есть)

```
The application is a personal command-line tool used by the owner of one YouTube channel
(Warm Burrow Stories) to upload that channel's own video episodes and schedule their publication.

The scope https://www.googleapis.com/auth/youtube.upload is used to upload the finished episode
file to the owner's own channel.

The broader scope https://www.googleapis.com/auth/youtube is used to: set the video thumbnail,
add the uploaded video to the channel's playlist, and read the channel name and statistics so that
uploads go to the correct channel when the signed-in Google account manages more than one YouTube
channel.

There are no third-party users, no sign-up, and no viewer, subscriber, comment or analytics data is
read. No other Google services are accessed. The tool runs locally on the owner's computer and is not
distributed as a product.
```

## Демо-видео: сценарий (60–90 секунд, без монтажа)

1. Открыть `https://dx0t1011.github.io/publish-app/` — показать главную целиком.
2. Открыть `privacy.html` — показать, что политика доступна без входа.
3. В терминале: `node publish/auth.mjs --client-id ... --client-secret ...`
   → показать **ссылку** → открыть её → **экран согласия Google** со списком scopes
   → выбрать канал **Warm Burrow Stories** → разрешить.
4. В терминале появилось `✓ Канал: «Warm Burrow Stories» (id …)`.
5. `node publish/upload.mjs --ep episodes/EP002-tea-and-rain` → видно `загружаю…` → `✓ загружено: …`
6. YouTube Studio → Контент → **Запланированные** → показать ролик с датой.

Загрузить это видео на канал как **unlisted**, ссылку вставить в заявку.

---

## Чек-лист перед отправкой

- [ ] нет плейсхолдеров: `grep -rn "PLACEHOLDER" .` ничего не находит
- [ ] название приложения одинаково в консоли и в `<title>`
- [ ] обе страницы открываются в инкогнито
- [ ] логотип загружен (120×120)
- [ ] «Publish app» нажато — статус In production
- [ ] `node publish/check.mjs` показывает нужный канал
- [ ] демо-видео записано и загружено unlisted
- [ ] обоснование scope вставлено
- [ ] заявка отправлена, дата записана в `docs/decisions.md`
