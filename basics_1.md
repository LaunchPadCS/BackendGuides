## An introduction to Backend Design

Many programs run directly on a user's device, like apps on a phone or laptop. However, when you want your app to be able to communicate with some central server, you probably need to write a backend. There's a lot of different ways to approach this, but we're going to cover some of the  basics in this section.


### Backend vs Frontend
It's important to clarify the difference between backend and frontend before moving further. A `frontend` application is the code that runs directly on a user's device. Most of the time, this just means a mobile app or a website. In the case of a website, the frontend code is the HTML, CSS, and JavaScript which runs directly inside the user's browser. A lot of products will have many different frontends instead of just one-- for example, Facebook has several mobile apps for iOS and Android as well as their main website. All of these would be considered the frontend for Facebook.

![HTTP Diagram](http://i.imgur.com/fSHDHxa.png)


The `backend` of an application is the code that runs on a server. The backend accepts requests from the frontend and sends back information. For example, if you open the Facebook app running on your phone, it doesn't know what posts it should show you. So it asks the Facebook backend to send back information about what posts it should show. The backend gets the request, takes a look at the database, decides what posts should be shown, and then sends back that information.

Most of the time, the frontend and backend communicate with each other using `HTTP`. If you want to know more about how HTTP works, you can take a look at [this](https://launchpadcs.gitbooks.io/core-guides/content/networking_01.html) article.

###How is backend development different?
On the frontend, you're usually pretty restricted on what tools you can use. If you're making a mobile app, you use Java or Swift. If you're making a web application, you're using HTML, CSS, and JavaScript. But on the backend, you can write an app using literally whatever you want. In fact, there's so many options to pick from that it can sometimes be hard to decide where to get started. We're going to cover one set of tools you can use for backend development, but just know that there's a lot of different options to choose from.

### Recommended Reading

[Networking & HTTP](https://launchpadcs.gitbooks.io/core-guides/content/networking_01.html)
