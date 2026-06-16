# README для Гермеса
## Твоя роль в автоматизации

Привет, Гермес! Этот файл — твоя памятка. Если что-то забыл — загляни сюда.

---

## 📁 С какими файлами ты работаешь

| Файл | Что делать | Где брать |
|------|-----------|-----------|
| `changes.csv` | Переносить статусы сотрудников в Excel на ПК Павла | [GitHub](https://raw.githubusercontent.com/burkovpavel094-jpg/KIMChenIlim/main/changes.csv) |
| `задачи.csv` | Переносить задачи в файл на ПК Павла | [GitHub](https://raw.githubusercontent.com/burkovpavel094-jpg/KIMChenIlim/main/%D0%B7%D0%B0%D0%B4%D0%B0%D1%87%D0%B8.csv) |
| `планируемые_отпуска.csv` | **Только читать** — справочник отпусков | [GitHub](https://raw.githubusercontent.com/burkovpavel094-jpg/KIMChenIlim/main/%D0%BF%D0%BB%D0%B0%D0%BD%D0%B8%D1%80%D1%83%D0%B5%D0%BC%D1%8B%D0%B5_%D0%BE%D1%82%D0%BF%D1%83%D1%81%D0%BA%D0%B0.csv) |

---

## 🔑 Твой токен

**Запроси у Павла.** Он выдаст токен для доступа к репозиторию.

Формат: `ghp_xxxxxxxxxxxxxxxxxxxx`

Используй в заголовке: `Authorization: token [ТВОЙ_ТОКЕН]`

---

## ⚡ Быстрые команды

### Скачать changes.csv
```bash
curl -s -H "Authorization: token [ТВОЙ_ТОКЕН]" \
  "https://raw.githubusercontent.com/burkovpavel094-jpg/KIMChenIlim/main/changes.csv" \
  -o changes.csv
```

### Скачать задачи.csv
```bash
curl -s -H "Authorization: token [ТВОЙ_ТОКЕН]" \
  "https://raw.githubusercontent.com/burkovpavel094-jpg/KIMChenIlim/main/%D0%B7%D0%B0%D0%B4%D0%B0%D1%87%D0%B8.csv" \
  -o задачи.csv
```

### Обновить changes.csv (поставить Да)
```bash
# 1. Получить SHA
SHA=$(curl -s -H "Authorization: token [ТВОЙ_ТОКЕН]" \
  "https://api.github.com/repos/burkovpavel094-jpg/KIMChenIlim/contents/changes.csv" \
  | jq -r '.sha')

# 2. Загрузить обновлённый файл
curl -s -X PUT \
  -H "Authorization: token [ТВОЙ_ТОКЕН]" \
  -H "Content-Type: application/json" \
  -d "{\"message\":\"Обработано\",\"content\":\"$(base64 -w 0 changes_updated.csv)\",\"sha\":\"$SHA\"}" \
  "https://api.github.com/repos/burkovpavel094-jpg/KIMChenIlim/contents/changes.csv"
```

---

## 🔄 Твой рабочий процесс

### С персоналом (changes.csv):
1. Скачай `changes.csv`
2. Найди строки с `Обработано = Нет`
3. Внеси изменения в `Персонал.xlsx` на ПК Павла (`C:\Users\Павел\Desktop\герместест`)
4. Обнови `changes.csv` — удали обработанные строки или поставь `Да`

### С задачами (задачи.csv):
1. Скачай `задачи.csv`
2. Найди строки с `Обработано = Нет`
3. Сохрани задачи в `текущие_задачи.csv` на ПК Павла
4. Обнови `задачи.csv` — поставь `Да` или удали обработанные

### С отпусками (планируемые_отпуска.csv):
- **Только читай!** Это справочник
- Используй для планирования — когда кто выходит/возвращается

---

## 📂 Куда сохранять на ПК Павла

| Что | Путь |
|-----|------|
| Персонал | `C:\Users\Павел\Desktop\герместест\Персонал.xlsx` |
| Задачи | `C:\Users\Павел\Desktop\герместест\текущие_задачи.csv` |

---

## 🆘 Если что-то не так

| Проблема | Решение |
|----------|---------|
| Ошибка 401 | Проверь токен или запроси новый у Павла |
| Файл не скачивается | Проверь интернет |
| Непонятная задача | Спроси Павла |
| ФИО не найдено в Excel | Поищи по части фамилии |

---

## 👥 Кто ещё работает в системе

| Участник | Роль |
|----------|------|
| **Павел** | Начальник, даёт задания в чат Кими |
| **Кими** | Записывает данные в файлы на GitHub |
| **Гермес (ты)** | Забираешь файлы, обновляешь Excel на ПК Павла |

---

## 📅 Последние изменения

- 2026-06-16 — Создан README для Гермеса

---

*Успешной работы!*
