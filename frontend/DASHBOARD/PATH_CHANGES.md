# Path Changes for Vercel Deployment

## Root Directory: `frontend/DASHBOARD`

All paths have been updated to use absolute paths from the root directory.

## ✅ Updated Files

### 1. `/index.html` (Homepage)

**Navigation Links:**
- ✅ `#home` - Same page anchor
- ✅ `#about` - Same page anchor
- ✅ `#team` - Same page anchor
- ✅ `#contact` - Same page anchor
- ✅ `/BV/chapters.html` - Chapters page
- ✅ `/BV/translation.html` - Translation page

**CSS/JS:**
- ✅ `/style.css`
- ✅ `/hamburger-menu.css`
- ✅ `/hamburger-menu.js`

---

### 2. `/BV/chapters.html` (Chapters List)

**Navigation Links:**
- ✅ `/index.html` - Homepage
- ✅ `/index.html#about` - About section
- ✅ `/BV/chapters.html` - Current page (active)
- ✅ `/index.html#team` - Team section
- ✅ `/index.html#contact` - Contact section
- ✅ `/BV/translation.html` - Translation page

**CSS/JS:**
- ✅ `/style.css`
- ✅ `/BV/chapters.css`
- ✅ `/hamburger-menu.css`
- ✅ `/BV/chapters.js`
- ✅ `/hamburger-menu.js`

---

### 3. `/BV/chapter.html` (Individual Chapter)

**Navigation Links:**
- ✅ `/index.html` - Homepage
- ✅ `/index.html#about` - About section
- ✅ `/BV/chapters.html` - Chapters list
- ✅ `/index.html#team` - Team section
- ✅ `/index.html#contact` - Contact section
- ✅ `/BV/translation.html` - Translation page

**Breadcrumb:**
- ✅ `/BV/chapters.html` - Back to chapters

**Dynamic Links (in JavaScript):**
- ✅ `/BV/translation.html?text=...` - Translate verse

**CSS/JS:**
- ✅ `/style.css`
- ✅ `/hamburger-menu.css`
- ✅ `/hamburger-menu.js`

---

### 4. `/BV/translation.html` (Translation Page)

**Navigation Links:**
- ✅ `/index.html` - Homepage
- ✅ `/index.html#about` - About section
- ✅ `/BV/chapters.html` - Chapters list (Note: was pointing to wrong path)
- ✅ `/index.html#team` - Team section
- ✅ `/index.html#contact` - Contact section

**CSS/JS:**
- ✅ `/BV/style.css`
- ✅ `/hamburger-menu.css`
- ✅ `/BV/script.js`
- ✅ `/hamburger-menu.js`

---

## Path Structure

```
Vercel Root: frontend/DASHBOARD/
│
├── index.html              → Access as: /index.html or /
├── style.css               → Access as: /style.css
├── hamburger-menu.css      → Access as: /hamburger-menu.css
├── hamburger-menu.js       → Access as: /hamburger-menu.js
├── hero.mp4                → Access as: /hero.mp4
│
└── BV/
    ├── chapters.html       → Access as: /BV/chapters.html
    ├── chapters.css        → Access as: /BV/chapters.css
    ├── chapters.js         → Access as: /BV/chapters.js
    │
    ├── chapter.html        → Access as: /BV/chapter.html?chapter=1
    │
    ├── translation.html    → Access as: /BV/translation.html
    ├── style.css           → Access as: /BV/style.css
    ├── script.js           → Access as: /BV/script.js
    │
    ├── chakra.png          → Access as: /BV/chakra.png
    ├── scroll.png          → Access as: /BV/scroll.png
    │
    ├── images/             → Access as: /BV/images/
    │   ├── ch-1.webp       → Access as: /BV/images/ch-1.webp
    │   ├── ch-2.jpg        → Access as: /BV/images/ch-2.jpg
    │   └── ...
    │
    └── BhagavatGitaJsonFiles/  → Access as: /BV/BhagavatGitaJsonFiles/
        ├── Ch-1_Arjuna's_Vishada_Yoga.json
        └── ...
```

