# 🔥 Daily Key Release System - User Guide

## Overview
The Daily Key Release System allows you to release **1-2 keys per day** to users through the Cen iOS Store website. Keys are released manually through the admin panel and automatically display on the main website with real-time countdown timers.

---

## 🎯 How It Works

### Flow:
1. **Admin Panel** → Release key daily → **Firebase Database** → **Website Display** → **Users activate**

### User Experience:
- Users see a **🔥 Featured Daily Key** banner on the main website
- Shows key code, countdown timer, and usage statistics
- Users can copy the key and activate it with one click
- Real-time countdown shows remaining time

### Admin Experience:
- Simple UI in admin panel to paste daily keys
- Set duration (default 6 hours)
- Set max uses (default 50)
- Select app (PUBG or AOV)
- Click "Phát Hành Key Hôm Nay" to publish

---

## 📋 Step-by-Step: Release a Daily Key

### 1. Access Admin Panel
```
Navigate to: admin-panel.html
```

### 2. Find "🔥 Phát Hành Hôm Nay" Section
Located at the top of the admin content area

### 3. Fill in the Form

| Field | Example | Description |
|-------|---------|-------------|
| **🔑 Key Code** | `CeniOs-hour-ijEXMWqmg1qyTa1d` | Your external key code |
| **⏱️ Duration** | `6` | How many hours until expiry |
| **📱 Max Uses** | `50` | How many times it can be used |
| **App** | `PUBG` or `AOV` | Which app this key is for |

**Example:**
```
Key Code: CeniOs-hour-ijEXMWqmg1qyTa1d
Duration: 6 hours
Max Uses: 50
App: FunTap PUBG (PUBG)
```

### 4. Click "🎁 Phát Hành Key Hôm Nay"
- Key is saved to Firebase
- Website updates automatically
- Banner appears on main page with countdown

### 5. View Current Daily Key
Below the form, you'll see:
```
🔑 Current Daily Key:
CeniOs-hour-ijEXMWqmg1qyTa1d

🎮 App: FunTap PUBG
⏱️ Duration: 6 giờ
📱 Max Uses: 50/50
📅 Expiry: [timestamp]

[Copy] [Delete]
```

### 6. Copy or Delete
- **Copy Button**: Copy to clipboard for sharing on social media
- **Delete Button**: Remove today's key (if you made a mistake)

---

## 📱 What Users See

### On Main Website:

```
┌─────────────────────────────────────┐
│ 🔥 KEY MIỄN PHÍ HÔM NAY              │
│                      Limited Time    │
├─────────────────────────────────────┤
│ 🎮 FunTap PUBG                       │
│                                      │
│ 🔑 Mã: CeniOs-hour-ijEXMWqmg1q...  │
│       [📋 Copy]                       │
│                                      │
│ ⏱️ Còn: 5h 23m 45s                   │
│ 📊 45/50 used | ⏳ 6h duration        │
├─────────────────────────────────────┤
│      [🚀 KÍCH HOẠT KEY]             │
└─────────────────────────────────────┘
```

### Features:
- **Glowing red banner** with gradient background (🔥 Eye-catching)
- **Real-time countdown** - updates every second
- **Copy button** - one-click copy to clipboard
- **Activate button** - opens key validation modal
- **Usage stats** - shows used vs max uses
- **Auto-hide** - disappears when key expires

---

## ⏱️ Key Lifecycle

| Status | Duration | Action | What Happens |
|--------|----------|--------|--------------|
| **Active** | < Duration | Users can activate | Key works normally |
| **Expiring** | < 1 hour | Users can still activate | Countdown shows red |
| **Expired** | Time passed | Cannot activate | Banner disappears |

---

## 🔧 Technical Details

### Firebase Database Structure

```json
/dailyKeys/{YYYY-MM-DD}/ {
  "code": "CeniOs-hour-ijEXMWqmg1qyTa1d",
  "app": "pubg",
  "duration": 6,
  "maxUses": 50,
  "used": 23,
  "created": 1699123456789,
  "expiry": 1699145456789,
  "expiryDate": "2023-11-05",
  "status": "active",
  "createdAt": "05/11/2023 12:30:56"
}
```

