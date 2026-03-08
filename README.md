# Pass or Ass 🎯

**The universal review app for everything you experience.**

Track restaurants, running gels, supplements, tech products, or anything else—and never forget what was worth it or what was complete ass.

![Pass or Ass Banner](https://via.placeholder.com/1200x400/007AFF/FFFFFF?text=Pass+or+Ass)

## ✨ Features

### 📱 **Two Review Types**
- **🍽️ Restaurants** - Rate food, service, and atmosphere
- **📦 Products** - Review tech, supplements, shoes, or anything else

### 🌟 **Smart Reviews**
- **3-Category Ratings** - Quality, Value, Experience (customized per type)
- **Photo Uploads** - Show what you're reviewing
- **Detailed Comments** - Add context to each rating
- **Pass or Ass Verdict** - Final judgment on every review

### 👥 **Social Features**
- **Follow Users** - See what your friends are reviewing
- **Feed** - Discover new restaurants and products
- **Comments** - Discuss reviews with others
- **Save Reviews** - Bookmark recommendations for later

### 🗺️ **Location Tracking**
- **Interactive Map** - See all your restaurant visits on Google Maps
- **City Filters** - Filter reviews by location

### 🔒 **Secure & Private**
- **Google Sign-In** - Easy, secure authentication
- **Cloud Storage** - Reviews saved to Firebase
- **Privacy Controls** - Only followers see your reviews

## 🚀 Quick Start

### 1. **Set Up Firebase**

Follow the detailed instructions in [FIREBASE_SETUP_INSTRUCTIONS.md](FIREBASE_SETUP_INSTRUCTIONS.md)

**Quick version:**
1. Create a Firebase project
2. Enable Google Authentication
3. Create Realtime Database
4. Copy your config into `food-review-app.html` (line ~948)
5. Set up security rules

### 2. **Deploy to GitHub Pages**

1. **Fork or clone this repo**
2. **Rename `food-review-app.html` to `index.html`**
3. Go to Settings → Pages
4. Select "main" branch
5. Your site will be live at: `https://[username].github.io/[repo-name]/`

**OR Deploy to Netlify:**
1. Drag and drop `food-review-app.html` (renamed to `index.html`)
2. Site goes live instantly!

## 📖 How to Use

### **Create an Account**
1. Click "Sign in with Google"
2. Set your username in the Social tab
3. Start reviewing!

### **Add a Review**
1. Choose **Restaurants** or **Products**
2. Click "+ Add New Review"
3. Fill in the details
4. Rate each category (1-5 stars)
5. Add optional comments
6. Choose **Pass ✅** or **Ass 🍑**
7. Submit!

### **Follow Friends**
1. Go to **Social** tab
2. Search by username or email
3. Click "Follow"
4. See their reviews in your **Feed**!

### **Save Favorites**
- Click 💾 **Save** on any review
- Access saved reviews in the **Saved** tab
- Build your "must-try" list!

## 🎨 Review Categories

### **Restaurants (🍽️)**
- **Taste** - How did the food taste?
- **Service** - How was the service? Were they speedy, slow, nice?
- **Atmosphere** - How was the ambiance? Was the music loud? Did it feel romantic or casual?

### **Products (📦)**
- **Quality** - Quality ingredients, is it a durable product?
- **Value** - Was the cost worth it in your eyes?
- **Experience** - How did this product make you feel? Did it boost performance, make your life better?

### **Product Categories Include:**
- 📱 Tech & Electronics
- 👟 Shoes & Footwear
- 👕 Clothing & Apparel
- 💊 Supplements & Vitamins
- 🏋️ Fitness Equipment
- 💄 Beauty & Skincare
- 🥫 Food Products
- 🥤 Beverages
- And more!

## 🛠️ Tech Stack

- **Frontend**: HTML, CSS, JavaScript (Vanilla)
- **Authentication**: Firebase Auth (Google Sign-In)
- **Database**: Firebase Realtime Database
- **Maps**: Google Maps JavaScript API
- **Hosting**: GitHub Pages / Netlify

## 📁 Project Structure

```
pass-or-ass/
├── index.html                          # Main app file (rename from food-review-app.html)
├── FIREBASE_SETUP_INSTRUCTIONS.md      # Detailed Firebase setup guide
├── README.md                           # This file
└── UNIVERSAL_REVIEW_UPDATE.md          # Update notes
```

## 🔧 Configuration

### **Required API Keys:**

1. **Firebase Config** (Replace in `index.html` around line 948):
```javascript
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

2. **Google Maps API Key** (Already included but can be replaced if needed)

## 🎯 Future Features

- [ ] Export reviews to CSV
- [ ] Import reviews from other platforms
- [ ] Rating analytics and insights
- [ ] Shareable review links
- [ ] Public profiles
- [ ] Desktop app
- [ ] Mobile app (iOS/Android)

## 🤝 Contributing

This is a personal project, but suggestions and feedback are welcome! Feel free to:
- Open an issue for bugs or feature requests
- Fork and experiment
- Share your deployed version!

## 📝 License

MIT License - Feel free to use, modify, and deploy your own version!

## 💡 Credits

Built with love for everyone tired of forgetting which restaurants were amazing and which products were complete ass.

---

**Made by foodies, for foodies (and product enthusiasts)** 🍕📦

*Restaurants, new running gel, or any product in the world—track what you love and never forget what wasn't worth it.*
