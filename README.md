# MyTVMax

Application Android légère basée sur Capacitor : catalogue de chaînes publiques en direct, recherche, filtres par pays et favoris persistants.

## Fonctionnalités

- Interface responsive sombre inspirée du prototype fourni.
- Recherche rapide et rendu par lots pour rester léger.
- Favoris sauvegardés localement sur l’appareil avec `localStorage`.
- Cache local du catalogue avec IndexedDB pendant 6 heures.
- Lecture des flux directs HLS avec support natif ou hls.js.
- Aucun serveur backend nécessaire.
- Workflow GitHub Actions pour produire un APK debug.

## Développement local

Pré-requis : Node.js 20+, Java 21 et Android Studio/SDK pour lancer Android localement.

```bash
npm install
npx cap sync android
npx cap open android
```

Pour générer l’APK localement :

```bash
cd android
./gradlew assembleDebug
```

Le fichier est créé dans `android/app/build/outputs/apk/debug/app-debug.apk`.

## GitHub Actions

Pousser le projet sur GitHub puis lancer `Build MyTVMax APK` depuis l’onglet Actions, ou pousser sur la branche `main`. L’APK est disponible dans les artifacts du workflow.

Le workflow fourni génère un APK debug non destiné à la publication Google Play. Pour une publication, ajouter une signature Android et générer un AAB signé.

## Limites des flux

La disponibilité des chaînes dépend de l’API iptv-org, des règles CORS, du format HLS et des droits de diffusion du flux. L’application ne contourne pas les protections des serveurs et ignore les flux nécessitant des en-têtes spéciaux.
