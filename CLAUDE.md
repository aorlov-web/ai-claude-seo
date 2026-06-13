# CLAUDE.md — Контекст проекту skin.land SEO

## Що це за проект

SEO-контент для блогу **Skin.Land** — маркетплейс скінів CS2.  
Сайт: `https://skin.land` | Блог: `https://skin.land/blog/`  
Репозиторій: `https://github.com/aorlov-web/ai-claude-seo`  
Всі статті зберігаються у папці `/articles/`.

**Журнал рішень:** `/SESSION-LOG.md` — стиснутий лог ключових обговорень і рішень
по датах. На початку нової сесії читати цей файл для контексту. Після кожного
значного блоку обговорення (нове дослідження, рішення по темах, зміна стратегії) —
додавати короткий запис туди, щоб економити контекст і не повторювати дослідження.

---

## Критичні правила бренду

- Бренд завжди пишеться **Skin.Land** — з великої S, великої L, крапка посередині
- В URL (href) — lowercase: `https://skin.land/...` — не змінювати
- Ніколи: `skin.land`, `Skin.land`, `SkinLand`

---

## Структура статей

Кожна стаття — Markdown-файл у `/articles/`. Стандартні елементи:

1. **Інтро** — 1–2 речення, вижимка статті для AI-пошуку. Тільки брендова ссилка `[Skin.Land](https://skin.land)`, без інших посилань.
2. **Тіло** — описи скінів/товарів, тир-лисити, гайди. Тут розміщується вся перелінковка.
3. **FAQ** — 4–6 питань у форматі H3 + відповідь.

---

## Транзакційні сторінки (sell/buy/маркет/головна)

Окрема папка `/pages/` — тексти для **транзакційних сторінок** (sell-skins, market, головна),
на відміну від `/articles/` (блог). Мета інша: ранжування за комерційними запитами
(`sell cs2 skins`, `buy cs2 skins`), конверсія, антиканібалізація між головною та лендингами.

Повний контекст стратегії, по-мовні знахідки, відкриті питання до продукту та технічні
обмеження адмінки (без `<ol>`, без таблиць) — у `/pages/CONTEXT.md`.

---

## HTML-версія для адмінки

Кожна стаття в `/articles/` має парний `.html` файл з тим самим контентом (той самий basename, наприклад `best-cs2-knives-under-100-2026.md` + `best-cs2-knives-under-100-2026.html`) — для вставки готового коду в CMS.

**Конвенції розмітки:**
- Заголовок (`# H1`) у HTML не дублюється — він окреме поле в CMS
- `## H2` → `<h2>`, `### H3` → `<h3>`
- Параграфи → `<p>...</p>`, більшість закінчуються на `&nbsp;`
- Списки → `<ul><li><p>...</p></li></ul>`
- Таблиці → `<table><thead><tr><th>...</th></tr></thead><tbody>...</tbody></table>`
- Посилання → `<a href="...">...</a>`, зображення → `<img src="..." alt="...">`
- FAQ: кожне питання — `<h3>`, відповідь — `<p>`

---

## Посилання на товари

**Шаблон URL:**
```
https://skin.land/market/csgo/{weapon-slug}-{skin-slug}-{wear}/
```

**Wears:**
| Абревіатура | URL-слово |
|---|---|
| FN | factory-new |
| MW | minimal-wear |
| FT | field-tested |
| WW | well-worn |
| BS | battle-scarred |

**Приклади:**
- `https://skin.land/market/csgo/desert-eagle-blaze-factory-new/`
- `https://skin.land/market/csgo/desert-eagle-printstream-field-tested/`

**Ножі та рукавиці (★):**
В URL для ножів і рукавиць (covert/extraordinary, "★" в назві Steam market hash) додається префікс `★-` (у URL-кодуванні `%E2%98%85-`):
```
https://skin.land/market/csgo/%E2%98%85-{weapon-slug}-{skin-slug}-{wear}/
```
Приклад: `https://skin.land/market/csgo/%E2%98%85-navaja-knife-rust-coat-well-worn/`
Для звичайної зброї (пістолети, рушниці, AK/AWP/M4 і т.д.) префікс **не** додається.

**Правила:**
- Заголовок скіна (`### Desert Eagle | Blaze`) — посилання на FN версію
- Рядок "Best buy" — посилання на рекомендований wear
- Cloudflare блокує скрипти — перевіряти URL вручну або через браузер
- Для перевірки актуальних цін і назв товарів використовувати `/data/csgo-market-export.json` (експорт каталогу CS:GO, поля `name`, `price`, `url`, `count`) — оновлювати періодично через `curl -sL -o data/csgo-market-export.json "https://app.skin.land/market_export_json/csgo.json"` (цей endpoint не блокується Cloudflare, але посилання в статтях все одно мають бути на домен `skin.land`, не `app.skin.land`)

---

## Внутрішня перелінковка

**Файл з усіма URL блогу:** `/sitemap-blog-urls.txt` (501 стаття, формат: `URL | anchor-hint`)

**Правила:**
- Мінімум 5–8 внутрішніх посилань на статтю
- Кожен URL — тільки 1 раз у статті (без дублів)
- Посилання вставляти **в тіло статті** на смислові слова — не call-out фрази типу "check out X" або "read more here"
- Підбирати по контексту: якщо стаття про Deagle — посилатись на статті про Deagle, pistols, wear, investing, інші tier lists

