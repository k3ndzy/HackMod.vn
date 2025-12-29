# 🔥 Daily Key Release - Quick Reference

## In 30 Seconds

### Release a Key:
1. Open **admin-panel.html**
2. Go to **"🔥 Phát Hành Hôm Nay"** section
3. Paste key → Set hours (6) → Set uses (50) → Select app (PUBG/AOV)
4. Click **"🎁 Phát Hành Key Hôm Nay"**
5. ✅ Done! Website updates automatically

---

## Admin Panel Buttons

| Button | What It Does |
|--------|-------------|
| 🎁 Phát Hành Key Hôm Nay | Publish today's key |
| 🗑️ Hủy Key | Delete today's key |
| 📋 Copy | Copy key to clipboard |

---

## What Users See

```
🔥 KEY MIỄN PHÍ HÔM NAY
⏱️ Còn: 5h 23m 45s
📊 45/50 used
[🚀 KÍCH HOẠT KEY] [📋 Copy]
```

---

## Settings

| Setting | Default | Range | Notes |
|---------|---------|-------|-------|
| **Duration** | 6 hours | 1-24h | How long key works |
| **Max Uses** | 50 | 1-100+ | How many activations |
| **App** | PUBG | PUBG/AOV | Which app |

---

## Firebase Locations

```
/dailyKeys/{today's-date}/
  └─ Stores today's active key

/keys/{keyCode}/
  └─ Also stores here for validation
```

---

## Status Indicators

- ✅ **Active** = Users can use
- ⏰ **Expiring Soon** = Less than 1h left
- ❌ **Expired** = Removed from website
- 🔄 **Syncing** = Real-time update happening

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| Enter | Publish key (from form) |
| Escape | Cancel/Close |
| Cmd/Ctrl+C | Copy key code |

---

## Common Durations

| Time | Best For |
|------|----------|
| 2h | High demand, limited stock |
| 4h | Morning/evening shift |
| 6h | Standard daily release |
| 12h | Weekend marathon |

---

## Icons & Meanings

| Icon | Meaning |
|------|---------|
| 🔥 | Featured/Hot |
| 🔑 | Key code |
| ⏱️ | Time remaining |
| 📊 | Usage statistics |
| 🎮 | App name |
| ✅ | Success |
| ❌ | Error |
| 🚀 | Activate/Launch |

---

## Real-Time Updates

✅ **Automatic Sync**: When you publish a key in admin panel, it appears on website **instantly** (no refresh needed)

✅ **Countdown Sync**: Each second, countdown updates in real-time across all users

✅ **Usage Counter**: When user activates, counter updates live

---

## Example Daily Schedule

```
9:00 AM  → Release Key 1 (6h)      → Expires 3:00 PM
3:00 PM  → Release Key 2 (6h)      → Expires 9:00 PM
```

---

## Troubleshooting in 2 Steps

| Problem | Solution |
|---------|----------|
| Key not showing | Refresh page / Check Firebase |
| Can't publish | Check all fields filled / Firebase connection |
| Wrong countdown | Check system time accuracy |
| Key won't activate | Check if expired / Try refreshing |

---

## File Locations

- **Admin Panel**: `/admin-panel.html`
- **Main Website**: `/index.html`
- **Styling**: `/styles.css`
- **Documentation**: `/DAILY_KEY_RELEASE_SYSTEM.md`

---

## API Functions (for developers)

```javascript
// Publish today's key
addDailyKey()

// Remove today's key
removeDailyKey()

// Copy key to clipboard
copyDailyKeyFromWebsite()

// Load current key
loadAndDisplayDailyKey()

// Update countdown
updateDailyKeyCountdown(expiryTime)
```

---

## Firebase Permissions

Ensure your Firebase rules allow:
- ✅ Read `/dailyKeys` by all users
- ✅ Write `/dailyKeys` by authenticated admins
- ✅ Read `/keys` by all users
- ✅ Write `/keys` by authenticated admins

---

## Security Checklist

- ✅ Admin panel access restricted (use auth)
- ✅ Keys stored securely in Firebase
- ✅ Device ID prevents key sharing
- ✅ Usage counter prevents abuse
- ✅ Auto-expiry time-based

---

**That's it! You're ready to release daily keys! 🚀**

For more details, see: `DAILY_KEY_RELEASE_SYSTEM.md`
