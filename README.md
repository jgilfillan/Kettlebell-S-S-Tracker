# Simple & Sinister - Kettlebell Progress Tracker

A simple, elegant web application for tracking your progress through Pavel Tsatsouline's "Simple & Sinister" kettlebell workout program.

## 🌐 Access the App

This app can be accessed in two ways:

1. **GitHub Pages**: Visit `https://jgilfillan.github.io/Kettlebell-S-S-Tracker/` (Note: GitHub Pages must be enabled in repository settings)
2. **Local Use**: Download or clone this repository and open `index.html` in your web browser

### Running Locally

```bash
# Clone the repository
git clone https://github.com/jgilfillan/Kettlebell-S-S-Tracker.git

# Navigate to the directory
cd Kettlebell-S-S-Tracker

# Open index.html in your browser
# On macOS:
open index.html
# On Linux:
xdg-open index.html
# On Windows:
start index.html
```

Alternatively, you can simply download the `index.html` file and open it in any modern web browser.

## 📋 What is Simple & Sinister?

Simple & Sinister is a minimalist kettlebell training program developed by Pavel Tsatsouline. The program consists of just two exercises:

- **Kettlebell Swings**: 10 sets of 10 reps (100 total)
- **Turkish Get-Ups**: 10 total (5 per side)

Along with warmup and cooldown stretches, this creates a complete, time-efficient workout focused on building strength and conditioning.

## 🎯 How to Use the App

### 1. **Complete Your Warmup**
- Check off each warmup exercise as you complete it
- The warmup includes: Goblet Squats, Hip Bridges, Halos, Deadlifts, and light Swings

### 2. **Track Your Swings**
- For each of the 10 sets:
  - Adjust the weight (in kg) if needed
  - Select swing type (Two-Handed or One-Handed)
  - Check the "Done" box after completing the set
- Default weight is 24kg
- Default swing type is Two-Handed
- Use the "Apply to All Sets" buttons to quickly set all sets to the same weight or swing type

### 3. **Track Your Get-Ups**
- For each of the 10 get-ups (5 left, 5 right):
  - Adjust the weight (in kg) if needed
  - Check the "Done" box after completing each get-up
- Default weight is 16kg
- Sets alternate between Left (L) and Right (R) sides

### 4. **Complete Your Cooldown**
- Check off each cooldown stretch as you complete it
- Stretches include: 90/90 Stretch, Bretzel Stretch, Cross-body Shoulder Stretch, and Deep Squat Hold

### 5. **Save Your Workout**
- Click the **"Complete Workout"** button when finished
- Your workout will be saved with an automatically calculated score

#### How Scoring Works

The scoring system rewards both completion and progression:

- **Warmup**: 2 points per exercise (10 points total)
  - Complete all 5 warmup exercises for the full 10 points
  
- **Swings**: 5 points per set + weight bonus + type bonus (50-90+ points possible)
  - Base: 5 points per completed set
  - Weight bonus: (weight - 16kg) / 4
  - Type bonus: +2 points for one-handed swings
  - Example: 24kg two-handed swing = 5 + (24-16)/4 + 0 = **7 points**
  - Example: 24kg one-handed swing = 5 + (24-16)/4 + 2 = **9 points**
  - Complete all 10 sets at 24kg two-handed = 70 points
  - Complete all 10 sets at 24kg one-handed = 90 points
  
- **Get-Ups**: 5 points per set + weight bonus (50-70+ points possible)
  - Base: 5 points per completed get-up
  - Weight bonus: (weight - 16kg) / 4
  - Example: 16kg get-up = 5 + 0 = **5 points**, 24kg get-up = 5 + 2 = **7 points**
  - Complete all 10 get-ups at 24kg = 70 points
  
- **Cooldown**: 2.5 points per stretch (10 points total)
  - Complete all 4 cooldown stretches for the full 10 points

**Maximum Possible Score**: 140+ points (with standard weights and two-handed swings), higher with heavier weights or one-handed swings

**Perfect Workout Examples**: 
- All warmups (10) + All swings at 24kg two-handed (70) + All get-ups at 24kg (70) + All cooldowns (10) = **160 points**
- All warmups (10) + All swings at 24kg one-handed (90) + All get-ups at 24kg (70) + All cooldowns (10) = **180 points**

