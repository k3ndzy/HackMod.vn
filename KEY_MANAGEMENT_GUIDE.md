# 🔑 Key Management System - Hướng Dẫn Sử Dụng

## 📋 Tổng Quan

Hệ thống Key Management với Firebase cho phép bạn:
- ✅ Tạo keys free hoặc premium
- ✅ Đặt hạn thời gian (6h, 24h, 7 ngày...)
- ✅ Giới hạn số lần dùng (10, 50, 100...)
- ✅ Real-time countdown
- ✅ Track sử dụng (device, IP, time)
- ✅ Analytics dashboard
- ✅ Anti-spam protection

---

## 🚀 Quick Start

### 1️⃣ Tạo 10 Keys Test Ngay Hôm Nay

**Cách 1: Admin Panel**
1. Mở `admin-panel.html` 
2. Click "🔄 Tạo 10 Keys"
3. Done! ✅

**Cách 2: Manual**
1. Mở `admin-panel.html`
2. Thiết lập:
   - ⏱️ Thời Lượng: **6** (giờ)
   - 📱 Lần Dùng: **10**
   - 🎮 App: **FunTap PUBG**
3. Click "🔐 Tạo Key" (lặp 10 lần)

### 2️⃣ Share Keys cho Users

Copy 10 keys này và share qua:
- 📱 Telegram group
- 💬 Zalo
- 📲 Facebook group
- 🌐 Website

**Format ví dụ:**
```
🔑 KEY MIỄN PHÍ (6 GIỜ - 10 LẦN DÙNG)
CENIOS-ABCD1234EFGH
CENIOS-IJKL5678MNOP
... (8 keys nữa)

Hướng dẫn: Mở app → Nhập key → Xác nhận
```

### 3️⃣ Users Sử Dụng Key

1. User click nút **"🔑 Lấy Key"** trên website
2. Nhập key được share
3. Click ✅ Xác Nhận
4. 🎉 Ứng dụng kích hoạt 6 giờ!

---

## 🔐 Admin Panel Features

### Tạo Keys
- **Duration**: Bao lâu key hoạt động (giờ)
- **Max Uses**: Tối đa bao nhiêu lần dùng
- **App**: Chọn app (PUBG / AOV)
- **Notes**: Ghi chú (optional)

### Thống Kê Real-time
- 📊 **Total Keys**: Tổng keys đã tạo
- 🟢 **Active Keys**: Keys còn hoạt động
- 📈 **Total Used**: Tổng lần dùng
- ⚠️ **Expired Keys**: Keys đã hết hạn

### Search & Filter
- Tìm kiếm by key code
- Xem chi tiết sử dụng
- Xóa key nếu cần

---

## 📊 Key Lifecycle

### Khi Key Được Tạo
```
✅ Status = Active
⏱️ Duration = 6 giờ
📱 Max Uses = 10
Used = 0
Expiry = Now + 6h
```

### Khi User Sử Dụng Key
```
1️⃣ System check: Valid?
2️⃣ Check: Hết hạn chưa?
3️⃣ Check: Dùng hết chưa?
4️⃣ If OK → Tăng Used counter
5️⃣ Log: Device ID + Timestamp
6️⃣ Show: "✅ Kích hoạt thành công!"
```

### Khi Key Hết Hạn
```
❌ Status = Expired
User thấy: "⚠️ Key đã hết hạn"
Cannot use anymore
```

---

## 🛡️ Security Features

### Device Tracking
- **Device ID**: Unique per browser
- **IP Tracking**: Server-side (Firebase)
- **Timestamp**: Lúc nào dùng
- **Prevention**: 1 device = 1 key/day (tuỳ chọn)

### Anti-Spam
- ✅ Rate limiting (tối đa 5 lần thử/phút)
- ✅ Invalid key blocking
- ✅ Expired key rejection
- ✅ Used-up key prevention
- ✅ XSS protection
- ✅ Input validation

### Fallback Protection
- ✅ Key check on server-side (Firebase)
- ✅ User không thể edit file local
- ✅ Real-time validation
- ✅ Immediate expiry update

---

## 💾 Firebase Structure

```
Firebase Realtime Database
└── keys/
    ├── CENIOS-ABC123XYZ/
    │   ├── code: "CENIOS-ABC123XYZ"
    │   ├── app: "pubg"
    │   ├── duration: 6
    │   ├── maxUses: 10
    │   ├── used: 5
    │   ├── created: 1735286400000
    │   ├── expiry: 1735308000000
    │   ├── expiryDate: "2025-12-27"
    │   ├── status: "active"
    │   ├── notes: "Test key"
    │   ├── createdAt: "27/12/2025 10:00:00"
    │   └── lastUsedBy:
    │       ├── deviceId: "device_1234567_abcdef"
    │       ├── timestamp: 1735286400000
    │       └── date: "27/12/2025 14:30:00"
    └── CENIOS-DEF456UVW/...
```

---

## 📱 User Experience

### Scenario: User muốn sử dụng app

