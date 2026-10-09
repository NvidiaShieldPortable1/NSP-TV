[README.md](https://github.com/user-attachments/files/33263215/README.md)

#NSP TV = Nvidia Shield Portable / TV app

## 🇷🇺 Описание (Russian)

**NSP TV** — это бесплатный, лёгкий и оптимизированный Android TV клиент для воспроизведения IPTV каналов. Приложение специально разработано для работы на устройствах с ограниченными ресурсами, таких как NVIDIA Shield TV (Android 5.1).

### ✨ Особенности

- 🎬 **Воспроизведение IPTV** — поддержка HLS, DASH и других форматов
- 📺 **Оптимизация для Android TV** — интерфейс адаптирован для управления пультом
- ⚡ **Минимальное потребление памяти** — специально оптимизировано для NVIDIA Shield Portable/TV
- 🖼️ **Локальные иконки каналов** — все иконки хранятся локально, без загрузки из интернета
- 🎯 **Умное отображение иконок** — иконки загружаются только для видимых групп каналов (±2 группы)
- 🔊 **Звуковые эффекты** — тактильная обратная связь при навигации (click.mp3)
- 📋 **Поддержка плейлистов** — загрузка M3U/M3U8 плейлистов
- 🚀 **Быстрый буфер плеера** — 1.5s начальный буфер, 0.5s переключение каналов, 8s максимум

### 📱 Совместимость

| Устройство | Android | Статус |
|------------|---------|--------|
| NVIDIA Shield TV | 5.1 | ✅ Оптимизировано |
| Android TV Box | 5.0+ | ✅ Совместимо |
| Android TV | 5.0+ | ✅ Совместимо |

### 🛠️ Технологии

- **Kotlin** — основной язык программирования
- **Jetpack Compose** — современный UI фреймворк
- **Media3/ExoPlayer** — воспроизведение медиа
- **Coil** — загрузка и отображение изображений
- **Coroutines** — асинхронная обработка
- **ViewModel** — управление состоянием

### 📂 Структура проекта

```
TV/
├── tv/                           # Модуль Android TV
│   └── src/main/
│       ├── java/com/example/tv/
│       │   ├── MainActivity.kt           # Главный экран
│       │   ├── MainApplication.kt        # Инициализация приложения
│       │   ├── AppContainer.kt           # Dependency Injection
│       │   ├── data/
│       │   │   ├── EmbeddedChannels.kt   # Встроенные каналы
│       │   │   ├── model/
│       │   │   │   └── Channel.kt        # Модель канала
│       │   │   ├── repository/
│       │   │   │   └── PlaylistRepository.kt  # Загрузка плейлистов
│       │   │   └── parser/
│       │   │       └── M3UParser.kt      # Парсер M3U/M3U8
│       │   ├── ui/
│       │   │   ├── playlist/
│       │   │   │   ├── PlaylistScreen.kt        # Экран выбора плейлиста
│       │   │   │   ├── PlaylistViewModel.kt       # ViewModel плейлиста
│       │   │   │   └── components/
│       │   │   │       └── ChannelCard.kt       # Карточка канала
│       │   │   ├── player/
│       │   │   │   ├── PlayerScreen.kt          # Экран плеера
│       │   │   │   └── PlayerViewModel.kt       # ViewModel плеера
│       │   │   └── urlinput/
│       │   │       └── UrlInputScreen.kt        # Ввод URL плейлиста
│       │   └── utils/
│       │       └── SoundPoolManager.kt  # Менеджер звуков
│       └── assets/
│           ├── channels/               # JSON файлы каналов
│           │   ├── General.json
│           │   ├── News.json
│           │   ├── Sports.json
│           │   ├── Movies.json
│           │   └── ...
│           └── logos/                  # Иконки каналов
│               ├── channel1.png
│               └── ...
├── mobile/                           # Модуль Mobile (опционально)
├── gradle/                           # Gradle wrapper
├── build.gradle.kts                  # Конфигурация сборки
└── settings.gradle.kts               # Настройки проекта
```

### 🔧 Сборка проекта

#### Требования

- Android Studio Hedgehog или новее
- JDK 17+
- Android SDK 21+ (minSdk)
- Android SDK 34 (targetSdk)

#### Шаги сборки

1. **Клонируйте репозиторий**
   ```bash
   git clone https://github.com/yourusername/russian-iptv-player.git
   cd russian-iptv-player
   ```

2. **Откройте в Android Studio**
   - Запустите Android Studio
   - File → Open → выберите папку проекта
   - Дождитесь синхронизации Gradle

3. **Соберите приложение (Debug)**
   ```bash
   ./gradlew assembleDebug
   ```
   Или через Android Studio: Build → Make Project

4. **Соберите приложение (Release)**
   ```bash
   ./gradlew assembleRelease
   ```

### 📲 Установка на устройство

#### Через ADB

```bash
# Проверьте подключение устройства
adb devices

# Установите APK
adb install -r tv/build/outputs/apk/debug/tv-debug.apk

# Или для Release версии
adb install -r tv/build/outputs/apk/release/tv-release.apk
```

#### На NVIDIA Shield Portable / TV

1. Включите режим отладки на Shield Portable / TV
   - Settings → Device Preferences → About → нажмите Build Number 7 раз
2. Включите USB-отладку
   - Settings → Device Preferences → Developer Options → USB Debugging
3. Подключите Shield TV к компьютеру по USB или через сеть
4. Выполните команду `adb install`

### 🎮 Управление

| Кнопка на пульте | Действие |
|------------------|----------|
| ← → ↑ ↓ | Навигация по меню |
| OK / Enter | Выбор элемента |
| Back | Возврат назад |
| Play/Pause | Воспроизведение/Пауза |
| Stop | Остановка воспроизведения |
| Rewind/Fast Forward | Перемотка (если поддерживается) |

### ⚙️ Конфигурация

#### Добавление каналов

Каналы хранятся в формате JSON в папке `assets/channels/`:

```json
[
  {
    "name": "Канал 1",
    "url": "http://example.com/stream.m3u8",
    "logoUrl": "logos/channel1.png",
    "group": "General",
    "tvgId": "channel1.id",
    "language": "ru"
  }
]
```

**Поля:**
- `name` — название канала
- `url` — URL потока (M3U8, HLS, DASH)
- `logoUrl` — путь к иконке (относительный)
- `group` — группа каналов
- `tvgId` — идентификатор для EPG
- `language` — язык канала (опционально)

#### Звуковые эффекты

Звук клика при навигации хранится в `assets/click.mp3`:
- Громкость: 25% (0.25f)
- Формат: MP3
- Длительность: короткая

### 🚀 Оптимизация производительности

#### Для NVIDIA Shield Portable / TV (Android 5.1)

1. **Кэширование изображений**
   - LRU Cache: 4MB
   - Максимальный размер иконки: 256×256px
   - Формат: RGB_565 (2 байта на пиксель)

2. **Кэширование звука**
   - SoundPool: 1MB
   - Максимум потоков: 2
   - Громкость: 0.25f (25%)

3. **Буфер плеера**
   - Начальный буфер: 1.5 секунды
   - Переключение каналов: 0.5 секунды
   - Максимальный буфер: 8 секунд

4. **Умное отображение иконок**
   - Загружаются только для текущей ±2 групп
   - Экономия ~80% памяти при отображении
   - Placeholder с первой буквой для скрытых групп

5. **Очистка кэша при запуске**
   - Автоматическая очистка при старте приложения
   - Предотвращение утечек памяти

### 📊 Потребление ресурсов

| Ресурс | Значение |
|--------|----------|
| APK размер | ~30 MB |
| RAM (idle) | ~150 MB |
| RAM (плеер) | ~250 MB |
| Диск | ~50 MB (с иконками) |
| Кэш изображений | 4 MB |
| Кэш звука | 1 MB |

### 🐛 Известные проблемы

1. **SIGSEGV краши при скролле** — исправлено ограничением рендеринга иконок
2. **ANR при загрузке плейлистов** — исправлено загрузкой в фоновом потоке
3. **Задержка переключения каналов** — оптимизировано до 0.5 секунд

### 📝 Лог изменений

#### Версия 1.0.0 (2024)

- ✅ Базовый функционал IPTV плеера
- ✅ Оптимизация для NVIDIA Shield TV
- ✅ Умное отображение иконок каналов
- ✅ Локальные иконки без загрузки из интернета
- ✅ Звуковые эффекты навигации
- ✅ Поддержка M3U/M3U8 плейлистов

### 📄 Лицензия

MIT License — свободно для личного и коммерческого использования.

### 🤝 Вклад в проект

Pull Requests приветствуются! Пожалуйста:

1. Forkните репозиторий
2. Создайте ветку для фичи (`git checkout -b feature/AmazingFeature`)
3. Закоммитьте изменения (`git commit -m 'Add some AmazingFeature'`)
4. Pushните в ветку (`git push origin feature/AmazingFeature`)
5. Откройте Pull Request

### 📧 Контакты

- **Автор:** [Витяев Михаил Павлович]
- **Email:** [postavil.rakom.youtub@gmail.com]
- **GitHub:** [mihailvityaev] - [NvidiaShieldPortable1]

### 🙏 Благодарности

- NVIDIA — за Shield TV
- Команда Android
- Open Source сообщество

Протестировано на Nvidia Shield Portable

---

#NSP TV = Nvidia Shield Portable/TV app (Russian IPTV Player for Android TV)

## 🇬🇧 Description (English)

**NSP TV** is a free, lightweight and optimized Android TV client for playing IPTV channels. The application is specifically designed to work on devices with limited resources, such as NVIDIA Shield TV (Android 5.1).

### ✨ Features

- 🎬 **IPTV Playback** — supports HLS, DASH and other formats
- 📺 **Android TV Optimized** — interface adapted for remote control
- ⚡ **Minimal Memory Usage** — specifically optimized for NVIDIA Shield Portable/TV
- 🖼️ **Local Channel Icons** — all icons stored locally, no internet download
- 🎯 **Smart Icon Display** — icons loaded only for visible channel groups (±2 groups)
- 🔊 **Sound Effects** — tactile feedback during navigation (click.mp3)
- 📋 **Playlist Support** — load M3U/M3U8 playlists
- 🚀 **Fast Player Buffer** — 1.5s initial buffer, 0.5s channel switch, 8s max

### 📱 Compatibility

| Device | Android | Status |
|--------|---------|--------|
| NVIDIA Shield TV | 5.1 | ✅ Optimized |
| Android TV Box | 5.0+ | ✅ Compatible |
| Android TV | 5.0+ | ✅ Compatible |

### 🛠️ Technologies

- **Kotlin** — main programming language
- **Jetpack Compose** — modern UI framework
- **Media3/ExoPlayer** — media playback
- **Coil** — image loading and display
- **Coroutines** — asynchronous processing
- **ViewModel** — state management

### 📂 Project Structure

```
TV/
├── tv/                           # Android TV Module
│   └── src/main/
│       ├── java/com/example/tv/
│       │   ├── MainActivity.kt           # Main screen
│       │   ├── MainApplication.kt        # App initialization
│       │   ├── AppContainer.kt           # Dependency Injection
│       │   ├── data/
│       │   │   ├── EmbeddedChannels.kt   # Embedded channels
│       │   │   ├── model/
│       │   │   │   └── Channel.kt        # Channel model
│       │   │   ├── repository/
│       │   │   │   └── PlaylistRepository.kt  # Playlist loading
│       │   │   └── parser/
│       │   │       └── M3UParser.kt      # M3U/M3U8 parser
│       │   ├── ui/
│       │   │   ├── playlist/
│       │   │   │   ├── PlaylistScreen.kt        # Playlist selection screen
│       │   │   │   ├── PlaylistViewModel.kt       # Playlist ViewModel
│       │   │   │   └── components/
│       │   │   │       └── ChannelCard.kt       # Channel card component
│       │   │   ├── player/
│       │   │   │   ├── PlayerScreen.kt          # Player screen
│       │   │   │   └── PlayerViewModel.kt       # Player ViewModel
│       │   │   └── urlinput/
│       │   │       └── UrlInputScreen.kt        # URL input screen
│       │   └── utils/
│       │       └── SoundPoolManager.kt  # Sound manager
│       └── assets/
│           ├── channels/               # Channel JSON files
│           │   ├── General.json
│           │   ├── News.json
│           │   ├── Sports.json
│           │   ├── Movies.json
│           │   └── ...
│           └── logos/                  # Channel icons
│               ├── channel1.png
│               └── ...
├── mobile/                           # Mobile module (optional)
├── gradle/                           # Gradle wrapper
├── build.gradle.kts                  # Build configuration
└── settings.gradle.kts               # Project settings
```

### 🔧 Building the Project

#### Requirements

- Android Studio Hedgehog or newer
- JDK 17+
- Android SDK 21+ (minSdk)
- Android SDK 34 (targetSdk)

#### Build Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/russian-iptv-player.git
   cd russian-iptv-player
   ```

2. **Open in Android Studio**
   - Launch Android Studio
   - File → Open → select project folder
   - Wait for Gradle sync to complete

3. **Build Debug Version**
   ```bash
   ./gradlew assembleDebug
   ```
   Or via Android Studio: Build → Make Project

4. **Build Release Version**
   ```bash
   ./gradlew assembleRelease
   ```

### 📲 Installation on Device

#### Via ADB

```bash
# Check device connection
adb devices

# Install APK
adb install -r tv/build/outputs/apk/debug/tv-debug.apk

# Or for Release version
adb install -r tv/build/outputs/apk/release/tv-release.apk
```

#### On NVIDIA Shield Portable / TV

1. Enable debug mode on Shield Portable / TV
   - Settings → Device Preferences → About → click Build Number 7 times
2. Enable USB debugging
   - Settings → Device Preferences → Developer Options → USB Debugging
3. Connect Shield TV to computer via USB or network
4. Execute `adb install` command

### 🎮 Controls

| Remote Button | Action |
|---------------|--------|
| ← → ↑ ↓ | Menu navigation |
| OK / Enter | Select item |
| Back | Go back |
| Play/Pause | Play/Pause |
| Stop | Stop playback |
| Rewind/Fast Forward | Seek (if supported) |

### ⚙️ Configuration

#### Adding Channels

Channels are stored in JSON format in `assets/channels/`:

```json
[
  {
    "name": "Channel 1",
    "url": "http://example.com/stream.m3u8",
    "logoUrl": "logos/channel1.png",
    "group": "General",
    "tvgId": "channel1.id",
    "language": "ru"
  }
]
```

**Fields:**
- `name` — channel name
- `url` — stream URL (M3U8, HLS, DASH)
- `logoUrl` — icon path (relative)
- `group` — channel group
- `tvgId` — EPG identifier
- `language` — channel language (optional)

#### Sound Effects

Click sound during navigation stored in `assets/click.mp3`:
- Volume: 25% (0.25f)
- Format: MP3
- Duration: short

### 🚀 Performance Optimization

#### For NVIDIA Shield Portable / TV (Android 5.1)

1. **Image Caching**
   - LRU Cache: 4MB
   - Max icon size: 256×256px
   - Format: RGB_565 (2 bytes per pixel)

2. **Sound Caching**
   - SoundPool: 1MB
   - Max streams: 2
   - Volume: 0.25f (25%)

3. **Player Buffer**
   - Initial buffer: 1.5 seconds
   - Channel switch: 0.5 seconds
   - Max buffer: 8 seconds

4. **Smart Icon Display**
   - Loaded only for current ±2 groups
   - Saves ~80% memory when displaying
   - Placeholder with first letter for hidden groups

5. **Cache Clear on Launch**
   - Automatic cleanup on app start
   - Prevents memory leaks

### 📊 Resource Usage

| Resource | Value |
|----------|-------|
| APK Size | ~30 MB |
| RAM (idle) | ~150 MB |
| RAM (player) | ~250 MB |
| Disk | ~50 MB (with icons) |
| Image Cache | 4 MB |
| Sound Cache | 1 MB |

### 🐛 Known Issues

1. **SIGSEGV crashes on scroll** — fixed by limiting icon rendering
2. **ANR on playlist loading** — fixed by loading in background thread
3. **Channel switch delay** — optimized to 0.5 seconds

### 📝 Changelog

#### Version 1.0.0 (2024)

- ✅ Basic IPTV player functionality
- ✅ NVIDIA Shield TV optimization
- ✅ Smart channel icon display
- ✅ Local icons without internet download
- ✅ Navigation sound effects
- ✅ M3U/M3U8 playlist support

### 📄 License

MIT License — free for personal and commercial use.

### 🤝 Contributing

Pull Requests are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### 📧 Contact

- **Author:** [Vityaev Mikhail Pavlovich]
- **Email:** [postavil.rakom.youtub@gmail.com]
- **GitHub:** [mihailvityaev] - [NvidiaShieldPortable1]

### 🙏 Acknowledgments

- NVIDIA — for Shield TV
- Android Team
- Open Source Community

Tested on Nvidia Shield Portable
Write me message if you need same project for your region - EU, US, etc...
