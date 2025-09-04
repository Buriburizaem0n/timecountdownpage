# Static HTML Countdown Timer

A simple, self-contained HTML file that displays a dynamic countdown timer to a specific date and time. This project is designed to be easy to use and modify, with no external dependencies (no jQuery, no external libraries).

## ✨ Features

* **Self-Contained**: Everything is in a single `index.html` file.
* **Easy to Use**: Simply open the HTML file in any modern browser to see it work.
* **Accurate Timezone Handling**: The countdown is based on a universal time point (UTC timestamp), making it accurate for all users worldwide, regardless of their local timezone.
* **User-Friendly Display**: Automatically detects the user's local timezone and displays the event's end time in their local format, eliminating confusion.
* **Customizable**: Easily change the target date, text, and visual appearance (CSS).
* **Lightweight & Fast**: No external libraries, ensuring fast load times.

## 🚀 How to Use

1.  Save the code as an `.html` file (e.g., `countdown.html`).
2.  Open the file in your web browser.

That's it! The countdown will start immediately.

## 🔧 How to Modify

You can easily customize the timer by editing the HTML file directly.

### 1. Changing the Target Date and Time

This is the most important part to modify.

1.  Open the `.html` file in a text editor.
2.  Find the following line inside the `<script>` tag:

    ```javascript
    const auctionEndDateObject = new Date('2025-09-09T23:59:00+01:00');
    ```

3.  Replace the date string with your desired end time. **It is crucial to use the ISO 8601 format (`YYYY-MM-DDTHH:mm:ss+HH:MM`) to ensure timezone accuracy.**

    * `YYYY-MM-DD`: Year-Month-Day
    * `T`: A required separator.
    * `HH:mm:ss`: Hour-Minute-Second
    * `+HH:MM` or `-HH:MM`: The timezone offset from UTC. This is the key to making the time absolute and universal.

    **Examples:**
    * **New York (EST, UTC-5):** `2026-01-15T22:00:00-05:00`
    * **Tokyo (JST, UTC+9):** `2025-12-25T18:00:00+09:00`
    * **UTC/GMT:** `2025-11-20T12:00:00Z` (The `Z` stands for Zulu time, which is UTC)

### 2. Customizing Appearance (CSS)

All visual styles (colors, fonts, sizes, etc.) are located within the `<style>` tags in the `<head>` section of the file. You can modify the CSS rules to match your website's design.

For example, to change the countdown timer's color, find `#countdown-timer` and change the `color` property:

```css
#countdown-timer {
    font-size: 3em;
    font-weight: bold;
    color: #007bff; /* <-- Change this color */
}
```

### 3. Editing Text Content

All display text can be changed directly in the HTML `<body>` section.
* **Main Title**: Modify the `<h1>` tag.
* **End Message**: Modify the text inside the `<div id="end-message">`.
* **Local Time Info**: Modify the text within the `<p id="local-time-info">`.

## ⚙️ How It Works (Technical Notes)

The script's accuracy relies on two key JavaScript features:
1.  **Universal Timestamp**: The target date string is immediately converted into a universal UTC timestamp (milliseconds since Jan 1, 1970) using `.getTime()`.
2.  **Local Time Calculation**: The script compares this fixed future timestamp with the user's current timestamp (also in UTC). The difference is always correct, regardless of the user's location.
3.  **Local Time Display**: The `toLocaleString()` method is used on the initial date object to display the end time in a format and timezone that is familiar to the user.

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).