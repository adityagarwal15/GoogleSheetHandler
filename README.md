# 📝 Google Sheets Form

> A beautiful, modern contact form that automatically submits data to Google Sheets. Built with vanilla HTML, CSS, and JavaScript featuring a sleek dark design with glassmorphism effects.

![Form Preview](https://img.shields.io/badge/Status-Active-brightgreen) ![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## 🌟 Screenshots

### Desktop View
![Desktop Form](assets/form-demo.png)

### Mobile View  
![Mobile Form](assets/mobile-view.png)

---

## 🔗 Quick Start

1. **Clone this repository**
   ```bash
   git clone https://github.com/adityagarwal15/GoogleSheetHandler.git
   cd GoogleSheetHandler
   ```

2. **Set up Google Sheets integration** (see detailed steps below)

3. **Open `index.html`** in your browser or deploy to any web host

---

## ✨ Features

- **Modern UI/UX**: Dark theme with glassmorphism effects and smooth animations
- **Google Sheets Integration**: Automatically saves form submissions to a Google Sheet
- **Responsive Design**: Works perfectly on desktop, tablet, and mobile devices
- **Real-time Feedback**: Loading states, success animations, and toast notifications
- **Accessibility**: High contrast mode support and keyboard navigation
- **No Dependencies**: Pure HTML, CSS, and JavaScript - no frameworks required

## 🚀 Live Demo

👉 **[View Live Demo](https://adityagarwal15.github.io/GoogleSheetHandler)** 

### Form Fields:
- ✅ **Name** (required)
- ✅ **Email** (required) 
- ✅ **Message** (required)
- 🔄 **Real-time validation** and **loading states**

## 📋 Prerequisites

- A Google account
- Basic knowledge of Google Apps Script (for setup)

## 🛠️ Setup Instructions

### 1. Create a Google Sheet

1. Go to [Google Sheets](https://sheets.google.com)
2. Create a new spreadsheet
3. Add headers in the first row:
   - Column A: `Name`
   - Column B: `Email`
   - Column C: `Message`
   - Column D: `Timestamp` (optional)

### 2. Set up Google Apps Script

1. In your Google Sheet, go to `Extensions` → `Apps Script`
2. Delete the default code and paste this script:

```javascript
function doPost(e) {
  try {
    const sheet = SpreadsheetApp.getActiveSheet();
    const data = e.parameter;
    
    // Add data to sheet
    sheet.appendRow([
      data.name,
      data.email,
      data.message,
      new Date() // timestamp
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

3. Save the script (`Ctrl+S` or `Cmd+S`)
4. Click `Deploy` → `New deployment`
5. Choose type: `Web app`
6. Set execute as: `Me`  
7. Set access: `Anyone`
8. Click `Deploy`
9. Copy the web app URL

### 3. Update the HTML File

Replace the Google Apps Script URL in `index.html`:
```javascript
// Find this line around line 315
const response = await fetch("YOUR_GOOGLE_APPS_SCRIPT_URL_HERE", {
```
Replace with your actual deployment URL

## 📁 Project Structure

```
GoogleSheetHandler/
├── 📄 index.html          # Main form with embedded CSS/JS
├── 📖 README.md           # Project documentation
├── 📜 LICENSE             # MIT License
└── 🖼️ assets/             # Screenshots and demo images
    ├── form-demo.png
    └── mobile-view.png
```

## 🎨 Customization

### Colors and Styling

The form uses CSS custom properties. You can easily customize:

- **Background**: Change the `body` background color
- **Form styling**: Modify the glassmorphism effects in the `form` selector
- **Button colors**: Update the button background and hover states
- **Text colors**: Adjust the color values throughout the CSS

### Form Fields

To add more fields:

1. Add the HTML input in the form
2. Update the Google Apps Script to handle the new field
3. Add corresponding column headers in your Google Sheet

## 🌐 Browser Support

- Chrome (recommended)
- Firefox
- Safari
- Edge
- Mobile browsers (iOS Safari, Chrome Mobile)

## 📱 Mobile Responsiveness

The form is fully responsive and includes:
- Optimized touch targets
- Proper viewport scaling
- iOS-specific optimizations (prevents zoom on input focus)
- Mobile-friendly toast notifications

## 🔧 Troubleshooting

### Common Issues

1. **Form not submitting**: Check that your Google Apps Script URL is correct
2. **CORS errors**: The form uses `mode: 'no-cors'` which is required for Google Apps Script
3. **Data not appearing in sheet**: Verify your script permissions and deployment settings

### Debug Mode

Add this to the fetch error handling for more detailed logs:
```javascript
catch (error) {
  console.error("Detailed error:", error);
  // existing error handling
}
```

## 🚀 Deployment Options

### GitHub Pages
1. Push your code to a GitHub repository
2. Enable GitHub Pages in repository settings
3. Your form will be available at `https://adityagarwal15.github.io/GoogleSheetHandler`

### Netlify
1. Drag and drop your HTML file to Netlify
2. Get instant deployment with custom domain options

### Vercel
1. Connect your GitHub repository to Vercel
2. Automatic deployments on every push

## 💡 About

This project demonstrates how to create a modern, accessible web form that integrates seamlessly with Google Sheets for data collection. Perfect for:

- 📧 Contact forms
- 📝 Feedback collection  
- 📊 Survey responses
- 🎫 Event registrations
- 💼 Lead generation

**Built with ❤️ using vanilla web technologies**

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## ⭐ Star this Repository

If this project helped you, please consider giving it a ⭐ star on GitHub!

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! 

1. **Fork** the repository
2. **Create** your feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Ideas for Contributions:
- 🎨 Additional themes/color schemes
- 📱 Enhanced mobile animations  
- 🔧 More form field types
- 🌍 Multi-language support
- ♿ Accessibility improvements

## 📞 Support

If you encounter any issues or have questions:

1. Check the troubleshooting section above
2. Review Google Apps Script documentation
3. Open an issue in this repository

## 📊 GitHub Stats

![GitHub stars](https://img.shields.io/github/stars/adityagarwal15/GoogleSheetHandler?style=social)
![GitHub forks](https://img.shields.io/github/forks/adityagarwal15/GoogleSheetHandler?style=social)
![GitHub issues](https://img.shields.io/github/issues/adityagarwal15/GoogleSheetHandler)
![GitHub license](https://img.shields.io/github/license/adityagarwal15/GoogleSheetHandler)

---

Made with ❤️ for seamless form submissions to Google Sheets
