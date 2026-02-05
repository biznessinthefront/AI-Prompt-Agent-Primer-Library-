# 🚀 Firebase Setup Guide for AI Prompt & Agent Library

This guide will walk you through setting up Firebase for your prompt library. Don't worry - it's easier than it sounds!

## 📋 What You'll Need
- A Google account (free)
- 10-15 minutes of your time

---

## Step 1: Create a Firebase Project

1. Go to https://console.firebase.google.com/
2. Click **"Add project"** or **"Create a project"**
3. Enter a project name (e.g., "AI Prompt Library")
4. Click **Continue**
5. Disable Google Analytics (you don't need it for this) and click **Create project**
6. Wait for the project to be created, then click **Continue**

---

## Step 2: Register Your Web App

1. On the Firebase console homepage, click the **Web icon** (`</>`) to add a web app
2. Give your app a nickname (e.g., "Prompt Library Web")
3. **Do NOT** check "Also set up Firebase Hosting" (we'll deploy elsewhere)
4. Click **Register app**
5. You'll see a code snippet that looks like this:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyXXXXXXXXXXXXXXXXXXXXXX",
  authDomain: "your-project-123.firebaseapp.com",
  projectId: "your-project-123",
  storageBucket: "your-project-123.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef123456"
};
```

6. **COPY THIS ENTIRE CONFIG OBJECT** - you'll need it in Step 5
7. Click **Continue to console**

---

## Step 3: Set Up Firestore Database

1. In the left sidebar, click **Build** → **Firestore Database**
2. Click **Create database**
3. Choose **Start in production mode** (we'll set rules next)
4. Select a Cloud Firestore location (choose one close to you or your users)
5. Click **Enable**

### Set Security Rules

1. Click on the **Rules** tab
2. Replace the existing rules with this:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Prompts and agents are publicly readable
    match /prompts/{promptId} {
      allow read: if true;
      allow create: if true;  // Anyone can submit
      allow update, delete: if request.auth != null;  // Only admins can update/delete
    }
    
    match /agents/{agentId} {
      allow read: if true;
      allow create: if true;  // Anyone can submit
      allow update, delete: if request.auth != null;  // Only admins can update/delete
    }
    
    // Only authenticated users can read admin list
    match /admins/{adminId} {
      allow read, write: if request.auth != null;
    }
  }
}
```

3. Click **Publish**

---

## Step 4: Enable Authentication

1. In the left sidebar, click **Build** → **Authentication**
2. Click **Get started**
3. Click on **Email/Password** in the sign-in providers list
4. Toggle **Enable** to ON
5. Click **Save**

### Create Your First Admin User

1. Click the **Users** tab at the top
2. Click **Add user**
3. Enter your email address and a strong password
4. Click **Add user**

**IMPORTANT:** Save these credentials securely - this is your main admin account!

---

## Step 5: Configure Your HTML Files

Now you need to add your Firebase configuration to both HTML files.

### Update index.html

1. Open `index.html` in a text editor
2. Find this section near the bottom (around line 850):

```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

3. Replace it with the config you copied in Step 2

### Update admin.html

1. Open `admin.html` in a text editor
2. Find the same section (around line 600)
3. Replace it with your Firebase config

---

## Step 6: Add Your Email to the Admins Collection

You need to manually add your admin email to Firestore so the settings page works:

1. Go back to Firebase Console → Firestore Database
2. Click **Start collection**
3. Collection ID: `admins`
4. Click **Next**
5. Document ID: Click **Auto-ID**
6. Add field:
   - Field: `email`
   - Type: `string`
   - Value: Your admin email (the one you used in Step 4)
7. Click **Save**

---

## Step 7: Deploy Your Site

You have several free options to host your site:

### Option A: Netlify (Easiest)

1. Go to https://www.netlify.com/
2. Sign up for a free account
3. Drag and drop your `index.html` and `admin.html` files onto Netlify
4. Done! You'll get a URL like `https://your-site-name.netlify.app`

### Option B: GitHub Pages

1. Create a GitHub account if you don't have one
2. Create a new repository
3. Upload `index.html` and `admin.html`
4. Go to Settings → Pages
5. Select the main branch and save
6. Your site will be live at `https://yourusername.github.io/repo-name`

### Option C: Vercel

1. Go to https://vercel.com/
2. Sign up for a free account
3. Click **Add New** → **Project**
4. Upload your files
5. Deploy!

---

## Step 8: Test Everything

1. Visit your deployed site
2. Try submitting a prompt or agent primer
3. Go to the admin panel (`/admin.html`)
4. Log in with your admin credentials
5. You should see your submission in the "Pending Review" tab
6. Try approving it!

---

## 🎉 You're Done!

Your AI Prompt & Agent Library is now live and ready to use!

---

## 🔐 Managing Multiple Admins

To add additional admin users:

1. Log in to the admin panel
2. Go to the **Settings** tab
3. Enter the new admin's email and password
4. Click **Add Admin**

The new admin can now log in and help you manage the library!

---

## 🛠️ Troubleshooting

### "Firebase is not defined" error
- Make sure you replaced the Firebase config in **both** `index.html` and `admin.html`

### Can't log in as admin
- Double-check that you created the user in Firebase Authentication (Step 4)
- Make sure you added your email to the `admins` collection (Step 6)

### Submissions not appearing
- Check Firestore rules are set correctly (Step 3)
- Look in Firebase Console → Firestore to see if data is being written

### Still stuck?
- Check the browser console (F12) for error messages
- Make sure your Firebase config values don't have typos
- Verify your Firebase project is on the free "Spark" plan (it should be by default)

---

## 💾 Backup Your Data

Firebase automatically backs up your data, but you can also export it:

1. Go to Firebase Console → Firestore Database
2. Click the **three dots** menu
3. Select **Export data**
4. Choose a Cloud Storage bucket
5. Click **Export**

---

## 📊 Monitor Usage

Firebase free tier includes:
- 50,000 reads per day
- 20,000 writes per day
- 1 GB storage

This is more than enough for most small to medium libraries. You can monitor usage in Firebase Console → Usage.

---

## 🔒 Security Notes

1. **Never share your Firebase config in public repos** - it's okay to expose it on the public site, but don't commit sensitive data
2. **Regularly review admin users** - remove access for people who no longer need it
3. **Keep your admin password secure** - use a password manager
4. **Monitor Firestore usage** - watch for unusual activity

---

Good luck with your library! 🚀
