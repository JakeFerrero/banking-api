# Banking API
A basic Banking API - written in Typescript and that uses NestJS and sqlite - that simulates day-to-day operations that a bank employee may use.

## Setup
Install the project's dependancies via `npm i`.

Compile Typescript using `npm run compile`.

Run `node initDb.js` to initialize a test database.

## How to Use
Start the NestJS server with either `npm run start` or `nest start`.
Then use Postman, Thunderclient for VSCode, or any other API client to hit the API.
The API runs on `localhost:3000`.

## Testing
Each module has its own set of unit tests, aside from the controllers. The controllers are tested within the integration tests.

There are unit tests and integration tests. Unit tests leverage mocks to ensure an individual module is working as expected. Each integration test suite
uses a test sqlite database, which are initialized cleaned up before and after the tests.

To run the tests, use: `npm t`

## Additional Notes
This project uses controller-service-repository model, where the controllers are responsible for interacting with the consumer, services contain buisness logic,
and the repositories are responsible for interacting with the backend database. Each logical model of the API has its own controller, service, and repository.
In this case a `Customer`, `Accounts`, and `Transfers`.

The project uses a sqlite database to act as the backend data storage.

In a more realistic setting, you could potentially have many large data stores, or even need to make multiple requests to get certain data.
As such,there would ideally be a circuit breaker around data retrieval/manipulation operations in order to fail fast in case the external service
or database is having issues.