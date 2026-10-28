# Laboratorio 15 – FieldTech Móvil (IF0009)

## 1. Backend (Spring Boot 3 + H2)
```bash
cd fieldtech-backend
mvn spring-boot:run
```
- API: `GET/POST http://localhost:8080/api/v1/incidencias`
- Consola H2: `http://localhost:8080/h2-console` (JDBC: `jdbc:h2:mem:fieldtechdb`, user `sa`, sin password)

## 2. App móvil (Flutter)
Esta carpeta trae `lib/`, `pubspec.yaml` y el `AndroidManifest.xml`. Para generar el resto del proyecto nativo:
```bash
cd fieldtech_mobile
flutter create --org com.fieldtech .
```
> Si `flutter create` sobreescribe el `AndroidManifest.xml`, vuelva a copiar el de este zip.

Luego:
1. Pegue las claves de `ios/Runner/Info.plist.snippet.xml` dentro del `<dict>` de `ios/Runner/Info.plist`.
2. `flutter pub get`
3. `flutter run` (emulador Android: el backend se ve en `http://10.0.2.2:8080`; en teléfono real cambie la URL en `lib/main.dart` por la IP de su PC).
4. En el emulador: `...` > Location > escriba coordenadas > Set Location para probar el GPS.

## Reto autónomo
`SegmentedButton` (Todas / Offline / Sincronizadas) en `lib/main.dart`; las consultas con `WHERE is_synced` están en `DatabaseHelper.obtenerPorFiltro`.
