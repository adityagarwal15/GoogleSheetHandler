# 📝 Google Sheets Form

> A beautiful, modern contact form that automatically submits data to Google Sheets. Built with vanilla HTML, CSS, and JavaScript.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## 🚀 Live Demo

👉 **[View Live Demo](https://google-sheet-handler.vercel.app/)** 

## ✨ Features

- Modern dark UI with glassmorphism effects
- Automatic Google Sheets integration
- Fully responsive design
- Real-time form validation
- Toast notifications
- No external dependencies

## 🛠️ Setup

### 1. Create Google Sheet
1. Go to [Google Sheets](https://sheets.google.com) and create a new spreadsheet
2. Add headers: `Name`, `Email`, `Message`, `Timestamp`

### 2. Setup Google Apps Script
1. In your sheet: `Extensions` → `Apps Script`
2. Paste this code:

```javascript
function doPost(e) {
  try {
    const sheet = SpreadsheetApp.getActiveSheet();
    const data = e.parameter;
    
    sheet.appendRow([
      data.name,
      data.email,
      data.message,
      new Date()
    ]);
    
    return ContentService
      .createTextOutput(JSON.stringify({result: "success"}))
      .setMimeType(ContentService.MimeType.JSON);
      
  } catch (error) {
    return ContentService
      .createTextOutput(JSON.stringify({result: "error", error: error.toString()}))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```

3. Deploy as Web App: `Deploy` → `New deployment` → `Web app`
4. Set access to `Anyone` and copy the URL

### 3. Update Form
Replace the Google Apps Script URL in `index.html` (around line 315):
```javascript
const response = await fetch("YOUR_GOOGLE_APPS_SCRIPT_URL_HERE", {
```

## 📁 Project Structure

```
GoogleSheetHandler/
├── index.html    # Main form file
├── README.md     # Documentation
└── assets/       # Screenshots (optional)
```

## 🎨 Customization

- **Colors**: Modify CSS variables in the `<style>` section
- **Fields**: Add new inputs and update the Google Apps Script accordingly
- **Styling**: All CSS is embedded in the HTML file for easy editing

## 🚀 Deployment

**Vercel** (Currently used):
- Connect your GitHub repo to [Vercel](https://vercel.com)
- Automatic deployments on every push
- Live at: https://google-sheet-handler.vercel.app/

**Other options**: GitHub Pages, Netlify, or any static hosting service

## 💡 Use Cases

Perfect for contact forms, feedback collection, surveys, event registrations, and lead generation.

## 🤝 Contributing

Feel free to submit issues and pull requests to improve the project!

## 📄 License

MIT License - feel free to use this project for personal or commercial purposes.

---

⭐ **Star this repo if it helped you!**