```
1. User mở website → Thấy "🔑 Lấy Key" button

2. User click → Mở modal nhập key

3. User paste key → CENIOS-ABC123XYZ

4. System validate:
   ✅ Key exists?
   ✅ Still active?
   ✅ Not expired?
   ✅ Not used-up?
   ✅ Device not spam?

5. If ALL OK:
   ✅ Show "Kích hoạt thành công!"
   ✅ Countdown: "Hết hạn trong 6h"
   ✅ Save to localStorage
   ✅ Log usage to Firebase

6. User can now use app for 6 hours
   - If refresh page → countdown still shows
   - If close browser → still active
   - After 6h → "Key expired" message
```

---

## 🔄 Real-time Updates

### Countdown Timer
- Synchronized with Firebase timestamp
- Not affected by local clock
- Survives refresh/close/reopen
- Auto-expire (not relying on client)

### Usage Counter
- Updates instantly on Firebase
- Visible in admin panel
- Shows remaining uses
- Progress bar animation

### Status Changes
- Active → Expired (auto)
- Active → Used-up (when counter reaches max)
- Deleted keys removed instantly

---

## 🎯 Use Cases

### Case 1: Daily Free Keys
```
Every day at 10 AM:
- Admin tạo 100 keys
- Duration: 6 giờ (10 AM - 4 PM)
- Max Uses: 10
- Share qua Telegram group
- Keys tự expire lúc 4 PM
```

### Case 2: Special Event
```
Event: "Game Tournament Prize"
- Create 50 keys
- Duration: 7 days
- Max Uses: 50 (unlimited basically)
- Give to tournament winners
- Expire after event
```

### Case 3: Beta Testing
```
Beta Phase:
- Create 10 keys
- Duration: 30 days (720 giờ)
- Max Uses: 1000 (unlimited)
- Track behavior
- Analytics
```

### Case 4: Premium Trial
```
Premium Trial:
- Create 100 keys
- Duration: 3 days
- Max Uses: 5
- Try before buy
- Upgrade option
```

---

## 📊 Analytics

### Metrics to Track
```
Per Key:
- Total uses
- Unique devices used
- Last used time
- Device list

Overall:
- Total keys created
- Active keys count
- Used keys count
- Expired keys count
- Usage trend
- Popular apps
```

### Admin Dashboard Views
1. **Overview**: Quick stats
2. **Keys List**: All keys with progress
3. **Usage History**: Who used what
4. **Analytics**: Trends and patterns

---

## ⚙️ Configuration

### In Admin Panel
```javascript
// Defaults
Duration: 6 hours
Max Uses: 10
App: PUBG (changeable)
```

### In Firebase Rules
```json
{
  "rules": {
    "keys": {
      ".read": true,
      ".write": true,
      "$keyId": {
        ".validate": "newData.hasChildren(['code', 'app', 'duration', 'maxUses'])"
      }
    }
  }
}
```

---

## 🐛 Troubleshooting

### Issue: Keys not appearing
**Solution**: 
- Check Firebase connection
- Verify database URL
- Check internet connection
- Refresh page

### Issue: Key validation fails
**Solution**:
- Ensure Firebase initialized
- Check key code spelling
- Verify key is still active
- Check if key is expired

### Issue: Countdown not showing
**Solution**:
- Check browser console (F12)
- Verify Firebase enabled
- Check localStorage isn't full
- Try private/incognito mode

### Issue: Admin panel blank
**Solution**:
- Copy Firebase config from index.html
- Paste into admin-panel.html
- Make sure same Firebase project
- Check network tab for errors

---

## 🔒 Best Practices

### For Admin
- ✅ Regularly check analytics
- ✅ Set reasonable key limits
- ✅ Monitor suspicious patterns
- ✅ Backup keys periodically
- ✅ Update security rules if needed
- ✅ Archive old keys

### For Distribution
- ✅ Share via secure channels
- ✅ Announce duration clearly
- ✅ Provide clear instructions
- ✅ Track redemption rate
- ✅ Gather feedback

### For Users
- ✅ Save key code immediately
- ✅ Use before expiry
- ✅ Don't share key widely
- ✅ Report issues to admin
- ✅ Check expiry timer

---

## 📞 Support

### Common Questions

**Q: Có thể tạo bao nhiêu keys?**
A: Unlimited! Firebase free tier supports millions.

**Q: Key có thể extend được không?**
A: Có, admin có thể tạo key mới.

**Q: Nếu browser clear cache, key còn hoạt động không?**
A: Có! Vì timestamp lưu trên Firebase.

**Q: Có thể prevent sharing key không?**
A: Partially - can add device fingerprinting.

**Q: Có thể track ai dùng key không?**
A: Có - device ID + timestamp + IP.

---

## 🚀 Next Steps

1. ✅ Setup Firebase (nếu chưa)
2. ✅ Update admin-panel.html config
3. ✅ Create 10 test keys
4. ✅ Test key validation on website
5. ✅ Share keys with beta users
6. ✅ Monitor analytics
7. ✅ Gather feedback
8. ✅ Scale up if needed

---

**Happy key management! 🎉**
