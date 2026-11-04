# Skyldig!

Familiens eget festspil. Peg på den skyldige. Jo mere uenige I er, jo flere point. Først til 21 vinder.

**Spil her:** https://mikkelholstkruse-max.github.io/Skyldig-2026/

---

## 1. Læg spillet på hjemmeskærmen

1. Åbn linket ovenfor i **Safari** på iPhone.
2. Tryk på **Del-knappen** (firkanten med pilen op).
3. Vælg **Føj til hjemmeskærm**.

Nu ligger Skyldig! som en app med eget ikon. Gør det på alle familiens telefoner.

## 2. Det virker med det samme

- **Én telefon:** Man sender telefonen rundt om bordet. Det kræver ingen opsætning.
- **Familiestudiet:** Rejser, kælenavne, familieord, citater og kastebilleder. Indtil trin 3 er gjort, bliver det gemt på den telefon, man skriver det på.

## 3. Slå "Hver sin telefon" til (en gang, cirka 10 minutter, gratis)

Det kræver en gratis Firebase-database fra Google. Der skal ikke bruges kreditkort.

1. Gå til **console.firebase.google.com** og log ind med din Google-konto.
2. Tryk **Opret projekt**, kald det `skyldig`, og slå **Google Analytics fra**.
3. Gå til **Build → Firestore Database → Create database**. Vælg placering **eur3 (Europe)** og **Start in production mode**.
4. Åbn fanen **Rules**, erstat alt med teksten nedenfor, og tryk **Publish**:

   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /{document=**} {
         allow read, write: if true;
       }
     }
   }
   ```

5. Gå til **Projektoversigt** og tryk på **`</>`** for at tilføje en web-app. Kald den `skyldig`, og lad være med at slå hosting til.
6. Firebase viser nu en kodeblok med `firebaseConfig = { apiKey: ..., projectId: ... }`. **Kopiér den og send den til Claude.** Claude lægger den i `config.js` for dig.

Bagefter virker "Hver sin telefon" på alle telefoner, og Familiestudiet deles mellem jer.

> Om sikkerhed: Databasen er åben for alle, der kender spillets nøgler. Til et familiespil er det fint, men skriv ikke noget meget privat i Familiestudiet.

## 4. Fulde sange i Disko (valgfrit, kræver Apple-udviklerkonto)

Uden dette spiller Disko Apples 30-sekunders klip. Med det kan DJ'en, der har Apple Music, afspille hele sange.

1. Meld dig ind i **Apple Developer Program** på developer.apple.com (cirka 700 kr. om året).
2. Gå til **Certificates, Identifiers & Profiles → Keys**, opret en nøgle, og sæt flueben ved **Media Services (MusicKit)**.
3. Download nøglefilen (.p8), og notér **Key ID** og dit **Team ID**.
4. Send de tre ting til Claude. Claude laver et udviklertoken og lægger det i `config.js`. Tokenet skal fornyes hvert halve år.

Første gang DJ'en starter en Disko, beder Apple om at logge ind med Apple Music.

---

## Sådan arbejder du effektivt med GitHub og Claude

**Du skal ikke selv kode.** GitHub er bare stedet, hvor spillet bor. Claude laver ændringerne og lægger dem op.

**Ændringer:** Skriv til Claude, hvad du vil have, fx *"Opdater Skyldig: tilføj en runde med babybilleder"*. Claude retter koden og lægger den op. Hjemmesiden opdaterer sig selv efter 1–2 minutter. Tving siden til at genindlæse på telefonen, hvis du ikke ser ændringen med det samme.

**Fortryd:** Alle versioner bliver gemt. Hvis noget går i stykker, så skriv *"Rul Skyldig tilbage til versionen fra i går"*. Under **Commits** på GitHub kan du se hver ændring med dato.

**Idéliste:** Brug fanen **Issues** på GitHub som en fælles idéliste. Familien kan også skrive forslag der. Bed Claude om at "lave issue #3".

**Hvad ligger hvor:**

| Ting | Hvor | Hvem kan se det |
|---|---|---|
| Selve spillet (koden) | GitHub, `index.html` | Alle (repoet er offentligt) |
| Firebase-nøglerne | GitHub, `config.js` | Alle (det er normalt for web-apps) |
| Jeres rejser, citater, selfies, kastebilleder | Firebase eller telefonen | Kun dem med spillet |

Familiens personlige ting ligger aldrig i koden på GitHub.

**Gode beskeder til Claude:**
- "Opdater Skyldig: flere kærlige spørgsmål"
- "Skyldig: gør retssalen 30 sekunder i stedet for 20"
- "Her er vores firebaseConfig: …"
- "Skyldig virker ikke på Fars telefon, han ser …"
