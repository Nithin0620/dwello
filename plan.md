# Dwello - Comprehensive Roadmap & Improvement Plan

This document outlines the end-to-end plan to elevate **Dwello** from a basic tutorial project into a high-performance, production-grade real estate application for iOS and Android.

---

## 🧭 Project Vision
**Dwello** is a modern, fast, and intuitive real estate discovery platform built with React Native (Expo), Supabase, and TailwindCSS (NativeWind). The goal is to deliver an exceptional native user experience on par with market leaders like Zillow, Airbnb, and Realtor.com.

---

## 📋 Phased Execution Roadmap

### 🎨 Phase 1: Design System, Typography & Branding
*Goal: Establish a cohesive, premium brand identity and eliminate design inconsistencies across platforms.*

- [ ] **Custom Font Integration**:
  - Install and load `@expo-google-fonts/rubik` (or *Plus Jakarta Sans* / *Inter*) in `app/_layout.tsx` using `useFonts` and `expo-splash-screen` to avoid font flash.
  - Apply consistent font utilities (`font-sans`, `font-medium`, `font-bold`) throughout all screens.
- [ ] **Unified Theme & Color Palette**:
  - Clean up `tailwind.config.js` with structured semantic colors:
    - **Primary**: Deep Slate / Navy (`#0F172A` / `#1E293B`)
    - **Accent**: Warm Amber / Gold (`#F59E0B` / `#D97706`)
    - **Surface / Background**: Clean neutral slates (`#F8FAFC`, `#FFFFFF`)
    - **Borders & Dividers**: Subtle borders (`#E2E8F0`, `#F1F5F9`)
  - Replace hardcoded hex colors and arbitrary blue shades across all components with standard Tailwind theme classes.
- [ ] **Dark Mode Foundation**:
  - Configure NativeWind dark mode support (`dark:` classes) with deep slate and zinc surface colors.

---

### 📱 Phase 2: Navigation, Performance & Platform Stability
*Goal: Fix cross-platform issues and maximize rendering performance.*

- [ ] **Cross-Platform Tab Bar Overhaul**:
  - Replace `expo-router/unstable-native-tabs` (which relies on iOS-only SF Symbols) with stable Expo Router `<Tabs />` and `@expo/vector-icons` (Ionicons/Lucide).
  - Add frosted glass / blur background (`expo-blur`) and active micro-animations.
- [ ] **Image Optimization**:
  - Replace all standard React Native `<Image>` components with `expo-image`.
  - Enable automatic disk/memory caching, smooth fade-in transitions, and blurhash placeholders to eliminate stutter during list scrolling.
- [ ] **Skeleton Shimmers & Micro-Interactions**:
  - Replace generic `ActivityIndicator` spinners with animated skeleton cards (`react-native-reanimated`).
  - Integrate subtle haptic feedback (`expo-haptics`) on tab navigation, bookmarking, and key actions.

---

### 🏡 Phase 3: Screen Redesigns & High-Value Features
*Goal: Enhance core screens with rich, interactive, and practical features.*

- [ ] **Home Screen Enhancements**:
  - Dynamic greeting and location selector header.
  - Category pill filter with quick badges (Villas, Apartments, Penthouses, Studios, Commercial).
  - "Featured" and "Recently Added" carousels with smooth pagination.
- [ ] **Property Details Screen**:
  - **Native Amenities Grid**: Visual amenity badges with relevant icons (WiFi, Pool, Parking, AC, Gym, Security).
  - **Built-in Mortgage / EMI Calculator**: Interactive monthly installment calculator with customizable down payment and interest rate sliders.
  - **Agent Contact & Action Sheet**: Modal with direct WhatsApp message, phone call, email inquiry, and "Schedule a Tour" booking request.
  - **Share Sheet**: Native system share integration (`expo-sharing` / React Native `Share`).
- [ ] **Search & Advanced Filter Overhaul**:
  - Real-time debounced search by city, neighborhood, and property title.
  - Bottom sheet modal (`@gorhom/bottom-sheet`) for advanced filters:
    - Price range dual slider
    - Bedroom & bathroom selectors
    - Property type and listing status (Buy vs. Rent)
- [ ] **Saved / Favorites Management**:
  - Offline caching of favorited properties.
  - Option to organize saved properties into custom lists/folders (e.g. "Dream Homes", "Shortlisted").

---

### 🗺️ Phase 4: Interactive Map View & Location Services
*Goal: Deliver an engaging map-first discovery experience.*

- [ ] **Native Map Integration**:
  - Replace the detail screen's `WebView` OpenStreetMap with native `react-native-maps` for buttery smooth 60fps scrolling and native gesture support.
- [ ] **Interactive Explorer Map (Airbnb/Zillow Style)**:
  - Full-screen interactive map with custom price-tag marker pills (`$850k`).
  - Bottom swipeable horizontal carousel of property cards linked to map marker selection.
  - "Search in this area" button when panning/zooming.

---

### 🛡️ Phase 5: Architecture, State Management & Security
*Goal: Build a scalable data layer with reliable error handling and security.*

- [ ] **Data Layer with TanStack Query (React Query)**:
  - Centralize Supabase queries into a dedicated service layer (`lib/services/properties.ts`).
  - Implement query caching, automatic stale-while-revalidate, pull-to-refresh, and optimistic UI updates for saves/likes.
- [ ] **Error Handling & Feedback**:
  - Global toast notifications for success/error feedback.
  - Friendly empty states with clear calls-to-action (e.g. "No properties saved yet").
- [ ] **Secure Property Creation & Validation**:
  - Add schema validation using `zod` and `react-hook-form` for creating and editing listings.
  - Image compression before uploading to Supabase Storage to save bandwidth and storage.
  - Enforce backend Supabase Row Level Security (RLS) policies for write/delete operations.

---

### 🚀 Phase 6: QA, Polish & Production Readiness
*Goal: Final verification, testing, and store asset preparation.*

- [ ] Complete end-to-end testing on physical iOS and Android devices.
- [ ] App store asset generation (App icon, splash screen, adaptive icons).
- [ ] Production build verification with EAS (Expo Application Services).
