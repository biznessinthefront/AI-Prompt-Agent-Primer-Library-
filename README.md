[README.md](https://github.com/user-attachments/files/25109724/README.md)
# 🤖 AI Prompt & Agent Primer Library

A collaborative, community-driven library for sharing AI prompts and agent configurations. Built with Firebase for real-time collaboration and easy administration.

![Status](https://img.shields.io/badge/status-active-success.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## 📖 Overview

This project provides a simple, maintainable platform where:
- **Users** can browse, search, and copy AI prompts and agent primers
- **Contributors** can submit new prompts and agent configurations
- **Admins** can review and approve submissions to maintain quality

All submissions start as "experimental" and require admin approval to become "approved" and trusted resources.

## ✨ Features

### For Users
- 🔍 **Search & Filter** - Find prompts by keywords, filter by status
- 📋 **Easy Copy** - One-click copy to clipboard
- ✅ **Quality Indicators** - Clear badges show approved vs. experimental status
- 📱 **Responsive Design** - Works on desktop, tablet, and mobile

### For Contributors
- ➕ **Simple Submission** - User-friendly forms for adding content
- 🏷️ **Structured Data** - Required fields ensure consistency
- 🔄 **Real-time Updates** - See new content appear instantly

### For Admins
- 🛠️ **Admin Panel** - Dedicated interface for management
- ✓ **Approval Workflow** - Review and approve submissions
- 👥 **Multi-Admin Support** - Add team members to help moderate
- 📊 **Dashboard Stats** - Track pending and approved items
- 🗑️ **Content Moderation** - Approve, reject, or delete entries

## 🚀 Quick Start

### Prerequisites
- A Google account (for Firebase)
- A web browser
- 10-15 minutes for setup

### Installation

1. **Clone this repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/ai-prompt-library.git
   cd ai-prompt-library
   ```

2. **Follow the setup guide**
   - Open `SETUP_GUIDE.md` and follow the step-by-step instructions
   - You'll create a free Firebase project and configure authentication

3. **Deploy**
   - The easiest option is GitHub Pages (see deployment section below)
   - Or use Netlify, Vercel, or any static host

## 📁 Project Structure

```
ai-prompt-library/
├── index.html          # Main public-facing website
├── admin.html          # Admin panel for managing submissions
├── README.md           # This file
├── SETUP_GUIDE.md      # Detailed Firebase setup instructions
├── LICENSE             # MIT License
└── .gitignore          # Git ignore file
```

## 🔧 Configuration

After cloning, you need to add your Firebase configuration:

1. Create a Firebase project (see `SETUP_GUIDE.md`)
2. Copy your Firebase config
3. Update the `firebaseConfig` object in **both** `index.html` and `admin.html`

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

## 🌐 Deployment

### Option 1: GitHub Pages (Recommended)

1. Go to your repository settings
2. Navigate to **Pages** section
3. Under "Source", select your main branch
4. Click **Save**
5. Your site will be live at `https://YOUR_USERNAME.github.io/REPO_NAME`

### Option 2: Netlify

1. Push your code to GitHub
2. Go to [Netlify](https://www.netlify.com/)
3. Click "New site from Git"
4. Select your repository
5. Deploy!

### Option 3: Vercel

1. Push your code to GitHub
2. Go to [Vercel](https://vercel.com/)
3. Import your repository
4. Deploy!

## 📊 Data Structure

### Prompt Library Fields
- **Purpose** - What the prompt accomplishes
- **Audience** - Who should use it
- **Prompt Text** - The actual prompt
- **Use Cases** - Specific applications
- **Alternate Variables** - Customization options
- **Notes** - Additional tips or context
- **Status** - `experimental` or `approved`

### Agent Primer Library Fields
- **Agent Name** - Descriptive name
- **Purpose** - What the agent does
- **Intended Users** - Target audience
- **Allowed Tasks** - What it can do
- **Explicit Exclusions** - What it cannot do
- **Tone & Behavior** - Communication style
- **Data Handling** - Privacy/security guidelines
- **Status** - `experimental` or `approved`

## 👥 Contributing

We welcome contributions! Here's how:

1. **Submit via the website** - Use the "Submit New Entry" tab
2. **Wait for review** - Admins will review your submission
3. **Get approved** - Quality submissions get the ✅ badge

### Contribution Guidelines

- Be clear and specific in descriptions
- Include practical use cases
- Test prompts before submitting
- For agent primers, clearly define boundaries
- Follow the existing format and style

## 🔐 Admin Access

To become an admin:
1. Contact the repository owner
2. They'll add your email in the admin panel
3. You'll receive credentials to log in at `/admin.html`

Admin responsibilities:
- Review new submissions promptly
- Maintain quality standards
- Remove spam or inappropriate content
- Help other admins as needed

## 🛡️ Security

- Firebase handles all authentication
- Firestore security rules prevent unauthorized changes
- Admin credentials should be kept secure
- Regular security audits recommended

## 📈 Usage & Limits

Firebase free tier includes:
- 50,000 reads/day
- 20,000 writes/day  
- 1 GB storage
- 10 GB/month bandwidth

This is sufficient for most small to medium libraries. Monitor usage in Firebase Console.

## 🐛 Troubleshooting

### Common Issues

**"Firebase is not defined"**
- Ensure you've added your config to both HTML files

**Can't log in as admin**
- Verify you created the auth user in Firebase
- Check that your email is in the `admins` collection

**Submissions not appearing**
- Check Firestore security rules
- Look in Firebase Console → Firestore for data

**More help**
- Check browser console (F12) for errors
- Review `SETUP_GUIDE.md`
- Open an issue on GitHub

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Built with [Firebase](https://firebase.google.com/)
- Designed for the AI community
- Inspired by collaborative knowledge sharing

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/YOUR_USERNAME/ai-prompt-library/issues)
- **Discussions**: [GitHub Discussions](https://github.com/YOUR_USERNAME/ai-prompt-library/discussions)

## 🗺️ Roadmap

Future enhancements:
- [ ] Category/tag system
- [ ] User accounts with favorites
- [ ] Rating system for prompts
- [ ] Export functionality
- [ ] API access
- [ ] Prompt versioning

## 🌟 Star History

If you find this project useful, please consider giving it a star! ⭐

---

**Made with ❤️ for the AI community**
