//[appdimens_dynamic](../../../index.md)/[com.appdimens.dynamic.code](../index.md)/[AppDimens](index.md)/[dynamicPercentageDp](dynamic-percentage-dp.md)

# dynamicPercentageDp

[androidJvm]\
fun [dynamicPercentageDp](dynamic-percentage-dp.md)(percentage: [Float](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-float/index.html), type: ScreenType = ScreenType.LOWEST, resources: [Resources](https://developer.android.com/reference/kotlin/android/content/res/Resources.html)): [Float](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-float/index.html)

Calcula um valor de dimensão dinâmico com base em uma porcentagem (0.0 a 1.0) da dimensão da tela. Retorna o valor em Dp (Float).

#### Return

O valor ajustado em Dp (Float).

#### Parameters

androidJvm

| | |
|---|---|
| percentage | A porcentagem (0.0f a 1.0f). |
| type | A dimensão da tela a ser usada (LOWEST/HIGHEST). |
| resources | Os Resources do Context. |