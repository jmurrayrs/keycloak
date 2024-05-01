# Keycloak OpenID Connect Routes

This repository contains a collection of payloads for Keycloak OpenID Connect routes. Each route has a specific function within the Keycloak authentication and authorization process. Below are the details of each route:

## Token
- **Method**: POST
- **Description**: This route is used to obtain an access token using an authorization code.
- **Payload**:
  - `grant_type`: Authorization code.
  - `code`: The authorization code.
  - `client_id`: The ID of your client.
  - `redirect_uri`: The redirect URI.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/token`

## Introspect
- **Method**: POST
- **Description**: This route is used to introspect an access token.
- **Payload**:
  - `token`: The access token to introspect.
  - `client_id`: The ID of your client.
  - `client_secret`: The client secret.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/token/introspect`

## Userinfo
- **Method**: GET
- **Description**: This route retrieves user information using an access token.
- **Headers**: 
  - `Authorization`: Bearer token.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/userinfo`

## Logout
- **Method**: POST
- **Description**: This route logs out a user by invalidating their refresh token.
- **Payload**:
  - `client_id`: The ID of your client.
  - `client_secret`: The client secret.
  - `refresh_token`: The refresh token.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/logout`

## Certs
- **Method**: GET
- **Description**: This route retrieves the public certificates for the realm.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/certs`

## Revoke
- **Method**: POST
- **Description**: This route revokes an access token.
- **Payload**:
  - `client_id`: The ID of your client.
  - `client_secret`: The client secret.
  - `token`: The token to revoke.
  - `token_type_hint`: The type of token to revoke (e.g., access token).
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/revoke`

## Device Auth
- **Method**: POST
- **Description**: This route is used for device authorization.
- **Payload**:
  - `client_id`: The ID of your client.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/auth/device`

## CIBA Auth
- **Method**: POST
- **Description**: This route is used for Client Initiated Backchannel Authentication (CIBA).
- **Payload**:
  - `client_id`: The ID of your client.
  - `scope`: The scope (e.g., openid).
  - `binding_message`: A message used for binding.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/ext/ciba/auth`

## PAR
- **Method**: POST
- **Description**: This route is used for Pushed Authorization Requests (PAR).
- **Payload**:
  - `client_id`: The ID of your client.
  - `request_uri`: The URI for the request.
- **URL**: `{{base_url}}/realms/{{realm}}/protocol/openid-connect/ext/par/request`

## Contributions

If you would like to contribute more information or improve the documentation, please open a discussion topic or submit a pull request.

## Importing the Files

The JSON files in this repository can be imported into Postman and Insomnia for testing and development.
