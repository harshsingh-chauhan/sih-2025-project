# Product Requirements Document (PRD)
## AI-Based Animal Type Classification System

---

## Project Information

### Project Title
**ATC Mobile** - AI-Based Animal Type Classification System for Cattle and Buffaloes

### Project Description

**Short Description:**
An AI-powered mobile application that automates animal type classification for cattle and buffaloes using image analysis, enabling field personnel to capture standardized body structure scores with minimal human error and seamless integration with the Bharat Pashudhan App.

**Long Description:**

**Problem Statement:**
Under the Rashtriya Gokul Mission (RGM), Animal Type Classification (ATC) is crucial for identifying elite dams in Progeny Testing and Pedigree Selection programs. Currently, trained personnel manually evaluate physical traits through visual inspection and measurement, which is prone to human error, observer bias, and inconsistent data quality. These limitations affect the scientific validity of breeding decisions and productivity assessments.

**Proposed Solution:**
ATC Mobile is an Android-based AI solution that leverages computer vision and deep learning to automate the animal type classification process. Field personnel can capture images of cattle and buffaloes using their mobile devices, and the AI system automatically extracts body structure parameters (body length, height at withers, chest width, rump angle, etc.), generates objective classification scores, and stores the data both locally and in the Bharat Pashudhan App.

**Key Differentiators:**
- **Offline-First Architecture:** Works in rural areas with limited connectivity, syncing data when online
- **AI-Driven Accuracy:** Eliminates subjective bias through standardized computer vision algorithms
- **Real-Time Processing:** Instant feedback and scoring within seconds of image capture
- **Seamless Integration:** Direct data synchronization with existing BPA infrastructure
- **Field-Optimized UX:** Simple interface designed for non-technical field workers

**Expected Impact:**
- Improve data accuracy and consistency by 80-90% compared to manual methods
- Reduce evaluation time from 15-20 minutes to under 2 minutes per animal
- Enable scientific breeding decisions based on reliable, standardized data
- Support the RGM mission to enhance indigenous bovine breeds and milk productivity
- Create a scalable solution deployable across India's dairy farming regions

**Target Market:**
- Department of Animal Husbandry & Dairying field officers
- Veterinary professionals in rural and semi-urban areas
- Dairy farm managers and cooperative societies
- Research institutions conducting breeding programs

---

## Learning Objectives

### Primary Learning Outcomes:
1. **Mobile AI/ML Implementation** - Deploy computer vision models on Android devices using TensorFlow Lite
2. **Offline-First Architecture** - Design and implement robust offline data storage with intelligent sync mechanisms
3. **Image Processing & Computer Vision** - Extract morphometric measurements from images using pose estimation and object detection
4. **API Integration** - Build secure REST API integrations with government systems (BPA)
5. **Production-Ready Mobile Development** - Create enterprise-grade Android applications with proper architecture patterns

### Secondary Learning Outcomes:
1. **State Management in Complex Apps** - Handle offline/online states, image processing workflows, and data synchronization
2. **Agricultural Technology Domain Knowledge** - Understand dairy farming, animal breeding, and government agricultural programs
3. **Accessibility & Localization** - Build apps for users with varying technical literacy and regional language support

---

## Technology Stack

### Frontend (Android Mobile):
- **Language:** Kotlin 1.9
- **Build Tool:** Gradle 8.x with Kotlin DSL
- **UI Framework:** Jetpack Compose (Modern Android UI)
- **Navigation:** Navigation Component with Compose
- **State Management:** ViewModel + StateFlow/SharedFlow
- **Dependency Injection:** Hilt (Dagger)
- **Image Handling:** CameraX for capture, Coil for loading/caching
- **Local Database:** Room Database with SQLite
- **Additional Libraries:**
    - TensorFlow Lite for on-device ML inference
    - Retrofit + OkHttp for API calls
    - WorkManager for background sync
    - DataStore for preferences
    - Timber for logging

### Backend:
- **Runtime:** Node.js v22 LTS
- **Language:** TypeScript 5
- **Framework:** Express.js v5
- **Database:** MongoDB with Mongoose v9
- **File Storage:** AWS S3 or Google Cloud Storage for images
- **Authentication:** JWT-based authentication
- **API Documentation:** Swagger/OpenAPI 3.0
- **Additional Services:**
    - Redis for caching and job queues
    - Bull for background job processing
    - Winston for logging

