# CAENView Monitoring Dashboard

A GitHub Pages implementation that embeds CAENView and adds comprehensive monitoring and logging capabilities.

## Features

- **Dashboard View**: Displays room status information in an easy-to-read card format
- **Original CAENView**: Embeds the original CAENView interface via an iframe
- **Activity Logs**: Tracks and logs all user interactions and system events
- **Search & Filter**: Quickly find rooms by name or filter by building
- **Export Functionality**: Export logs for analysis or record-keeping

## Setup Instructions

1. **Create a GitHub Repository**

   - Sign in to your GitHub account
   - Click "New Repository"
   - Name it something like `caenview-monitor`
   - Make sure it's set to "Public" if you want to use GitHub Pages for free

2. **Upload the Files**

   - Upload `index.html` (main dashboard file)
   - Upload `README.md` (this file)
   - Upload any additional assets (JavaScript files, CSS, images) if you've separated them

3. **Enable GitHub Pages**

   - Go to your repository Settings
   - Scroll down to "GitHub Pages" section
   - Select "main" branch as the source
   - Click "Save"
   - GitHub will provide a URL where your site is published (typically https://yourusername.github.io/caenview-monitor)

4. **Access Your CAENView Monitor**

   - Visit the GitHub Pages URL provided in the previous step
   - Your CAENView Monitoring Dashboard is now live!

## Technical Details

### Same-Origin Policy and CORS

The implementation attempts to embed CAENView via an iframe. However, due to same-origin policy restrictions, there are limitations:

- The iframe will load CAENView, but JavaScript cannot directly access its content
- Interactions within the iframe cannot be monitored directly
- If CAENView sets X-Frame-Options to deny framing, the iframe approach won't work

### Alternatives for Production Use

For a more robust solution:

1. **Proxy Server**: Set up a server to proxy requests to CAENView, allowing you to bypass CORS restrictions
2. **API Integration**: If CAENView offers an API, use it instead of iframe embedding
3. **Web Scraping**: Use a server-side script to periodically scrape CAENView data and store it in your own database

## Customization

### Adding More Rooms

Modify the `roomData` array in the JavaScript section to add more rooms:

```javascript
const roomData = [
    // Existing rooms...
    { building: "NewBuilding", room: "123", power: "ok", source: "ok", projector: [{ hours: 1000 }], mics: { expected: 2, actual: 2 }, cameraStatus: "ok" },
];
```

### Changing the Theme

Update the CSS styles in the `<style>` section of index.html to match your organization's branding.

## Troubleshooting

### CAENView Not Loading in Iframe

If the CAENView website cannot be loaded in an iframe:

1. Check if CAENView sets X-Frame-Options to DENY or SAMEORIGIN
2. Consider implementing one of the alternative approaches mentioned in the Technical Details section

### Logs Not Persisting

The current implementation uses localStorage which:
- Has limited storage (typically 5-10MB)
- Is browser-specific (logs won't transfer between devices)

For a production environment, consider:
- Using a backend service to store logs (Firebase, AWS, etc.)
- Implementing a download/backup feature for logs

## License

This project is available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
