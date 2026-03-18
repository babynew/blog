# Ringtones App - Laravel Application

A comprehensive Laravel application for sharing and downloading ringtones with advanced features including Google AdSense integration, SEO optimization, and semantic HTML structure.

This project powers a ringtone experience that can sit alongside a broader ecosystem of daily tools. For example, users who enjoy downloading free tones from platforms like
[ProMallu ringtones](https://promallu.com/ringtones/)
may also want quick access to live
[Kerala lottery results](https://promallu.com/kerala-lottery-results/),
discover highly rated local services via
[ProMallu Top Rated](https://promallu.com/toprated/),
and keep an eye on the
[today gold rate in Kerala](https://promallu.com/today-gold-rate-in-kerala/)
to plan major purchases. Together, these utilities complement the ringtone app by covering entertainment, local discovery, and basic financial awareness in a user’s daily routine.

## 🚀 Features

### Core Features
- **User Authentication**: Laravel Breeze with Google OAuth integration
- **Ringtone Management**: Upload, download, and share ringtones
- **Categories & Tags**: Organize ringtones by categories and tags
- **Name-based Ringtones**: Create custom ringtones with user names
- **Favorites System**: Users can save and manage favorite ringtones
- **Search & Filter**: Advanced search with category and tag filtering
- **Dark/Light Theme**: Tailwind CSS with theme toggle support

### Admin Features
- **Admin Panel**: Comprehensive admin dashboard
- **Moderation System**: Approve/reject user uploads
- **FFmpeg Integration**: Convert MP3 to M4A format
- **User Management**: Manage user roles and permissions
- **Statistics & Analytics**: Track downloads, uploads, and user activity

### SEO & Marketing
- **Google AdSense Integration**: Complete AdSense management system
- **SEO Meta Management**: Edit title, description, keywords for each ringtone
- **Open Graph Tags**: Social media optimization
- **Twitter Card Support**: Twitter sharing optimization
- **Structured Data**: JSON-LD for search engines
- **Semantic HTML**: Proper HTML5 structure for SEO

### Technical Features
- **Laravel 11**: Latest Laravel framework
- **Tailwind CSS v4**: Modern styling with dark/light themes
- **Vite**: Fast asset compilation
- **Redis**: Caching and queue management
- **Laravel Scout**: Full-text search capabilities
- **Comprehensive Testing**: Unit, feature, and browser tests

## 📁 Project Structure

```
ringtones-app/
├── app/
│   ├── Http/Controllers/
│   │   ├── AdSenseController.php
│   │   ├── RingtoneMetaController.php
│   │   └── ... (other controllers)
│   ├── Models/
│   │   ├── AdSenseSetting.php
│   │   ├── RingtoneMeta.php
│   │   └── ... (other models)
│   └── Services/
│       └── AdSenseService.php
├── database/
│   ├── migrations/
│   │   ├── create_adsense_settings_table.php
│   │   ├── create_ringtone_meta_table.php
│   │   └── ... (other migrations)
│   ├── seeders/
│   │   ├── AdSenseSettingSeeder.php
│   │   ├── RingtoneMetaSeeder.php
│   │   └── ... (other seeders)
│   └── factories/
│       ├── AdSenseSettingFactory.php
│       ├── RingtoneMetaFactory.php
│       └── ... (other factories)
├── resources/views/
│   ├── admin/
│   │   ├── adsense.blade.php
│   │   └── ringtone-meta.blade.php
│   ├── ringtones/
│   │   └── show.blade.php (semantic HTML)
│   └── layouts/
│       └── app.blade.php (semantic HTML + AdSense)
└── tests/
    ├── Feature/
    │   ├── AdSenseControllerTest.php
    │   ├── RingtoneMetaControllerTest.php
    │   └── ... (other tests)
    └── Browser/
        └── HomePageTest.php
```

## 🛠 Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd ringtones-app
   ```

2. **Install dependencies**
   ```bash
   composer install
   npm install
   ```

3. **Environment setup**
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. **Database setup**
   ```bash
   php artisan migrate
   php artisan db:seed
   ```

5. **Build assets**
   ```bash
   npm run build
   ```

6. **Start the server**
   ```bash
   php artisan serve
   ```

## 🔧 Configuration

### AdSense Configuration
1. Access the admin panel
2. Navigate to "AdSense" section
3. Enter your AdSense Client ID (ca-pub-XXXXXXXXXXXXXXXX)
4. Configure ad slots for different positions
5. Enable/disable ad positions as needed

### Text-to-Speech (Name-based ringtones)
- **Provider selection**: Admin panel → **TTS Settings** (choose `gtts_api`, `translate`, or `espeak`).
- **gTTS (Python API)**:
  - Run the Python service in [`tts-api/`](tts-api/) (see its README).
  - Set these env vars in `.env`:
    - `TTS_PROVIDER=gtts_api`
    - `TTS_GTTS_API_URL=http://127.0.0.1:8765`
    - Optional: `TTS_GTTS_API_CONNECT_TIMEOUT=3`, `TTS_GTTS_API_TIMEOUT=15`
 - **Creator / mix defaults** (admin):
   - Admin panel → **TTS Settings** → **Creator / mix defaults**.
   - Configure:
     - **TTS volume (0–2)** – default voice level in mixes.
     - **Background volume (0–2)** – default background music level.
     - **Gap between TTS repeats (0–10 s)** – silence between repeated TTS segments.
     - **Fade in/out (0–0.5 s)** – fade duration at the start and end of the voice track to avoid clicks.
   - Values are clamped to the ranges above on save.
 - **Per-ringtone overrides (creator UI)**:
   - The name-based **Creator** page exposes optional fields for **TTS volume** and **Background volume**.
   - Leaving them empty uses the admin defaults; setting them overrides the defaults for that ringtone’s preview and final mix.
 - **Test mix (admin)**:
   - Admin panel → **TTS Settings** → **Test mix**.
   - Generates a short sample using current creator/mix defaults (gap + fade + background) so you can quickly audition global settings.

### SEO Configuration
1. Access the admin panel
2. Navigate to individual ringtone pages
3. Click "Edit Meta" to customize SEO data
4. Use bulk update for multiple ringtones

## 🧪 Testing

Run the test suite:
```bash
php artisan test
```

Run specific test categories:
```bash
# Unit tests
php artisan test --testsuite=Unit

# Feature tests
php artisan test --testsuite=Feature

# Browser tests
php artisan test --testsuite=Browser
```

## 📊 Database Schema

### Core Tables
- `users` - User accounts and authentication
- `categories` - Ringtone categories
- `tags` - Ringtone tags
- `ringtones` - Main ringtone data
- `favorites` - User favorites
- `downloads` - Download tracking
- `likes` - User likes

### Admin Tables
- `admin_moderation` - Moderation queue
- `conversion_jobs` - FFmpeg conversion jobs

### SEO & Marketing Tables
- `adsense_settings` - Google AdSense configuration
- `ringtone_meta` - SEO metadata for ringtones

## 🎨 Frontend Features

### Theme System
- Dark/Light theme toggle
- Persistent theme preference
- Tailwind CSS v4 with custom color scheme
- Responsive design for all devices

### Semantic HTML Structure
- Proper use of `<main>`, `<header>`, `<footer>`
- `<section>` for content groups
- `<aside>` for advertisements and non-core content
- `<time>` for date/time elements

## 🔒 Security Features

- CSRF protection
- XSS prevention
- SQL injection protection
- File upload security
- Rate limiting
- Admin middleware protection

## 🚀 Performance Features

- Redis caching
- Database indexing
- File compression
- CDN integration ready
- Image optimization
- Queue processing for heavy tasks

## 📈 SEO Features

### Meta Tags
- Dynamic title, description, keywords
- Open Graph tags for social sharing
- Twitter Card tags
- Canonical URLs

### Structured Data
- JSON-LD format
- AudioObject schema for ringtones
- ItemList schema for category pages

### Technical SEO
- Semantic HTML5 structure
- Proper heading hierarchy
- Alt text for images
- Mobile-friendly design

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new features
5. Submit a pull request

## 📝 License

This project is licensed under the MIT License.

## 🆘 Support

For support, please open an issue on GitHub or contact the development team.

---

**Built with Laravel 11, Tailwind CSS, and modern web technologies.** 