### AI/ML Pipeline:
- **Model Training:** Python 3.11 with TensorFlow/PyTorch
- **Computer Vision:** OpenCV, MediaPipe for pose estimation
- **Model Format:** TensorFlow Lite (.tflite) for mobile deployment
- **Key Models:**
    - Object Detection: MobileNetV3 or EfficientDet-Lite
    - Pose Estimation: MediaPipe Pose or custom keypoint detector
    - Measurement Extraction: Custom regression model for body metrics

---

## MVP Scope

### Phase 1: Core Platform (Days 1-8)
**Priority: P0 (Must Have)**

#### 1.1 Image Capture & Real-Time Processing
- Camera interface with guided overlay for proper animal positioning
- Real-time image quality validation (blur detection, lighting check, distance estimation)
- Multi-angle capture workflow (side view, rear view, front view)
- Immediate on-device AI inference for instant results
- Visual feedback during capture (alignment guides, confirmation indicators)

#### 1.2 AI-Based Classification Engine
- On-device TensorFlow Lite model for body structure analysis
- Automatic extraction of 12-15 key body parameters:
    - Height at withers
    - Body length
    - Chest width and depth
    - Rump width and angle
    - Leg conformation
    - Udder attachment (for females)
    - Overall body condition score
- Standardized scoring algorithm (0-100 scale or breed-specific standards)
- Confidence scores for each measurement
- Error handling for poor quality images

#### 1.3 Offline-First Data Management
- Local SQLite database for all captured data
- Image compression and local storage
- Queue system for pending sync operations
- Conflict resolution for offline edits
- Data integrity validation before sync
- Automatic retry mechanism for failed syncs

#### 1.4 Historical Data Tracking
- Animal profile creation and management
- Classification history timeline per animal
- Comparison view for tracking changes over time
- Search and filter by animal ID, date, score ranges
- Export functionality (CSV, PDF reports)
- Visual charts showing score trends

#### 1.5 BPA Integration
- Secure API authentication with BPA servers
- Automatic data synchronization when online
- Batch upload for multiple classifications
- Sync status indicators (pending, in-progress, completed, failed)
- Manual sync trigger option
- Data mapping to BPA schema format

### Phase 2: Enhanced Features (Days 9-11)
**Priority: P1 (Should Have)**

#### 2.1 Enhanced User Experience
- Dashboard with daily/weekly statistics
- Push notifications for sync completion/failures
- In-app tutorial and help system
- Image annotation tools for marking specific features
- Voice notes for observations
- Bulk operations (batch classification review)

#### 2.2 Advanced Analytics
- Comparative analytics across animals
- Breed-specific scoring benchmarks
- Quality metrics dashboard (image quality, confidence scores)
- Performance reports for field officers
- Exportable analytics reports

#### 2.3 Quality Assurance Features
- Manual override option for AI scores with justification
- Flag questionable results for supervisor review
- Image retake suggestions based on quality metrics
- Audit trail for all classifications and modifications

### Phase 3: Advanced Features (Day 12 - Polish & Deploy)
**Priority: P2 (Nice to Have)**

#### 3.1 Collaboration Features
- Share classification results with colleagues
- Comments and feedback system
- Supervisor approval workflows

#### 3.2 Regional Language Support
- Hindi, Tamil, Telugu, Marathi, Gujarati localization
- Voice commands for hands-free operation

#### 3.3 Advanced AI Features
- Breed identification from images
- Health indicators detection (lameness, body condition issues)
- Pregnancy detection support

---

## Target Users / Personas

### Primary Persona: Field Animal Typer

**Demographics:**
- **Age:** 25-45 years
- **Location:** Rural and semi-urban areas across India
- **Occupation:** Animal Husbandry field officer, Veterinary Assistant
- **Tech Savviness:** Medium (comfortable with smartphones, limited technical training)
- **Education:** Diploma/Bachelor's in Veterinary Science or Animal Husbandry

**Goals & Motivations:**
- Evaluate 15-25 animals per day efficiently and accurately
- Reduce paperwork and manual data entry time
- Improve accuracy of classifications to support breeding programs
- Meet departmental targets for data collection
- Contribute to improving indigenous cattle breeds

