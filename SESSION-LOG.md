# SESSION-LOG — журнал рішень і обговорень

Цей файл — стиснутий журнал ключових рішень по проекту, щоб не втрачати контекст
при компактизації чатів і продовжувати роботу з будь-якого пристрою/сесії.
Регулярно (після кожного значного блоку обговорення) сюди додається новий запис.
Деталі реалізації — у відповідних файлах (CLAUDE.md, TOPICS-BANK.md, articles/).

---

## 2026-06-13

**Semrush research (бюджет 50k API units, використано ~5200):**
- Розширили TOPICS-BANK.md новою секцією "Нова семантика за даними Semrush" — пункти #71-79
- Високий пріоритет: AK-47 | Inheritance (~3300/мо), AK-47 | Case Hardened blue-gem (~2770/мо, доповнює існуючий п.56), CS2 Sticker Craft guide (~3740/мо), Holo/Slab stickers, найдешевші Covert/red скіни (1300/мо)
- Середній пріоритет: red/purple/green gloves (390-480/мо кожна, формат як успішна Best Blue Gloves стаття), пілар "All CS2 Gloves by color" (320/мо)

**AK-47 | Inheritance — аналіз семантики:**
- Загальний/інформаційний запит (~2780/мо) → стаття в блог
- Wear-специфічні запити → product pages, лінкувати з тіла статті
- Висновок: канібалізації немає, якщо стаття таргетить broad query
- Pattern-секція (blue-gem style) НЕ потрібна — обсяг по паттернах низький (30-40/мо), і Steam-гайд по паттернах (id=1728104691) не покриває Inheritance взагалі
- Статтю по AK-47 Inheritance ще не написано — задача відкладена, поки фокус на gloves

**Новий xlsx-план (`skin_land_blog_plan_final_1.xlsx`, 56 тем):**
- В основному general CS2 how-to (FPS, Premier, ranks, settings) — слабко пов'язані з маркетплейсом скінів, окреме рішення чи додавати в TOPICS-BANK
- Категорія Gloves (4 теми, всі Low, 30-50/мо): Moto, Hand Wraps, Broken Fang, Driver — модельна розбивка
- Порівняння з нашими знахідками: кольорова розбивка (red/purple/green, 390-480/мо) має у 8-16 разів більший обсяг і повторює формат Best Blue Gloves (#1 на "blue gloves cs2", 480/мо)

**Рішення по Gloves (для тесту ефективності) — ВИПРАВЛЕНО:**
Користувач вказав, що `best-red-gloves-in-cs2` і `all-best-purple-gloves-in-csgo-and-cs2`
**вже існують**. Перевірка sitemap-blog-urls.txt підтвердила: кольорові рукавиці
(red/blue/green/purple/yellow/white/black/pink/orange) — ВСІ кольори вже покриті.
Пункти 76-79 (кольорові) в TOPICS-BANK скасовано як дублікати.

Натомість — модельна розбивка з xlsx (Moto/Hand Wraps/Broken Fang/Driver Gloves,
30-50/мо) НЕ дублює жодну існуючу статтю — перейменовано в TOPICS-BANK як нові
п.76-79. Рекомендований порядок оновлено: Driver Gloves першим у тижні 5-6.

Очікуємо підтвердження користувача, з яких саме gloves-статей (модельних) почати.

---

## Існуючі написані статті (актуальний список)
- `articles/deagle-skin-tier-list-cs2-2026.md`
- `articles/best-cs2-knives-under-100-2026.md`
- `articles/best-driver-gloves-skins-in-cs2-2026.md` (нове, 2026-06-13)
- (+ HTML-пари для кожної)

## 2026-06-13 (продовження) — Driver Gloves стаття

Написано `best-driver-gloves-skins-in-cs2-2026.md` + `.html` — 8 фінішів
(King Snake, Garden, Plum Quill, Brocade Crane, Brocade Flowers, Imperial Plaid,
Overtake, Racing Green), ціни з `data/csgo-market-export.json`, картинки —
Steam CDN icon_url отримано через `WebFetch` на
`steamcommunity.com/market/search/render/?query=...&appid=730&norender=1`.
8 внутрішніх лінків зі sitemap. Перевірено: усі тайтли скінів лінкують на FN
(окрім Brocade Flowers — FN не існує в каталозі, лінк на MW).

Наступний кандидат: **Best Moto Gloves Skins in CS2** (другий пріоритет після Driver,
п.76 у TOPICS-BANK).

## Відкриті задачі
- [ ] Написати Best Moto Gloves Skins in CS2 (наступний gloves-тест)
- [ ] AK-47 | Inheritance — стаття (інформаційний фокус, без pattern-секції)
- [ ] Вирішити, чи додавати general CS2 how-to теми з нового xlsx в TOPICS-BANK
