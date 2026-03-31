# 🚀 Quick Deployment Commands - Copy & Paste

## Prerequisites
```bash
# You should have:
npm --version          # Check npm installed
node --version         # Check Node.js installed
git --version          # Check git installed

# If any are missing, install them
```

---

## Commands to Run (In Order)

### 1. Setup Local Git
```bash
cd /path/to/the-middle-ground
git init
git config user.name "Your Name"
git config user.email "your.email@gmail.com"
git add .
git commit -m "Initial commit: The Middle Ground"
```

### 2. Create GitHub Repo
```bash
# Go to https://github.com/new
# Name it: the-middle-ground
# Then run these (replace YOUR_USERNAME):

git remote add origin https://github.com/YOUR_USERNAME/the-middle-ground.git
git branch -M main
git push -u origin main
```

### 3. Install Heroku CLI
```bash
npm install -g heroku
heroku login
```

### 4. Create Heroku App
```bash
# Replace app-name with something unique
# (must be unique across entire Heroku)
heroku create your-unique-app-name

# Examples:
# heroku create news-reader-2024
# heroku create middle-ground-news
# heroku create balanced-perspective
```

### 5. Set Environment Variables
```bash
# Replace with YOUR actual NewsAPI key
heroku config:set NEWS_API_KEY=your_actual_key_here

# Replace with your Heroku app URL
heroku config:set ALLOWED_ORIGINS=https://your-unique-app-name.herokuapp.com

# Set production
heroku config:set NODE_ENV=production

# Verify
heroku config
```

### 6. Deploy!
```bash
git push heroku main
```

### 7. Open Your App
```bash
heroku open
# Opens at: https://your-unique-app-name.herokuapp.com
```

### 8. Check Logs
```bash
heroku logs --tail
# Ctrl+C to exit
```

---

## Useful Commands After Deployment

```bash
# View logs
heroku logs --tail                    # Real-time logs
heroku logs -n 100                    # Last 100 lines
heroku logs --since 1h                # Logs from past hour

# Check status
heroku ps                             # Show running processes
heroku config                         # Show all env vars

# Restart
heroku restart

# View database size
heroku run "du -h news.db"

# Update environment variable
heroku config:set NEWS_API_KEY=new_key

# Remove environment variable
heroku config:unset NEWS_API_KEY

# Check app info
heroku apps:info

# Rollback to previous version
heroku releases:rollback
```

---

## Getting Your API Key

```
1. Go to https://newsapi.org
2. Click "Get API Key"
3. Sign up (FREE - no credit card)
4. Copy your API key (long string of letters/numbers)
5. Use in: heroku config:set NEWS_API_KEY=your_key_here
```

---

## After Deployment

### Test Your App
```bash
# In browser, go to:
https://your-unique-app-name.herokuapp.com

# Should see "The Middle Ground" homepage
# Try searching
# Try filtering
```

### Test API
```bash
curl https://your-unique-app-name.herokuapp.com/api/health
# Should return: {"status":"ok",...}

curl "https://your-unique-app-name.herokuapp.com/api/articles?search=climate"
# Should return articles
```

### Share Your Link
```
https://your-unique-app-name.herokuapp.com

Share on:
- Twitter/X
- Reddit
- HackerNews
- Facebook
- Discord
- Your website
```

---

## Common Issues

### "Can't find module"
```bash
heroku logs --tail
# Check the error message
# Usually need to: npm install missing-package
# Then redeploy
```

### "NEWS_API_KEY is not set"
```bash
heroku config:set NEWS_API_KEY=your_actual_key_here
heroku restart
```

### "Port not available"
```bash
# server-secure.js should have:
# const PORT = process.env.PORT || 5000;
# Check it's in the file
grep "process.env.PORT" server-secure.js
```

### "App sleeps after 30 min"
```bash
# Normal on free tier
# First request wakes it up (~10 sec)
# To remove sleep, upgrade: heroku dynos:upgrade standard-1x
```

---

## File Checklist

Before deploying, make sure you have:
```
✅ server-secure.js      (main app file)
✅ package.json          (dependencies)
✅ public/index.html     (frontend)
✅ .env.example          (config template)
✅ .gitignore            (what to ignore)
✅ Procfile              (how to run on Heroku)
✅ README.md             (documentation)
✅ SECURITY.md           (security guide)
```

---

## Next Steps After Going Live

### Week 1
- [ ] Share link with friends
- [ ] Post on social media
- [ ] Check logs daily
- [ ] Get feedback

### Week 2
- [ ] Apply for Google AdSense
- [ ] Add monitoring alerts
- [ ] Optimize based on feedback
- [ ] Check visitor stats

### Week 3
- [ ] Advertise on Reddit/HackerNews
- [ ] First revenue from ads!
- [ ] Plan premium features
- [ ] Scale infrastructure if needed

### Month 2+
- [ ] Reach 100K users
- [ ] Upgrade Heroku if needed ($7/month)
- [ ] Add custom domain ($12/year)
- [ ] Launch premium tier
- [ ] Expand to other countries

---

## Success! 🎉

Your app is live at: `https://your-unique-app-name.herokuapp.com`

You're running:
✅ Secure Node.js backend
✅ Auto-updating news database
✅ Beautiful responsive frontend
✅ Rate limiting & security headers
✅ Logging & monitoring
✅ Zero upfront cost
✅ Ready to monetize!

Start sharing and making money! 💰
