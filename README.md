<h1 align="center">auth-nodejs</h1>

Simple Nodejs authentication system with JWT tokens and confirmation via email

<h2>Installation</h2>

```bash
$ npm install
```

<h2>.env</h2>

Check 'example.env' file.

<h2>Run</h2>

```bash
$ npm run start
```

<h2>Endpoints</h2>

This API provides functionalities for user registration, login, logout, account activation, refresh tokens, and user retrieval (with authorization).

Endpoints:

- POST /registration
  - Description: Registers a new user.
  - Request Body:
    - email: User's email address (required, must be a valid email format).
    - password: User's password (required, minimum length of 3 characters, maximum length of 32 characters).
  - Response:
    - Upon successful registration, a response indicating success or a relevant success code
    - In case of errors, a response with appropriate error messages and status code.
- POST /login
  - Description: Logs in a user.
  - Request Body:
    - email: User's email address (required).
    - password: User's password (required).
  - Response:
    - Upon successful login, a response containing an authentication token and any additional relevant information.
    - In case of errors, a response with appropriate error messages and status code
- POST /logout
  - Description: Logs out a user, potentially invalidating their authentication token.
    - Request Body: (Optional, depending on implementation)
    - Response:
      - Upon successful logout, a response indicating success or a relevant success code
      - In case of errors, a response with an appropriate error message and status code.
- GET /activate/:link
  - Description: Activates a user's account using an activation link sent via email.
  - URL Parameter:
    - :link: Activation link token (required).
  - Response:
    - Upon successful activation, a response indicating success or a relevant success code
    - In case of errors, a response with an appropriate error message and status code
- GET /refresh
  - Description: Refreshes an expired authentication token (if implemented).
  - Request Headers:
    - Authorization: May contain the existing authentication token.
  - Response:
    - Upon successful token refresh, a response with a new authentication token and any additional relevant information.
    - In case of errors, a response with an appropriate error message and status code.
- GET /users (Authorized - Requires a valid authentication token)
  - Description: Retrieves a list of users (or filtered data based on implementation).
  - Request Headers: (Required)
    - Authorization: Must contain a valid authentication token.
  - Response:
    - Upon successful authorization and data retrieval, a response containing a JSON array of user data.
    - In case of authorization errors, a response with an appropriate error message and status code.
    - In case of other errors, a response with an appropriate error message and status code
