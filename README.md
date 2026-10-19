# Smart Home Automation Dashboard

A modern, fully responsive, and animated smart home dashboard built with HTML, CSS, and vanilla JavaScript. It connects directly to a **Firebase Realtime Database** to visualize the live status of your physical IoT devices (like NodeMCU, ESP8266, or ESP32).

## 🌟 Features

*   **Real-time Synchronization:** Instantly reflects changes from your physical smart home devices via Firebase.
*   **Custom Animations:** Features smooth, dynamic animations (e.g., a spinning ceiling fan with startup/slowdown physics, glowing bulbs, and illuminating tube lights).
*   **Glassmorphism UI:** A sleek, dark-themed, futuristic user interface.
*   **Responsive Design:** Works flawlessly on desktop, tablet, and mobile screens.
*   **No Build Tools Required:** Pure HTML/JS/CSS, making it incredibly easy to host anywhere (Vercel, Netlify, GitHub Pages).

## 🛠️ Technologies Used

*   HTML5
*   CSS3 (Custom styling and animations)
*   JavaScript (ES6 Modules)
*   Firebase JavaScript SDK (v10+)

## 📦 Setup & Deployment (Vercel)

### 1. Firebase Configuration
Before deploying, you must connect the dashboard to your own Firebase project. 
1. Open the `index.html` file in your code editor.
2. Scroll down to the `<script type="module">` section.
3. Locate the `firebaseConfig` object and replace the placeholder strings with your actual Firebase project credentials:
   ```javascript
   const firebaseConfig = {
       apiKey: "YOUR_API_KEY",
       authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
       databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com", 
       projectId: "YOUR_PROJECT_ID",
       // ... other credentials
   };
   ```

### 2. Expected Database Structure
By default, the application listens to the following paths in your Firebase Realtime Database. The values can be boolean (`true`/`false`), strings (`"ON"`/`"OFF"`), or numbers (`1`/`0`).

```json
{
  "automation": {
    "light": true,
    "tube": false,
    "fan": true
  }
}
```
*(If your database paths are different, you can easily change them in the `index.html` file where the `onValue()` listeners are defined).*

### 3. Deploying to Vercel
1. Push this repository to GitHub (Make sure your repository is **Private** so you don't leak your Firebase API keys!).
2. Log into [Vercel](https://vercel.com/) with your GitHub account.
3. Click **Add New** > **Project** and import this repository.
4. Leave all build settings as default (Framework Preset: Other) and click **Deploy**.
5. Your live smart home dashboard will be ready in seconds!

## ⚠️ Security Note
Since this is a front-end only application, your Firebase Configuration is exposed in the source code. To keep your database secure:
*   Keep your GitHub repository private.
*   Restrict your Firebase API Key in the Google Cloud Console to only allow requests from your Vercel Domain.
*   Set your Firebase Realtime Database rules strictly to `.read: true` and `.write: false` for the public, ensuring only your IoT devices (using a secure backend or secret key) can update the values.