---

## Why Absolute Paths?

### Before (Relative Paths) ❌
```html
<!-- From /BV/chapters.html -->
<a href="../DASHBOARD/index.html">Home</a>
<link rel="stylesheet" href="../DASHBOARD/style.css">
```
**Problem:** Breaks when deployed to Vercel because `../DASHBOARD/` doesn't exist from the root.

### After (Absolute Paths) ✅
```html
<!-- From /BV/chapters.html -->
<a href="/index.html">Home</a>
<link rel="stylesheet" href="/style.css">
```
**Solution:** Always starts from root directory, works everywhere.

---

## Testing Checklist

### Local Testing (Before Deploy)
- [ ] Open `/index.html` in browser
- [ ] Click "Chapters" → Should go to chapters page
- [ ] Click "Translate" → Should go to translation page
- [ ] From chapters page, click "Home" → Should go back to homepage
- [ ] From any page, test all navigation links
- [ ] Test hamburger menu on mobile view

### After Vercel Deployment
- [ ] Visit your Vercel URL (e.g., `https://your-site.vercel.app`)
- [ ] Homepage loads correctly
- [ ] Click all navigation links
- [ ] Test chapters page
- [ ] Test individual chapter page
- [ ] Test translation page
- [ ] Test hamburger menu on mobile
- [ ] Check browser console for errors (F12)

---

## Common Issues & Solutions

### Issue: 404 Not Found
**Cause:** File path is incorrect
**Solution:** 
- Verify file exists in `frontend/DASHBOARD/`
- Check path starts with `/`
- Check spelling and case sensitivity

### Issue: CSS/JS Not Loading
**Cause:** Wrong file path
**Solution:**
- Check browser Network tab (F12)
- Verify path in HTML matches actual file location
- Ensure path starts with `/`

### Issue: Navigation Broken
**Cause:** Using relative paths instead of absolute
**Solution:**
- All navigation links should start with `/`
- Example: `/index.html`, `/BV/chapters.html`

### Issue: Images Not Loading
**Cause:** Image paths might still be relative
**Solution:**
- Update image paths to start with `/`
- Example: `/BV/images/ch-1.webp`

---

## Vercel Configuration

### Option 1: No Configuration Needed
If you set the root directory to `frontend/DASHBOARD` in Vercel dashboard, no additional configuration is needed.

### Option 2: Using vercel.json (Optional)
Create `vercel.json` in project root:

```json
{
  "buildCommand": null,
  "outputDirectory": "frontend/DASHBOARD",
  "devCommand": null,
  "installCommand": null,
  "framework": null
}
```

---

## Deployment Steps

1. **Push to Git**
   ```bash
   git add .
   git commit -m "Fixed paths for Vercel deployment"
   git push
   ```

2. **Deploy to Vercel**
   - Go to [vercel.com](https://vercel.com)
   - Import your repository
   - Set Root Directory: `frontend/DASHBOARD`
   - Click Deploy

3. **Test Deployment**
   - Visit your Vercel URL
   - Test all navigation
   - Test on mobile
   - Check for errors

---

## Summary of Changes

| File | Old Path Example | New Path | Status |
|------|-----------------|----------|--------|
| index.html | `href="../BV/chapters.html"` | `href="/BV/chapters.html"` | ✅ Fixed |
| chapters.html | `href="../DASHBOARD/index.html"` | `href="/index.html"` | ✅ Fixed |
| chapter.html | `href="../DASHBOARD/index.html"` | `href="/index.html"` | ✅ Fixed |
| translation.html | `href="../../DASHBOARD/index.html"` | `href="/index.html"` | ✅ Fixed |
| All CSS | `href="style.css"` | `href="/style.css"` | ✅ Fixed |
| All JS | `src="hamburger-menu.js"` | `src="/hamburger-menu.js"` | ✅ Fixed |

---

**Status:** ✅ All paths updated and ready for Vercel deployment!
