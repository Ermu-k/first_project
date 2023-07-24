# Шпаргалка по Git для начинающих
---
В данном файле содержится короткое описание информации котрую я изучил на курсе ["Основы работы с Git"](https://practicum.yandex.ru/git-basics/) на данный момент.

> *Кто хочет научиться летать, тот должен сперва научиться стоять, и*
> *ходить, и бегать, и лазить, и танцевать: нельзя сразу научиться* 
> *полету!* (c) Ф. Ницше

---
## Начало работы с Git (Локальный репозиторий)
Для начала установите систему контроля версий Git на ваше устройство.

### 1. Инициализация репозитория
Для инициализации репозитория нужо в папке с проектом (или в папке где этот проект будет) открыть терминал(командную строку) и выполнить команду:
```bash
git init
```

### 2. Удаление репозитория
Для удаления репозитория(фактически это скрытая папка с файлами git'а) нужно в папке с проектом отерыть терминал(командную строку) и выполнить команду:
```bash
rm -rf .git
```

### 3. Проверка состояния репозитория
Для проверки состояния репозитория нужно в папке с проектом отерыть терминал(командную строку) и выполнить команду:
```bash
git status 
```

### 4. Добавление отслеживаемых файлов
Для добавления файла в список отслеживаемых git'ом нужно в папке с проектом отерыть терминал(командную строку) и выполнить команду:
```bash
git add <название файла> (--all - все файлы в каталоге)
```

### 5. Сохранение изменений отслеживаемых файлов (комит)
Для того чтобы сохранить изменения в отслеживаемых файлах (сделать комит) нужно в папке с проектом отерыть терминал(командную строку) и выполнить команду:
```bash
git commit (-m 'строка описывающая изменения'/если без флага то откроется текстовый редактор) 
```

### 6. просмотр истории комитов
Для просмотра истории комитов нужно в папке с проектом отерыть терминал(командную строку) и выполнить команду:
```bash
git log
```

---
## Удаленный репозиторий 
Для работы в команде(когда над проектом одновременно могут работать несколько человек) или из разных мест удобно использовать удаленный репозиторий (можно сделать самому). Существуют несколько сервисов предоставляющих подобные услуги (GitHub, GitLab, GitFlic(russia), Gogs(china) и т.п.) Как правило большинство использует GitHub но впрниципе они все аналогичны друг другу. Для безопасной работы нужна крипторгафия ssh ключи.

### 1. Создание SSH пары ключей
В терминале нужно ввести команду для генерации ключей:
1. С использованием актуального алгоритма шифрования
```bash
ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт" 
```
2. На устаревших системах 
```bash
ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт" 
```

Далее потребуется следуйте инструкциям выводимым программой: предложат указать местоположение, имя ключей (можно оставить по умаолчанию) и кодовую фразу(passphrase) - фактически это небольшой пароль для использования ssh пары.

### 2. Привязываем SSH ключ к удаленному аккаунту(в данном случае GitHub)
1. В папке в которую сохранили пару ключей (по-умолчанию : ~/.ssh) находим файлы id_ed25519/id_rsa и id_ed25519.pub/id_rsa.pub (в зависимости от выбранного ранее алгоритма)
2. Копируем содержимое файла с расширением .pub в специализированное поле в своем аккаунте сервиса для удаленного репозитория

### 3. Привязывание уаленного репозитория к локальному
Открыв терминал в каталоге с проеком(локальным репозиторием) нужно ввести команду 
```bash
git remote add origin <ссылка на удаленный репозиторий>
git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
```
После этого можно проверить успешность операции командой:
```bash
git remote -v
```
Пример ответа на команду:
```bash
$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push) 
```

### 4. Синхронизирование локального и удаленного репозиториев
Открыв терминал в каталоге с проеком(локальным репозиторием) нужно ввести команду 
```bash
git push
```
### 5. Файл README.md
Как правило, в README.md проекта можно найти следующую информацию:
1. Название проекта и его краткое описание: кем создан, для чего, какие решает задачи и какие закрывает проблемы.
2. Технологии, которые применяются в проекте. В чём его отличие от аналогичных.
3. Документация проекта — подробная инструкция о том, что представляет собой проект.
4. Планы проекта, если они есть.

Информацию по синтаксису можно найти на в [шпаргалке на GitHub](https://gist.github.com/fomvasss/8dd8cd7f88c67a4e3727f9d39224a84c#code) или в [этом гайде](https://www.markdownguide.org/cheat-sheet/).