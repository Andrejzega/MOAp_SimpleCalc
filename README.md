# Enostavni kalkulator (SimpleCalc)

Preprosta Android aplikacija kalkulatorja za spoznavanje razhroščevanja (debugging) in lokalnega enotnega testiranja (unit testing) v Android Studiu pri predmetu MOAp. Namen naloge je sistematično raziskovanje in odpravljanje napak pri vnosu podatkov (prazen vnos, deljenje z nič) ter spoznavanje orodij razhroščevalnika (prekinitvene točke, klicni sklad, spremljanje in spreminjanje spremenljivk, Logcat).

## Opis aplikacije

Aplikacija ponuja osnovne računske operacije med dvema številoma:
- **Vnos operandov**: Dve ločeni vnosni polji za vnos števil (prvi in drugi operand).
- **Seštevanje (Add)**: Izračun vsote dveh števil z uporabo operacije `mCalculator.add()`.
- **Odštevanje (Sub)**: Izračun razlike dveh števil z uporabo operacije `mCalculator.sub()`.
- **Deljenje (Div)**: Izračun količnika z operacijo `mCalculator.div()`. Pri deljenju z nič aplikacija namesto neskončnosti izpiše opozorilo `Cannot divide by zero`.
- **Množenje (Mul)**: Izračun zmnožka z operacijo `mCalculator.mul()`.
- **Prikaz rezultata**: Veliko in pregledno besedilno polje pod gumbi, ki prikaže rezultat ali opozorilo.
- **Prazen vnos**: Če je polje prazno, aplikacija ne računa, ampak izpiše, katero število manjka (`Enter the first number`, `Enter the second number` ali `Enter both numbers`), prazno polje pa označi z rdečo ikono.

Vsa uporabniška besedila in opozorila so shranjena v `strings.xml`. Pred klici računskih operacij se preverja veljavnost vnosa, da se preprečijo sesutja aplikacije.

## Ikona aplikacije

Aplikacija ima nastavljeno prilagojeno ikono kalkulatorja z vijoličnim ozadjem Material 3 (#4F378B) in belim simbolom matematičnih operacij. Datoteke ikone se nahajajo na poti:
- `app/src/main/res/mipmap-anydpi-v26/ic_launcher.xml`
- `app/src/main/res/mipmap-anydpi-v26/ic_launcher_round.xml`
- `app/src/main/res/drawable/ic_launcher_foreground.xml`
- `app/src/main/res/drawable/ic_launcher_background.xml`
- `app/src/main/res/mipmap-*/ic_launcher.png`

## Posnetki delovanja aplikacije v AVD emulatorju (Pixel 7, Android 16)

| Začetni zaslon | Seštevanje (55 + 25) | Odštevanje (55 - 25) |
|---|---|---|
| ![Začetni zaslon](screenshot_main.png) | ![Seštevanje](screenshot_add.png) | ![Odštevanje](screenshot_sub.png) |

| Deljenje (55 / 25) | Množenje (55 * 25) | Deljenje z 0 (55 / 0) | Prazno prvo polje |
|---|---|---|---|
| ![Deljenje](screenshot_div.png) | ![Množenje](screenshot_mul.png) | ![Deljenje z 0](screenshot_div_zero.png) | ![Prazen vnos](screenshot_empty.png) |

## Enotni testi (Unit Tests)

Projekt vključuje celovite JUnit 4 lokalne enotne teste v razredu `CalculatorTest.java` (`app/src/test/java/com/example/android/SimpleCalc/CalculatorTest.java`), ki preverjajo delovanje seštevanja, odštevanja, množenja, deljenja, računanje z negativnimi števili, decimalnimi števili, velikimi števili ter pravilno proženje izjeme ob deljenju z nič (55 / 0 in 0 / 0).
