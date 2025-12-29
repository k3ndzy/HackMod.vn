# 🔥 Daily Key Release System - Visual Guide & Diagrams

## System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     DAILY KEY SYSTEM v1.0                        │
└─────────────────────────────────────────────────────────────────┘

┌──────────────┐      ┌──────────────┐      ┌──────────────┐
│  ADMIN SIDE  │      │  FIREBASE DB │      │  USER SIDE   │
│              │      │              │      │              │
│ Web Form     │      │  /dailyKeys/ │      │ Website      │
│  ↓           │  ←→  │    /{date}/  │  ←→  │  Display     │
│ Validate     │      │              │      │  Banner      │
│  ↓           │      │ Real-time    │      │              │
│ Publish      │      │ Listeners    │      │ Copy & Activate
└──────────────┘      └──────────────┘      └──────────────┘
       │                    │                      │
       │ addDailyKey()      │ db.ref().set()      │ loadAndDisplay()
       │ validateForm()     │ db.ref().on()       │ updateCountdown()
       │ showNotification() │ db.ref().remove()   │ copyToClipboard()
       │                    │                      │ validateKey()
```

---

## Data Flow Diagram

```
ADMIN RELEASES A KEY
│
├─ [1] Admin fills form
│   ├─ Key: CeniOs-hour-ijEXMWqmg1qyTa1d
│   ├─ Duration: 6 hours
│   ├─ Max Uses: 50
│   └─ App: PUBG
│
├─ [2] Click "Phát Hành Key Hôm Nay"
│   └─ addDailyKey() called
│
├─ [3] Validation
│   ├─ Check all fields filled ✅
│   ├─ Check duration 1-24 ✅
│   ├─ Check uses 1-100 ✅
│   └─ Check app is PUBG or AOV ✅
│
├─ [4] Calculate times
│   ├─ Created: now()
│   ├─ Expiry: now + 6 hours
│   └─ ExpiryDate: "2023-11-05"
│
├─ [5] Save to Firebase
│   ├─ /dailyKeys/2023-11-05/
│   └─ /keys/{keyCode}/
│
├─ [6] Update UI
│   ├─ Display box shows key
│   ├─ Show metadata
│   └─ Copy button enabled
│
├─ [7] Show notification
│   └─ "✅ Phát hành key hôm nay thành công!"
│
└─ [8] Real-time broadcast
    ├─ All browsers get notified
    ├─ Banners appear
    └─ Countdown starts