**Pain Points:**
- Manual measurements are time-consuming and physically demanding
- Inconsistent scoring due to fatigue or environmental factors
- Poor internet connectivity in rural field locations
- Need to carry physical measurement tools and forms
- Data entry delays and errors when transferring to BPA

**User Needs:**
- Simple, intuitive app that works without constant training
- Reliable offline functionality for remote areas
- Quick image capture and immediate results
- Easy-to-understand scoring interface
- Automatic sync when internet is available
- Minimal data entry requirements

### Secondary Persona: Veterinary Supervisor

**Demographics:**
- **Age:** 35-55 years
- **Location:** District headquarters or regional offices
- **Occupation:** Senior Veterinary Officer, Program Manager
- **Tech Savviness:** Medium-High
- **Education:** Bachelor's/Master's in Veterinary Science

**Goals & Motivations:**
- Monitor data quality across multiple field officers
- Ensure compliance with RGM program standards
- Generate reports for higher authorities
- Identify training needs for field staff
- Improve overall program outcomes

**Pain Points:**
- Difficulty in verifying field data accuracy
- Time-consuming manual review of classifications
- Lack of real-time visibility into field operations
- Inconsistent data quality across different field officers

**User Needs:**
- Dashboard view of all field activities
- Quality control and audit capabilities
- Analytics and reporting tools
- Ability to flag and review questionable classifications
- Export functionality for official reports

---

## Branding, Theming & Visual Identity

### Brand Identity

**Brand Name:** ATC Mobile (Animal Type Classification Mobile)

**Brand Personality:**
- **Tone:** Professional, Authoritative, Trustworthy
- **Voice:** Clear, Instructional, Supportive
- **Mood:** Efficient, Scientific, Government-Standard

**Brand Values:**
- **Accuracy First** - Scientific precision in all measurements and classifications
- **Accessibility** - Easy to use for field workers with varying technical skills
- **Reliability** - Works consistently in challenging rural environments
- **Transparency** - Clear explanations of AI decisions and confidence levels

**Brand Story:**
ATC Mobile represents the digital transformation of India's dairy sector under the Rashtriya Gokul Mission. Born from the need to modernize animal breeding programs, this application brings cutting-edge AI technology to field officers across rural India, empowering them to make scientifically sound decisions that will improve indigenous cattle breeds for generations to come.

### Logo & Visual Assets

**Logo Specifications:**
- **Primary Logo:** Government of India emblem integrated with modern cattle silhouette and AI circuit pattern
- **Logo Variations:**
    - Full color (for app splash screen)
    - Monochrome white (for dark backgrounds)
    - Icon-only (for app icon - simplified cattle head with tech accent)
- **Safe Space:** Minimum 20px clear space on all sides
- **Minimum Size:** 32px height for icon, 120px for full logo
- **File Formats:** SVG (primary), PNG (fallback)

**Imagery Style:**
- **Photography:** Documentary-style, authentic field photography showing real cattle in rural Indian settings
- **Illustrations:** Technical diagrams with clean lines for body measurement visualization
- **Icons:** Google Material Symbols - Rounded variant (softer, more approachable while maintaining professionalism)
- **Patterns:** Subtle geometric patterns inspired by traditional Indian textiles for decorative elements

---

## Color System (OKLCH)

### Understanding OKLCH
OKLCH provides perceptually uniform colors ensuring consistent visual weight and accessibility:
- **L (Lightness):** 0-100% (0 = black, 100 = white)
- **C (Chroma):** 0-0.4 (0 = grayscale, higher = more vibrant)
- **H (Hue):** 0-360 degrees (color wheel position)

### Color Palette Definition

#### Primary Brand Color - Government Blue
```css
--color-primary: oklch(50% 0.18 250);
--color-primary-content: oklch(98% 0.01 250);
```
**Usage:** Primary CTAs, header bars, important actions, navigation accents  
**Meaning:** Authority, trust, official government identity, professionalism  
**Accessibility:** Contrast ratio with base-100: 8.2:1 (AAA)

**Color Variations:**
- **Lighter:** `oklch(70% 0.15 250)` - Hover states, secondary backgrounds
- **Darker:** `oklch(35% 0.20 250)` - Active states, pressed buttons

