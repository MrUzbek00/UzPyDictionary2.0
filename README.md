# UzPyDictionary

A Python-based Uzbek dictionary engine built on structured JSON data.  
The project focuses on **data quality first**, then provides search, translation, and API access on top of it.

This repository is intended to be used as:
- a local/offline dictionary engine
- a backend service (API)
- a base dataset for language-learning or NLP projects

---

## English Version

## What is UzPyDictionary?

UzPyDictionary is a Python project that works with **structured Uzbek dictionary data stored in JSON files**.

It allows users to:
- search Uzbek words (Cyrillic or Latin)
- read definitions and example sentences
- access translations in different languages
- build APIs or applications on top of the dataset

The core value of this project is **clean, normalized, extensible dictionary data**.

---

## Key Features

- Search by:
  - Uzbek Cyrillic
  - Uzbek Latin
  - normalized transliteration
- Multiple meanings (senses) per word
- Example sentences separated from definitions
- Author and work metadata for examples
- Multi-language translation support
- Python API for programmatic access
- Ready to be extended with FastAPI / Flask

---

## Data Structure (Simplified)

Each dictionary entry follows this structure:

```json
{
  "entry_id": "b_000001",
  "headword_cyr": "ДАБДУРУСТДАН",
  "headword_lat": "Dabdurustdan",
  "transliteration": "dabdurustdan",
  "pos": "adv",
  "labels": [],
  "domain": null,
  "register": null,
  "senses": [
    {
      "sense_id": 1,
      "definition": "Suddenly; unexpectedly.",
      "examples": [
        {
          "text": "Dabdurustdan kirishga botinolmay qoldim.",
          "source": {
            "author": "F. Musajonov",
            "work": "Himmat"
          }
        }
      ],
      "translations": {
        "en": ["suddenly"],
        "ru": ["вдруг"]
      }
    }
  ],
  "translations": {},
  "crossrefs": [],
  "notes": "",
  "meta": {
    "source": "O‘zbek tilining izohli lug‘ati",
    "extracted_from": "PDF"
  }
}
```

---

## Project Goals

1. Create a **single unified Uzbek dictionary dataset**
2. Enforce **one strict JSON schema**
3. Make dictionary data reusable for:
   - search
   - translation
   - APIs
   - learning tools

---

## Core Tasks (Data-Focused)

### High Priority
- [ ] Merge all per-letter JSON files into **one unified JSON**
- [ ] Ensure **unique and stable `entry_id`**
- [ ] Normalize:
  - Cyrillic → Latin
  - apostrophes (`o‘`, `g‘`)
- [ ] Fill missing metadata:
  - part of speech
  - labels
  - register / domain
- [ ] Separate example sentences from definitions
- [ ] Extract and normalize:
  - author names
  - work titles
- [ ] Add empty translation placeholders where missing

### Medium Priority
- [ ] Detect and add cross-references (`see`, `qarang`)
- [ ] Validate JSON against schema
- [ ] Remove duplicated or malformed entries

---

## Python Usage (Example)

```python
from uzpydictionary import UzPyDictionary

d = UzPyDictionary("data/uz_dictionary.json")

entry = d.lookup("dabdurustdan")
print(entry["headword_lat"])
```

---

## API Usage (Optional)

The dataset is designed to be easily exposed via an API.

Example endpoints:
- `/lookup?q=word`
- `/search?q=prefix`
- `/translate?q=word&to=en`

FastAPI or Flask can be used.

---

## License Note

**MIT**

---

---

## Ўзбекча версия

## UzPyDictionary нима?

UzPyDictionary — бу **JSON форматдаги ўзбек луғат маълумотлари** билан ишлайдиган Python лойиҳа.

Лойиҳа қуйидагиларни таъминлайди:
- сўз қидириш (кирилл ва лотин)
- таъриф ва мисол гапларни кўриш
- турли тилларга таржима қилиш
- API ва иловалар қуриш учун база

Асосий эътибор — **маълумот тозалиги ва тузилиши**.

---

## Асосий имкониятлар

- Кирилл ва лотин бўйича қидириш
- Бир сўзда бир нечта маъно (senses)
- Мисол гаплар таърифдан ажратилган
- Муаллиф ва асар маълумоти
- Кўп тилли таржима тузилмаси
- Python орқали ишлатиш
- API учун тайёр структура

---

## Лойиҳа мақсадлари

1. Барча луғат маълумотларини **битта тоза форматга келтириш**
2. Ягона ва қатъий JSON схема
3. Луғатни қайта ишлатиш мумкин бўлган базага айлантириш

---

## Асосий вазифалар

### Энг муҳим
- [ ] Барча ҳарфларга бўлинган JSON файлларни биттага қўшиш
- [ ] `entry_id` ни уникал қилиш
- [ ] Кирилл → Лотин нормализация
- [ ] Етишмайдиган маълумотларни тўлдириш
- [ ] Мисол гапларни таърифдан ажратиш
- [ ] Муаллиф ва асар номларини тозалаш
- [ ] Таржима майдонларини қўшиш

### Кейинчалик
- [ ] Cross-reference (қаранг) қўшиш
- [ ] JSON текшириш (validation)
- [ ] Дубликатларни олиб ташлаш

---

## Хулоса

Бу лойиҳа:
- аввало **маълумот лойиҳаси**
- кейин **Python луғат**
- ундан кейин **API ёки илова**

Агар маълумот тоза бўлмаса — қолгани ишламайди.

---

## License

**MIT**
