# Торговый журнал — PWA

Прогрессивное веб-приложение: устанавливается на главный экран, работает офлайн, все данные хранит в `localStorage` устройства.

## Структура

```
journal-pwa/
├── index.html          ← v13 + PWA-патч
├── manifest.json
├── sw.js               ← service worker
└── icons/
    ├── icon-192.png
    ├── icon-512.png
    ├── icon-maskable-512.png
    └── apple-touch-icon.png
```

## Деплой на GitHub Pages

1. Создайте репозиторий (например, `trading-journal`).
2. Залейте всё содержимое этой папки в корень репозитория:
   ```bash
   git init
   git add .
   git commit -m "PWA"
   git branch -M main
   git remote add origin https://github.com/USERNAME/trading-journal.git
   git push -u origin main
   ```
3. **Settings → Pages → Source → Deploy from branch → main / (root) → Save**.
4. Через ~1 минуту откройте `https://USERNAME.github.io/trading-journal/`.

## Установка на телефон

**Android (Chrome):** откройте сайт → нажмите кнопку «⬇ Установить приложение» внизу справа. Или меню (⋮) → «Установить приложение».

**iPhone (Safari):** откройте сайт → кнопка «Поделиться» → «На экран «Домой».

## Обновление

После любого `git push`:
- GitHub Pages обновится за 1–2 минуты.
- При следующем открытии PWA service worker заметит новую версию и перезагрузит страницу автоматически.

После крупных правок меняйте `VERSION` в `sw.js` (`tj-v1` → `tj-v2`) — это очистит старый кеш.

## Локальный тест

Service worker работает только на HTTPS или localhost:

```bash
cd journal-pwa
python3 -m http.server 8000
```

Откройте `http://localhost:8000`.

## Бэкап данных

Все сделки в `localStorage`. Если очистить данные сайта в браузере — всё пропадёт. Используйте встроенный экспорт в CSV (есть кнопки в самом приложении).
