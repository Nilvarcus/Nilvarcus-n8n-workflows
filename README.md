# Nilvarcus n8n Templates

A collection of n8n workflows for automating various tasks, personal projects, and content creation pipelines.

## General Information

### ⚠️ Important: Sanitized Templates
All workflows in this repository have been **sanitized** for public sharing. This means:
- All personal credentials and account handles have been removed.
- Private system IDs and folder paths have been replaced with placeholders.
- Execution history (`pinData`) has been cleared.

### How to Use
1. **Choose a Workflow**: Browse the [Workflows](#available-workflows) section below and download the relevant `.json` file.
2. **Import into n8n**: In your n8n workspace, create a new workflow and select **Import from File**.
3. **Configure Placeholders**: Search the imported workflow for strings starting with `YOUR_` (e.g., `YOUR_GOOGLE_DRIVE_FOLDER_ID`) and replace them with your actual data.
4. **Link Credentials**: Assign your own n8n credentials to each node. You may need to create new credentials if you haven't used those services in n8n before.

---

## Available Workflows

### [Obsidian to Social Media Automation](./Obsidian%20to%20Social%20Media%20Automation.json)

Automates publishing Markdown notes from Obsidian to multiple social platforms.

#### How it Works
1. **Watcher**: Periodically scans a Google Drive folder for Markdown files (synced from your Obsidian vault).
2. **Filter**: Only processes files where the YAML frontmatter `status` is set to `ready`.
3. **Parser**: Extracts YAML metadata (platform, images, post content).
4. **Router**: Sends the formatted post to specified platforms (Twitter/X, Mastodon, Bluesky, Threads, Facebook, Instagram).
5. **Updater**: Updates the file in Google Drive, setting `status: published` and adding a `posted_date`.

#### Required Placeholders
- **Google Drive**: `YOUR_GOOGLE_DRIVE_FOLDER_ID`, `YOUR_ATTACHMENTS_FOLDER_ID`.
- **BlueSky**: `YOUR_BLUESKY_USERNAME`, `YOUR_BLUESKY_APP_PASSWORD`.
- **Meta (Threads/Instagram)**: `YOUR_THREADS_ACCOUNT_ID`, `YOUR_INSTAGRAM_ACCOUNT_ID`.
- **Google Cloud Storage**: `YOUR_GCS_BUCKET_NAME` (used for hosting temporary images for platform uploads).
- **Google Sheets**: `YOUR_GOOGLE_SHEETS_FILE_ID` (used for managing tokens/logs if applicable).

#### Example Frontmatter
```yaml
---
status: ready
platform: 
  - Twitter
  - Bluesky
image: ["post_image.png"]
final post: "Hello from my Obsidian vault! 🚀"
---
```

---

## License
[MIT](LICENSE) - Feel free to use and adapt these workflows for your own needs.