#### Secondary Brand Color - Agricultural Green
```css
--color-secondary: oklch(55% 0.16 140);
--color-secondary-content: oklch(98% 0.01 140);
```
**Usage:** Success indicators, confirmation actions, data sync status, growth metrics  
**Meaning:** Agriculture, growth, health, prosperity, fertility  
**Accessibility:** Contrast ratio with base-100: 7.5:1 (AAA)

#### Accent Color - Saffron Orange
```css
--color-accent: oklch(65% 0.17 40);
--color-accent-content: oklch(20% 0.03 40);
```
**Usage:** Highlights, badges, important notifications, special features  
**Meaning:** Energy, national pride (Indian flag reference), attention-drawing  
**Accessibility:** Contrast ratio with base-100: 4.8:1 (AA)

#### Neutral Colors
```css
--color-neutral: oklch(30% 0.02 250);
--color-neutral-content: oklch(95% 0.01 250);
```
**Usage:** Text, borders, subtle UI elements, disabled states  
**Meaning:** Professional foundation, readability, sophistication

#### Base Colors (Backgrounds & Surfaces)
```css
--color-base-100: oklch(98% 0.005 250);  /* Main background - off-white */
--color-base-200: oklch(94% 0.01 250);   /* Cards, panels - light gray */
--color-base-300: oklch(88% 0.015 250);  /* Dividers, borders - medium gray */
--color-base-content: oklch(22% 0.02 250); /* Primary text - dark charcoal */
```

#### Semantic Colors

**Info:**
```css
--color-info: oklch(60% 0.16 240);
--color-info-content: oklch(98% 0.01 240);
```
**Usage:** Info messages, help text, tooltips, measurement confidence indicators

**Success:**
```css
--color-success: oklch(60% 0.17 145);
--color-success-content: oklch(98% 0.01 145);
```
**Usage:** Successful sync, high-quality images, good classification scores, confirmations

**Warning:**
```css
--color-warning: oklch(75% 0.15 70);
--color-warning-content: oklch(25% 0.04 70);
```
**Usage:** Low confidence scores, image quality issues, sync pending alerts

**Error:**
```css
--color-error: oklch(60% 0.19 25);
--color-error-content: oklch(98% 0.01 25);
```
**Usage:** Failed operations, invalid data, critical errors, poor image quality

### Color Usage Guidelines

**Do's:**
✅ Use primary blue for all government-official actions and navigation  
✅ Use green for successful operations and agricultural context  
✅ Use saffron sparingly for critical attention points  
✅ Maintain high contrast (7:1 minimum) for field use in bright sunlight  
✅ Use semantic colors consistently (never green for errors)  
✅ Test colors on actual Android devices in outdoor conditions

**Don'ts:**
❌ Don't use more than 3 colors on a single screen  
❌ Don't rely solely on color to convey measurement accuracy (add icons/text)  
❌ Don't use decorative colors that distract from data  
❌ Don't use low-contrast combinations that fail in bright sunlight  
❌ Don't override government branding guidelines

### Color Accessibility Matrix

| Text Color | Background | Contrast Ratio | WCAG Level | Use Case |
|------------|------------|----------------|------------|----------|
| base-content | base-100 | 12.5:1 | AAA | Body text, data fields |
| primary-content | primary | 10.2:1 | AAA | Primary action buttons |
| secondary-content | secondary | 9.8:1 | AAA | Success buttons |
| accent-content | accent | 4.8:1 | AA | Accent badges |
| error-content | error | 8.5:1 | AAA | Error messages |

**Testing Tools:**
- WebAIM Contrast Checker for design phase
- Android Accessibility Scanner for in-app testing
- Outdoor sunlight testing with actual target devices

### Dark Mode Considerations
**Status:** Not implemented for MVP (field use primarily in daylight)  
**Future:** If dark mode is added, increase lightness values by 40-50% and reduce chroma slightly for night viewing comfort.

---

## UI/UX Design System

### Design Principles

