# Portfolio Deployment Guide

## 🚀 Quick Deployment Steps

### Option 1: GitHub Pages (Recommended)

1. **Create a new repository on GitHub**
   - Go to [GitHub](https://github.com) and click "New repository"
   - Name it `your-username.github.io` (replace with your GitHub username)
   - Make it public
   - Don't initialize with README (we already have one)

2. **Upload your portfolio files**
   ```bash
   # Navigate to your portfolio folder
   cd C:\Users\swath\DashCam_Practicum\portfolio_clean
   
   # Initialize git repository
   git init
   
   # Add all files
   git add .
   
   # Commit changes
   git commit -m "Initial portfolio commit"
   
   # Add remote origin (replace with your repository URL)
   git remote add origin https://github.com/your-username/your-username.github.io.git
   
   # Push to GitHub
   git push -u origin main
   ```

3. **Enable GitHub Pages**
   - Go to your repository on GitHub
   - Click "Settings" tab
   - Scroll down to "Pages" section
   - Select "Deploy from a branch"
   - Choose "main" branch and "/ (root)" folder
   - Click "Save"

4. **Access your portfolio**
   - Your portfolio will be available at: `https://your-username.github.io`
   - It may take a few minutes to deploy

### Option 2: Netlify (Alternative)

1. **Go to [Netlify](https://netlify.com)**
2. **Drag and drop** the `portfolio_clean` folder onto the Netlify dashboard
3. **Get your live URL** - Netlify will provide a random URL like `https://amazing-name-123456.netlify.app`
4. **Custom domain** (optional): You can add a custom domain in Netlify settings

### Option 3: Vercel

1. **Go to [Vercel](https://vercel.com)**
2. **Import your GitHub repository** or drag and drop the folder
3. **Deploy** - Vercel will automatically deploy your portfolio
4. **Get your live URL** - Vercel provides a URL like `https://your-project.vercel.app`

## 🔧 Before Deploying

### Update Personal Information

1. **Edit `index.html`**:
   - Update contact information (phone, email, location)
   - Update LinkedIn and GitHub links
   - Update project descriptions if needed

2. **Update `README.md`**:
   - Change the live demo URL to your actual URL
   - Update contact information

3. **Optional - Update Analytics**:
   - Replace Google Analytics ID in `index.html` with your own
   - Update Formspree form endpoint with your own

## 📁 Final File Structure

Your clean portfolio should have exactly these files:

```
portfolio_clean/
├── index.html              # Main portfolio page
├── amazon_dashboard.html   # Amazon analytics dashboard
├── style.css              # All styling and themes
├── script.js              # Interactive functionality
├── README.md              # Documentation
├── DEPLOYMENT_GUIDE.md    # This guide
└── assets/                # Static assets
    ├── profile.png        # Your profile picture
    ├── swathi_resume.pdf  # Your resume
    └── favicon.ico        # Website icon
```

## ✅ Verification Checklist

Before deploying, make sure:
- [ ] All images load correctly
- [ ] Resume PDF opens and downloads
- [ ] Contact form works (test with a real submission)
- [ ] Dark/light theme toggle works
- [ ] All links work (LinkedIn, GitHub, project links)
- [ ] Portfolio looks good on mobile and desktop
- [ ] No console errors in browser developer tools

## 🐛 Troubleshooting

### Images not loading
- Check file paths in HTML
- Ensure images are in the correct `assets/` folder
- Verify file names match exactly (case-sensitive)

### Contact form not working
- Check Formspree form endpoint URL
- Verify form action attribute in HTML
- Test with a real email submission

### Styling issues
- Check CSS file is linked correctly
- Verify no syntax errors in CSS
- Clear browser cache and reload

## 📞 Support

If you encounter any issues:
1. Check the browser console for errors
2. Verify all file paths are correct
3. Ensure all required files are present
4. Test locally before deploying

---

**Ready to deploy?** Choose your preferred method above and get your portfolio live! 🚀
