# Vercel Deployment Guide

## Project Structure
Your root folder for deployment is: `frontend/DASHBOARD/`

## Vercel Configuration

### Option 1: Using vercel.json (Recommended)
Create a `vercel.json` file in your project root:

```json
{
  "buildCommand": null,
  "outputDirectory": "frontend/DASHBOARD",
  "devCommand": null,
  "installCommand": null,
  "framework": null,
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ]
}
```

### Option 2: Vercel Dashboard Settings
1. Go to your project settings in Vercel
2. Set **Root Directory**: `frontend/DASHBOARD`
3. Set **Framework Preset**: Other
4. Leave build settings empty (static site)

## File Paths After Deployment

All paths in your HTML files are relative and should work correctly:

### From index.html:
- CSS: `style.css`, `hamburger-menu.css` ✅
- JS: `hamburger-menu.js` ✅
- Links to chapters: `../BV/chapters.html` ✅
- Links to translation: `../BV/translation.html` ✅

### From BV/chapters.html:
- CSS: `../DASHBOARD/style.css`, `chapters.css`, `../../DASHBOARD/hamburger-menu.css` ✅
- JS: `chapters.js`, `../../DASHBOARD/hamburger-menu.js` ✅

### From BV/chapter.html:
- CSS: `../DASHBOARD/style.css`, `../../DASHBOARD/hamburger-menu.css` ✅
- JS: `../../DASHBOARD/hamburger-menu.js` ✅

### From BV/translation.html:
- CSS: `style.css`, `../../DASHBOARD/hamburger-menu.css` ✅
- JS: `script.js`, `../../DASHBOARD/hamburger-menu.js` ✅

## Testing Before Deployment

### Local Testing
1. Open `frontend/DASHBOARD/index.html` in browser
2. Test navigation between pages
3. Resize browser to mobile width (≤ 768px)
4. Verify hamburger menu appears and works
5. Test all links in hamburger menu

### Mobile Testing
1. Open browser DevTools (F12)
2. Toggle device toolbar (Ctrl+Shift+M)
3. Select mobile device (iPhone, Android)
4. Test hamburger menu functionality

## Deployment Steps

### First Time Deployment
1. Push code to GitHub/GitLab/Bitbucket
2. Go to [vercel.com](https://vercel.com)
3. Click "New Project"
4. Import your repository
5. Set Root Directory: `frontend/DASHBOARD`
6. Click "Deploy"

### Updating Deployment
1. Push changes to your repository
2. Vercel auto-deploys on push
3. Check deployment status in Vercel dashboard

## Post-Deployment Checklist

- [ ] Homepage loads correctly
- [ ] All navigation links work
- [ ] Hamburger menu appears on mobile
- [ ] Hamburger menu functions properly
- [ ] All pages accessible
- [ ] Images load correctly
- [ ] Videos play (if any)
- [ ] Forms work (translation page)
- [ ] No console errors
- [ ] Responsive design works on all devices

## Common Issues & Solutions

### Issue: 404 on navigation
**Solution**: Check relative paths in HTML files

### Issue: CSS not loading
**Solution**: Verify CSS file paths are relative to HTML file location

### Issue: Hamburger menu not working
**Solution**: 
- Check JS file is loaded
- Verify no JavaScript errors in console
- Ensure hamburger-menu.js is in correct location

### Issue: Mobile view not responsive
**Solution**: 
- Verify viewport meta tag: `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- Check hamburger-menu.css is loaded

## Environment Variables
No environment variables needed for this static site.

## Custom Domain (Optional)
1. Go to Project Settings > Domains
2. Add your custom domain
3. Follow DNS configuration instructions
4. Wait for SSL certificate (automatic)

## Performance Optimization

### Already Implemented
- ✅ Responsive images
- ✅ Minified CSS (can be added)
- ✅ Efficient JavaScript
- ✅ Mobile-first design

### Recommended
- Consider adding CDN for images
- Enable Vercel Analytics
- Add meta tags for SEO
- Implement lazy loading for images

## Support
- Vercel Docs: https://vercel.com/docs
- Vercel Support: https://vercel.com/support
