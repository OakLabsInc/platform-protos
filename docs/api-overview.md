# OakOS API Overview

Welcome!  This documentation will introduce you to the different ways you can access the OakOS APIs.  For a full description of services offered, see the [OakOS API Services](/docs/api-overview.md) document.

# Use cases

Oak OS allows you to choose different application building strategies based on your needs and skillset:

  - You can build a browser based app loaded into our prebuilt container, which will host it and provide the supporting environment.
  - You can build both the browser and server components within your own container.  You can base this on our application starter or choose your own set of technologies to bundle.

Based on the type of app that you are building several different ways to connect to the OakOS APIs are available to you:

  - In a browser environment, `window.oak` is available and has methods on it that will communicate with the API.  You will pass normal Javascript objects to these methods, and all network communication will be handled for you.
  - On the server, you can access OakOS APIs via their `grpc` implementation.


# window.oak

If you are building a purely browser based application then `window.oak` is the most convenient way to access the OakOS APIs.  Authentication is performed automatically by the environment, and you are free to call any of the API methods that are documented, provided they are configured and running on your installation.  See [configuring services](#configuring_services) below for details.

# grpc

If you prefer to connect to the OakOS APIs from a server-based environment, you can use the `grpc` API.  The instructions for connecting will vary depending on your chosen language, but in general will involve:

1. Acquiring the `.proto` definitions for the API you wish to consume.  This github repository contains the OakOS `.proto` definitions.
2. Acquiring a `grpc` implementation for your chosen language.  These are implemented and well documented for most popular programming languages.
3. When you initialize the `grpc` client you will pass it the `.proto` definitions and give it the hostname that you want to connect to.
4. The `grpc` client will now have methods for all of the API services that are available, and will handle network communications for you.

# Configuring Services

Certain core services are provided with every OakOS installation.  Other services may need to be enabled so that they can be downloaded and booted on your kiosk.
