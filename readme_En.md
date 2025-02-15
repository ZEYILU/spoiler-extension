# Spoiler Detector (Chrome Extension)

A Chrome extension that detects potential spoilers in search queries or text input, combining **keyword filtering** and **OpenAI GPT-3.5-turbo** to determine if the content contains spoilers.

## Features

1. **Keyword Filtering**: Matches user-defined keywords.  
2. **Short-Circuit Logic**:  
   - If the text contains "spoiler" and does not include negations like "not spoiler" or "spoiler-free," it is directly classified as a spoiler.  
3. **Multiple Sensitivity Levels**: `low / medium / high` to adjust detection strictness via different prompts.  
4. **OpenAI Detection**: Calls OpenAI API for analysis only if keywords are matched; otherwise, it is skipped to improve efficiency.  

## Usage

1. **Load the Extension**  
   - Open `chrome://extensions/` → Enable **Developer Mode** → Click **"Load Unpacked"** and select the `spoiler-extension/` folder.  

2. **Configure Settings in Popup**  
   - Enable detection (`Enable Search Detection`)  
   - Select spoiler sensitivity (`Low / Medium / High`)  
   - Enter a comma-separated keyword list (e.g., `dies, killed, ending`).  

3. **Detect Spoilers While Browsing**  
   - When typing in a search bar or comment section, the extension analyzes the text.  
   - If a spoiler is detected, a **red warning banner** appears or the text is blurred.  

## Key Files

- **`manifest.json`**: Declares extension metadata and injects content scripts.  
- **`background.js`**: Handles `CHECK_SPOILER` requests, keyword filtering, and OpenAI API calls.  
- **`content.js`**: Listens for user input, sends detection requests, and modifies the webpage UI accordingly.  

## Important Notes

- **OpenAI API Key**:  
  - The API key is hardcoded in `background.js`; do not expose it publicly.  
  - It is recommended to use a backend proxy or private configuration for security.  

- **Performance & Costs**:  
  - Implement truncation, caching, and keyword pre-filtering to reduce API calls and save costs.  

- **Accuracy**:  
  - The detection is for demonstration purposes and may not be 100% accurate.  
  - Adjusting the prompt in `background.js` can help refine AI-based spoiler detection.  

---

### License & Disclaimer  

This project is for educational and demonstration purposes only. Please ensure **API key security** and follow OpenAI's usage policies. Contributions and improvements are welcome! 🚀
