# Keycloak OpenID Endpoint Configuration

This repository was created with the intention of sharing the OpenID Connect route payloads from Keycloak. If you would like to contribute more information, please open a discussion topic to improve this document.

The file is in JSON format and can be imported into [Postman](https://www.postman.com/) and [Insomnia](https://insomnia.rest/download).


# Keycloak OpenID Connect Payloads Documentation

This document describes the OpenID Connect routes for Keycloak, focusing on various grant types and other supported types of data. The following are the environment variables, routes, and payloads for each endpoint.

## Environment Variables
- **base_url**: The base URL for Keycloak, typically `http://localhost:8080` if you is running keycloak from docker container.
- **realm**: The Keycloak realm.

## Routes and Payloads

### Authorization Endpoint
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/auth`
- **Method**: GET
- **Description**: This route initiates the authorization process.

### Token Endpoint - Authorization Code
- **Method**: POST
- **Payload**:
  - `grant_type`: `authorization_code`
  - `code`: Authorization code.
  - `client_id`: Client ID.
  - `redirect_uri`: Redirect URI.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/token`
- **Description**: This endpoint is used to obtain an access token using an authorization code.

### Token Endpoint - Refresh Token
- **Method**: POST
- **Payload**:
  - `grant_type`: `refresh_token`
  - `refresh_token`: Refresh token.
  - `client_id`: Client ID.
  - `client_secret`: Client secret.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/token`
- **Description**: This endpoint is used to refresh tokens.

### Token Endpoint - Client Credentials
- **Method**: POST
- **Payload**:
  - `grant_type`: `client_credentials`
  - `client_id`: Client ID.
  - `client_secret`: Client secret.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/token`
- **Description**: This endpoint is used to get tokens via client credentials.

### Token Endpoint - Resource Owner Password
- **Method**: POST
- **Payload**:
  - `grant_type`: `password`
  - `username`: Username.
  - `password`: Password.
  - `client_id`: Client ID.
  - `client_secret`: Client secret.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/token`
- **Description**: This endpoint allows you to get an access token by providing username and password.

### Introspection Endpoint
- **Method**: POST
- **Payload**:
  - `token`: The token to introspect.
  - `client_id`: Client ID.
  - `client_secret`: Client secret.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/token/introspect`
- **Description**: This endpoint introspects tokens to check their validity.

### Userinfo Endpoint
- **Method**: GET
- **Headers**: `Authorization: Bearer <access_token>`
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/userinfo`
- **Description**: This endpoint retrieves user information.

### Logout Endpoint
- **Method**: POST
- **Payload**:
  - `client_id`: Client ID.
  - `client_secret`: Client secret.
  - `refresh_token`: Refresh token.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/logout`
- **Description**: This endpoint is used to log out a user by invalidating refresh tokens.

### Certs Endpoint
- **Method**: GET
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/certs`
- **Description**: This endpoint retrieves the JSON Web Key Set (JWKS) for token signature verification.

### Revoke Endpoint
- **Method**: POST
- **Payload**:
  - `client_id`: Client ID.
  - `client_secret`: Client secret.
  - `token`: The token to revoke.
  - `token_type_hint`: `access_token`
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/revoke`
- **Description**: This endpoint is used to revoke tokens.

### Device Authorization Endpoint
- **Method**: POST
- **Payload**:
  - `client_id`: Client ID.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/auth/device`
- **Description**: This endpoint is used for device-based authorization.

### CIBA Authentication Endpoint
- **Method**: POST
- **Payload**:
  - `client_id`: Client ID.
  - `scope`: Scope.
  - `binding_message`: Binding message.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/ext/ciba/auth`
- **Description**: This endpoint is used for Client Initiated Backchannel Authentication (CIBA).

### Pushed Authorization Request Endpoint (PAR)
- **Method**: POST
- **Payload**:
  - `client_id`: Client ID.
  - `request_uri`: Request URI.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/ext/par/request`
- **Description**: This endpoint is used for pushed authorization requests.

## Contributions and Further Information

If you'd like to contribute more information or have questions, feel free to open a discussion or submit a pull request.

