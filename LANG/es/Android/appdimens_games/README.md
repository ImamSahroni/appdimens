<div align="center">
    <h1>🎮 AppDimens Games</h1>
    <p><strong>Desarrollo de juegos responsivo para Android con C++/NDK</strong></p>
    <p>Módulo especializado con OpenGL ES, gestión de viewport y cálculos de dimensiones para juegos.</p>

[![Versión](https://img.shields.io/badge/version-1.0.6-blue.svg)](https://github.com/bodenberg/appdimens/releases)
[![Licencia](https://img.shields.io/badge/license-Apache%202.0-green.svg)](../../../LICENSE)
[![Plataforma](https://img.shields.io/badge/platform-Android%2023+-orange.svg)](https://developer.android.com/)
[![NDK](https://img.shields.io/badge/NDK-r21+-green.svg)](https://developer.android.com/ndk)
</div>

> Idiomas: [English](../../../../Android/appdimens_games/README.md) | [Português (BR)](../../pt-BR/Android/appdimens_games/README.md) | [हिन्दी](../../hi/Android/appdimens_games/README.md) | [Русский](../../ru/Android/appdimens_games/README.md) | [中文](../../zh/Android/appdimens_games/README.md) | [日本語](../../ja/Android/appdimens_games/README.md)

---

## 🎯 Descripción General
- Cálculos para UI de juego, mundo del juego y overlays
- Integración C++/NDK y utilidades OpenGL ES
- Gestión de viewport y monitor de rendimiento

## 🚀 Instalación
```kotlin
dependencies { implementation("io.github.bodenberg:appdimens-games:1.0.6") }
```

## 🎨 Uso (Kotlin)
```kotlin
val button = appDimensGames.calculateButtonSize(48f)
val player = appDimensGames.calculatePlayerSize(64f)
```

## 🧩 C++ (NDK)
```cpp
float size = appDimensGames.calculateDimension(48.0f, GameDimensionType::FIXED);
```

## 📚 Referencias
- Documentación: `Android/DOCS/`
- Licencia: `LICENSE`