### Real-Time Sync
- Changes in admin panel → **Instant update** on website
- No page refresh needed
- Countdown timer updates every second
- If key expires, banner auto-hides

---

## 📊 Usage Statistics

### View in Admin Panel
- **Used**: How many times activated
- **Max Uses**: Total activations allowed
- **Duration**: Hours from creation to expiry
- **Expiry**: Exact time key stops working

### Example:
```
45/50 used - Users have activated 45 times out of 50 allowed
```

---

## ✅ Best Practices

### Daily Release Schedule
- **Morning** (9:00 AM): Release first key → 6h duration → Expires 3:00 PM
- **Afternoon** (3:00 PM): Release second key → 6h duration → Expires 9:00 PM

### Settings Recommendation
- **Duration**: 6 hours (good balance)
- **Max Uses**: 50 (prevents abuse)
- **Timing**: Before peak user hours

### Sharing on Social Media
```
🔥 KEY MIỄN PHÍ HÔM NAY 🔥

✅ PUBG MOBILE - 6 HOURS FREE

🔑 Code: CeniOs-hour-ijEXMWqmg1qyTa1d
⏳ Valid until 3:00 PM today
📊 Only 50 uses available

💬 Comment to activate!
```

---

## 🚨 Troubleshooting

### Issue: Key doesn't appear on website
**Solution:**
1. Check Firebase connection (refresh page)
2. Verify key code is correct
3. Check if today's date is correct in database

### Issue: Key expires too fast
**Solution:**
1. Increase duration in admin panel
2. Delete and re-add with correct hours
3. Check server time (should match client time)

### Issue: Can't copy key
**Solution:**
1. Click copy button again
2. Use manual copy (Cmd+C)
3. Check browser permissions

### Issue: Countdown timer shows wrong time
**Solution:**
1. Refresh page
2. Check system clock (must be accurate)
3. Clear browser cache

---

## 🔐 Security

### Key Protection
- Keys stored in Firebase (secure database)
- Device tracking prevents sharing
- Usage counter prevents abuse
- Auto-expiry prevents indefinite use

### Admin Security
- Access only through admin-panel.html
- Stored in browser localStorage
- Should be hosted on secure server (HTTPS)

### User Security
- Keys are one-time use per activation
- Device ID prevents key selling
- Expiry ensures limited lifespan

---

## 📞 Support

### Common Issues
1. **Key not working?** → Check if expired
2. **Can't see banner?** → Refresh page
3. **Firebase error?** → Check internet connection
4. **Wrong app shown?** → Delete and re-add

### Questions?
Reference the Firebase setup guide or KEY_MANAGEMENT_GUIDE.md

---

## 🎉 Example Workflow

### 9:00 AM - Release Morning Key
```
Key: CeniOs-hour-ijEXMWqmg1qyTa1d
Duration: 6 hours
Max Uses: 50
App: PUBG

✅ Published at 9:00 AM
⏰ Expires at 3:00 PM
```

### 2:50 PM - Key Almost Expired
```
Banner shows: ⏰ Apenas 10m 15s
Users rushing to activate
24 activations already
```

### 3:00 PM - Banner Disappears
```
Key automatically removed from website
Database shows "expired"
Admin can release new key
```

### 3:00 PM - Release Afternoon Key
```
Key: CeniOs-hour-kjf9M2nd92bxZa5m
Duration: 6 hours
Max Uses: 50
App: AOV

✅ Published at 3:00 PM
⏰ Expires at 9:00 PM
```

---

## 📈 Monitoring

### Daily Key Analytics
- **Total Activations**: Count per day
- **Popular Keys**: Most used
- **App Distribution**: PUBG vs AOV
- **Time Analysis**: Peak usage hours

### Stored in Firebase at:
```
/keyAnalytics/{date}/{appId}/
  - activations: number
  - uniqueDevices: number
  - averageSessionTime: number
```

---

## 🎯 Next Steps

1. ✅ Admin panel daily key section ready
2. ✅ Website displays key with countdown
3. ✅ Real-time Firebase sync working
4. 🔄 Setup backup key system (optional)
5. 🔄 Add email notifications for admins
6. 🔄 Create analytics dashboard

---

**Happy releasing! 🚀 The system is designed to give your users free daily keys while keeping everything simple and secure.**
