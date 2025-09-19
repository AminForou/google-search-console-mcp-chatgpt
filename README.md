# Google Search Console MCP Server

This is a MCP (Machine Callable Program) server for interacting with Google Search Console API.

## Setup

1. Create a virtual environment:
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Create a Google Cloud service account and download credentials:
   - Go to the [Google Cloud Console](https://console.cloud.google.com/)
   - Create a new project or select an existing one
   - Enable the Search Console API for your project
   - Go to "IAM & Admin" > "Service Accounts"
   - Create a new service account
   - Grant it the necessary permissions (at least "Search Console API > Search Console API User" role)
   - Create a JSON key for this service account
   - Download the key and save it as `service_account_credentials.json` in this directory

4. Add your Search Console property to the service account:
   - In Google Search Console, add the service account email as a user to your property

## Usage

Run the server:

```
python -m mcp_gsc.main
```

The server exposes several MCP tools, including:

- `list_properties`: List Search Console properties accessible to the configured credentials.
- `delete_site`: Remove a Search Console property from the authenticated account.
- `get_search_analytics`: Retrieve performance metrics with configurable dimensions and lookback windows.
- `get_site_details`: Display metadata and verification status for a property.
- `get_sitemaps`: Summarize submitted sitemaps and their statuses.
- `inspect_url_enhanced`: Run the Search Console URL Inspection API for a specific page.
- `batch_url_inspection`: Inspect up to 10 URLs at once for quick diagnostics.
- `manage_sitemaps`: Submit, remove, or review sitemap information.
- `connector_search`: Search entry point required by ChatGPT connectors.
- `connector_fetch`: Fetch entry point required by ChatGPT connectors.
- `get_creator_info`: Basic information about the tool author.
