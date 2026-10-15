# Postman API Testing

A Postman project demonstrating REST API testing, JavaScript test assertions, environment variables, and asynchronous HTTP requests using the [JSONPlaceholder](https://jsonplaceholder.typicode.com/) fake REST API.

## Project Overview

This project explores two approaches to working with REST APIs in Postman:

- **Imperative API Scenario** — executes HTTP requests for creating, retrieving, updating, and deleting user resources, with response validation.
- **Asynchronous API Scenario** — sends multiple HTTP requests asynchronously using Postman's `pm.sendRequest()` and validates their responses.
- **Environment Variables** — uses configurable variables to manage the API base URL and user IDs.
- **Automated Tests** — validates HTTP status codes and response data using JavaScript assertions.

## Tech Stack

- Postman
- REST API
- JavaScript
- JSON
- JSONPlaceholder

## Repository Structure

```text
API/
├── Asynchronous API.json
├── Imperative API.json
├── JSONPlaceholder_Env.json
├── README.md
└── screenshots/
    ├── imperative-scenario-results1.png
    ├── imperative-scenario-results2.png
    ├── asynchronous-scenario-results1.png
    └── asynchronous-scenario-results2.png
```

## Getting Started

### Prerequisites

- [Postman](https://www.postman.com/downloads/)
- An internet connection to access JSONPlaceholder

### Installation

1. Clone or download this repository:

   ```bash
   git clone https://github.com/Sp0tik/API.git
   cd API
   ```

2. Open Postman.
3. Import the following files into Postman:
   - `Imperative API.json`
   - `Asynchronous API.json`
   - `JSONPlaceholder_Env.json`
4. Select the imported environment and make it active.
5. Verify that the environment variables are configured correctly.
6. Run the requests individually or use the Collection Runner where appropriate.

### Environment Variables

| Variable | Description |
|---|---|
| `baseUrl` | Base URL of the JSONPlaceholder API |
| `existingUserId` | ID of an existing user used in requests |
| `tempUserId` | Stores the ID returned by the user creation request |

The default API base URL is:

```text
https://jsonplaceholder.typicode.com
```

## API Scenarios

### 1. Imperative API Scenario

The imperative collection demonstrates common HTTP operations on user resources.

| Request | Method | Endpoint | Purpose |
|---|---|---|---|
| Create User | POST | `/users` | Creates a simulated user resource |
| Get User Details | GET | `/users/{{existingUserId}}` | Retrieves an existing user |
| Update User | PUT | `/users/{{existingUserId}}` | Sends updated user data |
| Delete User | DELETE | `/users/{{existingUserId}}` | Sends a delete request |

The collection includes JavaScript assertions to validate response status codes and response data. The creation request also stores the returned user ID in the `tempUserId` environment variable.

**Note:** The current requests use `existingUserId` for retrieval, update, and deletion. The collection does not yet automatically connect the newly created user's ID to the remaining requests.

### 2. Asynchronous API Scenario

The asynchronous collection demonstrates how to initiate multiple HTTP requests without waiting for each request to finish before starting the next one.

The pre-request script uses Postman's `pm.sendRequest()` to send requests to:

- `/posts`
- `/comments`
- `/users`

Each asynchronous callback validates the HTTP response status.

The main request retrieves `/posts/1`.

This scenario demonstrates asynchronous request handling and response validation in Postman. The callbacks may complete in a different order depending on response times.

## Test Execution Results

### Imperative API Scenario

The screenshots below show the execution results of the imperative scenario.

![Imperative Scenario Results - Part 1](screenshots/imperative-scenario-results1.png)

![Imperative Scenario Results - Part 2](screenshots/imperative-scenario-results2.png)

### Asynchronous API Scenario

The screenshots below show the execution results of the asynchronous scenario.

![Asynchronous Scenario Results - Part 1](screenshots/asynchronous-scenario-results1.png)

![Asynchronous Scenario Results - Part 2](screenshots/asynchronous-scenario-results2.png)

## Skills Demonstrated

- REST API fundamentals and HTTP methods
- API request and response validation
- Writing JavaScript assertions in Postman
- Managing environment variables
- Sending asynchronous HTTP requests
- Working with JSON data
- Organizing API collections for repeatable testing
- Documenting test scenarios and execution results

## Limitations

This project uses JSONPlaceholder, a public fake REST API intended for testing and learning.

- Write operations such as POST, PUT, and DELETE simulate API behavior.
- Changes are not permanently stored on the server.
- The generated user ID should not be treated as a persistent resource.
- The imperative collection currently uses an existing user ID for subsequent operations rather than automatically chaining all requests through the newly created user.

## Possible Improvements

- Connect the create, retrieve, update, and delete requests into a single end-to-end workflow.
- Add negative test cases for invalid IDs and unexpected responses.
- Validate additional response fields and data types.
- Add reusable test scripts and more detailed assertions.
- Document expected and actual results for each test scenario.

## Author

GitHub: [Sp0tik](https://github.com/Sp0tik)
