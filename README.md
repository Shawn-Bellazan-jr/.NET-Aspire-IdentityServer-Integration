# .NET Aspire IdentityServer Integration

This repository demonstrates how to integrate a .NET 9.0 application with Duende IdentityServer, leveraging the client credentials flow for secure API authentication and authorization.

## Overview

The project showcases a step-by-step implementation of the client credentials flow based on the [Duende IdentityServer Quickstart Guide](https://docs.duendesoftware.com/identityserver/v7/quickstarts/1_client_credentials/). It is designed to be a reference implementation for secure authentication in modern .NET applications.

## Features

- **Client Credentials Flow**: Authenticate clients directly for API access.
- **Duende IdentityServer Integration**: Secure and standards-compliant identity management.
- **.NET 9.0 Compatibility**: Built using the latest version of .NET for optimal performance and features.
- **Secure APIs**: Example implementation of a protected API endpoint using bearer tokens.
- **Extensible**: Ready to be adapted for additional flows like authorization code and PKCE.

## Prerequisites

- **.NET SDK 9.0**: [Download](https://dotnet.microsoft.com/download/dotnet/9.0)
- **Duende IdentityServer**: Installed and configured.
- **Postman or cURL**: For testing API endpoints.
- **MSSQL Server** (Optional): For storing clients and tokens in a database.

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/.NET-Aspire-IdentityServer-Integration.git
cd .NET-Aspire-IdentityServer-Integration
```

### 2. Configure IdentityServer
Follow the [Duende IdentityServer Quickstart Guide](https://docs.duendesoftware.com/identityserver/v7/quickstarts/1_client_credentials/) to set up IdentityServer.

- Define a client with the client credentials flow.
- Configure API scopes and resources.

### 3. Set Up the .NET Application
Update the `appsettings.json` file with your IdentityServer URL and client details:
```json
{
  "IdentityServer": {
    "Authority": "https://localhost:5001",
    "ClientId": "client-id",
    "ClientSecret": "client-secret",
    "Scopes": "api-scope"
  }
}
```

### 4. Run the Application
Build and run the application:
```bash
dotnet build
dotnet run
```

### 5. Test the API
- Obtain a token using your client credentials:
  ```bash
  curl -X POST \
    -d "grant_type=client_credentials&client_id=client-id&client_secret=client-secret&scope=api-scope" \
    https://localhost:5001/connect/token
  ```
- Use the token to access a protected API endpoint:
  ```bash
  curl -H "Authorization: Bearer {TOKEN}" https://localhost:5000/protected-endpoint
  ```

## Project Structure

- **`IdentityServer/`**: Configuration for the IdentityServer instance.
- **`AspireAPI/`**: .NET application with protected API endpoints.
- **`Shared/`**: Common utilities and models.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any changes.

## License

This project is licensed under the [MIT License](LICENSE).