**Найбільш релевантні URL за темами:**

*Wear / Float:*
- `https://skin.land/blog/how-does-skin-wear-affect-its-look/`
- `https://skin.land/blog/skin-wear-in-csgo/`

*Buying / Value:*
- `https://skin.land/blog/what-to-look-at-when-buying-csgo-skins/`
- `https://skin.land/blog/best-csgo-skins-to-invest-in/`
- `https://skin.land/blog/trading-or-investing-finding-the-right-approach-to-buying-csgo-skins/`

*Rarity:*
- `https://skin.land/blog/csgo-skins-rarity/`
- `https://skin.land/blog/rare-skins-in-csgo/`

*Tier lists (cross-linking):*
- `https://skin.land/blog/ak-47-skins-tier-list-in-cs2/`
- `https://skin.land/blog/csgo-and-cs2-knife-tier-list/`
- `https://skin.land/blog/gloves-tier-list-in-cs2/`

*Deagle-специфічні:*
- `https://skin.land/blog/best-cheap-desert-eagle-skins-in-cs2/`
- `https://skin.land/blog/full-deagle-heat-treated-patterns-guide/`
- `https://skin.land/blog/r8-vs-deagle-in-cs2-which-one-to-choose/`

---

## Стиль написання

Ніша — геймери, тому текст не повинен бути сухим/корпоративним. Орієнтир по тону: [cs2-update-knife-trade-up-and-retake-comeback](https://skin.land/blog/cs2-update-knife-trade-up-and-retake-comeback/) — розмовний стиль, геймерський сленг замість загальних SEO-фраз, риторичні питання до читача, особиста інтонація.

**Приклади заміни сухих формулювань:**
- "increase in value" → "waiting for their time to shine"
- "earn you some money" → "make you some serious dough"
- "one of the best value buys" → "one of the biggest steals"
- "underrated" → "slept-on pick"

**Банк фраз** (з інших статей автора Alex Johnson — best-p90-skins-in-cs2, best-sg-553-skins-in-cs2, best-asiimov-crafts-guide, cs2-map-pool-tier-list-guide-for-premier-and-competitive):
- Риторичні відкриття: "Is there any surprise we start the list from this classic?", "You might disagree, but X is a phenomenal...", "Yes, we know, some of you really don't like...", "We just can't put this niche yet somehow fan-favorite..."
- Бюджетний фреймінг: "If you are balling big time and the money's not an issue...", "won't break the bank"
- Яскраві епітети: "giving off strong [X] vibes", "the fliest one", "visually stunning", "breathtaking design", "time-tested", "legendary esports staple", "a piece of Counter-Strike history", "community favorite that players desperately want back"
- CTA: "head over to Skin.Land to upgrade your loadout!"
- Паттерн відкриття абзацу: "This right here is...", "This one is a fantastic...", "We had to mention at least one..."

**Правила застосування:**
- 1–3 сленгові/яскраві фрази на статтю максимум, кожен раз різні — не повторювати між статтями
- Риторичні питання та легка особиста інтонація у вступах/переходах де природно
- Можна додати мемну/смішну картинку в кінці, якщо тема дозволяє жарт — не обов'язково для серйозних гайдів
- SEO-структура (H2/H3 як питання, FAQ, перелінковка) залишається незмінною — змінюється тільки подача

---

## Банк тем і пріоритети

Повний список у `/TOPICS-BANK.md` (70 тем з пріоритетами 🔴🟡🟢).

**Найвищий пріоритет зараз:**
1. Fever Case CS2 — огляд
2. Найкращі ножі CS2 до $100
3. AK-47 | Asiimov — огляд скіна
4. Skin.Land vs Steam Market — порівняння

---

## Існуючі статті (не дублювати)

Повний список у `/data/EXISTING-ARTICLES.md`.  
Написані нами статті у `/articles/`:
- `deagle-skin-tier-list-cs2-2026.md`
- `best-cs2-knives-under-100-2026.md`

---

## SEO-стандарти

Повні стандарти у `/SEO-CONTENT-WORKFLOW.md` та `/SEO-WORKFLOW-SYSTEM-2026.md`.

**Ключові правила для статей:**
- Інтро: відповідь на пошуковий запит у першому реченні (inverted pyramid)
- H2/H3: формулювати як питання або пряму відповідь (AEO)
- FAQ: 4–8 питань, відповіді 40–70 слів
- Кожна стаття: мінімум 1 "citation-ready passage" (40–80 слів, самодостатній факт)
- Не дублювати існуючі статті блогу
- Зображення: Steam CDN або офіційний арт, alt text включає назву скіна + "buy on Skin.Land"

---

## Git workflow

```bash
git add articles/<filename>.md
git commit -m "Add/Revise article: <short description>"
git push
```
Git config: `user.email = a.orlov@trading.space`, `user.name = aorlov-web`

**Коміт відразу:** після кожного завершеного раунду правок (нова стаття, розділ, стилістичне оновлення) — комітити і пушити без додаткового підтвердження, щоб правки відразу були видні на GitHub з будь-якого пристрою.
