# 📘 StudyBuddy Assistant

**StudyBuddy** — интеллектуальный ассистент-тьютор на базе LLM и RAG, помогающий студентам осваивать учебный материал. Он может:

- Отвечать на вопросы по загруженному материалу
- Давать педагогические подсказки (вместо готовых решений)
- Генерировать тренировочные квизы по темам
- Работать локально, офлайн, с использованием Ollama 3.1 и FAISS

---

## 🚀 Бысткий старт

### 1. Установите зависимости

```bash
pip install -r requirements.txt

```
### 2. Установите и зарустите ollama

```bash
ollama run llama3.1

```
### 3. запустите приложение

```bash
streamlit run gui/streamlit_app.py

```

# 📂 Структура проекта
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
├── 📄 check_ollama_connection.py        # 🧪 Автопроверка Ollama
├── 📄 config.py                         # ⚙ Конфигурация
├── 📄 README.md                         # 📖 Документация
└── 📄 requirements.txt                  # 📦 Зависимости
```
### Файл .env:
```text
OLLAMA_MODEL=qwen2.5:1.5b-instruct
OLLAMA_EMBED_MODEL=nomic-embed-text
OLLAMA_BASE_URL=http://localhost:11434
```

