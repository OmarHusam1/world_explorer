[README (1).md](https://github.com/user-attachments/files/28659111/README.1.md)
# ✈️ World Explorer — Flutter Tourism App

A Flutter mobile application for discovering and exploring top tourist destinations around the world. Users can browse places, filter by category, search, save favorites, and open locations directly in Google Maps.

---

## 👨‍💻 Developer

| Field | Details |
|---|---|
| **Name** | Omar Husam AlShawabkeh |
| **Student ID** | 202110084 |
| **Course** | Mobile App Development |
| **Project Type** | Flutter Final Project |

---

## 📸 Screenshots

> Screenshots will be added after final testing.

---

## 📱 App Screens

The app has **5 screens** connected via a Bottom Navigation Bar with 4 tabs:

| Screen | Description |
|---|---|
| **Home** | Landing screen with featured destinations carousel and category shortcuts |
| **Explore** | Full destinations list with live search and category filter chips |
| **Details** | Full info for each destination — description, rating, best time to visit, and Google Maps button |
| **Saved** | All bookmarked destinations in one place, with unsave option |
| **Profile** | App info, feature list, and tech stack |

---

## ✨ Features

- Browse **8 world-class destinations** across 4 categories
- **Search** by destination name, country, or category
- **Filter** by category using animated chip buttons (All, Beach, Historical, Adventure, Cultural)
- **Bookmark / Save** destinations from both the list and details screen
- **Open in Google Maps** directly from the details screen using `url_launcher`
- Network images loaded from the web + local asset image in `assets/images/`
- Live stats on the Home screen (total destinations, categories, saved count)
- Smooth navigation with destination data passed between screens

---

## 🗂️ Project Structure

```
lib/
├── main.dart                        # App entry point + Bottom Navigation Bar
├── controllers/
│   └── tourism_controller.dart      # Data management, search, filter logic (MVC)
├── models/
│   ├── destination_model.dart       # DestinationModel class
│   └── category_model.dart          # CategoryModel class with factory constructor
├── screens/
│   ├── home_screen.dart             # Home / featured destinations
│   ├── destinations_screen.dart     # List + search + filter
│   ├── details_screen.dart          # Destination details + Maps button
│   ├── saved_screen.dart            # Saved/bookmarked destinations
│   └── profile_screen.dart          # About screen
└── widgets/
    └── destination_card.dart        # Reusable destination card widget
```

---

## 🧱 OOP Concepts Used

### 1. Encapsulation

The `TourismController` class keeps the destinations list **private** and only exposes it through a controlled getter. This prevents other parts of the app from directly modifying the data:

```dart
// Private list — cannot be accessed directly from outside
static final List<DestinationModel> _allDestinations = [...];

// Public getter — controlled read-only access
static List<DestinationModel> get allDestinations =>
    List.unmodifiable(_allDestinations);
```

### 2. Factory Constructor

`CategoryModel` uses a **factory constructor** to create objects from a Map. This is a standard OOP pattern for object creation from external data:

```dart
factory CategoryModel.fromMap(Map<String, dynamic> map) {
  return CategoryModel(
    id: map['id'],
    name: map['name'],
    icon: map['icon'],
    color: map['color'],
  );
}
```

---

## 📦 Packages Used

| Package | Version | Purpose |
|---|---|---|
| `google_fonts` | ^6.1.0 | Custom typography (Poppins + Playfair Display fonts) |
| `url_launcher` | ^6.2.4 | Opens Google Maps from the Details screen |

---

## 🗄️ Data & Models

- **DestinationModel** — holds id, name, country, description, fullDescription, imageAsset, networkImage, category, rating, bestTime, mapUrl, isSaved
- **CategoryModel** — holds id, name, icon, color; includes `fromMap()` factory constructor and `toMap()` method
- **TourismController** — manages all destination and category data; provides `search()`, `filterByCategory()`, `getSaved()`, `toggleSaved()` static methods

---

## 🗺️ Destinations & Categories

| Category | Destinations |
|---|---|
| Historical | Petra (Jordan), Machu Picchu (Peru) |
| Beach | Santorini (Greece), Maldives |
| Adventure | Swiss Alps (Switzerland), Sahara Desert (Morocco), Wadi Rum (Jordan) |
| Cultural | Kyoto (Japan) |

---

## 🖼️ Assets & Images

- Local asset image stored at `assets/images/placeholder.png` (registered in `pubspec.yaml`)
- Network images loaded from Wikipedia for all 8 destinations
- `pubspec.yaml` configured with assets path, `google_fonts`, and `url_launcher` dependencies

---

## 🔧 How to Run

```bash
# Clone the repository
git clone https://github.com/OmarHusam1/world_explorer

# Navigate to project folder
cd tourism_app

# Install dependencies
flutter pub get

# Run the app
flutter run
```

---

## 📝 Notes

- All destination data, descriptions, and design are written and customized for this project
- The **live bookmark system** is the unique feature — saved count updates in real time on the Home screen stats card, and destinations can be unsaved directly from the Saved screen
- The app follows MVC structure: `models/` for data, `controllers/` for logic, `screens/` for views, `widgets/` for reusable UI components
