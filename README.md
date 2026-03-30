# Obsidian to Social Media Automation

This n8n template automates publishing your markdown posts from an Obsidian vault (synced via Google Drive) to multiple social media platforms including Twitter (X), Mastodon, Bluesky, Threads, Facebook, Instagram, and Pixelfed.

## Features
- Periodically checks or triggers a workflow to fetch "ready" markdown files from a designated Google Drive folder.
- Extracts YAML frontmatter properties from the markdown (e.g. `category`, `platform`, `image` for attachments, `status`, etc.).
- Depending on the `platform` tags specified in your markdown files, it formats and routes the final post to the selected platforms.
- Optionally fetches images based on the filename in the frontmatter from a designated Google Drive attachments folder.
- Rewrites the markdown content in Google Drive to update its `status` from `ready` to `published` and stamps the `posted_date`.

## Installation & Setup
1. **Importing:** In your n8n workspace, go to your Workflows and import the `Obsidian to Social Media Automation.json` file.
2. **Credentials Setup:** The template requires credentials for multiple APIs. Due to the template scrub process, all personal credential IDs have been removed. 
   - You will need to click on any node requiring credentials (such as Google Drive, Twitter API, Mastodon, Facebook Graph API, etc.) and assign your own linked credentials.
3. **Updating Node Parameters:**
   - **Google Drive Nodes (Folders):** Check the "Search files and folders" nodes and replace `YOUR_SOCIAL_MEDIA_POSTS_FOLDER_ID` and `YOUR_ATTACHMENTS_FOLDER_ID` with the actual folder IDs from your Google Drive path.
   - **Bluesky Authentication:** Double click the HTTP Request nodes for Bluesky and replace `your.bsky.handle` with your own identifier, and `YOUR_APP_PASSWORD` with a newly generated app password.
   - **Meta Platforms Graph API:** For Threads and Instagram nodes utilizing the `facebookGraphApi` type, replace `YOUR_THREADS_ACCOUNT_ID` or `YOUR_INSTAGRAM_ACCOUNT_ID` values with your respective Meta page/user node IDs. 
4. **Trigger Testing:**
   - Modify your Obsidian markdown note to have `status: ready` and verify that the frontmatter values (e.g., image paths) are correctly formatted. 
   - Execute the workflow manually first before turning it to Active mode.

## Example File YAML Configuration

Your Obsidian Note needs to be somewhat formatted like this for the workflow to parse correctly:
```yaml
---
status: ready
category: Announcements
platform: 
  - Twitter
  - Mastodon
  - Bluesky
image: ["my_image_attachment.png"]
final post: "This is a post generated from my Obsidian vault! 🔥"
---
# The rest of the document here
```
