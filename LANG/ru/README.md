---
layout: default
title: "Podfile"
---

<div align="center">
    <img src="../../IMAGES/image_sample_devices.png" alt="AppDimens - Адаптивный дизайн на всех устройствах" height="300"/>
    <h1>📐 AppDimens</h1>
    <p><strong>Умное и адаптивное масштабирование для Android и iOS</strong></p>
    <p>Математически точное адаптивное масштабирование, которое гарантирует идеальную адаптацию вашего UI-дизайна к любому размеру экрана или соотношению сторон — от телефонов до телевизоров, автомобилей и носимых устройств.</p>

[![Версия](https://img.shields.io/badge/version-1.0.8-blue.svg)](https://github.com/bodenberg/appdimens/releases)
[![Лицензия](https://img.shields.io/badge/license-Apache%202.0-green.svg)](LICENSE)
[![Платформа](https://img.shields.io/badge/platform-Android%20%7C%20iOS-orange.svg)](https://github.com/bodenberg/appdimens)
[![Документация](https://img.shields.io/badge/docs-complete-brightgreen.svg)](https://appdimens-project.web.app/)
</div>

> Языки: [English](../../README.md) | [Português (BR)](../pt-BR/README.md) | [Español](../es/README.md) | [हिन्दी](../hi/README.md) | [中文](../zh/README.md) | [日本語](../ja/README.md)

---

## 🎯 Что такое AppDimens?

**AppDimens** — это комплексная система масштабирования, которая заменяет фиксированные значения пикселей на интеллектуально масштабируемые размеры на основе реальных характеристик экрана. В то время как традиционные DP/Points являются константами, AppDimens рассматривает их как базовые значения, которые предсказуемо масштабируются на разных размерах экрана, плотностях и соотношениях сторон.

### 🎨 Основные преимущества

- **🎯 Визуальная согласованность**: Поддерживайте идеальные пропорции на всех типах устройств
- **📱 Универсальная совместимость**: Безупречно работает на телефонах, планшетах, телевизорах, автомобилях и носимых устройствах
- **⚡ Оптимизация производительности**: Минимальные накладные расходы во время выполнения с кэшированными вычислениями
- **🔧 Простая интеграция**: Простой API, который работает с Jetpack Compose, XML Views, SwiftUI и UIKit
- **📐 Математическая точность**: Две модели масштабирования - **Fixed (РЕКОМЕНДУЕТСЯ)** для большинства случаев и Dynamic для специфических нужд

---

## 🚀 Быстрый старт

### Android

```kotlin
dependencies {
    // Основная библиотека (Dynamic + Fixed scaling)
    implementation("io.github.bodenberg:appdimens-dynamic:1.0.8")
    
    // Опционально: SDP и SSP scaling
    implementation("io.github.bodenberg:appdimens-sdps:1.0.8")
    implementation("io.github.bodenberg:appdimens-ssps:1.0.8")
    
    // Полный пакет (не включает модуль игр)
    implementation("io.github.bodenberg:appdimens-all:1.0.8")
    
    // Разработка игр с поддержкой C++/NDK (отдельная зависимость)
    implementation("io.github.bodenberg:appdimens-games:1.0.8")
}
```

### iOS

```ruby
# Podfile
pod 'AppDimens'
```

```swift
// Swift Package Manager
.package(url: "https://github.com/bodenberg/appdimens.git", from: "1.0.8")
```

---

## 🧠 Основные модели размеров

| Модель | Философия | Идеальный случай использования | Поддерживаемые платформы | Реализация |
|-------|------------|----------------|-------------------|----------------|
| **Fixed (FX)** | Логарифмическое масштабирование (утонченное) | Кнопки, отступы, поля, иконки | Android + iOS | Математическая пропорциональная корректировка |
| **Dynamic (DY)** | Пропорциональное масштабирование (агрессивное) | Контейнеры, сетки, плавные шрифты | Android + iOS | Пропорциональное масштабирование на основе экрана |
| **SDP / SSP** | Предварительно рассчитанные ресурсы | Прямое использование `@dimen` в XML | Android | 426+ предварительно сгенерированных файлов размеров |
| **Физические единицы** | mm/cm/inch → Dp/Sp/Px/Points | Носимые устройства, печать, точные макеты | Android + iOS | Преобразование реальных измерений |
| **Игровые размеры** | Специализированное масштабирование для игр | Игровой UI, вьюпорт, Metal/OpenGL | Android + iOS | Нативная реализация C++/NDK + Metal |

---

## 📱 Примеры для платформ

### 🤖 Android - Jetpack Compose

```kotlin
@Composable
fun ResponsiveCard() {
    Card(
        modifier = Modifier
            .width(300.dydp)           // Динамическая ширина
            .height(200.fxdp)          // Фиксированная высота
            .padding(16.fxdp)          // Фиксированный отступ
    ) {
        Column(
            modifier = Modifier.padding(16.fxdp)
        ) {
            Text(
                text = "Адаптивный заголовок",
                fontSize = 18.fxsp     // Фиксированный размер шрифта
            )
            Text(
                text = "Эта карточка адаптируется к любому размеру экрана",
                fontSize = 14.dysp     // Динамический размер шрифта
            )
        }
    }
}
```

### 🍎 iOS - SwiftUI

```swift
struct ResponsiveCard: View {
    var body: some View {
        VStack(alignment: .leading, spacing: 12.fxpt) {
            Text("Адаптивный заголовок")
                .font(.fxSystem(size: 18, weight: .semibold))
            
            Text("Эта карточка адаптируется к любому размеру экрана")
                .font(.fxSystem(size: 14))
                .foregroundColor(.secondary)
        }
        .fxPadding(16)
        .dyFrame(width: 300)           // Динамическая ширина
        .fxFrame(height: 200)          // Фиксированная высота
        .background(Color(.systemGray6))
        .fxCornerRadius(12)
    }
}
```

### 📄 Android - XML Views

```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    android:padding="@dimen/_16sdp">
    
    <TextView
        android:layout_width="@dimen/_300sdp"
        android:layout_height="wrap_content"
        android:textSize="@dimen/_18ssp"
        android:text="Адаптивный текст" />
        
    <Button
        android:layout_width="@dimen/_120sdp"
        android:layout_height="@dimen/_48sdp"
        android:text="Действие" />
</LinearLayout>
```

---

## 🎨 Расширенные возможности

### 🔄 Условное масштабирование

```kotlin
// Android
val buttonSize = 80.scaledDp()
    .screen(UiModeType.WATCH, DpQualifier.SMALL_WIDTH, 200, 40.dp)
    .screen(UiModeType.CAR, 120.dp)
    .screen(DpQualifier.SMALL_WIDTH, 720, 150)
```

```swift
// iOS
let buttonSize = AppDimens.fixed(80)
    .screen(.watch, 40)           // 40pt для Apple Watch
    .screen(.tablet, 120)         // 120pt для iPad
    .aspectRatio(enable: true)    // Включить корректировку соотношения сторон
    .toPoints()
```

### 📏 Физические единицы

```kotlin
// Android
val marginPx = AppDimensPhysicalUnits.toMm(5f, resources)
view.setPadding(marginPx.toInt(), 0, 0, 0)
```

```swift
// iOS
Rectangle()
    .frame(width: 2.cm, height: 1.cm)  // Физические единицы
```

### 🧮 Утилиты макета

```kotlin
// Android - Вычислить оптимальное количество столбцов сетки
val spanCount = AppDimens.calculateAvailableItemCount(
    containerSizePx = recyclerView.width,
    itemSizeDp = 100f,
    itemMarginDp = 8f,
    resources = resources
)
```

---

## 📊 Производительность и совместимость

### ⚡ Характеристики производительности

| Функция | Накладные расходы во время выполнения | Использование памяти | Время вычисления |
|---------|------------------|--------------|------------------|
| **Fixed/Dynamic** | ~0.001ms | ~50KB | Кэш на конфигурацию |
| **SDP/SSP** | Ноль | ~2MB (ресурсы) | Предварительно рассчитано |
| **Физические единицы** | ~0.002ms | ~10KB | По требованию |

### 📱 Поддержка платформ

| Платформа | Минимальная версия | UI фреймворки | Специальные возможности |
|----------|-------------|---------------|------------------|
| **Android** | API 21+ | Compose, Views, Data Binding | SDP/SSP, Физические единицы |
| **iOS** | 13.0+ | SwiftUI, UIKit | Нативные расширения |

---

## 📚 Документация и ресурсы

### 📖 Полная документация

- **[📘 Полная документация](https://appdimens-project.web.app/)** - Подробные руководства и справочник API
- **[🤖 Руководство по Android](../../Android/README.md)** - Документация для Android
- **[🍎 Руководство по iOS](../../iOS/README.md)** - Документация для iOS
- **[🎮 Модуль игр](../../Android/appdimens_games/README.md)** - Разработка игр с C++/NDK

### 🎯 Быстрые ссылки

- **[🚀 Руководство по установке](../../Android/README.md#installation)** - Начните за минуты
- **[📱 Примеры](../../Android/app/src/main/kotlin/)** - Примеры использования в реальном мире
- **[🔧 Справочник API](../../Android/DOCS/)** - Полная документация API
- **[❓ FAQ](https://appdimens-project.web.app/faq)** - Часто задаваемые вопросы и ответы

---

## 🎯 Варианты использования

### 📱 Мобильные приложения
Идеально подходит для приложений, которые должны работать на разных размерах телефонов и ориентациях.

### 📺 Приложения для ТВ и автомобилей
Идеально для приложений Android TV и Android Auto с различными размерами экранов.

### ⌚ Приложения для носимых устройств
Необходимо для приложений Wear OS, которые должны адаптироваться к разным размерам часов.

### 🎮 Разработка игр
Специализированный модуль для разработки игр с поддержкой C++/NDK и интеграцией OpenGL.

### 🏢 Корпоративные приложения
Отлично подходит для бизнес-приложений, которые должны работать на планшетах, телефонах и настольных компьютерах.

---

## 🤝 Вклад в проект

Мы приветствуем вклад! Пожалуйста, ознакомьтесь с нашими [Руководством по внесению вклада](CONTRIBUTING.md) для получения подробной информации.

### 🐛 Нашли ошибку?
- [Создайте issue](https://github.com/bodenberg/appdimens/issues)
- Включите информацию об устройстве и шаги воспроизведения
- Приложите скриншоты, если применимо

### 💡 Есть идея?
- [Начните обсуждение](https://github.com/bodenberg/appdimens/discussions)
- Предложите новые функции или улучшения
- Поделитесь своими вариантами использования

---

## 📄 Лицензия

Этот проект лицензирован под лицензией Apache License 2.0 - см. файл [LICENSE](../../LICENSE) для подробностей.

---

## 👨‍💻 Автор

**Jean Bodenberg**
- 🌐 [GitHub](https://github.com/bodenberg)

---

## 🌟 Покажите свою поддержку

Если AppDimens помог вашему проекту, пожалуйста, рассмотрите:

- ⭐ **Поставить звезду** этому репозиторию
- 🐦 **Поделиться** в социальных сетях
- 📝 **Написать** отзыв или пост в блоге
- 🤝 **Внести вклад** кодом или документацией

---

<div align="center">
    <p><strong>Сделано с ❤️ для сообщества мобильной разработки</strong></p>
    <p>AppDimens - Где адаптивный дизайн встречается с математической точностью</p>
</div>