1. **Consistency:** Every screen follows the same navigation patterns, button placements, and interaction models
2. **Accessibility:** Large touch targets (min 48dp), high contrast, simple language, works with Android TalkBack
3. **Responsiveness:** Optimized for 5"-7" Android phones in portrait orientation (primary) with landscape support
4. **Modularity:** Reusable components built with Jetpack Compose for easy maintenance
5. **Reusability:** Every UI pattern used in 2+ places becomes a shared component

### DaisyUI 5 Theme Configuration
**Note:** This project uses native Android/Jetpack Compose, but we'll define equivalent theme values for consistency.

```kotlin
// theme/Color.kt
object AppColors {
    // Base Colors
    val Base100 = Color(0xFFFAFAFB) // oklch(98% 0.005 250)
    val Base200 = Color(0xFFEFF0F3) // oklch(94% 0.01 250)
    val Base300 = Color(0xFFDCDEE3) // oklch(88% 0.015 250)
    val BaseContent = Color(0xFF2D3035) // oklch(22% 0.02 250)
    
    // Primary - Government Blue
    val Primary = Color(0xFF1E4D9B) // oklch(50% 0.18 250)
    val PrimaryContent = Color(0xFFFAFAFB)
    
    // Secondary - Agricultural Green
    val Secondary = Color(0xFF2E7D5D) // oklch(55% 0.16 140)
    val SecondaryContent = Color(0xFFFAFAFB)
    
    // Accent - Saffron Orange
    val Accent = Color(0xFFC8762A) // oklch(65% 0.17 40)
    val AccentContent = Color(0xFF2D2216)
    
    // Semantic Colors
    val Info = Color(0xFF2563B8) // oklch(60% 0.16 240)
    val Success = Color(0xFF2B7A52) // oklch(60% 0.17 145)
    val Warning = Color(0xFFD4A134) // oklch(75% 0.15 70)
    val Error = Color(0xFFC93A3A) // oklch(60% 0.19 25)
}

// theme/Theme.kt
private val LightColorScheme = lightColorScheme(
    primary = AppColors.Primary,
    onPrimary = AppColors.PrimaryContent,
    secondary = AppColors.Secondary,
    onSecondary = AppColors.SecondaryContent,
    tertiary = AppColors.Accent,
    onTertiary = AppColors.AccentContent,
    background = AppColors.Base100,
    onBackground = AppColors.BaseContent,
    surface = AppColors.Base200,
    onSurface = AppColors.BaseContent,
    error = AppColors.Error,
    // ... additional mappings
)
```

### Typography

**Google Fonts Integration:**
```xml
<!-- res/font/fonts.xml -->
<font-family xmlns:android="http://schemas.android.com/apk/res/android">
    <font
        android:fontStyle="normal"
        android:fontWeight="400"
        android:font="@font/inter_regular" />
    <!-- Additional weights -->
</font-family>
```

**Font System:**

**Primary Font (Headings & UI):**
- **Font Family:** Inter
- **Weights:** 400 (Regular), 500 (Medium), 600 (SemiBold), 700 (Bold)
- **Usage:** Headings, buttons, navigation, data labels
- **Characteristics:** Highly legible, professional, optimized for screens

**Secondary Font (Body Text):**
- **Font Family:** Inter (same as primary for consistency)
- **Weights:** 300 (Light), 400 (Regular), 500 (Medium)
- **Usage:** Body text, descriptions, help text
- **Characteristics:** Excellent readability at small sizes

