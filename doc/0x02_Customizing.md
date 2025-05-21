## **Подробная настройка Git**  

### **1. Базовая конфигурация**  

Перед началом работы с Git необходимо задать **имя пользователя** и **email**, которые будут использоваться в истории коммитов. Эти данные привязываются к каждому вашему действию в репозитории и важны для идентификации автора изменений.  

#### **1.1 Установка имени пользователя**  

```bash
git config --global user.name "Иван Петров"
```  

- **Что делает:** Задаёт глобальное имя пользователя для всех репозиториев на этом компьютере.  
- **Где используется:** Отображается в логах (`git log`), на GitHub/GitLab и других платформах.  
- **Рекомендации:**  
  - Используйте реальное имя или узнаваемый никнейм.  
  - Если работаете в команде, имя должно позволять коллегам легко идентифицировать вас.  

#### **1.2 Установка email**  

```bash
git config --global user.email "ivan@example.com"
```  

- **Что делает:** Привязывает email к коммитам.  
- **Где используется:**  
  - В истории Git (`git log --pretty=format:'%h %an <%ae>'`).  
  - На GitHub/GitLab — email должен быть привязан к вашему аккаунту.  
- **Рекомендации:**  
  - Если работаете с **GitHub**, используйте email, привязанный к вашему профилю.  
  - Для рабочих проектов указывайте корпоративную почту.  
  - Если хотите скрыть email, используйте `noreply`-адрес GitHub (доступен в настройках профиля).  

#### **1.3 Проверка настроек**  

Чтобы убедиться, что данные введены правильно, выполните:  

```bash
git config --global --get user.name  # Проверит имя
git config --global --get user.email # Проверит email
```  

Или посмотрите все настройки:  

```bash
git config --list
```  

### **2. Дополнительные настройки (опционально, но рекомендуются)**  

#### **2.1 Выбор редактора по умолчанию**  

Git использует текстовый редактор для написания сообщений коммитов. Можно задать свой:  

```bash
git config --global core.editor "nano"  # Простой редактор (Linux/Mac)
git config --global core.editor "code --wait"  # VS Code
git config --global core.editor "notepad"  # Блокнот (Windows)
```  

- **Как проверить текущий редактор:**  
  ```bash
  git config --global --get core.editor
  ```  

#### **2.2 Настройка основной ветки (main вместо master)**  

Современные проекты используют `main` как ветку по умолчанию:  

```bash
git config --global init.defaultBranch "main"
```  

#### **2.3 Кэширование учётных данных (чтобы не вводить логин/пароль)**  

```bash
git config --global credential.helper cache  # Хранит пароль 15 минут
git config --global credential.helper "cache --timeout=3600"  # 1 час
```  
**Для Windows:** Лучше использовать встроенный менеджер:  
```bash
git config --global credential.helper wincred
```  

#### **2.4 Настройка переносов строк (CRLF vs LF)**  

Чтобы избежать проблем между Windows и Unix-системами:  

```bash
git config --global core.autocrlf true  # Windows
git config --global core.autocrlf input # Linux/Mac
```  

### **3. Где хранятся настройки?**  

- **Глобальные** (`--global`) → Файл `~/.gitconfig` (или `C:\Users\ВашеИмя\.gitconfig`).  
- **Локальные** (`--local`) → `.git/config` в папке проекта.  

Чтобы отредактировать файл вручную:  

```bash
nano ~/.gitconfig  # Linux/Mac
notepad C:\Users\ВашеИмя\.gitconfig  # Windows
```  

### **4. Пример полной настройки для разработчика**  

```bash
# Устанавливаем имя и email
git config --global user.name "Иван Петров"
git config --global user.email "ivan@example.com"

# Настройка редактора (VS Code)
git config --global core.editor "code --wait"

# Основная ветка — main
git config --global init.defaultBranch "main"

# Кэшировать пароль на 1 час
git config --global credential.helper "cache --timeout=3600"

# Цветной вывод в терминале
git config --global color.ui true

# Создаём алиасы для удобства
git config --global alias.st "status -s"
git config --global alias.co "checkout"
```  

После этого Git полностью готов к работе!
