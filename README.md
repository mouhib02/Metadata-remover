# Metadata Remover

Your photos carry hidden details. When you take a picture, your phone or camera automatically embeds extra information inside the file: your GPS location, the exact time, your device model, and the editing software you used. Most people share these files online without realizing this data is attached.

This tool strips that hidden data away. Open the page, select a photo, and get a clean copy.

**Nothing is uploaded.** Everything happens locally in your web browser. No accounts, no cookies, no tracking.

---

## How to use it

You can run this on any computer, tablet, or phone (Windows, macOS, Linux, iOS, Android).

1. **Open the tool**: 
   * You can open `index.html` directly in any browser or host it via web server/GitHub Pages.
2. **Add your photos**:
   * **Drag and drop** files directly into the dashed box.
   * **Click or tap** inside the box to open your device's file selector.
   * **Paste** an image from your clipboard with `Ctrl + V` (or `Cmd + V` on macOS).
   * **Keyboard shortcut**: Press `Ctrl + O` (or `Cmd + O`) to open the file picker.
3. **Download the clean copies**:
   * The tool will analyze the image, show you what metadata was found (like location or camera info), and generate a new, clean version.
   * Click **Download** (or **Download all** for multiple photos) to save the clean copies.

---

## Google Search Engine Optimization (SEO) & Webmaster Setup

This project is fully optimized for **Google Search Engine** indexing, high ranking, and rich search results.

### SEO Features Included
- **Canonical URLs & Meta Tags**: Pre-configured canonical URL (`https://metadataremover.site/`), search-optimized titles, and intent-focused meta descriptions.
- **Structured Data (JSON-LD Schemas)**:
  - `WebApplication` schema for software application indexing.
  - `FAQPage` schema to enable Google **People Also Ask (PAA)** rich snippets.
  - `BreadcrumbList` schema.
- **Sitemap & Robots Configuration**:
  - `sitemap.xml` for indexer discovery.
  - `robots.txt` referencing `https://metadataremover.site/sitemap.xml`.
- **Social Sharing & Search Cards**: `og-image.png` Open Graph and Twitter Card thumbnails.
- **Web App Manifest**: `manifest.json` for PWA compliance and mobile Google indexing.

### How to Submit to Google Search Console

1. **Add Property**: Go to [Google Search Console](https://search.google.com/search-console) and add `https://metadataremover.site`.
2. **Verify Ownership**: Verify via HTML meta tag (add `<meta name="google-site-verification" content="..." />` to `<head>`) or DNS TXT record.
3. **Submit Sitemap**: In Search Console, navigate to **Sitemaps** and submit:
   ```
   https://metadataremover.site/sitemap.xml
   ```
4. **Validate Structured Data**: Test your live site using the official [Google Rich Results Test](https://search.google.com/test/rich-results) tool to confirm schema validation.

---

## How to verify it worked

You don't need technical tools to check if the metadata is gone. You can verify it using your computer's built-in file explorer:

### On Windows
1. Right-click your original image, select **Properties**, and go to the **Details** tab. You will see camera information, dates, and sometimes GPS location.
2. Right-click the cleaned image (ending in `_cleaned.jpg`) and open **Properties -> Details**. The details will be empty or reset.

### On macOS
1. Click your original image, press `Cmd + I` (or right-click and select **Get Info**). Look under the **More Info** section to see camera settings and location coordinates.
2. Do the same for the cleaned image. The **More Info** section will no longer show these details.

### On iOS / Android
1. View the details or swipe up on the original photo in your camera roll to see the map/location and camera info.
2. Save the cleaned photo to your device. Swiping up on it will show no map, location, or camera properties.

---

## Supported formats

| Format | Output Quality |
|--------|----------------|
| **JPEG** (`.jpg`, `.jpeg`) | High quality (0.95 compression) |
| **PNG** (`.png`) | Lossless (perfect preservation of pixels and transparency) |
| **WebP** (`.webp`) | High quality (0.95 compression) |

*Note: HEIC, TIFF, RAW, GIF, and SVG files are not supported. If you attempt to add them, the application will let you know and ask you to use a standard format.*

---

## How it works (The technical part)

When you load an image file, the browser decodes the raw pixels. This application draws those pixels onto a clean `<canvas>` element (an offscreen drawing board in the browser). 

When we ask the canvas to export the drawing using the browser's standard `canvas.toBlob()` method, it builds a brand new image file using only those raw pixels. Because the file is written completely from scratch by the browser's graphics engine, the original metadata container headers (like EXIF, XMP, and IPTC) are never copied over.

---

## License

This project is open source and available under the [MIT License](LICENSE).
