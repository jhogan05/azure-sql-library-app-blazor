# API Testing Files

This folder contains HTTP request files for testing the Data API Builder (DAB) endpoints using the REST Client extension in VS Code.

## Files:

- **`books.http`** - REST API tests for book operations (CRUD)
- **`authors.http`** - REST API tests for author operations (CRUD)  
- **`graphql.http`** - GraphQL queries and mutations

## Usage:

1. Start your Data API Builder service:
   ```bash
   # In the dab folder
   dab start --config=dab.config.json --no-https-redirect
   ```

2. Open any `.http` file in VS Code
3. Click "Send Request" above any HTTP request
4. View the response inline

## Variables:

The base URL is centrally configured in two ways:

### Option 1: VS Code Settings (Active)
The `baseUrl` is configured in `.devcontainer/devcontainer.json` under `rest-client.environmentVariables`. This automatically provides `{{baseUrl}}` and `{{graphqlUrl}}` to all `.http` files.

### Option 2: Environment File (Alternative)
Use `rest-client.env.json` for multiple environments. Change environment by:
1. Open VS Code Command Palette (Cmd/Ctrl + Shift + P)
2. Type "Rest Client: Switch Environment"
3. Select "development" or "production"

## Notes:

- Make sure your SQL Server database is running and DAB is configured
- Some endpoints may require authentication depending on your DAB configuration
- GraphQL mutations may not be enabled by default in DAB - check your configuration
- Adjust field names and structure based on your actual database schema

## Testing Workflow:

1. Test basic GET operations first
2. Verify your database schema matches the expected fields
3. Test POST operations to create data
4. Test PUT/PATCH for updates
5. Test GraphQL queries for complex data retrieval