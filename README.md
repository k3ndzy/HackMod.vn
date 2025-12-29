# 🎮 Cen iOS Store - Version 2.0

> App store cho iOS với ứng dụng mod/hack game, tích hợp Firebase real-time database và analytics.

![Version](https://img.shields.io/badge/version-2.0-blue.svg)
![Firebase](https://img.shields.io/badge/firebase-integrated-orange.svg)
![License](https://img.shields.io/badge/license-free-green.svg)

---

## ✨ Features

### 🔥 Core Features
- ✅ **App Installation** - Cài đặt ứng dụng iOS qua Enterprise certificate
- ✅ **Key System** - Quản lý license key free và premium
- ✅ **Real-time Stats** - Thống kê người online và downloads thực tế
- ✅ **Cloud Reviews** - Đánh giá và review lưu trên cloud
- ✅ **Favorites** - Đánh dấu ứng dụng yêu thích
- ✅ **Dark Mode** - Chế độ tối/sáng với theme switcher

### 📊 Statistics & Analytics
- Real-time online counter (Firebase Presence)
- Total downloads tracking
- Today's downloads counter
- Per-app statistics
- Firebase Analytics integration

### 💬 Review System
- 5-star rating system
- Text reviews (min 10 characters)
- Average rating calculation
- Review count display
- Cloud storage with Firebase
- Local fallback when offline

### 🎨 UI/UX
- Modern responsive design
- Smooth animations
- Beautiful notifications
- Loading states
- Hover effects
- Mobile optimized

---

## 🚀 Quick Start

### Option 1: Without Firebase (Instant)
1. Clone/download this repository
2. Open `index.html` in Safari (iOS) or any browser
3. Done! ✅

Website sẽ hoạt động ở **fallback mode** với:
- Realistic online counter simulation
- Local download tracking
- LocalStorage reviews
- All UI features working

### Option 2: With Firebase (Recommended)
1. Follow [FIREBASE_SETUP.md](FIREBASE_SETUP.md) guide
2. Setup takes ~10-15 minutes
3. Get real-time features! 🔥

---

## 📱 Supported Apps

### FunTap PUBG
- **Version**: 4.1
- **Features**: Aim hack, safe to use
- **Price**: 30k/day, 150k/week, 350k/month
- **Key Free**: 5 hours trial

### Cen Map AOV
- **Version**: 4.1  
- **Bundle ID**: `com.soimap.game.kvgn.map`
- **Features**: Map hack for Arena of Valor
- **Price**: 35k/day, 80k/week, 200k/month
- **Key Free**: 1 day trial

---

## 🛠️ Tech Stack

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Database**: Firebase Realtime Database
- **Analytics**: Firebase Analytics
- **Storage**: LocalStorage (fallback)
- **Installation**: iOS Enterprise certificate (`itms-services://`)

---

## 📂 Project Structure

```
CeniOs-main/
├── index.html              # Main HTML file with JavaScript
├── styles.css              # All styles and animations
├── README.md              # This file
├── CHANGELOG.md           # Version history
├── FIREBASE_SETUP.md      # Firebase setup guide
├── *.plist                # iOS app manifests
├── *.png / *.jpg          # Images and icons
└── replit.md              # Replit config (if hosted there)
```

---

## 🎯 What's New in v2.0

### Major Improvements ✨

#### 1. Firebase Integration
- Real-time database for stats and reviews
- Cloud persistence  
- Analytics tracking
- Automatic fallback mode

#### 2. Better Statistics
- Real online counter (not fake anymore!)
- Accurate download tracking
- Daily/monthly breakdowns
- Session management

#### 3. Enhanced Reviews
- Cloud-based storage
- Real-time sync
- Better validation
- Rating calculations

#### 4. UI/UX Upgrades
- Favorite system
- Better notifications
- Smooth animations
- Loading states
- Better mobile experience

#### 5. Code Quality
- Error handling
- Fallback mechanisms
- Security improvements
- Performance optimizations

See [CHANGELOG.md](CHANGELOG.md) for complete details.

---

## 🔒 Security

### Current Setup
- Public read/write (with validation)
- Input sanitization (XSS protection)
- Firebase security rules
- Review validation (10-500 chars)

### Recommendations
- Monitor Firebase usage regularly
- Add rate limiting if traffic is high
- Consider authentication for admin features
- Review Firebase security rules

---

## 📈 Performance

### Metrics
- **Page Load**: ~600ms (with Firebase)
- **First Paint**: <1s
- **Interactive**: ~800ms
- **Firebase Init**: ~200ms

### Optimization
- Lazy loading reviews
- Efficient Firebase queries
- Session cleanup
- Optimized images (recommended)

---

## 🌐 Browser Support

| Browser | Support |
|---------|---------|
| Safari (iOS) | ✅ Full |
| Chrome | ✅ Full |
| Firefox | ✅ Full |
| Edge | ✅ Full |
| Safari (macOS) | ✅ Full |

**Recommended**: Safari on iPhone/iPad for app installation

---

## 📱 Installation Guide for Users

### Install Apps
1. Open website in **Safari** (iPhone/iPad)
2. Click **"📥 Cài đặt"** button
3. Click **"Install"** in popup
4. Go to **Settings** → **General** → **VPN & Device Management**
5. Trust the profile
6. Launch app from home screen

### Get License Keys
- **Free keys**: Follow "FunLink" or "Lấy Mã" buttons
- **Premium keys**: Contact admin via Zalo/Telegram
- **Enter key**: Open app → Input key from website

---

## 🐛 Troubleshooting

### App won't install
- ✅ Use Safari browser (not Chrome/Firefox)
- ✅ Check internet connection
- ✅ Trust the profile in Settings

### Certificate revoked
- Certificate may be revoked by Apple
- Contact admin for new link
- Check Telegram group for updates

### Reviews not saving
- Check if Firebase is configured
- Look for errors in browser console (F12)
- Fallback to localStorage is automatic

### Online counter shows 0
- Wait 10-15 seconds after page load
- Refresh the page
- Check Firebase configuration

---

## 🔗 Contact & Support

- **Zalo**: [Cen iOS](https://zalo.me/420773099399)
- **Telegram Admin**: [@cenios](https://t.me/cenios)
- **Telegram Group**: [CenIOSMOD](https://t.me/CenIOSMOD)

---

## 📄 License

This project is free to use. No warranty provided.

⚠️ **Disclaimer**: This website distributes modified iOS apps. Use at your own risk. The developers are not responsible for:
- Account bans
- Security risks
- Certificate revocation
- Terms of service violations

---

## 🙏 Acknowledgments

- Firebase for free hosting and database
- iOS Enterprise Program for distribution
- Community for feedback and support

---

## 📊 Statistics

- **Total Apps**: 2
- **Active Users**: Real-time tracking
- **Reviews**: Cloud-based system
- **Downloads**: Tracked per app

---

## 🔮 Roadmap

### Planned Features
- [ ] User authentication
- [ ] Admin dashboard
- [ ] App upload system  
- [ ] Search & filter
- [ ] Push notifications
- [ ] PWA support
- [ ] Multi-language (EN, VN, CN)

### Under Consideration
- Payment integration
- Subscription system
- Community features
- Live chat support

---

## 🤝 Contributing

This is a private project, but suggestions are welcome!

Contact via Zalo/Telegram if you have:
- Feature ideas
- Bug reports
- UI/UX improvements
- Security concerns

---

## ⭐ Show Your Support

If you like this project:
1. Star the repository (if on GitHub)
2. Share with friends
3. Join Telegram group
4. Provide feedback

---

**Made with ❤️ by Cen iOS Team**

*Last updated: December 29, 2025*
