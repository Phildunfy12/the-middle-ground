# 🚀 The Middle Ground - Deployment Checklist

## BEFORE YOU START

You need 3 things (all free):
1. **GitHub account** - https://github.com/signup
2. **Heroku account** - https://signup.heroku.com
3. **NewsAPI key** - https://newsapi.org (no card needed)

---

## STEP 1: Get Your API Key (2 minutes)

```bash
# Go to https://newsapi.org
# Click "Get API Key"
# Sign up (free)
# Copy your API key (looks like: a1b2c3d4e5f6g7h8i9j0)
# SAVE THIS - you'll need it in Step 5
```

**You now have:** ✅ API Key

---

## STEP 2: Setup Git Locally (5 minutes)

**On your computer:**

```bash
# Open terminal/command prompt
# Go to the folder with your code
cd /path/to/the-middle-ground

# Initialize git repository
git init

# Configure git
git config user.name "Your Name"
git config user.email "your.email@example.com"

# Add all files
git add .

# Make first commit
git commit -m "Initial commit: The Middle Ground news aggregator"
```

**You now have:** ✅ Local git repo

---

## STEP 3: Create GitHub Repository (3 minutes)

1. Go to https://github.com/new
2. **Repository name:** `the-middle-ground`
3. **Description:** "Unbiased news aggregator with balanced perspectives"
4. **Public** (leave public - no code security risk with news app)
5. Click **"Create repository"**

GitHub shows you commands. Copy and run:

```bash
git remote add origin https://github.com/YOUR_USERNAME/the-middle-ground.git
git branch -M main
git push -u origin main

# Replace YOUR_USERNAME with your actual GitHub username
```

**Verify:** Go to github.com/YOUR_USERNAME/the-middle-ground - should see your files

**You now have:** ✅ GitHub repository

---

## STEP 4: Create Heroku App (3 minutes)

```bash
# Install Heroku CLI
npm install -g heroku

# Login (opens browser)
heroku login

# Create app (choose a unique name!)
heroku create your-unique-app-name

# Examples:
# heroku create news-middle-ground-2024
# heroku create balanced-news-reader
# heroku create unbiased-news-hub

# Heroku tells you: "https://your-unique-app-name.herokuapp.com"
# SAVE THIS URL - this is where your app will live
```

**You now have:** ✅ Heroku app created

---

## STEP 5: Set Environment Variables (2 minutes)

**In your terminal:**

```bash
# Set your NewsAPI key
heroku config:set NEWS_API_KEY=your_actual_api_key_here

# Example (replace with YOUR actual key):
# heroku config:set NEWS_API_KEY=a1b2c3d4e5f6g7h8i9j0

# Set production mode
heroku config:set NODE_ENV=production

# Set allowed origins (replace with your Heroku URL)
heroku config:set ALLOWED_ORIGINS=https://your-unique-app-name.herokuapp.com

# Verify they're set
heroku config

# Should show all 3 variables ✓
```

**You now have:** ✅ Environment variables configured

---

## STEP 6: Deploy to Heroku (2 minutes)

```bash
# Push your code to Heroku
git push heroku main

# Watch the build happen...
# Takes 30-60 seconds
# Should see: "Launching..."

# When done, see:
# "remote: Verifying deploy... done."
# "To https://git.heroku.com/your-app-name.git"
```

**If you see an error:**
- Check `heroku logs --tail` to see what went wrong
- Most common: NODE_ENV or NEWS_API_KEY not set correctly

**You now have:** ✅ App deployed!

---

## STEP 7: Open Your App (1 minute)

```bash
# Open in browser automatically
heroku open

# OR manually go to:
# https://your-unique-app-name.herokuapp.com

# Should see "The Middle Ground" homepage!
```

---

## STEP 8: Test Everything (5 minutes)

### Test 1: Health Check
```bash
curl https://your-unique-app-name.herokuapp.com/api/health

# Should return: {"status":"ok",...}
```

### Test 2: Load Articles
Go to `https://your-unique-app-name.herokuapp.com` in browser
- Should see article cards loading
- Try searching for something
- Try filtering by perspective