```

---

## Website User Flow

```
USER VISITS WEBSITE
│
├─ [1] Page loads
│   └─ DOMContentLoaded event
│
├─ [2] Check Firebase
│   └─ Query /dailyKeys/{today's-date}
│
├─ [3] Key exists?
│   │
│   ├─ YES:
│   │  ├─ displayDailyKeyBanner()
│   │  ├─ Setup countdown timer
│   │  ├─ Setup real-time listener
│   │  └─ Show banner
│   │
│   └─ NO:
│      └─ Hide banner (display: none)
│
├─ [4] User sees banner
│   │   🔥 KEY MIỄN PHÍ HÔM NAY
│   │   🔑 CeniOs-hour-ijEXMWqmg1q...
│   │   ⏱️ Còn: 5h 23m 45s
│   │   [Copy] [Activate]
│   │
│   └─ Two options:
│      │
│      ├─ Copy button clicked
│      │  └─ navigator.clipboard.writeText()
│      │     "✅ Đã copy key!"
│      │
│      └─ Activate clicked
│         └─ openKeyModal()
│            keyInput.value = keyCode
│            validateKey() runs
│            ✅ Access granted
│
├─ [5] Countdown updates
│   ├─ Every 1 second
│   ├─ Calculate: expiry - now
│   ├─ Format: "Xh Ym Zs"
│   └─ Update display
│
├─ [6] Key expires
│   ├─ Check: remaining <= 0
│   ├─ Show: "⏰ Hết hạn"
│   └─ Hide banner (display: none)
│
└─ [7] Admin releases new key
    └─ Banner reappears (new countdown)
```

---

## Real-Time Sync Timeline

```
Time    Admin Panel          Firebase Database        Website Browser
────    ────────────────     ─────────────────        ────────────────

00:00   User opens form

00:10   Fills form            
        Key: CeniOs-...
        Duration: 6h
        App: PUBG

00:15   Clicks "Publish"      

00:16   Validates input ✅    

00:17   Saves data        →   /dailyKeys/2023-11-05
                             ├─ code: CeniOs-...
                             ├─ app: pubg
                             ├─ duration: 6
                             └─ expiry: 1699145456789

00:18   UI updates        ←   Real-time listener
        Shows success         triggers on all
        Clears form          connected clients

00:19   ✅ Message shows                            ← All users get
                                                      notification
                                                    
00:20                                              displayDailyKeyBanner()
                                                   called instantly
                                                   
00:21                                              Countdown starts:
                                                   5h 59m 45s
                                                   5h 59m 44s
                                                   5h 59m 43s
                                                   ...

06:17                                              Countdown:
                                                   0h 0m 3s
                                                   0h 0m 2s
                                                   0h 0m 1s
                                                   0h 0m 0s
                                                   
06:18   Admin can          →   Status: "expired"  Banner hides
        release new key        Updates all clients  automatically
                                                   
06:19                                              New banner
                                                   appears with
                                                   new countdown
```

---

## Component Interaction Diagram

```
┌─────────────────────────────────────────────────────┐
│                    INDEX.HTML                        │
│  (Website for Users)                                 │
├─────────────────────────────────────────────────────┤
│                                                       │
│  ┌──────────────────────────────────────────────┐   │
│  │    Daily Key Banner (HTML)                   │   │
│  │  ┌─────────────────────────────────────────┐ │   │
│  │  │ 🔥 KEY MIỄN PHÍ HÔM NAY                 │ │   │
│  │  │ 🔑 Key Code Display                     │ │   │
│  │  │ ⏱️ Countdown Timer                      │ │   │
│  │  │ 📊 Usage Stats                          │ │   │
│  │  │ [Copy] [Activate]                       │ │   │
│  │  └─────────────────────────────────────────┘ │   │
│  └──────────────────────────────────────────────┘   │
│         │          │         │         │             │
│         ↓          ↓         ↓         ↓             │
│    loadAndDisplay  updateCount  copyKey  activateKey│
│         │          │         │         │             │
└─────────┼──────────┼─────────┼─────────┼─────────────┘
          │          │         │         │
          │ Firebase Queries   │         │
          │          │         │         │
┌─────────┼──────────┼─────────┼─────────┼─────────────┐
│         │          │         │         │             │
│  ┌──────▼──────────▼──────┐  │         │             │
│  │ Database Listeners     │  │         │             │
│  │ /dailyKeys/{date}      │  │         │             │
│  │ Real-time .on()        │  │         │             │
│  └────────────────────────┘  │         │             │
│                                │         │             │
│  ┌───────────────────────────┐ │         │             │
│  │ Firebase Database Paths   │ │         │             │
│  │ /dailyKeys/2023-11-05     │ │         │             │
│  │ /keys/{keyCode}           │ │         │             │
│  │ /statistics/              │─┼─────────┤             │
│  │ /users/{deviceId}         │ │         │             │
│  └───────────────────────────┘ │         │             │
│                                │         │             │
│         Validate Key ──────────┘         │             │
│         Update Counter ──────────────────┘             │
│                                                        │
│                 FIREBASE                              │
└────────────────────────────────────────────────────────┘

         ↑          ↑          ↑          ↑
         │          │          │          │
         
┌────────┴──────────┴──────────┴──────────┴──────────┐
│         ADMIN-PANEL.HTML                           │
│         (Admin Dashboard)                          │
├────────────────────────────────────────────────────┤
│                                                    │
│  ┌──────────────────────────────────────────────┐ │
│  │  Daily Key Form Section                      │ │
│  │  ┌─────────────────────────────────────────┐│ │
│  │  │ Key Code Input      [              ]    ││ │
│  │  │ Duration (hours)    [6            ]    ││ │
│  │  │ Max Uses            [50           ]    ││ │
│  │  │ App Selection       [PUBG ▼       ]    ││ │
│  │  │                                        ││ │
│  │  │ [🎁 Publish]  [🗑️ Delete]          ││ │
│  │  └─────────────────────────────────────────┘│ │
│  │                                              │ │
│  │  ┌─────────────────────────────────────────┐│ │
│  │  │ Current Daily Key Display                ││ │
│  │  │ Key: CeniOs-hour-...                    ││ │
│  │  │ Duration, Uses, Expiry                  ││ │
│  │  │ [Copy]                                  ││ │
│  │  └─────────────────────────────────────────┘│ │
│  └──────────────────────────────────────────────┘ │
│         │          │          │         │         │
│         ↓          ↓          ↓         ↓         │
│    addDailyKey  removeDailyKey  copyDailyKey    │
│    loadDailyKey                  showNotification│
│         │          │          │         │         │
│         └──────────┴──────────┴────────┬─────────┘
│                                        │
└────────────────────────────────────────┘
         │          │          │         
         Firebase Write/Read Operations
         Real-time Updates Back to UI
```

---

## State Machine Diagram

```
KEY LIFECYCLE

      ┌─ Admin Releases
      │  (addDailyKey)
      │
      ▼
┌──────────────┐
│  CREATED     │
│  ────────    │
│  just saved  │
│  in Firebase │
└──────┬───────┘
       │
       │ Time passes
       │ Countdown runs
       │ Users activating
       ▼
┌──────────────────┐
│  ACTIVE          │
│  ──────────      │
│  Users can use   │
│  Counter updates │
│  Countdown < 1h  │
└──────┬───────────┘
       │
       │ Time reached
       │ expiry date/time
       ▼
┌──────────────────┐
│  EXPIRING        │
│  ──────────      │
│  Last 1 hour     │
│  Warn users      │
│  Still usable    │
└──────┬───────────┘
       │
       │ Time reached
       │ expiry time exactly
       ▼
┌──────────────────┐
│  EXPIRED         │
│  ──────────      │
│  Cannot use      │
│  Banner hidden   │
│  In database     │
└──────┬───────────┘
       │
       │ Admin deletes
       │ or new day starts
       ▼
┌──────────────────┐
│  ARCHIVED        │
│  ──────────      │
│  Removed         │
│  Statistics kept │
└──────────────────┘
```

---

## Database Schema Visualization

```
FIREBASE REALTIME DATABASE

root
├── dailyKeys/
│   └── 2023-11-05/                    ← Today's date
│       ├── code: "CeniOs-hour-ijEXMWqmg1qyTa1d"
│       ├── app: "pubg"                ← PUBG or AOV
│       ├── duration: 6                ← Hours
│       ├── maxUses: 50                ← Total uses allowed
│       ├── used: 23                   ← Current uses
│       ├── created: 1699123456789     ← Timestamp created
│       ├── expiry: 1699145456789      ← Timestamp expires
│       ├── expiryDate: "2023-11-05"   ← Expiry date
│       ├── status: "active"           ← active/expired
│       └── createdAt: "05/11/2023..."  ← Readable time
│
├── keys/
│   └── CeniOs-hour-ijEXMWqmg1qyTa1d/  ← Key code as path
│       ├── code: "CeniOs-hour-ijEXMWqmg1qyTa1d"
│       ├── app: "pubg"
│       ├── duration: 6
│       ├── maxUses: 50
│       ├── used: 23
│       ├── created: 1699123456789
│       ├── expiry: 1699145456789
│       ├── isDaily: true              ← Marks as daily key
│       ├── status: "active"
│       └── lastUsedBy:
│           ├── deviceId: "device_1234_xxxx"
│           ├── timestamp: 1699130123456
│           └── date: "2023-11-05"
│
└── statistics/                        ← Optional analytics
    ├── dailyKeys/
    │   ├── 2023-11-05:
    │   │   ├── pubg: 45
    │   │   └── aov: 5
    │   └── 2023-11-04:
    │       ├── pubg: 38
    │       └── aov: 12
    │
    └── usage/
        └── CeniOs-hour-ijEXMWqmg1qyTa1d:
            ├── total: 50
            ├── today: 23
            └── devices: 15
```

---

## User Journey Map

```
BEFORE RELEASE                      AFTER RELEASE
─────────────────                  ─────────────

User visits website                User visits website
        │                                  │
        ├─ No banner                       ├─ Sees 🔥 Banner
        ├─ Shows normal apps               ├─ Shows key code
        └─ Can download app                ├─ Shows countdown
           with paid methods               ├─ Sees "5h 23m 45s"
                                          └─ Has 2 options:
                                             
                                          ┌─ Option A: Copy
                                          │  ├─ Clicks copy
                                          │  ├─ "✅ Key copied"
                                          │  ├─ Open game
                                          │  └─ Paste key
                                          │
                                          └─ Option B: Activate
                                             ├─ Clicks activate
                                             ├─ Modal opens
                                             ├─ Key pre-filled
                                             ├─ Validates
                                             └─ ✅ Access granted!
                                             
                                          User happy!
                                          ├─ Got free access
                                          ├─ Easy process
                                          ├─ Come back daily
                                          └─ Recommend to friends
```

---

## Countdown Algorithm

```
EVERY 1 SECOND:

1. Get current time
   now = Date.now()

2. Get expiry time from database
   expiry = key.expiry

3. Calculate remaining
   remaining = expiry - now

4. Check if expired
   if (remaining <= 0) {
     show "⏰ Hết hạn"
     hide banner
     stop countdown
     exit
   }

5. Convert to readable format
   hours = Math.floor(remaining / 3600000)
   minutes = Math.floor((remaining % 3600000) / 60000)
   seconds = Math.floor((remaining % 60000) / 1000)

6. Display
   "5h 23m 45s"

7. Update UI
   document.getElementById('timer').text = "5h 23m 45s"

8. Go back to step 1 (1 second later)
```

---

## Copy & Paste Flow

```
USER WANTS TO COPY KEY:

Click [📋 Copy] Button
        │
        ▼
copyDailyKeyFromWebsite()
        │
        ├─ Get key code from display
        │  keyCode = "CeniOs-hour-ijEXMWqmg1q..."
        │
        ├─ Access clipboard
        │  navigator.clipboard.writeText(keyCode)
        │
        ├─ Success callback
        │  showNotification("✅ Đã copy key!")
        │
        └─ Clipboard now has:
           "CeniOs-hour-ijEXMWqmg1qyTa1d"

User can now:
├─ Cmd/Ctrl+V in game input
├─ Send to friend
├─ Post on social media
└─ Paste anywhere

Key validation happens when:
└─ User pastes in activation modal
   └─ validateKey() runs
   └─ Firebase checks validity
   └─ ✅ Access granted
```

---

## Error Handling Flow

```
USER ACTION
    │
    ├─ Try to publish key
    │      │
    │      ├─ Check Firebase enabled?
    │      │  NO → "❌ Firebase không kết nối"
    │      │
    │      ├─ Check all fields filled?
    │      │  NO → "❌ Vui lòng điền đầy đủ"
    │      │
    │      ├─ Check duration valid (1-24)?
    │      │  NO → "❌ Duration must be 1-24"
    │      │
    │      ├─ Check uses valid (1-100)?
    │      │  NO → "❌ Uses must be 1-100"
    │      │
    │      ├─ Try to save to Firebase
    │      │  ERROR → "❌ Lỗi: " + error.message
    │      │
    │      └─ Success → "✅ Phát hành thành công!"
    │
    └─ All error paths show notification
       in red (error) or green (success)
```

---

**This visual guide shows the complete architecture and flow of the Daily Key Release System!** 🎯
