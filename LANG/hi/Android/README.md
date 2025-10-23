<div align="center">
    <img src="../../IMAGES/image_sample_devices.png" alt="AppDimens Android - सभी डिवाइसों पर रिस्पॉन्सिव डिज़ाइन" height="250"/>
    <h1>📐 AppDimens Android</h1>
    <p><strong>Android के लिए स्मार्ट और रिस्पॉन्सिव डाइमेंशनिंग</strong></p>
    <p>गणितीय रूप से सटीक रिस्पॉन्सिव स्केलिंग जो आपके UI डिज़ाइन को किसी भी स्क्रीन साइज़ या आस्पेक्ट रेशियो में पूरी तरह अनुकूल बनाती है — फोन से लेकर TV, कार और वियरेबल्स तक।</p>

[![संस्करण](https://img.shields.io/badge/version-1.0.8-blue.svg)](https://github.com/bodenberg/appdimens/releases)
[![लाइसेंस](https://img.shields.io/badge/license-Apache%202.0-green.svg)](../../LICENSE)
[![प्लेटफॉर्म](https://img.shields.io/badge/platform-Android%2021+-orange.svg)](https://developer.android.com/)
[![दस्तावेज़ीकरण](https://img.shields.io/badge/docs-complete-brightgreen.svg)](https://appdimens-project.web.app/)
</div>

> भाषाएँ: [English](../../../Android/README.md) | [Português (BR)](../pt-BR/Android/README.md) | [Español](../es/Android/README.md) | [Русский](../ru/Android/README.md) | [中文](../zh/Android/README.md) | [日本語](../ja/Android/README.md)

---

## 🎯 AppDimens Android क्या है?

**AppDimens Android** एक व्यापक डाइमेंशनिंग सिस्टम है जो स्थिर DP मानों को वास्तविक स्क्रीन विशेषताओं के आधार पर स्मार्ट तरीके से स्केल की गई डाइमेंशन्स से बदल देता है। जबकि Android का डिफ़ॉल्ट DP (1 DP = 1/160 इंच) स्थिर है, AppDimens इसे एक बेस वैल्यू के रूप में मानता है जो विभिन्न स्क्रीन साइज़, डेंसिटीज़ और एस्पेक्ट रेशियो में पूर्वानुमानित रूप से स्केल करता है।

### 🎨 मुख्य लाभ

- **🎯 विजुअल कंसिस्टेंसी**: सभी Android डिवाइस प्रकारों में परफेक्ट अनुपात बनाए रखें
- **📱 यूनिवर्सल कंपैटिबिलिटी**: फोन, टैबलेट, TV, कार और वियरेबल्स पर बिना किसी समस्या के काम करता है
- **⚡ परफॉर्मेंस ऑप्टिमाइज़्ड**: कैश्ड कैलकुलेशन्स के साथ मिनिमल रनटाइम ओवरहेड
- **🔧 आसान इंटीग्रेशन**: Jetpack Compose, XML Views और Data Binding के साथ काम करने वाला सरल API
- **📐 मैथमेटिकल प्रिसिजन**: विभिन्न डिज़ाइन जरूरतों के लिए दो स्केलिंग मॉडल (Fixed & Dynamic)
- **🎮 गेम डेवलपमेंट**: हाई-परफॉर्मेंस गेम डेवलपमेंट के लिए विशेष C++/NDK मॉड्यूल
- **🚀 नेटिव परफॉर्मेंस**: गेम-स्पेसिफिक कैलकुलेशन्स और OpenGL इंटीग्रेशन के लिए C++ इम्प्लीमेंटेशन

---

## 🚀 इंस्टॉलेशन

### Gradle (Kotlin DSL)

```kotlin
dependencies {
    // मुख्य लाइब्रेरी (Dynamic + Fixed स्केलिंग)
    implementation("io.github.bodenberg:appdimens-dynamic:1.0.8")
    
    // वैकल्पिक: SDP & SSP स्केलिंग
    implementation("io.github.bodenberg:appdimens-sdps:1.0.8")
    implementation("io.github.bodenberg:appdimens-ssps:1.0.8")
    
    // ऑल-इन-वन पैकेज (गेम्स मॉड्यूल शामिल नहीं)
    implementation("io.github.bodenberg:appdimens-all:1.0.8")
    
    // C++/NDK सपोर्ट के साथ गेम डेवलपमेंट (अलग डिपेंडेंसी)
    implementation("io.github.bodenberg:appdimens-games:1.0.8")
}
```

### Gradle (Groovy)

```groovy
dependencies {
    implementation 'io.github.bodenberg:appdimens-dynamic:1.0.8'
    implementation 'io.github.bodenberg:appdimens-sdps:1.0.8'
    implementation 'io.github.bodenberg:appdimens-ssps:1.0.8'
    implementation 'io.github.bodenberg:appdimens-all:1.0.8'
    implementation 'io.github.bodenberg:appdimens-games:1.0.8'
}
```

---

## 🧠 कोर डाइमेंशन मॉडल्स

| मॉडल | फिलॉसफी | आइडियल यूज़ केस | सपोर्टेड इन |
|------|----------|------------------|-------------|
| **Fixed (FX)** | लॉगरिथमिक स्केलिंग (रिफाइंड) | बटन्स, पैडिंग्स, मार्जिन्स, आइकन्स | Compose + Views + Data Binding |
| **Dynamic (DY)** | प्रोपोर्शनल स्केलिंग (एग्रेसिव) | कंटेनर्स, ग्रिड्स, फ्लुइड फॉन्ट्स | Compose + Views + Data Binding |
| **SDP / SSP** | प्री-कैलकुलेटेड रिसोर्सेज़ | XML में डायरेक्ट `@dimen` यूज़ | Compose + Views (XML) |
| **फिजिकल यूनिट्स** | mm/cm/inch → Dp/Sp/Px | वियरेबल्स, प्रिंटिंग, प्रिसिजन लेआउट्स | Compose + Views |

---

## 🎨 यूज़ेज एक्साम्पल्स

### 🧩 Jetpack Compose

#### Fixed और Dynamic स्केलिंग

```kotlin
@Composable
fun ResponsiveCard() {
    Card(
        modifier = Modifier
            .width(300.dydp)           // डायनामिक चौड़ाई - स्क्रीन के अनुपात में
            .height(200.fxdp)          // फिक्स्ड ऊंचाई - रिफाइंड स्केलिंग
            .padding(16.fxdp)          // फिक्स्ड पैडिंग - कंसिस्टेंट फील
    ) {
        Column(
            modifier = Modifier.padding(16.fxdp)
        ) {
            Text(
                text = "रिस्पॉन्सिव टाइटल",
                fontSize = 18.fxsp     // फिक्स्ड फॉन्ट साइज़ - कंफर्टेबल रीडिंग
            )
            Text(
                text = "यह कार्ड किसी भी स्क्रीन साइज़ में एडैप्ट होता है",
                fontSize = 14.dysp     // डायनामिक फॉन्ट साइज़ - प्रोपोर्शनल
            )
        }
    }
}
```

### 📄 XML Views और Data Binding

#### Data Binding के साथ डायनामिक स्केलिंग

```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    app:dynamicWidthDp="@{100f}"
    app:dynamicHeightDp="@{56f}"
    app:dynamicTextSizeDp="@{20f}">
    
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="डायनामिक टेक्स्ट साइज़"
        app:dynamicTextSizeDp="@{18f}" />
</LinearLayout>
```

### 💻 Kotlin/Java कोड

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        // फिक्स्ड स्केलिंग - सूटल एडजस्टमेंट
        val fixedWidthPx = AppDimens.fixedPx(
            value = 200f,
            screenType = ScreenType.LOWEST,
            resources = resources
        ).toInt()
        
        // डायनामिक स्केलिंग - प्रोपोर्शनल एडजस्टमेंट
        val dynamicTextSizeSp = AppDimens.dynamicSp(
            value = 18f,
            screenType = ScreenType.LOWEST,
            resources = resources
        )
        
        // Views पर अप्लाई करें
        myView.layoutParams.width = fixedWidthPx
        myTextView.textSize = dynamicTextSizeSp
    }
}
```

---

## 📊 मॉड्यूल ओवरव्यू

### 🎯 कोर मॉड्यूल्स

| मॉड्यूल | डिस्क्रिप्शन | यूज़ केस |
|---------|-------------|----------|
| **appdimens-dynamic** | Fixed & Dynamic स्केलिंग के साथ कोर लाइब्रेरी | सभी रिस्पॉन्सिव ऐप्स के लिए जरूरी |
| **appdimens-sdps** | कंडीशनल लॉजिक के साथ SDP स्केलिंग | XML-बेस्ड रिस्पॉन्सिव डिज़ाइन |
| **appdimens-ssps** | कंडीशनल लॉजिक के साथ SSP स्केलिंग | रिस्पॉन्सिव टेक्स्ट साइज़िंग |
| **appdimens-all** | सभी मॉड्यूल्स के साथ कंप्लीट पैकेज (गेम्स को छोड़कर) | स्टैंडर्ड ऐप्स के लिए वन-स्टॉप सॉल्यूशन |
| **appdimens-games** | C++/NDK के साथ गेम डेवलपमेंट | Android गेम डेवलपमेंट |

---

## 📱 डिवाइस सपोर्ट

### 📱 सपोर्टेड डिवाइस टाइप्स

| डिवाइस टाइप | डिस्क्रिप्शन | स्केलिंग बिहेवियर |
|-------------|-------------|------------------|
| **Phone** | स्टैंडर्ड Android फोन्स | बैलेंस्ड स्केलिंग |
| **Tablet** | Android टैबलेट्स | बड़ी स्क्रीन्स के लिए एन्हांस्ड स्केलिंग |
| **TV** | Android TV डिवाइसेज़ | व्यूइंग डिस्टेंस के लिए ऑप्टिमाइज़्ड |
| **Car** | Android Auto | बड़े टच टार्गेट्स |
| **Watch** | Wear OS डिवाइसेज़ | कॉम्पैक्ट स्केलिंग |
| **VR** | VR हेडसेट्स | इमर्सिव स्केलिंग |

---

## ⚡ परफॉर्मेंस और ऑप्टिमाइज़ेशन

### 📊 परफॉर्मेंस कैरेक्टरिस्टिक्स

| फीचर | रनटाइम ओवरहेड | मेमोरी यूज़ | कैलकुलेशन टाइम |
|-------|----------------|-------------|-----------------|
| **Fixed/Dynamic** | ~0.001ms | ~50KB | कॉन्फिगरेशन प्रति कैश्ड |
| **SDP/SSP** | जीरो | ~2MB (रिसोर्सेज़) | प्री-कैलकुलेटेड |
| **फिजिकल यूनिट्स** | ~0.002ms | ~10KB | ऑन-डिमांड |

### 🚀 ऑप्टिमाइज़ेशन टिप्स

1. **डाइमेंशन्स कैश करें**: अक्सर यूज़ होने वाली डाइमेंशन्स को प्रॉपर्टीज़ में स्टोर करें
2. **अप्रोप्रिएट मॉडल यूज़ करें**: UI एलिमेंट्स के लिए Fixed, लेआउट्स के लिए Dynamic
3. **एक्सेसिव नेस्टिंग से बचें**: डाइमेंशन चेन्स को सिंपल रखें
4. **परफॉर्मेंस प्रोफाइल करें**: बिल्ट-इन परफॉर्मेंस मॉनिटरिंग यूज़ करें

---

## 📚 डॉक्यूमेंटेशन और रिसोर्सेज़

### 📖 कंप्लीट डॉक्यूमेंटेशन

- **[📘 फुल डॉक्यूमेंटेशन](https://appdimens-project.web.app/)** - कंप्रिहेंसिव गाइड्स और API रेफरेंस
- **[🎯 कोर डॉक्यूमेंटेशन](../../../Android/DOCS/)** - डिटेल्ड टेक्निकल डॉक्यूमेंटेशन
- **[🎮 गेम्स मॉड्यूल](../../../Android/appdimens_games/README.md)** - गेम डेवलपमेंट गाइड
- **[📱 एक्साम्पल्स](../../../Android/app/src/main/kotlin/)** - रियल-वर्ल्ड यूज़ेज एक्साम्पल्स

### 🔗 क्विक लिंक्स

- **[🚀 इंस्टॉलेशन गाइड](#इंस्टॉलेशन)** - मिनटों में शुरू करें
- **[📱 एक्साम्पल्स](#यूज़ेज-एक्साम्पल्स)** - रियल-वर्ल्ड यूज़ेज एक्साम्पल्स
- **[🔧 API रेफरेंस](../../../Android/DOCS/)** - कंप्लीट API डॉक्यूमेंटेशन
- **[❓ FAQ](https://appdimens-project.web.app/faq)** - कॉमन क्वेश्चन्स और आंसर्स

---

## 🤝 कंट्रिब्यूटिंग

हम कंट्रिब्यूशन्स का स्वागत करते हैं! डिटेल्स के लिए हमारे [कंट्रिब्यूटिंग गाइडलाइंस](../../CONTRIBUTING.md) देखें।

### 🐛 बग मिला?
- [इश्यू बनाएं](https://github.com/bodenberg/appdimens/issues)
- डिवाइस इनफॉर्मेशन और रिप्रोडक्शन स्टेप्स शामिल करें
- अगर लागू हो तो स्क्रीनशॉट्स अटैच करें

### 💡 कोई आइडिया है?
- [डिस्कशन शुरू करें](https://github.com/bodenberg/appdimens/discussions)
- नए फीचर्स या इम्प्रूवमेंट्स प्रपोज़ करें
- अपने यूज़ केसेज़ शेयर करें

---

## 📄 लाइसेंस

यह प्रोजेक्ट Apache License 2.0 के तहत लाइसेंस्ड है - डिटेल्स के लिए [LICENSE](../../LICENSE) फाइल देखें।

---

## 👨‍💻 ऑथर

**Jean Bodenberg**
- 🌐 [GitHub](https://github.com/bodenberg)

---

## 🌟 अपना सपोर्ट दिखाएं

अगर AppDimens Android ने आपके प्रोजेक्ट में मदद की है, तो कृपया:

- ⭐ **स्टार** इस रिपॉजिटरी को
- 🐦 **शेयर** सोशल मीडिया पर
- 📝 **लिखें** एक रिव्यू या ब्लॉग पोस्ट
- 🤝 **कंट्रिब्यूट** कोड या डॉक्यूमेंटेशन

---

<div align="center">
    <p><strong>Android डेवलपमेंट कम्युनिटी के लिए ❤️ के साथ बनाया गया</strong></p>
    <p>AppDimens Android - जहां रिस्पॉन्सिव डिज़ाइन मैथमेटिकल प्रिसिजन से मिलता है</p>
</div>

