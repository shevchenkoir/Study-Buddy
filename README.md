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
ollama run llama3

```
### 3. запустите приложение

```bash
streamlit run gui/streamlit_app.py

```

# 📂 Структура проекта
```text
StudyBuddy_Assistant/
├── 📁 gui/
│   └── 📄 streamlit_app.py           # Веб-интерфейс (Streamlit)
├── 📁 core/
│   ├── 📄 rag_engine.py              # Логика RAG-поиска
│   └── 📄 pedagogy.py                # Педагогические подсказки
├── 📁 llm/
│   ├── 📄 ollama_client.py           # Клиент для Ollama
│   ├── 📄 answer_generator.py        # Генератор ответов
│   └── 📄 quiz_generator.py          # Генератор тестов
├── 📁 vector_db/
│   ├── 📄 faiss_interface.py         # Работа с FAISS
│   └── 📄 embedding_model.py         # Модель эмбеддингов
├── 📁 data_ingestion/
│   ├── 📄 pdf_loader.py              # Загрузчик PDF
│   ├── 📄 docx_loader.py             # Загрузчик DOCX
│   ├── 📄 preprocessor.py            # Препроцессинг текста
│   └── 📄 splitter.py                # Разделение на чанки
├── 📁 ethics/
│   └── 📄 user_feedback.py           # Обратная связь
├── 📄 config.py                      # Конфигурация
├── 📄 .env                           # Переменные окружения
├── 📄 requirements.txt               # Зависимости
└── 📄 README.md                      # Документация

### Файл .env:

OLLAMA_MODEL=llama3:latest
LLM_MODEL_ID=llama3
EMBEDDING_MODEL_ID=ollama/llama3



### в  терминале Windows PowerShell
 cd "C:\Users\irina\Downloads\Telegram Desktop\StudyBuddy_Assistant\StudyBuddy_Assistant"
 ollama run llama3.1
>>> Send a message (/? for help)