### Test 3: Check Logs
```bash
heroku logs --tail

# Should see:
# "The Middle Ground server running..."
# No errors = success! ✅

# Exit logs: Ctrl+C
```

---

## STEP 9: Setup Auto-Deployment (Optional, 2 minutes)

When you push to GitHub, automatically deploy to Heroku:

```bash
# Connect GitHub to Heroku
heroku apps:info

# Copy your app name, then:
# Go to: https://dashboard.heroku.com/apps
# Click your app
# Go to "Deploy" tab
# Click "Connect to GitHub"
# Search for "the-middle-ground"
# Click "Connect"
# Click "Enable Automatic Deploys"

# Now: Every time you git push origin main, it auto-deploys! ✅
```

---

## STEP 10: Monitor Your App (Ongoing)

```bash
# View live logs
heroku logs --tail

# Check performance
heroku metrics

# View all config variables
heroku config

# Restart if needed
heroku restart
```

---

## 🎉 You're Live!

Your app is now running at: `https://your-unique-app-name.herokuapp.com`

**Share this link with friends!**

---

## What to Do Next

### Week 1: Get Traffic
- Share link on social media
- Post on Reddit/HackerNews
- Tell friends & family
- Get first 1,000 users

### Week 2: Setup Monetization
- Sign up for Google AdSense: https://adsense.google.com
- Submit your site for approval (takes 1-2 weeks)
- Place ad code in your app
- Start earning money!

### Week 3: Optimize
- Monitor which searches are popular
- Add trending topics section
- Improve UI based on user feedback
- Monitor logs for errors

### Month 2: Scale
- At 100K users, upgrade Heroku ($7/month)
- Consider custom domain ($12/year)
- Add email newsletter feature
- Launch premium subscription

---

## If Something Goes Wrong

### App won't start
```bash
heroku logs --tail
# Read error message carefully
# Common issues:
# - NEWS_API_KEY not set
# - PORT not set
# - Dependencies not installed
```

### Articles not showing
```bash
# Check API key is set
heroku config | grep NEWS_API_KEY

# Check logs
heroku logs --tail

# Restart
heroku restart
```

### Slow response
```bash
# Free tier apps sleep after 30 min inactivity
# First request wakes them up (takes 10 seconds)
# This is normal!

# To remove sleep, upgrade to paid tier ($7/month)
```

### Getting 429 errors
```bash
# You're hitting rate limits
# This is good! Means you have traffic!
# Either:
# 1. Upgrade Heroku ($7) to get more resources
# 2. Optimize your code to use less API calls
```

---

## Troubleshooting Commands

```bash
# View last 50 lines of logs
heroku logs -n 50

# View logs from last hour
heroku logs --tail --since 1h

# Check running processes
heroku ps

# Restart the app
heroku restart

# Check config variables
heroku config

# Update a config variable
heroku config:set NEWS_API_KEY=new_key_here

# View database size (SQLite)
heroku run "du -h news.db"

# SSH into dyno (advanced)
heroku ps:exec
```

---

## Next: Monetization

Once you have traffic (10K+ users), setup Google AdSense:

1. Go to https://adsense.google.com
2. Sign up with your site URL
3. Google reviews your site (1-2 weeks)
4. Once approved, add ad code to `public/index.html`
5. Start earning!

**At 10K monthly users, you'll make $30-50/month**

---

## Custom Domain (Optional, $12/year)

Once you have traffic, buy a domain:

```bash
# Buy domain on Namecheap, GoDaddy, or Google Domains
# Then add to Heroku:

heroku domains:add www.themiddleground.com

# Setup SSL (automatic)
heroku certs:auto:enable

# Update DNS (instructions from Heroku)

# Done! Your app is now at your custom domain
```

---

## Success! 🎉

You now have:
✅ Live news aggregator
✅ 6-month searchable database  
✅ Automatic article updates
✅ Rate limiting & security
✅ $0 hosting cost
✅ Ready to monetize

**Next step: Start getting traffic and making money!**

---

## Questions?

If you get stuck:
1. Check `heroku logs --tail` for errors
2. Re-read the DEPLOY_HEROKU.md guide
3. Check Heroku docs: https://devcenter.heroku.com/
4. Check Node.js docs: https://nodejs.org/docs/

You've got this! 🚀