**Typography Scale:**
```kotlin
// theme/Type.kt
val Typography = Typography(
    // Headings
    displayLarge = TextStyle(
        fontFamily = InterFontFamily,
        fontWeight = FontWeight.Bold,
        fontSize = 28.sp,
        lineHeight = 36.sp
    ), // Screen titles
    
    displayMedium = TextStyle(
        fontFamily = InterFontFamily,
        fontWeight = FontWeight.SemiBold,
        fontSize = 24.sp,
        lineHeight = 32.sp
    ), // Section headings
    
    headlineMedium = TextStyle(
        fontFamily = InterFontFamily,
        fontWeight = FontWeight.SemiBold,
        fontSize = 20.sp,
        lineHeight = 28.sp
    ), // Card titles
    
    titleLarge = TextStyle(
        fontFamily = InterFontFamily,
        fontWeight = FontWeight.Medium,
        fontSize = 18.sp,
        lineHeight = 24.sp
    ), // List item titles
    
    // Body Text
    bodyLarge = TextStyle(
        fontFamily = InterFontFamily,
        fontWeight = FontWeight.Normal,
        fontSize = 16.sp,
        lineHeight = 24.sp
    ), // Primary body text
    
    bodyMedium = TextStyle(
        fontFamily = InterFontFamily,
        fontWeight = FontWeight.Normal,
        fontSize = 14.sp,
        lineHeight = 20.sp
    ), // Secondary text
    
    bodySmall = TextStyle(
        fontFamily = InterFontFamily,
        fontWeight = FontWeight.Normal,
        fontSize = 12.sp,
        lineHeight = 16.sp
    ), // Captions, timestamps
    
    // UI Elements
    labelLarge = TextStyle(
        fontFamily = InterFontFamily,
        fontWeight = FontWeight.Medium,
        fontSize = 16.sp,
        lineHeight = 20.sp,
        letterSpacing = 0.5.sp
    ), // Button text
    
    labelMedium = TextStyle(
        fontFamily = InterFontFamily,
        fontWeight = FontWeight.Medium,
        fontSize = 14.sp,
        lineHeight = 16.sp
    ), // Form labels
)
```

