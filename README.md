<h1 align="center">📝 GoogleSheetHandler — Google Sheets Form</h1>
<p align="center">
  <i>A visually stunning, modern contact form that seamlessly submits data to Google Sheets.<br>
  Built with pure HTML, CSS, and JavaScript.</i>
</p>

<p align="center">
  <a href="https://google-sheet-handler.vercel.app/"><img alt="Live Demo" src="https://img.shields.io/badge/Live%20Demo-Click%20Here-22c55e?style=for-the-badge&logo=vercel&logoColor=white"></a>
  <img alt="HTML5" src="https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white&style=for-the-badge">
  <img alt="CSS3" src="https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white&style=for-the-badge">
  <img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black&style=for-the-badge">
</p>

<br/>

<p align="center">
  <a href="https://google-sheet-handler.vercel.app/"><b>👉 View Live Demo</b></a>
</p>

---

## 📸 Screenshot

<p align="center">
  <img src="https://res.cloudinary.com/dcf0cpuqf/image/upload/v1749772085/Screenshot_2025-06-13_051531_idbj8k.png" alt="GoogleSheetHandler Screenshot" width="80%" style="border-radius: 16px; box-shadow: 0 8px 24px rgba(0,0,0,0.15);" />
</p>

## 🎥 Walkthrough Video

<p align="center">
  <a href="https://res.cloudinary.com/dcf0cpuqf/video/upload/v1745092437/balanced_video_ndakjd.mp4">
    <img src="https://res.cloudinary.com/dcf0cpuqf/image/upload/v1749772085/Screenshot_2025-06-13_051531_idbj8k.png" alt="Video Thumbnail" width="65%" style="border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.12);" />
  </a>
  <br>
  <i>Click the image above to watch the video!</i>
</p>

---

## ✨ Features

- 🖤 **Modern dark UI** with elegant glassmorphism effects
- 🔗 **Instant Google Sheets integration**—no backend required
- 📱 **Fully responsive** for all devices
- ✅ **Real-time form validation** and feedback
- 🔔 **Toast notifications** for user actions
- ⚡ **Zero dependencies**—just pure web tech

---

## 🛠️ Quick Start

### 1. Create Your Google Sheet

1. Go to [Google Sheets](https://sheets.google.com) and create a new spreadsheet.
2. Add headers: `Name`, `Email`, `Message`, `Timestamp`.

### 2. Set Up Google Apps Script

1. In your sheet, navigate to `Extensions` → `Apps Script`.
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

3. Deploy as Web App: `Deploy` → `New deployment` → `Web app`.
4. Set access to **Anyone** and copy the deployment URL.

> **Security Note:**  
> Setting your script to "Anyone" means anyone with the link can submit data. For sensitive use, restrict access or monitor submissions.

### 3. Connect the Form

Replace the Apps Script URL in your `index.html` (around line 315):

```javascript
const response = await fetch("YOUR_GOOGLE_APPS_SCRIPT_URL_HERE", {
```

---

## 📁 Project Structure

```
GoogleSheetHandler/
├── index.html    # Main form file
├── README.md     # Documentation
```

---

## 🎨 Customization

- 🎨 **Colors:** Change CSS variables in the `<style>` section for instant theming.
- 📝 **Fields:** Add inputs and adjust the Apps Script to capture more data.
- 💅 **Styling:** All CSS is inlined for quick, easy edits.

---

## 🚀 Deployment

- **Vercel (Recommended):** Connect your repo to [Vercel](https://vercel.com) for auto-deployments.
- **Other Options:** GitHub Pages, Netlify, or any static file host.

---

## 💡 Use Cases

Perfect for:
- Contact forms
- Feedback & surveys
- Event registrations
- Lead generation

---

## 🤝 Contributing

Pull requests and suggestions are welcome!  
Feel free to open issues to help improve the project.

---

## 📄 License

MIT License — Use freely for personal & commercial projects.

---

<p align="center"><b>⭐ Star this repo if you found it helpful!</b></p>

---

## 📬 Connect with Me
- 🌐 [Portfolio Website](https://adityagarwal.netlify.app/)
- 💼 [LinkedIn](https://www.linkedin.com/in/adityagarwal15)
- 🐙 [GitHub](https://github.com/adityagarwal15)
