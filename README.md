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
  - Check the "Done" box after completing the set
- Default weight is 24kg

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
  
- **Swings**: 5 points per set + weight bonus (50-70+ points possible)
  - Base: 5 points per completed set
  - Weight bonus: +0.25 points for every 4kg above 16kg
  - Example: 24kg swing set = 5 + (24-16)/4 = 7 points
  - Complete all 10 sets at 24kg = 70 points
  
- **Get-Ups**: 5 points per set + weight bonus (50-70+ points possible)
  - Base: 5 points per completed get-up
  - Weight bonus: +0.25 points for every 4kg above 16kg
  - Example: 16kg get-up = 5 points, 24kg get-up = 7 points
  - Complete all 10 get-ups at 24kg = 70 points
  
- **Cooldown**: 2.5 points per stretch (10 points total)
  - Complete all 4 cooldown stretches for the full 10 points

**Maximum Possible Score**: 120+ points (with standard weights), higher with heavier weights

**Perfect Workout Example**: 
- All warmups (10) + All swings at 24kg (70) + All get-ups at 24kg (70) + All cooldowns (10) = **160 points**

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

Your workout data is stored locally in your browser using the Web Storage API. This means:
- ✅ Your data stays private on your device
- ✅ No internet connection required after initial load
- ✅ Data persists between sessions
- ⚠️ Clearing browser data will delete your workout history

## 🎨 Features

- **Clean, modern interface** with dark theme
- **Real-time progress tracking** with visual feedback
- **Automatic scoring system** that rewards consistency and progression
- **Workout history** to track your journey
- **Streak tracking** to maintain motivation
- **Responsive design** works on desktop and mobile devices

## 🏋️ Tips for Success

1. **Start Light**: If you're new to kettlebells, start with lighter weights than the defaults
2. **Focus on Form**: Quality over quantity - perfect your form before increasing weight
3. **Be Consistent**: Aim for 3-5 sessions per week
4. **Listen to Your Body**: Rest when needed; the program is designed for long-term progress
5. **Track Everything**: Use the app to monitor your progress and celebrate improvements

## 🛠️ Technical Details

This is a single-page application built with:
- Pure HTML, CSS, and JavaScript
- No external dependencies or frameworks
- Lightweight and fast
- Works offline after initial load

## 📄 License

This project is open source and available for personal use.

## 🙏 Credits

Based on the "Simple & Sinister" program by Pavel Tsatsouline.
