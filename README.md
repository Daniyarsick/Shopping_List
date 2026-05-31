# Shopping List

Android-приложение для ведения списка покупок. Проект написан на Kotlin и показывает базовую архитектуру мобильного приложения: отдельный доменный слой, репозиторий, ViewModel, RecyclerView-список, Material Design-интерфейс и экраны добавления/редактирования товара.

## Кратко о проекте

Shopping List помогает хранить список товаров, отмечать позиции как активные или неактивные, добавлять новые товары, редактировать существующие и удалять элементы свайпом. Приложение подходит для демонстрации базовых навыков Android-разработки на Kotlin и работы с Android Jetpack-компонентами.

## Возможности

- Просмотр списка покупок в `RecyclerView` с Material-карточками.
- Добавление товара с названием и количеством.
- Редактирование существующего товара.
- Удаление товара свайпом влево или вправо.
- Переключение состояния товара долгим нажатием.
- Валидация полей ввода.
- Поддержка одноэкранного и двухпанельного режима через `Activity` и `Fragment`.
- Material toolbar, FloatingActionButton, outlined input-поля и MaterialButton.

## Технологии

- Kotlin
- Android SDK
- AndroidX AppCompat
- AndroidX Lifecycle ViewModel
- LiveData
- RecyclerView
- DiffUtil
- Material Components
- ConstraintLayout
- Gradle

## Архитектура

Проект разделен на три основных слоя:

```text
app/src/main/java/com/sumin/shoppinglist
├── data
│   └── ShopListRepositoryImpl.kt
├── domain
│   ├── AddShopItemUseCase.kt
│   ├── DeleteShopItemUseCase.kt
│   ├── EditShopItemUseCase.kt
│   ├── GetShopItemUseCase.kt
│   ├── GetShopListUseCase.kt
│   ├── ShopItem.kt
│   └── ShopListRepository.kt
└── presentation
    ├── MainActivity.kt
    ├── MainViewModel.kt
    ├── ShopItemActivity.kt
    ├── ShopItemFragment.kt
    ├── ShopItemViewModel.kt
    ├── ShopListAdapter.kt
    └── ShopItemViewHolder.kt
```

### Domain

Содержит бизнес-сущность `ShopItem`, интерфейс репозитория и use case-классы для основных действий: добавление, удаление, редактирование и получение товаров.

### Data

Содержит реализацию репозитория `ShopListRepositoryImpl`. Сейчас данные хранятся в памяти приложения через `MutableLiveData` и коллекцию `SortedSet`. Это удобно для учебного проекта и демонстрации архитектуры без подключения базы данных.

### Presentation

Содержит UI-логику: активности, фрагмент редактирования, ViewModel, адаптер списка и DiffUtil callbacks. `MainViewModel` управляет списком, а `ShopItemViewModel` отвечает за добавление, редактирование и валидацию данных.

## Основной пользовательский сценарий

1. Пользователь открывает приложение и видит список покупок.
2. Нажимает кнопку добавления.
3. Вводит название товара и количество.
4. Сохраняет товар.
5. Может открыть товар для редактирования, удалить его свайпом или изменить состояние долгим нажатием.

## Интерфейс

В актуальной версии интерфейс обновлен под Material Design:

- зеленая primary-палитра для верхней панели;
- желтая FloatingActionButton-кнопка добавления;
- светлый фон экрана;
- карточки покупок с бейджем количества;
- приглушенное состояние для уже отмеченных товаров;
- форма добавления/редактирования с outlined-полями.

## Сборка проекта

Требования:

- Android Studio или Android SDK
- JDK 17
- Gradle Wrapper из репозитория

Команда для сборки debug APK:

```bash
./gradlew assembleDebug
```

На Windows:

```powershell
.\gradlew.bat assembleDebug
```

После успешной сборки APK будет находиться здесь:

```text
app/build/outputs/apk/debug/app-debug.apk
```

## Скачать APK

Готовый debug APK для установки на устройство или эмулятор:

```text
downloads/shopping-list-material-debug.apk
```

Дополнительно сохранена совместимая копия:

```text
downloads/shopping-list-debug.apk
```

Если репозиторий открыт на GitHub, APK можно скачать из папки `downloads`.

## Установка APK

Если Android SDK добавлен в `PATH`, APK можно установить на подключенное устройство или эмулятор:

```bash
adb install app/build/outputs/apk/debug/app-debug.apk
```

## Что можно улучшить

- Добавить постоянное хранение данных через Room.
- Добавить Dependency Injection.
- Перевести UI на Jetpack Compose.
- Добавить unit-тесты для use case-классов.
- Добавить инструментальные тесты для пользовательских сценариев.

## Статус

Учебный Android-проект для портфолио. Основная цель проекта - показать Kotlin, работу со списками, ViewModel, LiveData, фрагментами и разделение приложения на слои.
