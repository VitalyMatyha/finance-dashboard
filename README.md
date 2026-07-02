# 💰 Finance Dashboard

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white)
![Alpha Vantage](https://img.shields.io/badge/Alpha_Vantage-API-brightgreen?style=flat)
![pytest](https://img.shields.io/badge/pytest-passing-brightgreen?style=flat&logo=pytest&logoColor=white)

> Инструмент для анализа личных финансов. Обрабатывает банковские транзакции из CSV, генерирует JSON-отчёты со статистикой по картам, курсами валют и ценами акций S&P500.

---

## 🚀 Возможности

- **Приветствие** в зависимости от времени суток
- **Статистика по картам** — расходы и кэшбэк за период
- **Топ-5 транзакций** по сумме платежа
- **Курсы валют** через Alpha Vantage API
- **Цены акций** из S&P500 через Alpha Vantage API
- **Инвесткопилка** — расчёт суммы для инвестирования
- **Поиск транзакций** с телефонными номерами в описании
- **Анализ кэшбэка** — выгодные категории для повышенного кэшбэка
- Логирование всех операций через стандартный модуль `logging`
- Покрытие **pytest + pytest-cov** тестами

---

## 🛠 Стек технологий

| Категория | Технологии |
|---|---|
| Язык | Python 3.8+ |
| Обработка данных | pandas |
| Внешние API | Alpha Vantage (курсы валют, акции S&P500) |
| Тестирование | pytest, pytest-cov |
| Зависимости | requests, python-dotenv |

---

## 📁 Структура проекта

```
finance-dashboard/
├── src/
│   ├── views.py           # Основная логика — generate_main_page_data()
│   ├── services.py        # Инвесткопилка, поиск телефонов, кэшбэк
│   └── reports.py         # Отчёты по тратам
├── tests/
│   ├── test_views.py      # Тесты: приветствие, статистика, моки API
│   ├── test_services.py   # Тесты: инвесткопилка, поиск, кэшбэк
│   └── test_reports.py    # Тесты: средние траты, фильтрация по дате
├── data/
│   └── operations.csv     # CSV с транзакциями пользователя
├── user_settings.json     # Настройки: валюты и акции для отслеживания
├── .env.example
└── requirements.txt
```

---

## ⚡ Быстрый старт

### 1. Клонировать репозиторий

```bash
git clone https://github.com/VitalyMatyha/finance-dashboard.git
cd finance-dashboard
```

### 2. Создать виртуальное окружение и установить зависимости

```bash
python -m venv .venv
.venv\Scripts\activate      # Windows
source .venv/bin/activate   # Linux/macOS

pip install -r requirements.txt
```

### 3. Создать файл `.env`

```env
API_KEY=your_alpha_vantage_api_key
```

> Получить бесплатный ключ: [alphavantage.co](https://www.alphavantage.co/support/#api-key)

### 4. Запустить

```python
from src.views import generate_main_page_data

data = generate_main_page_data("2024-12-20 14:30:00")
print(data)
```

---

## 📊 Формат JSON-ответа

```json
{
  "greeting": "Добрый день",
  "cards": [
    {
      "last_digits": "1234",
      "total_spent": 15234.50,
      "cashback": 152.34
    }
  ],
  "top_transactions": [
    {
      "date": "2024-12-15",
      "amount": 5000.00,
      "category": "Супермаркеты",
      "description": "Лента"
    }
  ],
  "currency_rates": [
    {"currency": "USD", "rate": 89.50},
    {"currency": "EUR", "rate": 97.20}
  ],
  "stock_prices": [
    {"stock": "AAPL", "price": 195.50},
    {"stock": "GOOGL", "price": 140.20}
  ]
}
```

---

## 🧪 Тестирование

```bash
# Запуск тестов
pytest tests/

# С отчётом о покрытии
pytest --cov=src --cov-report=html
```

Отчёт о покрытии открывается в `htmlcov/index.html`.

### Что покрыто тестами

| Файл | Что тестируется |
|---|---|
| `test_views.py` | Приветствие по времени, статистика по картам, моки API |
| `test_services.py` | Инвесткопилка, поиск телефонов, анализ кэшбэка |
| `test_reports.py` | Средние траты, фильтрация по дате, формат JSON |

---

## 👤 Автор

**Виталий Матюха** — [GitHub](https://github.com/VitalyMatyha) · [Telegram](https://t.me/vitalymj)
