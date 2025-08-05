
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

2. Установите и запустите Ollama

```bash
ollama run llama3

### 3. запустите приложение

```bash
streamlit run gui/streamlit_app.py

# стуктура проета
StudyBuddy_Assistant/
│
├── gui/
│   └── streamlit_app.py           # Веб-интерфейс (Streamlit)
│
├── core/
│   ├── rag_engine.py              # Логика RAG-поиска
│   ├── pedagogy.py                # Педагогические подсказки
│
├── llm/
│   ├── ollama_client.py           # Клиент для Ollama (LLM)
│   ├── answer_generator.py        # Генерация ответа с LLM
│   └── quiz_generator.py         # Генерация квизов
│
├── vector_db/
│   ├── faiss_interface.py         # Работа с FAISS
│   └── embedding_model.py         # Получение эмбеддингов (через Ollama)
│
├── data_ingestion/
│   ├── pdf_loader.py              # Извлечение текста из PDF
│   ├── docx_loader.py             # Извлечение текста из DOCX
│   ├── preprocessor.py            # Очистка текста
│   └── splitter.py                # Разделение текста на чанки
│
├── ethics/
│   └── user_feedback.py           # Сбор обратной связи
│
├── config.py                      # Конфигурация моделей
├── .env                           # Переменные окружения (OLLAMA_MODEL и т.д.)
├── requirements.txt               # Зависимости
└── README.md                      # Этот файл

### Файл .env:

OLLAMA_MODEL=llama3:latest
LLM_MODEL_ID=llama3
EMBEDDING_MODEL_ID=ollama/llama3
