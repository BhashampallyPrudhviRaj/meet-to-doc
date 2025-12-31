# meet-to-doc

Python script for converting markdown meeting notes to formatted Google Docs.

## Overview

This project provides a Google Colab notebook that converts markdown-formatted meeting notes into a well-formatted Google Document with proper styling, including:
- Heading hierarchy (H1, H2, H3)
- Nested bullet points with proper indentation
- Markdown checkboxes converted to Google Docs checkboxes
- Styled @mentions (bold and colored)
- Distinct footer formatting

## Features

✨ **Automated Conversion**: Converts markdown to Google Docs with a single click
📝 **Smart Formatting**: Preserves document structure and hierarchy
☑️ **Checkbox Support**: Markdown `- [ ]` becomes actual Google Docs checkboxes
👤 **Mention Styling**: @mentions are automatically styled with bold blue text
🔒 **Secure Authentication**: Uses Google Colab's built-in authentication

## Requirements

- Google Account
- Access to Google Colab
- Google Docs API enabled (automatically handled in Colab)

## Required Dependencies

The notebook automatically installs these packages:
```
google-auth
google-auth-oauthlib
google-auth-httplib2
google-api-python-client
```

## How to Run in Colab

### Step 1: Open the Notebook
1. Click the link below to open the notebook in Google Colab:
   - [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/BhashampallyPrudhviRaj/meet-to-doc/blob/main/markdown_to_google_doc.ipynb)
   
   OR
   
2. Navigate to [Google Colab](https://colab.research.google.com/)
3. Click **File > Open notebook**
4. Select **GitHub** tab
5. Paste the repository URL: `https://github.com/BhashampallyPrudhviRaj/meet-to-doc`
6. Click on `markdown_to_google_doc.ipynb`

### Step 2: Authenticate
1. Run the authentication cell
2. Click the authentication link when prompted
3. Select your Google account
4. Click **Allow** to grant permissions

### Step 3: Run the Conversion
1. Execute all cells in order (Runtime > Run all)
2. The script will create a new Google Doc
3. A link to the created document will be displayed

## Setup Instructions

### For Local Development

If you want to run this locally (not in Colab), you'll need to:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/BhashampallyPrudhviRaj/meet-to-doc.git
   cd meet-to-doc
   ```

2. **Install dependencies**:
   ```bash
   pip install google-auth google-auth-oauthlib google-auth-httplib2 google-api-python-client
   ```

3. **Set up Google Cloud Project**:
   - Go to [Google Cloud Console](https://console.cloud.google.com/)
   - Create a new project
   - Enable Google Docs API
   - Create OAuth 2.0 credentials
   - Download credentials JSON file

4. **Modify authentication**:
   - Replace Colab auth with OAuth flow using credentials file

## Project Structure

```
meet-to-doc/
│
├── markdown_to_google_doc.ipynb    # Main Colab notebook
├── README.md                        # This file
└── sample_output/                   # Example outputs (optional)
```

## How It Works

1. **Authentication**: Uses Google Colab's built-in `auth.authenticate_user()` for seamless OAuth
2. **Document Creation**: Creates a new Google Doc via the Docs API
3. **Markdown Parsing**: Parses markdown text line by line
4. **Format Mapping**: Maps markdown syntax to Google Docs formatting:
   - `# Heading` → Heading 1
   - `## Heading` → Heading 2  
   - `### Heading` → Heading 3
   - `* Item` or `- Item` → Bullet points with nesting
   - `- [ ]` → Checkbox (unchecked)
   - `@name` → Bold blue text
5. **Batch Updates**: Applies all formatting in efficient batch requests

## Example Input/Output

### Input (Markdown)
```markdown
# Product Team Sync - May 15, 2023

## Attendees
- Sarah Chen (Product Lead)
- Mike Johnson (Engineering)

## Action Items
- [ ] @sarah: Finalize Q3 roadmap by Friday
- [ ] @mike: Schedule technical review
```

### Output
A formatted Google Doc with:
- "Product Team Sync - May 15, 2023" as Heading 1
- "Attendees" and "Action Items" as Heading 2
- Proper bullet points
- Actual checkboxes for action items
- @mentions in bold blue text

## Limitations

- Runs in Google Colab environment (requires browser)
- Creates new documents (doesn't edit existing ones)
- Basic markdown support (headings, bullets, checkboxes)
- @mention styling is decorative (doesn't create actual Google Docs mentions)

## Error Handling

The script includes error handling for:
- Authentication failures
- API rate limits
- Invalid markdown syntax
- Network issues

## Contributing

Feel free to fork this repository and submit pull requests for improvements!

## Troubleshooting

**Issue**: Authentication fails
- **Solution**: Make sure you're running in Google Colab and click the authentication link

**Issue**: Document creation fails  
- **Solution**: Check your Google account permissions and try re-authenticating

**Issue**: Formatting doesn't match expected output
- **Solution**: Verify your markdown syntax matches the expected format

---

**Note**: This project is designed to run in Google Colab for ease of use and authentication. For production use, consider implementing proper OAuth flow with credential management.
