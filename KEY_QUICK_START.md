# 🔑 Quick Reference - Key Management System

## 5-Minute Setup

### Step 1: Copy Firebase Config
```javascript
// From index.html, copy your Firebase config:
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "...",
  databaseURL: "...",
  projectId: "...",
  storageBucket: "...",
  messagingSenderId: "...",
  appId: "..."
};
```

### Step 2: Paste into admin-panel.html
Line ~150, replace:
```javascript
const firebaseConfig = {
  // ← Paste your config here
};
```

### Step 3: Open admin-panel.html
- Click "🔄 Tạo 10 Keys"
- Wait for creation
- Done! ✅

---

## 📋 Files Overview

| File | Purpose | Access |
|------|---------|--------|
| `index.html` | Main website | Public |
| `admin-panel.html` | Create/manage keys | Admin only |
| `KEY_MANAGEMENT_GUIDE.md` | Full documentation | Reference |

---

## 🎯 Workflow

### For Admin:
```
1. Open admin-panel.html
   ↓
2. Set: Duration (6h), Max Uses (10), App (PUBG)
   ↓
3. Click "🔄 Tạo 10 Keys" or "🔐 Tạo Key"
   ↓
4. Copy generated keys
   ↓
5. Share via Telegram/Zalo/etc
   ↓
6. Monitor analytics in admin panel
```

### For Users:
```
1. User opens website
   ↓
2. Clicks "🔑 Lấy Key" button
   ↓
3. Pastes key: CENIOS-ABC123XYZ
   ↓
4. Clicks ✅ Xác Nhận
   ↓
5. App kích hoạt 6 giờ! 🎉
```

---

## 🔧 Configuration

### Key Creation Parameters

| Setting | Default | Min | Max | Example |
|---------|---------|-----|-----|---------|
| Duration (hours) | 6 | 1 | 720 | 6 = 6h |
| Max Uses | 10 | 1 | 100 | 10 = 10x |
| App | PUBG | - | - | pubg/aov |

---

## 📊 Admin Dashboard Metrics

```
🔢 Total Keys          : Số keys đã tạo
🟢 Active Keys         : Còn hoạt động
📈 Total Used          : Tổng lần dùng
⚠️ Expired Keys        : Đã hết hạn
```

---

## ✨ Key Features

### User Side
- ✅ Simple key input modal
- ✅ Real-time countdown timer
- ✅ Clear success/error messages
- ✅ Auto-expire after duration
- ✅ Keyboard support (Enter to submit)

### Admin Side
- ✅ Create single or batch keys
- ✅ Real-time statistics
- ✅ Search keys by code
- ✅ Delete keys
- ✅ View usage history
- ✅ Progress bar for each key

### Backend (Firebase)
- ✅ Server-side validation
- ✅ Real-time counter sync
- ✅ Device tracking
- ✅ Timestamp logging
- ✅ Auto-expire mechanism
- ✅ Usage analytics

---

## 🛡️ Security

### Built-in
- ✅ XSS protection
- ✅ Input validation
- ✅ Server-side checks
- ✅ Real-time validation
- ✅ Device ID tracking
- ✅ Usage logging

### Against Common Attacks
- ✅ Cannot edit key in localStorage
- ✅ Cannot extend expiry manually
- ✅ Cannot increase usage limit
- ✅ Cannot use same device twice
- ✅ Cannot brute force keys

---

## 🎨 UI Elements

### Key Modal
```
┌─────────────────────────────┐
│ 🔑 Nhập Key Kích Hoạt      │
│                             │
│ [CENIOS-ABC123XYZ]         │
│                             │
│ [✅ Xác Nhận] [❌ Đóng]    │
│                             │
│ ⚠️ Không có key?            │
│ Lấy key free tại đây       │
└─────────────────────────────┘
```

### Success Message
```
✅ Kích hoạt thành công!
Hết hạn trong 6h
```

### Error Messages
```
❌ Key không hợp lệ
❌ Key đã hết hạn
❌ Key đã dùng hết số lần
⚠️ Firebase không kết nối
```

---

## 📱 Responsive

- ✅ Works on mobile
- ✅ Touch-friendly buttons
- ✅ Auto-size input
- ✅ Readable on small screens
- ✅ Full admin panel on tablet

---

## 💡 Pro Tips

### Maximize Engagement
- Create fresh keys daily
- Announce time windows clearly
- Set limited duration (6h is good)
- Set reasonable use limit (10-20)
- Promote on active hours

### Track Metrics
- Monitor analytics regularly
- Check device usage patterns
- See most used apps
- Track redemption rate
- Identify peak hours

### Prevent Abuse
- Set max uses limit (not too high)
- Use device tracking
- Monitor unusual patterns
- Rotate certificate regularly
- Archive old keys

---

## 🚀 Scaling

### If Keys Used Up Quickly
1. Create more keys
2. Increase max uses limit
3. Extend duration
4. Create themed batches

### If Not Many Users
1. Promote more
2. Lower max uses (more fresh keys)
3. Shorter duration (urgency)
4. Higher frequency (daily drops)

### If Server Load High
1. Monitor Firebase usage
2. Optimize queries
3. Add caching layer
4. Use read limits

---

## 📞 Emergency Procedures

### Key Compromised
1. Delete key from admin panel
2. Create new keys
3. Announce via Telegram
4. Update links

### Database Issues
1. Check Firebase console
2. Verify security rules
3. Check network connection
4. Fallback to local mode

### Admin Panel Broken
1. Check console (F12)
2. Verify Firebase config
3. Try private mode
4. Clear localStorage

---

## 🔑 API Reference

```javascript
// Open key modal
openKeyModal()

// Validate key
validateKey()

// Close modal
closeKeyModal()

// Check expiry
checkKeyExpiry()

// Device ID (auto-generated)
userDeviceId
```

---

## 📈 Expected Usage

### Day 1: Launch
- Create: 100 keys
- Duration: 6h
- Max Uses: 10
- Expect: 50-100 activations

### Week 1: Growth
- Daily keys: 100-200
- Improved: Based on feedback
- Monitor: Analytics

### Month 1: Optimization
- Seasonal: Adjust by day
- Events: Special batches
- Premium: Introduce paid keys

---

## ✅ Checklist

### Setup
- [ ] Firebase configured
- [ ] Admin config copied
- [ ] admin-panel.html working
- [ ] Can create keys
- [ ] Keys appear in list

### Testing
- [ ] Created 10 test keys
- [ ] Can validate key on website
- [ ] Countdown timer works
- [ ] Key expires correctly
- [ ] Error messages show

### Launch
- [ ] Security rules applied
- [ ] First keys created
- [ ] Shared with users
- [ ] Analytics enabled
- [ ] Support ready

---

**That's it! You're ready to go! 🚀**

For detailed info, see `KEY_MANAGEMENT_GUIDE.md`
