# 🔥 Firebase Setup Instructions for Food Review App

## Step 1: Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project"
3. Name it: `food-reviews` (or whatever you want)
4. Disable Google Analytics (you don't need it)
5. Click "Create project"

---

## Step 2: Enable Google Authentication

1. In your Firebase project, go to **Build** → **Authentication**
2. Click "Get started"
3. Click on **Google** under "Sign-in providers"
4. Toggle "Enable"
5. Add your email as the project support email
6. Click "Save"

---

## Step 3: Create Realtime Database

1. Go to **Build** → **Realtime Database**
2. Click "Create Database"
3. Choose **United States** (or your region)
4. Start in **Test mode** (we'll secure it later)
5. Click "Enable"

---

## Step 4: Get Your Firebase Config

1. Go to **Project Settings** (⚙️ gear icon at top left)
2. Scroll down to "Your apps"
3. Click the **Web** icon (`</>`)
4. Register app name: `Food Reviews`
5. **Copy the firebaseConfig object**

It will look like this:
```javascript
const firebaseConfig = {
  apiKey: "AIzaSyC...",
  authDomain: "food-reviews-xxxxx.firebaseapp.com",
  databaseURL: "https://food-reviews-xxxxx-default-rtdb.firebaseio.com",
  projectId: "food-reviews-xxxxx",
  storageBucket: "food-reviews-xxxxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef123456"
};
```

---

## Step 5: Update Your HTML File

1. Open `food-review-app.html`
2. Find this section (around line 948):
```javascript
// Firebase configuration - YOU NEED TO REPLACE THIS WITH YOUR OWN
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.appspot.com",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

3. **Replace it with YOUR config from Step 4**

---

## Step 6: Set Up Security Rules (Important!)

1. Go back to **Realtime Database** in Firebase
2. Click on the **Rules** tab
3. Replace the rules with this:

```json
{
  "rules": {
    ".read": "auth != null",
    "reviews": {
      "$uid": {
        ".read": "auth != null",
        "$reviewId": {
          ".write": "auth.uid === $uid"
        }
      }
    },
    "feed": {
      "$viewerUid": {
        ".read": "auth.uid === $viewerUid",
        "$reviewId": {
          ".write": "auth != null"
        }
      }
    },
    "profiles": {
      "$uid": {
        ".read": "auth != null",
        ".write": "auth.uid === $uid"
      }
    },
    "savedReviews": {
      "$uid": {
        ".read": "auth.uid === $uid",
        "$reviewId": {
          ".write": "auth.uid === $uid"
        }
      }
    },
    "users": {
      "$uid": {
        ".read": "auth != null",
        ".write": "auth.uid === $uid"
      }
    },
    "userEmails": {
      "$uid": {
        ".read": "auth != null",
        ".write": "auth.uid === $uid"
      }
    },
    "following": {
      "$uid": {
        ".read": "auth != null",
        "$targetUid": {
          ".write": "auth.uid === $uid"
        }
      }
    },
    "followers": {
      "$uid": {
        ".read": "auth != null",
        "$followerUid": {
          ".write": "auth.uid === $followerUid"
        }
      }
    },
    "comments": {
      "$authorUid": {
        "$reviewId": {
          "$commentId": {
            ".read": "auth != null",
            ".write": "auth != null"
          }
        }
      }
    },
    "usernames": {
      "$username": {
        ".read": "auth != null",
        ".write": "!data.exists()"
      }
    }
  }
}
```

4. Click **Publish**

This ensures:
- Users can see anyone's public reviews (for the feed)
- Users can only edit/delete their own reviews
- Users can follow/unfollow others
- Anyone can comment on reviews
- Users can save reviews privately
- Lightweight feed path optimizes performance
- Usernames are searchable by everyone

---

## Step 7: Deploy Your Website

### Option A: GitHub Pages (Free)
1. Create GitHub account at github.com
2. Create new repository called `food-reviews`
3. Upload `food-review-app.html` and rename it to `index.html`
4. Go to Settings → Pages
5. Select "main" branch
6. Your site will be at: `https://[username].github.io/food-reviews/`

### Option B: Netlify (Free)
1. Go to netlify.com
2. Drag and drop your `food-review-app.html` file (renamed to `index.html`)
3. Your site will be live instantly!

---

## How to Use the App

### Login:
- Click "Sign in with Google"
- Use your Gmail account

### Set Up Your Profile:
1. Go to the **Social** tab
2. Choose a unique username (e.g., @foodlover123)
3. Click "Set Username"
4. This is how others will find you!

### Add Reviews:
- Go to **My Reviews** tab
- Click "+ Add New Review"
- Fill in restaurant info, ratings, photos
- Reviews are saved to YOUR account
- Your followers will see it in their feed!

### Follow People:
1. Go to **Social** tab
2. Search for users by username or email
3. Click "Follow" button
4. You'll now see their reviews in your Feed!

### View Your Feed:
- Click the **Feed** tab
- See all reviews from people you follow
- Discover new restaurants through your friends!
- Reviews show who posted them and when

### Interact with Reviews:
- **💬 Comment**: Click "Comment" to leave your thoughts on someone's review
- **💾 Save**: Click "Save" to bookmark reviews you want to reference later
- **View Saved**: Go to the **Saved** tab to see all your saved reviews

### Comment on Reviews:
- Any review in the feed can receive comments
- Click the "Comment" button
- Type your thoughts and click "Post"
- See what others think about the same places!

### Save Reviews:
- See a great recommendation? Click "Save"
- The review gets bookmarked to your **Saved** tab
- Access it anytime without scrolling through the feed
- Perfect for building your "must-try" list!

### View Map:
- In **My Reviews** tab, scroll down
- See all YOUR reviewed locations on the map
- Red dots show where you've been

---

## Troubleshooting

**"Firebase not initialized" error:**
- Make sure you replaced the Firebase config with YOUR config from Step 4

**"Permission denied" error:**
- Check that you set up the security rules in Step 6

**Can't find user to share with:**
- The person needs to log in at least once so their email is registered

**Login button doesn't work:**
- Make sure you enabled Google authentication in Step 2
- Check that your domain is authorized in Firebase → Authentication → Settings

---

## Need Help?

If something isn't working:
1. Open browser console (F12)
2. Look for error messages
3. Make sure all steps above are completed
4. Double-check your Firebase config is correct

---

🎉 **You're all set!** Enjoy tracking your food adventures together!
