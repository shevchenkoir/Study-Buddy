# 📘 StudyBuddy Assistant

**StudyBuddy** — интеллектуальный ассистент-тьютор на базе **LLM** и **RAG**, помогающий студентам осваивать учебный материал.

## 💡 Возможности
- 📖 **Отвечает** на вопросы по загруженному материалу.
- 🎓 Даёт **педагогические подсказки** вместо готовых решений.
- 📝 Генерирует **тренировочные квизы** по темам.
- 🖥 Работает **локально и офлайн** с использованием **Ollama** и **FAISS**.

---

## 🛠 Технологии
- **Python 3.12**
- **Streamlit** — веб-интерфейс.
- **Ollama** — локальный LLM сервер.
- **FAISS** — векторная база данных.
  
---

## 🚀 Быстрый старт

### 1️⃣ Установка зависимостей
```bash
pip install -r requirements.txt
```

### 2️⃣ Подготовка Ollama
Теперь **не нужно вручную запускать `ollama serve` и подгружать модели** — всё делает скрипт **`check_ollama_connection.py`**.

Запуск:
```bash
python check_ollama_connection.py
```

Скрипт:
- 🔍 Проверяет, запущен ли сервер Ollama, и при необходимости **автоматически его поднимает**.
- 📦 Проверяет наличие моделей:
  - Генеративная — `qwen2.5:1.5b-instruct`
  - Эмбеддинги — `nomic-embed-text`
- ⬇ При необходимости загружает модели (`ollama pull <model>`).
- 🧪 Делает тестовые запросы к API:
  - `/api/chat` — проверка генеративной модели.
  - `/api/embeddings` — проверка эмбеддингов.
- 🖥 (Опционально) открывает **отдельное окно** с интерактивной сессией:
  ```bash
  ollama run qwen2.5:1.5b-instruct
  ```
  Отключить можно, установив в файле:
  ```python
  AUTO_OPEN_INTERACTIVE_RUN = False
  ```

> 💡 Если Ollama ещё не установлена — скачайте её с [официального сайта](https://ollama.ai/).

---

### 3️⃣ Запуск приложения
После успешной проверки Ollama и моделей:
```bash
streamlit run gui/streamlit_app.py
```
Приложение откроется в браузере (по умолчанию — `http://localhost:8501`).

---

## 📂 Структура проекта

```text
StudyBuddy_Assistant/
├── 📁 app/                              # 🖥 Логика запуска
│   ├── 📄 main.py                       # 🚀 Основная точка входа
│   └── 📄 telegram_bot.py               # 🤖 Telegram-бот
├── 📁 assets/                           # 🖼 Статические ресурсы
├── 📁 core/                             # 🧠 Основная логика
│   ├── 📄 chat_context.py               # 💬 Контекст диалога
│   ├── 📄 pedagogy.py                   # 📚 Педагогические подсказки
│   ├── 📄 prompt_manager.py             # 📝 Управление промптами
│   └── 📄 rag_engine.py                 # 🔍 RAG-поиск
├── 📁 data_ingestion/                   # 📥 Загрузка данных
│   ├── 📄 docx_loader.py                # 📄 DOCX-загрузчик
│   ├── 📄 pdf_loader.py                 # 📑 PDF-загрузчик
│   ├── 📄 preprocessor.py               # 🧹 Очистка текста
│   └── 📄 splitter.py                   # ✂ Разделение на чанки
├── 📁 ethics/                           # ⚖ Этика
│   ├── 📄 solution_filter.py            # 🚫 Фильтрация
│   └── 📄 user_feedback.py              # 🗣 Обратная связь
├── 📁 gui/                              # 🖼 Интерфейс
│   ├── 📄 helpers_new_formats.py        # 🛠 Хелперы GUI
│   ├── 📄 session_manager.py            # 📂 Менеджер сессий
│   └── 📄 streamlit_app.py              # 🌐 Streamlit-приложение
├── 📁 llm/                              # 🤖 Работа с LLM
│   ├── 📄 answer_generator.py           # ✏ Генерация ответов
│   ├── 📄 ollama_client.py              # 🔌 API Ollama
│   └── 📄 quiz_generator.py             # 📝 Генератор тестов
├── 📁 Ollama/                           # 📦 Данные и модели Ollama
├── 📁 output/                           # 🔊 Вывод
│   └── 📄 speech_output.py              # 🗣 Синтез речи
├── 📁 uploaded_materials/               # 📤 Загруженные материалы
├── 📁 utils/                            # 🛠 Утилиты
│   ├── 📄 constants.py                  # 📌 Константы
│   ├── 📄 helpers.py                    # 🔧 Хелперы
│   ├── 📄 image_ocr.py                   # 🔍 OCR-распознавание
│   └── 📄 interface.py                  # 🔄 Интерфейс
├── 📁 vector_db/                        # 📊 Векторная база
│   ├── 📄 embedding_model.py            # 🧩 Модель эмбеддингов
│   └── 📄 faiss_interface.py            # 📈 Работа с FAISS
├── 📄 .env                              # ⚙ Переменные окружения
├── 📄 check_ollama_connection.py        # 🧪 Автопроверка Ollama и моделей
├── 📄 config.py                         # ⚙ Конфигурация
├── 📄 README.md                         # 📖 Документация
└── 📄 requirements.txt                  # 📦 Зависимости
```

---

## 📄 Файл `.env`
```ini
# Модель генерации ответов
OLLAMA_MODEL=qwen2.5:1.5b-instruct

# Модель эмбеддингов
OLLAMA_EMBED_MODEL=nomic-embed-text

# URL Ollama API
OLLAMA_BASE_URL=http://localhost:11434

# Скорость TTS (слов в минуту)
TTS_RATE=175
```

- **pyttsx3** — синтез речи.
- **dotenv** — управление переменными окружения.
