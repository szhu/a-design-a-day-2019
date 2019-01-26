# Low-Cost Indoor Positioning System

## Background

There are tools* that allow computers to measure the signal strength of all Wi-Fi routers, not just those that the computer is connected to. If we have enough nearby Wi-Fi routers, even if none of them are connected to the internet, you can use that data let the computer locate itself.

\*Example of tool: https://superuser.com/a/1281319/110699

## Idea

An app that reads Wi-Fi signal strength data to determine location.

Since many factors (not just distance from the router) influence Wi-Fi signal strength, we can't just enter the locations of the routers and do triangulation. However, the app can be trained using machine learning, where the input is all the signal strengths and the output is the answer to a location-related question ("What are my coordinates?", "Am I at my desk?"). The app will have a training mode where the user can enter where the computer is currently located.

Because of the trust and large amount of training input data required, this setup couldn't be used for all situations that require locating a device, but it could be used in an office setting so that coworkers can find each other in person. If all computers in the office are similar, the training data from all computers can be combined (data can be sent to a server) for to improve data for everyone and to make it so that not everyone needs to add training data to benefit from the system.
