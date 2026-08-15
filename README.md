# Jili Super Ace Slot Demo

Build a web-based slot machine game inspired by Jili Super Ace.

## ✨ Features

### 🎮 Gameplay
- **5 Reels × 4 Rows** grid layout
- **Jili-style Symbols**: A, K, Q, J (playing cards), 7, 🍒 Cherry, 💎 Diamond, 🔔 Bell
- **Special Symbols**: 
  - ⭐ **WILD** (Super Ace) - 2.5× multiplier, glowing green
  - ✨ **SCATTER** (Magic) - 2× multiplier, glowing orange
- **Winning Combos**: 3, 4, or 5 symbols in a row (horizontal)
- **Multiplier System**: ×1, ×2, ×3, ×5 bet multipliers
- **Dynamic Payouts**: Win amounts scale with match length and multipliers

### 🎯 User Interface
- **Premium Purple/Gold Casino Theme** with glowing effects
- **Real-time Stats Display**:
  - Balance (player's current coins)
  - Bet (current bet amount × multiplier)
  - Win (latest win amount)
- **Control Buttons**:
  - 🎯 **SPIN** (Normal speed, 1.5s animation)
  - ⚡ **TURBO** (Fast speed, 0.6s animation)
  - 💰 **BUY BONUS** (100 coins → 250 coins reward)
- **Multiplier Bar** at top for quick bet adjustment
- **Info Bar** displays game status and messages

### 🔔 Visual Effects
- **Spinning Animation**: All 20 slots animate smoothly with 3D rotation effect
- **Win Glow**: Matched symbols pulse with golden light
- **Overlay Messages**: Large pop-up notifications for wins (auto-fade after 2.5s)
- **Color-coded Symbols**:
  - WILD: Bright green gradient with glow
  - SCATTER: Bright orange/yellow gradient with glow
  - Regular: Purple/blue gradient

### 📊 Game Mechanics
- **Starting Balance**: 1000 coins
- **Base Bet**: 10 coins (multiplied by selected multiplier)
- **Bonus Rewards**:
  - 3+ SCATTER symbols: +100× bet
  - 3+ WILD symbols: +150× bet
  - 3-in-a-row combos: Variable payout (20-40 base + length bonus)
- **Unlimited Spins**: Play as long as you have balance
- **No House Edge Demo**: Focus on fun gameplay

### 🔥 Firebase Analytics Integration
**Real-time Event Tracking**:
- `game_session_start` - Player joins
- `spin` - Each spin attempt (bet, multiplier, turbo mode)
- `spin_win` - Winning spin (amount, balance, multiplier)
- `spin_loss` - Losing spin (bet lost, balance)
- `scatter_bonus` - SCATTER bonus triggered
- `wild_bonus` - WILD bonus triggered
- `bonus_purchase` - BUY BONUS activated
- `multiplier_change` - Multiplier changed
- `game_session_end` - Player leaves (total stats)

**Firebase Project**: `jili-c6b1a`
- Real-time event monitoring via Firebase Console
- Session tracking with timestamps
- Player behavior analytics

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| **Frontend** | HTML5, CSS3, Vanilla JavaScript (ES6) |
| **Analytics** | Firebase Analytics (via Web SDK v12.17.1) |
| **Styling** | CSS Grid, CSS Animations, Gradients |
| **State Management** | JavaScript Object (gameState) |
| **Async Operations** | Promises, async/await |

---

## 📁 File Structure

```
Jili/
├── index.html          # Single-file web application
│   ├── <style>         # All CSS (embedded)
│   │   ├── Casino theme styling
│   │   ├── Grid layout
│   │   ├── Button animations
│   │   └── Overlay effects
│   ├── <div>           # HTML structure
│   │   ├── Header (title)
│   │   ├── Stats row (Balance/Bet/Win)
│   │   ├── Multiplier bar (×1 ×2 ×3 ×5)
│   │   ├── Slot grid (5×4)
│   │   ├── Action buttons (SPIN/TURBO/BONUS)
│   │   ├── Info bar (messages)
│   │   └── Firebase status indicator
│   └── <script>        # All JavaScript (embedded)
│       ├── Firebase initialization
│       ├── Game state management
│       ├── Spin mechanics
│       ├── Win detection
│       ├── Event logging
│       └── UI updates
└── README.md           # This file
```

---

## 🚀 How to Use

### 1. **Open in Browser**
   - Download or clone the repository
   - Open `index.html` directly in any modern browser
   - No server or build process needed

### 2. **Play the Game**
   ```
   1. Set your bet multiplier (×1, ×2, ×3, ×5)
   2. Click SPIN to spin the reels
   3. Match 3+ symbols in a row to win
   4. Use TURBO for faster spins
   5. Buy BONUS for extra coins
   6. Watch your balance and win stats update
   ```

### 3. **Track Analytics**
   - Go to [Firebase Console](https://console.firebase.google.com)
   - Select project: `jili-c6b1a`
   - Navigate to **Analytics** → **Realtime** or **Events**
   - Watch events stream in real-time as you play

### 4. **Deploy to GitHub Pages** (Optional)
   ```bash
   # Push to GitHub
   git add index.html README.md
   git commit -m "Deploy Jili Super Ace demo"
   git push origin main
   
   # Enable GitHub Pages in repo settings
   # Your game will be live at: https://aniflexai.github.io/Jili/
   ```

---

## 🎲 Game Rules

### Winning Combinations
- **3-in-a-row**: Base payout (20 + length bonus) × bet × multiplier
- **4-in-a-row**: 2× base payout × bet × multiplier
- **5-in-a-row**: 3× base payout × bet × multiplier

### Special Symbols
| Symbol | Effect | Multiplier |
|--------|--------|-----------|
| ⭐ WILD | Substitute any symbol | 2.5× payout |
| ✨ SCATTER | Bonus trigger (3+) | 2× payout |
| A, K, Q, J | Playing cards | 1× payout |
| 7 | Lucky number | 1× payout |
| 🍒 Cherry | Fruit symbol | 1× payout |
| 💎 Diamond | Gem symbol | 1× payout |
| 🔔 Bell | Bell symbol | 1× payout |

### Bonuses
- **SCATTER Bonus** (3+ ✨): +100× current bet
- **WILD Bonus** (3+ ⭐): +150× current bet
- **BUY BONUS** (100 coins): Instant +250 coins

### Balance Rules
- Starting balance: **1000 coins**
- Minimum bet: **10 coins** (×1 multiplier)
- Maximum active bet: **50 coins** (×5 multiplier)
- Auto-disable SPIN if balance < current bet

---

## 📊 Event Tracking Examples

### Spin Event
```json
{
  "event": "spin",
  "parameters": {
    "multiplier": 3,
    "bet_amount": 30,
    "turbo_mode": false,
    "balance_before": 970
  }
}
```

### Win Event
```json
{
  "event": "spin_win",
  "parameters": {
    "win_amount": 180,
    "balance_after": 1150,
    "multiplier_used": 3,
    "total_spins": 5
  }
}
```

### Session End Event
```json
{
  "event": "game_session_end",
  "parameters": {
    "final_balance": 1150,
    "total_spins": 5,
    "total_wins": 2,
    "total_losses": 3,
    "net_change": 150,
    "timestamp": "2026-08-15T19:53:21Z"
  }
}
```

---

## 🔧 Customization

### Change Starting Balance
Edit line ~391:
```javascript
const gameState = {
    balance: 5000,  // Change this value
    bet: 10,
    multiplier: 3,
    // ...
};
```

### Add More Symbols
Edit line ~435-440:
```javascript
const SYMBOLS = {
    'A': 'A',
    'K': 'K',
    // Add more here
    '🎰': '🎰',
};
```

### Adjust Win Payouts
Edit the `checkWins()` function (~447-515):
```javascript
const baseWin = gameState.bet * (50 + matchLength * 10);  // Change multipliers
```

### Change Colors
Edit CSS variables in `<style>` section:
- `#ffd700` - Gold
- `#ff6400` - Orange
- `#00ff88` - Green (WILD)
- `#16213e` - Dark blue (background)

---

## ✅ Testing Checklist

- [x] All 20 slots spin smoothly
- [x] Symbols randomize on each spin
- [x] 3, 4, 5-in-a-row combos detected
- [x] WILD and SCATTER bonuses trigger correctly
- [x] Multipliers work (×1, ×2, ×3, ×5)
- [x] Unlimited spins until balance depleted
- [x] Firebase events log to console
- [x] Overlay messages appear and fade
- [x] Stats update correctly
- [x] Responsive design (mobile-friendly)
- [x] No console errors
- [x] BUY BONUS increases balance properly
- [x] TURBO mode spins faster than normal
- [x] SPIN button disables during spin
- [x] Info messages display correctly

---

## 🐛 Known Issues & Limitations

1. **Demo Only**: No real money transactions. All coins are for entertainment.
2. **Local Only**: Balance resets on page refresh. Use Firebase Firestore for persistence (future feature).
3. **No Authentication**: Anyone can play. Add Google login for user tracking (future feature).
4. **No Sound**: Visual effects only. Could add sound effects (future feature).
5. **Browser Only**: Desktop and tablet optimized. Mobile UX can be improved.

---

## 🚀 Future Enhancements

- [ ] Google Sign-In for player authentication
- [ ] Firestore for persistent player data
- [ ] Sound effects and background music
- [ ] Mobile-optimized touch controls
- [ ] Leaderboard (high scores, most wins)
- [ ] Different game modes (free play, tournament)
- [ ] Custom symbol themes
- [ ] Network multiplayer
- [ ] Progressive jackpot
- [ ] Seasonal events and promotions

---

## 📄 License

Apache License 2.0 - See LICENSE file for details

---

## 👨‍💻 Author

**AniFlexAI**
- GitHub: [@aniflexai](https://github.com/aniflexai)
- Project: Jili Super Ace Slot Demo
- Built: August 2026

---

## 📞 Support

For issues, feature requests, or questions:
1. Check the troubleshooting section above
2. Review Firebase Console for analytics issues
3. Open a GitHub issue in the repository
4. Check browser console (F12) for error messages

---

## 🎉 Enjoy the Game!

Thanks for playing Jili Super Ace! May the reels be in your favor! 🍀✨🎰

**Happy Spinning!** 🎲🎯