**Responsive Typography:**
- **Baseline (5"-6" screens):** Standard sizes as defined
- **Large screens (>6.5"):** Increase by 1.15x
- **Small screens (<5"):** Reduce by 0.9x (but maintain minimum 14sp for body text)

### Icons - Google Material Symbols

**Integration:**
```xml
<!-- res/values/styles.xml -->
<style name="MaterialSymbolsStyle">
    <item name="fontFamily">@font/material_symbols_rounded</item>
    <item name="android:fontVariationSettings">'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 24</item>
</style>
```

**Icon Variant:** Rounded (softer, more approachable)

**Icon Usage:**

| Category | Icon Names | Context |
|----------|------------|---------|
| Navigation | home, menu, arrow_back, arrow_forward, close | Bottom nav, toolbars |
| Camera | photo_camera, camera_alt, flip_camera_android, flash_on, flash_off | Image capture |
| Actions | check, close, edit, delete, save, refresh, sync, download, share | User actions |
| Status | check_circle, error, warning, info, cloud_done, cloud_off, pending | Sync status, quality |
| Animals | pets (cattle icon fallback), local_hospital (vet) | Animal-specific |
| Data | bar_chart, analytics, history, assessment, monitoring | Analytics screens |
| User | person, account_circle, badge, group | User profile |
| Measurements | straighten, square_foot, height, width | Body metrics |

**Icon Sizes:**
```kotlin
// theme/Dimensions.kt
object IconSize {
    val Small = 16.dp  // Inline with text
    val Medium = 20.dp // List items, chips
    val Large = 24.dp  // Buttons, prominent UI
    val XL = 32.dp     // Feature icons
    val XXL = 48.dp    // Empty states, onboarding
}
```

**Icon Component:**
```kotlin
@Composable
fun AppIcon(
    name: String,
    contentDescription: String?,
    modifier: Modifier = Modifier,
    size: Dp = IconSize.Large,
    tint: Color = LocalContentColor.current
) {
    Icon(
        imageVector = Icons.Rounded[name], // Material Icons
        contentDescription = contentDescription,
        modifier = modifier.size(size),
        tint = tint
    )
}
```

---

## Responsive Design

### Breakpoint System
Android focuses on screen size classes rather than specific breakpoints:

```kotlin
// Compose Window Size Classes
enum class WindowSizeClass {
    Compact,   // < 600dp (phones in portrait)
    Medium,    // 600-840dp (tablets, phones in landscape)
    Expanded   // > 840dp (large tablets, foldables)
}
```

**Target Devices:**
- **Primary:** Compact phones (5"-6.5" in portrait) - 90% of field use
- **Secondary:** Medium tablets (7"-10") - supervisors in office
- **Tertiary:** Compact landscape - occasional field use

### Layout Patterns

**Compact (Portrait Phone - Primary):**
- Single column layouts
- Bottom navigation (4-5 items max)
- Floating Action Button (FAB) for primary action
- Full-width cards with vertical stacking
- Collapsible app bar for more screen space
- Modal bottom sheets for secondary actions

**Medium (Tablet / Landscape):**
- 2-column grid where appropriate (history list)
- Side navigation rail instead of bottom nav
- Side panels for details (master-detail pattern)
- More generous spacing and larger touch targets

**Responsive Utilities:**
```kotlin
@Composable
fun ResponsiveLayout(
    windowSize: WindowSizeClass,
    compactContent: @Composable () -> Unit,
    expandedContent: @Composable () -> Unit
) {
    when (windowSize) {
        WindowSizeClass.Compact -> compactContent()
        else -> expandedContent()
    }
}

// Usage example
ResponsiveLayout(
    windowSize = windowSizeClass,
    compactContent = {
        Column(modifier = Modifier.fillMaxSize()) {
            // Stacked layout
        }
    },
    expandedContent = {
        Row(modifier = Modifier.fillMaxSize()) {
            // Side-by-side layout
        }
    }
)
```

---

## Accessibility Requirements

### WCAG 2.1 AA Compliance Checklist

**Perceivable:**
- ✅ All images have contentDescription for TalkBack
- ✅ Color contrast ratio ≥ 4.5:1 for normal text (tested for sunlight readability)
- ✅ Color contrast ratio ≥ 3:1 for large text (18sp+)
- ✅ Never use color alone (always pair with icons/text)
- ✅ Text scales with system font size settings (up to 200%)
- ✅ Support for high contrast mode

**Operable:**
- ✅ All functionality available via touch and keyboard (external keyboard support)
- ✅ No touch traps in modal dialogs
- ✅ Visible focus indicators (2dp outline)
- ✅ Touch targets minimum 48x48dp
- ✅ Logical focus order (top to bottom, left to right)
- ✅ Swipe gestures have alternatives

**Understandable:**
- ✅ Language declared (`<application android:locale="en">`)
- ✅ Consistent navigation across all screens
- ✅ Input labels and hints for all form fields
- ✅ Error messages with clear correction suggestions
- ✅ Confirmation dialogs for destructive actions

**Robust:**
- ✅ Semantic content descriptions for TalkBack
- ✅ Proper heading hierarchy in complex screens
- ✅ ARIA-equivalent roles via semantics modifiers
- ✅ State announcements for loading/success/error

**Field-Specific Accessibility:**
- ✅ Works with gloves (enlarged touch targets)
- ✅ Readable in direct sunlight (high contrast mode)
- ✅ Audio feedback for image capture success
- ✅ Haptic feedback for important actions
- ✅ Voice commands for hands-free operation (Phase 3)

---

## Component Design System

### Component Organization Structure

```
app/src/main/java/com/atc/mobile/
├── ui/
│   ├── components/
│   │   ├── atoms/
│   │   │   ├── AppButton.kt
│   │   │   ├── AppTextField.kt
│   │   │   ├── StatusBadge.kt
│   │   │   ├── AppIcon.kt
│   │   │   ├── ScoreIndicator.kt
│   │   │   └── LoadingSpinner.kt
│   │   │
│   │   ├── molecules/
│   │   │   ├── FormField.kt
│   │   │   ├── AnimalCard.kt
│   │   │   ├── MeasurementItem.kt
│   │   │   ├── SyncStatusBar.kt
│   │   │   └── ImagePreview.kt
│   │   │
│   │   ├── organisms/
│   │   │   ├── TopAppBar.kt
│   │   │   ├── BottomNavigation.kt
│   │   │   ├── CameraViewfinder.kt
│   │   │   ├── ClassificationResults.kt
│   │   │   └── HistoryList.kt
│   │   │
│   │   └── templates/
│   │       ├── MainScaffold.kt
│   │       ├── CameraScreen.kt
│   │       └── DetailScreen.kt
│   │
│   └── screens/
│       ├── home/
│       ├── camera/
│       ├── history/
│       ├── animal_detail/
│       └── settings/
```

---

## Atom Components

### Component Template
```kotlin
/**
 * [ComponentName] - Brief description
 *
 * @param requiredProp Description of required parameter
 * @param optionalProp Description with default value
 * @param modifier Standard Compose modifier
 */
@Composable
fun ComponentName(
    requiredProp: Type,
    optionalProp: Type = defaultValue,
    modifier: Modifier =