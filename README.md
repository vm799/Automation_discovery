# Vaishali Mehmi - AI Automation Consultant Portfolio

Enterprise-grade portfolio website showcasing AI automation consulting expertise with advanced tracking and dark mode support.

## Features

### 🎨 Design & UX
- **Luxury Typography**: Playfair Display for headings, Inter for body text
- **Dark Mode**: Persistent theme toggle with localStorage
- **Responsive Design**: Mobile-first approach with collapsible sidebar
- **Enterprise Aesthetics**: Clean, professional design suitable for B2B consulting

### ⚡ Advanced Tracking
- **Session Timer**: Real-time session duration tracking
- **Activity Timeline**: Chronological event tracking with timestamps
- **Scroll Depth Tracking**: Automatic milestones at 25%, 50%, 75%, and 100%
- **Interaction Tracking**: CTA clicks, section views, navigation events

### 🛠️ Technical Features
- **CSS Custom Properties**: Complete theming system for light/dark modes
- **No Build Step**: Pure HTML/CSS/JS - enterprise-ready without complex tooling
- **localStorage Persistence**: Theme preferences saved across sessions
- **Smooth Animations**: Professional transitions and hover effects
- **Mobile Optimized**: Hamburger menu for sidebar on smaller screens

## File Structure

```
Automation_discovery/
├── index.html          # Main portfolio page (single-file architecture)
├── README.md          # This file
└── LICENSE            # MIT License
```

## Quick Start

1. **Open the file**: Simply open `index.html` in any modern web browser
2. **No build required**: Works immediately without npm, webpack, or any bundler
3. **Customize**: Edit the HTML directly to update content

## Customization Guide

### Update Personal Information

**Profile Image** (line 515):
```html
<img src="YOUR_IMAGE_URL" alt="Vaishali Mehmi">
```

**Email Address** (search for `your.email@example.com`):
```html
<a href="mailto:YOUR_EMAIL@example.com">
```

**LinkedIn URL** (search for `vaishali7`):
```html
<a href="https://www.linkedin.com/in/YOUR_LINKEDIN_ID/">
```

### Color Scheme

Colors are defined in CSS custom properties (`:root` for light mode, `[data-theme="dark"]` for dark mode):

```css
:root {
    --accent-primary: #0066cc;    /* Primary brand color */
    --accent-hover: #0052a3;      /* Hover state */
}
```

### Typography

The design uses two Google Fonts:
- **Playfair Display**: Luxury serif for headings
- **Inter**: Modern sans-serif for body text

To change fonts, update the Google Fonts import (line 8-10) and CSS variables (line 26-27).

## Dark Mode Implementation

The dark mode system uses:
1. **CSS Custom Properties**: All colors defined as variables
2. **Data Attribute**: `data-theme="dark"` on `<html>` element
3. **localStorage**: Persistent theme preference
4. **Smooth Transitions**: All color changes animated

### Accessing Dark Mode
- Click the "Dark Mode" toggle in the sidebar
- Theme preference is automatically saved
- Loads your preferred theme on return visits

## Timeline Tracking Events

The sidebar timeline automatically tracks:
- ✅ Page load
- ✅ Theme changes
- ✅ Section views (when collapsible sections are opened)
- ✅ Navigation clicks
- ✅ CTA button clicks
- ✅ Scroll depth milestones (25%, 50%, 75%, 100%)
- ✅ Sidebar menu toggles (mobile)

### Adding Custom Events

```javascript
addTimelineEvent('Your custom event description');
```

## Browser Support

- ✅ Chrome/Edge (latest 2 versions)
- ✅ Firefox (latest 2 versions)
- ✅ Safari (latest 2 versions)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

## Performance

- **No external dependencies** (except Google Fonts and Font Awesome CDN)
- **Minimal JavaScript**: ~200 lines of vanilla JS
- **Fast load times**: Single HTML file architecture
- **Optimized animations**: GPU-accelerated transforms

## Accessibility

- ✅ Semantic HTML5 elements
- ✅ ARIA labels where needed
- ✅ Keyboard navigation support
- ✅ Sufficient color contrast (WCAG AA compliant)
- ✅ Responsive font sizes

## Deployment

### GitHub Pages
1. Push to GitHub repository
2. Go to Settings → Pages
3. Select main branch
4. Your site will be live at `https://yourusername.github.io/repository-name/`

### Netlify
1. Drag and drop the folder to Netlify
2. Site is live immediately

### Custom Domain
- Add `CNAME` file with your domain
- Configure DNS settings at your registrar

## License

MIT License - See LICENSE file for details

## Credits

**Design & Development**: Enterprise-grade portfolio template
**Fonts**: Google Fonts (Playfair Display, Inter)
**Icons**: Font Awesome 6.4.0
**Author**: Vaishali Mehmi

## Contact

- **LinkedIn**: [linkedin.com/in/vaishali7](https://www.linkedin.com/in/vaishali7/)
- **Email**: your.email@example.com

---

**Built with enterprise standards in mind** - Clean code, accessible design, production-ready
