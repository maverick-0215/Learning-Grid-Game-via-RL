# 🔧 Troubleshooting Guide

## Common Issues and Solutions

### Issue: Page doesn't load or shows blank screen

**Possible Causes:**
- Browser compatibility issue
- JavaScript is disabled
- File path contains special characters

**Solutions:**
1. Try a different browser (Chrome, Firefox, Edge recommended)
2. Check if JavaScript is enabled in browser settings
3. Move the folder to a simpler path (e.g., `C:\gridworld-rl\`)
4. Right-click `index.html` → "Open with" → Choose your browser

---

### Issue: Grid doesn't appear or is not clickable

**Possible Causes:**
- CSS not loaded properly
- Browser window too small
- JavaScript error

**Solutions:**
1. Refresh the page (F5 or Ctrl+R)
2. Zoom out if needed (Ctrl + Mouse wheel)
3. Open browser console (F12) and check for errors
4. Try maximizing browser window

---

### Issue: "Train Agents" button does nothing

**Possible Causes:**
- No algorithm selected
- JavaScript execution blocked
- Browser is frozen

**Solutions:**
1. Ensure at least one algorithm checkbox is checked
2. Check browser console (F12) for errors
3. Refresh the page and try again
4. Reduce episode count to 500 and try

---

### Issue: Training takes too long or browser freezes

**Possible Causes:**
- Too many episodes selected
- Large grid size (9×9 or 10×10)
- Browser performance

**Solutions:**
1. Reduce episodes (start with 500-1000)
2. Use smaller grid size (6×6 or 7×7)
3. Train one algorithm at a time
4. Close other browser tabs
5. Use a modern browser (Chrome/Edge for best performance)

---

### Issue: Learning curves look wrong or erratic

**This is usually NORMAL behavior!**

**What's Normal:**
- High initial steps (100-200)
- Gradual decrease over episodes
- Some noise/variance in the curve
- Occasional spikes upward

**What's NOT Normal:**
- Flat line at 200 steps throughout (path is blocked)
- Increasing trend (check hyperparameters)
- All algorithms fail (environment issue)

**Solutions:**
1. Check if path to goal is blocked by obstacles
2. Increase exploration (ε) to 0.2 or 0.3
3. Increase episodes to 1500-2000
4. Adjust learning rate (try α=0.1)
5. Reset and redesign environment

---

### Issue: All algorithms show ~200 steps consistently

**Cause:** Agent can't find path to goal (blocked or needs more exploration)

**Solutions:**
1. Click "Reset" and remove some obstacles
2. Ensure there's a valid path from start (top-left) to goal (bottom-right)
3. Increase exploration parameter (ε) to 0.3
4. Increase episodes to 2000+
5. Try a simpler environment first

---

### Issue: Chart doesn't display or is blank

**Possible Causes:**
- Canvas not supported (very unlikely)
- Training hasn't completed
- No results to display

**Solutions:**
1. Wait for training to complete
2. Check if "Training in progress..." message disappeared
3. Refresh page and run training again
4. Try a different browser
5. Check browser console (F12) for errors

---

### Issue: Statistics cards show "NaN" or weird values

**Possible Causes:**
- Training failed
- Division by zero
- Invalid hyperparameters

**Solutions:**
1. Reset environment and try again
2. Check hyperparameters are valid (α, γ, ε between 0 and 1)
3. Ensure episodes > 0
4. Refresh page

---

### Issue: Algorithms perform poorly (high steps, no improvement)

**This might be expected depending on environment!**

**Check:**
1. **Environment complexity** - Is there a clear path to goal?
2. **Episodes** - Complex environments need 1500-3000 episodes
3. **Exploration** - Too low (ε < 0.05) may miss optimal path
4. **Learning rate** - Too high (α > 0.5) may be unstable
5. **Discount factor** - Too low (γ < 0.7) may be too myopic

**Recommended starting values:**
- α = 0.1
- γ = 0.9
- ε = 0.1
- episodes = 1000

---

### Issue: Differences between algorithms are unclear

**This is normal for simple environments!**

**To see clear differences:**
1. Create a corridor or maze-like environment
2. Add obstacles that create risky vs safe paths
3. Use larger grids (8×8 or more)
4. Look at learning speed, not just final performance
5. Try the example scenarios in EXAMPLES.md

---

### Issue: Grid cells are too small or too large

**Solutions:**
1. Adjust browser zoom (Ctrl + Plus/Minus)
2. Use different device (mobile vs desktop)
3. The grid is responsive and should adapt
4. Maximum grid size is 10×10 by design

---

### Issue: Can't remove obstacles

**Cause:** Trying to click start (S) or goal (G) cells

**Solution:**
- Start and goal positions are fixed (top-left and bottom-right)
- You can only toggle regular empty cells
- This is by design for consistency

---

### Issue: Results differ each time I run

**This is EXPECTED and NORMAL!**

**Why:**
- RL algorithms use randomness (ε-greedy exploration)
- Each run takes different exploration paths
- This variance is inherent to RL

**What to do:**
- Run multiple times and average results
- Look at general trends, not exact numbers
- This is how real RL research works too!

---

## Performance Tips

### For Best Performance:
1. Use Chrome or Edge (fastest JavaScript engines)
2. Close unnecessary browser tabs
3. Start with smaller grids (5×5 or 6×6)
4. Use fewer episodes for initial testing (500-1000)
5. Train one algorithm at a time for large grids

### For Best Learning Results:
1. Start with empty grid to understand basics
2. Gradually add obstacles
3. Keep start in top-left, goal in bottom-right
4. Leave at least one clear path
5. Don't make environment too complex initially

---

## Browser Compatibility

### ✅ Fully Supported:
- Google Chrome (recommended)
- Microsoft Edge (recommended)
- Mozilla Firefox
- Safari (desktop)
- Opera

### ⚠️ Limited Support:
- Mobile browsers (smaller screen, may need zoom)
- Older browsers (IE not supported)

### Minimum Requirements:
- HTML5 support
- JavaScript enabled
- Canvas API support
- CSS Grid support

---

## Getting Help

### Steps to Debug:
1. **Open browser console** (F12 or right-click → Inspect)
2. **Click "Console" tab**
3. **Look for error messages** (red text)
4. **Take a screenshot** if you need to ask for help

### Common Console Errors:

**"Cannot read property of undefined"**
- Usually indicates a bug, try refreshing

**"Maximum call stack size exceeded"**
- Infinite loop detected, refresh page

**No errors but not working**
- Check if JavaScript is enabled

---

## Quick Fixes

### Nuclear Option (if nothing works):
1. Download the files again
2. Clear browser cache (Ctrl+Shift+Delete)
3. Try a different browser
4. Restart your computer
5. Check if antivirus is blocking

### Reset Everything:
1. Click the "Reset" button in the simulator
2. Or refresh the page (F5)
3. Or close and reopen the HTML file

---

## FAQ

**Q: Do I need internet?**
A: No! Works completely offline.

**Q: Do I need to install anything?**
A: No! Just open the HTML file.

**Q: Can I modify the code?**
A: Yes! Open `index.html` in any text editor.

**Q: Why isn't my trained agent shown on the grid?**
A: The current version shows learning curves. Path visualization could be added in future versions.

**Q: Can I save my environment?**
A: Not currently, but you can note down obstacle positions and recreate them.

**Q: Why are there only 3 algorithms?**
A: These are the fundamental RL algorithms. More could be added in future versions.

---

## Still Having Issues?

If you're still experiencing problems:

1. Make sure you're using a modern browser (2020+)
2. Try the example scenarios in EXAMPLES.md
3. Start with the simplest case (5×5, no obstacles, 500 episodes)
4. Check if the issue persists with different hyperparameters
5. Try on a different computer if available

---

## Known Limitations

1. **Grid size:** Limited to 10×10 (by design for performance)
2. **Episodes:** Works best up to 10,000 episodes
3. **Visualization:** Shows learning curves, not step-by-step agent movement
4. **Single-threaded:** Training blocks UI (expected for web apps)
5. **Memory:** Very large episode counts (>20,000) may slow down browser

These are design choices, not bugs!

---

**Remember:** Reinforcement learning is inherently noisy and random. Results will vary. This is normal and expected! 🎲
