# Athan Myanmar Website

Official website for Athan (Freedom of Expression Activists) - a Myanmar-based civil society organization dedicated to defending freedom of expression, media safety, and human rights.

## 🌐 Live Site

- **Production:** https://athanmm.cloud (custom domain via Namecheap)
- **Vercel:** https://athan-myanmar.vercel.app

## 🛠️ Tech Stack

- **Frontend:** HTML5, Tailwind CSS, Vanilla JavaScript
- **Code Storage:** GitHub
- **Hosting:** Vercel
- **Backend:** Supabase (for contact forms, newsletter, data)
- **Domain:** Namecheap/GoDaddy

## 📁 Project Structure

```
athan-myanmar-website/
├── index.html          # Main website
├── script.js           # Interactive features
├── README.md           # This file
├── vercel.json         # Vercel configuration
├── .gitignore          # Git ignore rules
├── reports/            # PDF research reports
│   └── *.pdf
├── covers/             # Report cover images
│   └── *.jpg
└── images/             # Logo and other images
    └── athan-logo.png
```

## 🚀 Quick Start - Local Development

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/athan-myanmar-website.git
   cd athan-myanmar-website
   ```

2. **Open in browser:**
   ```bash
   # Simply open index.html in your browser
   open index.html
   # Or use a local server:
   python -m http.server 8000
   # Or with Node.js:
   npx http-server
   ```

3. **View at:** http://localhost:8000

## 📤 Deployment

### Deploy to Vercel (Recommended)

#### Option 1: Via Vercel CLI
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Deploy to production
vercel --prod
```

#### Option 2: Via GitHub (Automatic)
1. Push code to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Import your GitHub repository
4. Vercel auto-deploys on every push to main branch

### Deploy to Netlify (Alternative)
```bash
# Install Netlify CLI
npm i -g netlify-cli

# Deploy
netlify deploy

# Deploy to production
netlify deploy --prod
```

## 🔧 Configuration

### Vercel Configuration

The `vercel.json` file includes:
- Static file serving
- Security headers
- Custom routes

### Custom Domain Setup

**For Namecheap/GoDaddy:**

1. **Go to your domain registrar (Namecheap/GoDaddy)**
2. **Add DNS records:**
   ```
   Type: A Record
   Name: @
   Value: 76.76.21.21 (Vercel IP)

   Type: CNAME
   Name: www
   Value: cname.vercel-dns.com
   ```

3. **In Vercel:**
   - Go to Project Settings → Domains
   - Add your custom domain: `athanmm.cloud`
   - Add www version: `www.athanmm.cloud`
   - Vercel auto-configures SSL

## 🗄️ Supabase Integration (Optional)

### Setup Supabase for Contact Form & Newsletter

1. **Create Supabase project:**
   - Go to [supabase.com](https://supabase.com)
   - Create new project
   - Get your API URL and anon key

2. **Create tables:**

```sql
-- Contact form submissions
CREATE TABLE contact_submissions (
  id UUID DEFAULT uuid_generate_v4() PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT NOT NULL,
  organization TEXT,
  subject TEXT NOT NULL,
  message TEXT NOT NULL,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT TIMEZONE('utc', NOW())
);

-- Newsletter subscriptions
CREATE TABLE newsletter_subscriptions (
  id UUID DEFAULT uuid_generate_v4() PRIMARY KEY,
  email TEXT UNIQUE NOT NULL,
  subscribed_at TIMESTAMP WITH TIME ZONE DEFAULT TIMEZONE('utc', NOW()),
  active BOOLEAN DEFAULT true
);
```

3. **Add environment variables:**

Create `.env.local`:
```env
VITE_SUPABASE_URL=your-project-url
VITE_SUPABASE_ANON_KEY=your-anon-key
```

4. **Update script.js** to use Supabase for form submissions

## 📝 Content Updates

### Add New Research Report

1. **Add PDF to `/reports` folder:**
   ```bash
   cp your-report.pdf reports/new-report-2026.pdf
   ```

2. **Update `index.html`** (around line 240):
   ```html
   <div class="report-card ... " data-category="research">
     <!-- Copy existing card and update: -->
     <h3>Your New Report Title</h3>
     <p>Report description...</p>
     <a href="reports/new-report-2026.pdf" download>Download PDF</a>
   </div>
   ```

3. **Commit and push:**
   ```bash
   git add reports/new-report-2026.pdf index.html
   git commit -m "Add new research report"
   git push
   ```

Vercel auto-deploys!

### Update Logo

1. **Add logo to `/images` folder:**
   ```bash
   cp athan-logo.png images/
   ```

2. **Update `index.html` (line 107):**
   ```html
   <img src="images/athan-logo.png" alt="Athan Logo">
   ```

## 🎨 Design System

### Colors

- **Primary (Amber):** `#d97706` - Main buttons, highlights
- **Secondary (Yellow):** `#f59e0b` - Gradients, accents
- **Background:** `#f9fafb` - Light gray
- **Text:** `#111827` - Dark gray

### Fonts

- **Primary:** Inter (Google Fonts)
- **Weights:** 300, 400, 500, 600, 700, 800

## 🔐 Security

- HTTPS enabled automatically via Vercel
- Security headers configured in `vercel.json`
- No sensitive data in client-side code
- Environment variables for API keys

## 📊 Analytics

### Add Google Analytics

1. **Get tracking ID** from Google Analytics
2. **Add to `index.html`** (before `</head>`):

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

## 🤝 Contributing

1. Fork the repository
2. Create feature branch: `git checkout -b feature/new-feature`
3. Commit changes: `git commit -m 'Add new feature'`
4. Push to branch: `git push origin feature/new-feature`
5. Open Pull Request

## 📄 License

Copyright © 2026 Athan Myanmar. All rights reserved.

## 📞 Contact

- **Website:** https://athanmm.cloud
- **Email:** contact@athanmyanmar.org
- **Twitter:** @AthanMyanmar
- **Facebook:** Athan Myanmar

## 🙏 Acknowledgments

Built with ❤️ for freedom of expression in Myanmar.

---

**Version:** 2.0  
**Last Updated:** February 2026  
**Status:** Production Ready ✅