### 6. **View Your Progress**
- The stats bar at the top shows:
  - **Total Workouts**: Number of completed sessions
  - **Average Score**: Your average workout score
  - **Best Score**: Your highest score achieved
  - **Current Streak**: Number of consecutive calendar days with at least one workout

- The **Workout History** section displays all your past sessions with dates and scores

### 7. **Reset or Start Over**
- Click **"Reset"** to clear the current session without saving
- Use **"Clear History"** to delete all saved workout data (this cannot be undone)

## 💾 Data Storage

The app supports two storage modes:

| Mode | When active | Notes |
|------|-------------|-------|
| **Local (localStorage)** | Firebase not configured, or user not signed in | Data stays in your browser only |
| **Cloud (Firestore)** | Firebase configured **and** user signed in with Google | Data syncs across devices |

> **Note:** Local and cloud histories are independent. Data saved before signing in will not be automatically migrated to the cloud.

## 🔒 Google Authentication & Cloud Sync (optional manual setup)

Follow these steps once to enable Google sign-in and persistent cloud storage:

### Step 1 — Create a Firebase project

1. Go to [https://console.firebase.google.com/](https://console.firebase.google.com/) and sign in.
2. Click **Add project**, enter a name (e.g. `kettlebell-tracker`), then click **Continue** → **Create project**.

### Step 2 — Add a web app

1. In your project overview, click the **Web** icon (`</>`).
2. Enter a nickname (e.g. `Kettlebell Tracker`) and click **Register app**.
3. Firebase shows a `firebaseConfig` object — **copy all six values** (apiKey, authDomain, projectId, storageBucket, messagingSenderId, appId).

### Step 3 — Enable Google Authentication

1. In the Firebase console sidebar, click **Build → Authentication**.
2. Click **Get started**, then select the **Sign-in method** tab.
3. Click **Google**, toggle it **Enabled**, pick a support email, then click **Save**.

### Step 4 — Enable Firestore

1. In the sidebar click **Build → Firestore Database**.
2. Click **Create database**, choose **Production mode**, select a region, then click **Enable**.
3. Navigate to the **Rules** tab and replace the default rule with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/workouts/{workoutId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

4. Click **Publish**.

### Step 5 — Add your authorised domain

1. In the sidebar click **Build → Authentication → Settings → Authorized domains**.
2. Click **Add domain** and enter the domain where the app is hosted:
   - For GitHub Pages: `yourusername.github.io` (replace with your GitHub username)
   - For local testing: `localhost` is already included by default

### Step 6 — Paste the config into index.html

Open `index.html` and find the `FIREBASE_CONFIG` block near the top of the `<script>` section (search for `YOUR_API_KEY`). Replace all six placeholder values with the ones you copied in Step 2:

```js
const FIREBASE_CONFIG = {
  apiKey: "AIzaSy...",
  authDomain: "my-project.firebaseapp.com",
  projectId: "my-project",
  storageBucket: "my-project.appspot.com",
  messagingSenderId: "1234567890",
  appId: "1:1234567890:web:abc123"
};
```

Save the file and deploy (or reload locally). The **Sign in with Google** button will appear in the header.

## 🎨 Features

- **Clean, modern interface** with dark theme
- **Real-time progress tracking** with visual feedback
- **Automatic scoring system** that rewards consistency and progression
- **Workout history** to track your journey
- **Streak tracking** to maintain motivation
- **Responsive design** works on desktop and mobile devices
- **Google Sign-In** with cloud sync via Firebase (optional)

## 🏋️ Tips for Success

1. **Start Light**: If you're new to kettlebells, start with lighter weights than the defaults
2. **Focus on Form**: Quality over quantity - perfect your form before increasing weight
3. **Be Consistent**: Aim for 3-5 sessions per week
4. **Listen to Your Body**: Rest when needed; the program is designed for long-term progress
5. **Track Everything**: Use the app to monitor your progress and celebrate improvements

## 🛠️ Technical Details

This is a single-page application built with:
- Pure HTML, CSS, and JavaScript
- No build step or package manager required
- Lightweight and fast
- Works offline after initial load (localStorage mode)
- **Optional**: [Firebase](https://firebase.google.com/) (Authentication + Firestore) loaded from CDN for cloud sync

## 📄 License

This project is open source and available for personal use.

## 🙏 Credits

Based on the "Simple & Sinister" program by Pavel Tsatsouline.
