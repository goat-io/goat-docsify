# Configuration

## Introduction

Your Goat backend can do a lot of things for you. We have a bunch of possible configurations for managing Databases, Queues, Messages and many others. All of those services require credentials and they are all present in the ENV file.

## Configuring your Environment

Goat uses DotEnv to manage environment configuration variables. Every fresh installation comes with a `.env.example` file with all possible variables that you can use, depending on the services that your application requires. At the moment that you create your app using `goat new` command, the `.env.example` file will be automatically copied to the same location under the name `.env` so it will start working from the start.

Please DO NOT include the .env file in your git repository, you don´t want to expose your personal keys to the world! You might want to leave your .env.example as reference, but make sure not to input real credentials in there.

> All variables in the .env file can be overwritten by external environment variables present at the server level

It is also recommended that you remove all environment variables that you are not using. Make sure that your `.env` file is readable and that your `.env.example` file represents exactly all the required variables.

## Using the variables

As any other ENV variable in JS, you Goat ENV variables can be used by referring to the process.env variable `process.env.<NAME-OF-THE-VARIABLE>`. Please remember that all `.env` variables will be parsed as `strings`, so make sure that you are using the proper logical comparisons.

## Important ENV variables

As mentioned, all libraries we use have their own **_ENV_** variables for configuration. We will cover individual cases under the docs of each one, but there are a couple "global" variables that we would like you to meet. **_Developer these are your variables, variables this is your dev._**

| Variable        | Description                                                                                                                                 |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **APP_DEBUG**   | Defines the log level of the Logger helper. Use one of these `trace`,`debug` , `info` , `warn` , `error` , `silent`                         |
| **APP_PORT**    | Sets the running port for the Backend. Remember that Manager expects the app to run on port `3001`                                          |
| **WORKER_NODE** | Defines if the server should process background Jobs. Use either `true` or `false`                                                          |
| **WORKER_ONLY** | A worker only server does not process API calls but will process Jobs, very useful for multi node deployments. Use either `true` or `false` |
| **GOAT_AUTH**   | Wether to use or not the out of the box Goat `Users`, `Roles` and `JWT` token for auth. Use either `true` or `false`                        |  |
