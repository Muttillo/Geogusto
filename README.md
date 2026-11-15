# Geogusto – MVP

## 1. Backend (Supabase)
1. Crea un progetto gratuito su https://supabase.com
2. SQL Editor → incolla ed esegui `supabase/schema.sql`
3. Project Settings → API: copia URL e anon key in `lib/config.dart`

## 2. App (Flutter)
1. Installa Flutter: https://docs.flutter.dev/get-started/install
2. Nella cartella del progetto: `flutter create .` (genera le cartelle android/ e ios/ senza toccare lib/)
3. `flutter pub get`
4. Permessi:
   - Android, `android/app/src/main/AndroidManifest.xml`, dentro <manifest>:
     `<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>`
     `<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>`
     `<uses-permission android:name="android.permission.INTERNET"/>`
   - iOS, `ios/Runner/Info.plist`, aggiungi:
     `NSLocationWhenInUseUsageDescription` = "Serve per mostrarti i prodotti tipici vicino a te"
     `NSPhotoLibraryUsageDescription` = "Serve per allegare una foto al prodotto"
5. `flutter run`

## 3. Moderazione
1. SQL Editor → esegui `supabase/moderation.sql`
2. Authentication → Users: copia il tuo UUID, poi esegui `insert into admins (user_id) values ('IL-TUO-UUID');`
3. Riapri l'app: in alto compare l'icona dello scudo, con la lista dei prodotti da approvare o rifiutare.

## 4. Mappa
La mappa usa OpenStreetMap (nessuna chiave API). I server tile pubblici vanno bene per lo sviluppo;
prima del lancio con molti utenti passa a un provider dedicato (es. MapTiler, Mapbox) cambiando `urlTemplate` in `lib/screens/map_screen.dart`.

## 5. Pubblicazione
1. SQL Editor → esegui anche `supabase/publication.sql` (segnalazioni ed eliminazione account)
2. Segui `docs/CHECKLIST_PUBBLICAZIONE.md`
3. Testi per gli store: `docs/STORE_LISTING.md`; modello di privacy policy: `docs/PRIVACY_POLICY.md`
