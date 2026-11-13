# FitHer Studio Shop

Flutter lab: Cloud Product Explorer & Detail Carousel.
Theme: women's fitness center shop.
API: https://fakestoreapi.com/products

## Features

- `http` GET request with a 10 second timeout and try-catch
- Handles status codes 200, 404 and 500+
- Safe JSON parsing with `(json['price'] as num).toDouble()` and fallbacks
- 3 UI states: loading spinner, product list, error screen with "Retry Connection"
- Pull-to-refresh with `RefreshIndicator`
- `ListView.separated` with image, title, rating and price
- Hero transition (`product_image_{id}`) from list to detail
- Photo carousel (`PageView.builder`) with counter (`1 / 3`) and animated dots
- Category badge, full description, sticky "Add to Cart" button
- Share button opens a bottom sheet with the deep link `narxoz://store/product/{id}` and a copy button

## Project structure

```
lib/
  main.dart
  models/product.dart
  services/product_service.dart
  screens/product_list_screen.dart
  screens/product_detail_screen.dart
  widgets/share_sheet.dart
```

## How to run

1. Install Flutter and open this folder.
2. Create the platform folders (android, ios) once:
   ```
   flutter create .
   ```
   Delete the generated `test/widget_test.dart` (it is for the default counter app).
3. Add internet permission in `android/app/src/main/AndroidManifest.xml`,
   above the `<application>` tag:
   ```xml
   <uses-permission android:name="android.permission.INTERNET" />
   ```
4. Get packages and run:
   ```
   flutter pub get
   flutter run
   ```

## Offline test (for the defense)

1. Run the app with internet: the list loads.
2. Turn on Airplane mode and restart the app (or pull to refresh): the error screen appears.
3. Turn Airplane mode off and tap "Retry Connection": the list loads without restarting the app.

## Note

The API returns only one image per product, so the carousel shows
3 pages built from the same image.
