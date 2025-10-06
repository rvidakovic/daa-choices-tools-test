# Protect My Choices (PMC) v2.0 Technical Specifications
This document outlines how participants can read the AdChoices Signal from the Protect My Choices browser extension. The extension stores preferences expressed through the WebChoices tool as an AdChoices Signal string.

## Key Concepts

**Accessing User Preferences (JavaScript 'Reader'):** Web participants can access user preferences in real-time by listening for the "ExtensionLoaded" event and then sending a "GetAdPreferences" message via window.postMessage(). The extension will respond with an "AdPreferences" event containing the preference data.

**Accessing User Preferences (Header String):** The extension inserts the AdChoices Signal into an HTTP header for every request. This header is "X-Adchoices" for Chrome and "Cookie2" for Safari. The header value can then be decoded to interpret the AdChoices Signal.

**Important Note on Decoding:** When decoding the base64url string back to binary, extra zeros (padding) may appear at the end due to the conversion process. These should be ignored when parsing the binary strings.