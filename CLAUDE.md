# CLAUDE.md — Контекст проекту skin.land SEO

## Що це за проект

SEO-контент для блогу **Skin.Land** — маркетплейс скінів CS2.  
Сайт: `https://skin.land` | Блог: `https://skin.land/blog/`  
Репозиторій: `https://github.com/aorlov-web/ai-claude-seo`  
Всі статті зберігаються у папці `/articles/`.

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
