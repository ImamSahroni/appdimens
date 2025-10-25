---
layout: default
title: "Podfile"
---

<div align="center">
    <img src="../../IMAGES/image_sample_devices.png" alt="AppDimens - सभी डिवाइसों पर रिस्पॉन्सिव डिज़ाइन" height="300"/>
    <h1>📐 AppDimens</h1>
    <p><strong>Android और iOS के लिए स्मार्ट और रिस्पॉन्सिव डाइमेंशनिंग</strong></p>
    <p>गणितीय रूप से रिस्पॉन्सिव स्केलिंग जो सुनिश्चित करती है कि आपका UI डिज़ाइन किसी भी स्क्रीन साइज़ या आस्पेक्ट रेशियो के लिए पूरी तरह से अनुकूल हो — फोन से लेकर TV, कार और वियरेबल्स तक।</p>

[![संस्करण](https://img.shields.io/badge/version-1.0.8-blue.svg)](https://github.com/bodenberg/appdimens/releases)
[![लाइसेंस](https://img.shields.io/badge/license-Apache%202.0-green.svg)](LICENSE)
[![प्लेटफॉर्म](https://img.shields.io/badge/platform-Android%20%7C%20iOS-orange.svg)](https://github.com/bodenberg/appdimens)
[![दस्तावेज़ीकरण](https://img.shields.io/badge/docs-complete-brightgreen.svg)](https://appdimens-project.web.app/)
</div>

> भाषाएँ: [English](../../README.md) | [Português (BR)](../pt-BR/README.md) | [Español](../es/README.md) | [Русский](../ru/README.md) | [中文](../zh/README.md) | [日本語](../ja/README.md)

---

## 🎯 AppDimens क्या है?

**AppDimens** एक व्यापक डाइमेंशनिंग सिस्टम है जो निश्चित पिक्सेल मानों को वास्तविक स्क्रीन विशेषताओं के आधार पर बुद्धिमानी से स्केल किए गए आयामों से बदल देता है। जबकि पारंपरिक DP/Points स्थिर होते हैं, AppDimens उन्हें आधार मानों के रूप में मानता है जो विभिन्न स्क्रीन साइज़, घनत्व और आस्पेक्ट रेशियो में अनुमानित रूप से स्केल होते हैं।

### 🎨 मुख्य लाभ

- **🎯 दृश्य स्थिरता**: सभी डिवाइस प्रकारों में पूर्ण अनुपात बनाए रखें
- **📱 सार्वभौमिक संगतता**: फोन, टैबलेट, TV, कार और वियरेबल्स पर निर्बाध रूप से काम करता है
- **⚡ प्रदर्शन अनुकूलित**: कैश की गई गणनाओं के साथ न्यूनतम रनटाइम ओवरहेड
- **🔧 आसान एकीकरण**: सरल API जो Jetpack Compose, XML Views, SwiftUI और UIKit के साथ काम करता है
- **📐 गणितीय सटीकता**: दो स्केलिंग मॉडल - **Fixed (अनुशंसित)** अधिकांश मामलों के लिए और Dynamic विशिष्ट आवश्यकताओं के लिए

---

## 🚀 त्वरित शुरुआत

### Android

```kotlin
dependencies {
    // मुख्य लाइब्रेरी (Dynamic + Fixed scaling)
    implementation("io.github.bodenberg:appdimens-dynamic:1.0.8")
    
    // वैकल्पिक: SDP और SSP scaling
    implementation("io.github.bodenberg:appdimens-sdps:1.0.8")
    implementation("io.github.bodenberg:appdimens-ssps:1.0.8")
    
    // सभी-इन-वन पैकेज (गेम्स मॉड्यूल शामिल नहीं)
    implementation("io.github.bodenberg:appdimens-all:1.0.8")
    
    // C++/NDK समर्थन के साथ गेम डेवलपमेंट (अलग निर्भरता)
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

## 🧠 मुख्य डाइमेंशन मॉडल

| मॉडल | दर्शन | आदर्श उपयोग केस | समर्थित प्लेटफॉर्म | कार्यान्वयन |
|-------|------------|----------------|-------------------|----------------|
| **Fixed (FX)** | लॉगरिदमिक स्केलिंग (परिष्कृत) | बटन, पैडिंग, मार्जिन, आइकन | Android + iOS | गणितीय अनुपात समायोजन |
| **Dynamic (DY)** | आनुपातिक स्केलिंग (आक्रामक) | कंटेनर, ग्रिड, फ्लूइड फॉन्ट | Android + iOS | स्क्रीन-आधारित आनुपातिक स्केलिंग |
| **SDP / SSP** | पूर्व-गणना किए गए संसाधन | XML में सीधे `@dimen` उपयोग | Android | 426+ पूर्व-जेनरेटेड डाइमेंशन फाइलें |
| **भौतिक इकाइयाँ** | mm/cm/inch → Dp/Sp/Px/Points | वियरेबल्स, प्रिंटिंग, सटीक लेआउट | Android + iOS | वास्तविक दुनिया के माप का रूपांतरण |
| **गेम डाइमेंशन** | गेम-विशिष्ट स्केलिंग | गेम UI, व्यूपोर्ट, Metal/OpenGL | Android + iOS | नेटिव C++/NDK + Metal कार्यान्वयन |

---

## 📱 प्लेटफॉर्म उदाहरण

### 🤖 Android - Jetpack Compose

```kotlin
@Composable
fun ResponsiveCard() {
    Card(
        modifier = Modifier
            .width(300.dydp)           // डायनामिक चौड़ाई
            .height(200.fxdp)          // निश्चित ऊंचाई
            .padding(16.fxdp)          // निश्चित पैडिंग
    ) {
        Column(
            modifier = Modifier.padding(16.fxdp)
        ) {
            Text(
                text = "रिस्पॉन्सिव शीर्षक",
                fontSize = 18.fxsp     // निश्चित फ़ॉन्ट साइज़
            )
            Text(
                text = "यह कार्ड किसी भी स्क्रीन साइज़ के अनुकूल होता है",
                fontSize = 14.dysp     // डायनामिक फ़ॉन्ट साइज़
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
            Text("रिस्पॉन्सिव शीर्षक")
                .font(.fxSystem(size: 18, weight: .semibold))
            
            Text("यह कार्ड किसी भी स्क्रीन साइज़ के अनुकूल होता है")
                .font(.fxSystem(size: 14))
                .foregroundColor(.secondary)
        }
        .fxPadding(16)
        .dyFrame(width: 300)           // डायनामिक चौड़ाई
        .fxFrame(height: 200)          // निश्चित ऊंचाई
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
        android:text="रिस्पॉन्सिव टेक्स्ट" />
        
    <Button
        android:layout_width="@dimen/_120sdp"
        android:layout_height="@dimen/_48sdp"
        android:text="क्रिया" />
</LinearLayout>
```

---

## 🎨 उन्नत सुविधाएँ

### 🔄 सशर्त स्केलिंग

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
    .screen(.watch, 40)           // Apple Watch के लिए 40pt
    .screen(.tablet, 120)         // iPad के लिए 120pt
    .aspectRatio(enable: true)    // आस्पेक्ट रेशियो समायोजन सक्षम करें
    .toPoints()
```

### 📏 भौतिक इकाइयाँ

```kotlin
// Android
val marginPx = AppDimensPhysicalUnits.toMm(5f, resources)
view.setPadding(marginPx.toInt(), 0, 0, 0)
```

```swift
// iOS
Rectangle()
    .frame(width: 2.cm, height: 1.cm)  // भौतिक इकाइयाँ
```

### 🧮 लेआउट उपयोगिताएँ

```kotlin
// Android - इष्टतम ग्रिड कॉलम की गणना करें
val spanCount = AppDimens.calculateAvailableItemCount(
    containerSizePx = recyclerView.width,
    itemSizeDp = 100f,
    itemMarginDp = 8f,
    resources = resources
)
```

---

## 📊 प्रदर्शन और संगतता

### ⚡ प्रदर्शन विशेषताएँ

| सुविधा | रनटाइम ओवरहेड | मेमोरी उपयोग | गणना समय |
|---------|------------------|--------------|------------------|
| **Fixed/Dynamic** | ~0.001ms | ~50KB | कॉन्फ़िगरेशन के अनुसार कैश | 
| **SDP/SSP** | शून्य | ~2MB (संसाधन) | पूर्व-गणना की गई |
| **भौतिक इकाइयाँ** | ~0.002ms | ~10KB | मांग पर |

### 📱 प्लेटफॉर्म समर्थन

| प्लेटफॉर्म | न्यूनतम संस्करण | UI फ्रेमवर्क | विशेष सुविधाएँ |
|----------|-------------|---------------|------------------|
| **Android** | API 21+ | Compose, Views, Data Binding | SDP/SSP, भौतिक इकाइयाँ |
| **iOS** | 13.0+ | SwiftUI, UIKit | मूल एक्सटेंशन |

---

## 📚 दस्तावेज़ीकरण और संसाधन

### 📖 पूर्ण दस्तावेज़ीकरण

- **[📘 पूर्ण दस्तावेज़ीकरण](https://appdimens-project.web.app/)** - व्यापक गाइड और API संदर्भ
- **[🤖 Android गाइड](../../Android/README.md)** - Android-विशिष्ट दस्तावेज़ीकरण
- **[🍎 iOS गाइड](../../iOS/README.md)** - iOS-विशिष्ट दस्तावेज़ीकरण
- **[🎮 गेम्स मॉड्यूल](../../Android/appdimens_games/README.md)** - C++/NDK के साथ गेम डेवलपमेंट

### 🎯 त्वरित लिंक

- **[🚀 इंस्टॉलेशन गाइड](../../Android/README.md#installation)** - मिनटों में शुरू करें
- **[📱 उदाहरण](../../Android/app/src/main/kotlin/)** - वास्तविक दुनिया के उपयोग उदाहरण
- **[🔧 API संदर्भ](../../Android/DOCS/)** - पूर्ण API दस्तावेज़ीकरण
- **[❓ FAQ](https://appdimens-project.web.app/faq)** - सामान्य प्रश्न और उत्तर

---

## 🎯 उपयोग के मामले

### 📱 मोबाइल ऐप्स
विभिन्न फोन साइज़ और ओरिएंटेशन में काम करने वाले ऐप्स के लिए बिल्कुल सही।

### 📺 TV और कार ऐप्स
विभिन्न स्क्रीन साइज़ वाले Android TV और Android Auto एप्लिकेशन के लिए आदर्श।

### ⌚ वियरेबल ऐप्स
Wear OS ऐप्स के लिए आवश्यक जिन्हें विभिन्न घड़ी साइज़ के अनुकूल होना चाहिए।

### 🎮 गेम डेवलपमेंट
C++/NDK समर्थन और OpenGL एकीकरण के साथ गेम डेवलपमेंट के लिए विशेष मॉड्यूल।

### 🏢 एंटरप्राइज़ ऐप्स
टैबलेट, फोन और डेस्कटॉप पर काम करने वाले व्यावसायिक एप्लिकेशन के लिए बढ़िया।

---

## 🤝 योगदान

हम योगदान का स्वागत करते हैं! कृपया विवरण के लिए हमारे [योगदान दिशानिर्देश](CONTRIBUTING.md) देखें।

### 🐛 बग मिला?
- [एक इश्यू बनाएं](https://github.com/bodenberg/appdimens/issues)
- डिवाइस जानकारी और पुनरुत्पादन चरण शामिल करें
- यदि लागू हो तो स्क्रीनशॉट संलग्न करें

### 💡 कोई विचार है?
- [चर्चा शुरू करें](https://github.com/bodenberg/appdimens/discussions)
- नई सुविधाओं या सुधारों का प्रस्ताव करें
- अपने उपयोग के मामले साझा करें

---

## 📄 लाइसेंस

यह प्रोजेक्ट Apache License 2.0 के तहत लाइसेंस प्राप्त है - विवरण के लिए [LICENSE](../../LICENSE) फ़ाइल देखें।

---

## 👨‍💻 लेखक

**Jean Bodenberg**
- 🌐 [GitHub](https://github.com/bodenberg)

---

## 🌟 अपना समर्थन दिखाएं

यदि AppDimens ने आपके प्रोजेक्ट में मदद की है, तो कृपया विचार करें:

- ⭐ इस रिपॉजिटरी को **स्टार** करना
- 🐦 सोशल मीडिया पर **साझा** करना
- 📝 एक समीक्षा या ब्लॉग पोस्ट **लिखना**
- 🤝 कोड या दस्तावेज़ीकरण में **योगदान** करना

---

<div align="center">
    <p><strong>मोबाइल डेवलपमेंट समुदाय के लिए ❤️ के साथ बनाया गया</strong></p>
    <p>AppDimens - जहाँ रिस्पॉन्सिव डिज़ाइन गणितीय सटीकता से मिलता है</p>
</div>
