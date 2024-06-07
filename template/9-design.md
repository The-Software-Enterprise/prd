# Design and Implementation

## Frontend

### Implementation Framework

Our application will be developed in Kotlin using the Jetpack Compose framework and will follow the Model-View-ViewModel (MVVM) architecture. This approach ensures a modern, efficient, and scalable development process, facilitating a clear separation of concerns. With MVVM, we can achieve a more manageable and testable codebase, where the UI components are decoupled from the business logic. This structure enhances maintainability, simplifies UI updates, and improves overall app performance and user experience.

### Essential Screens

In most cases, the application is visually composed of the title of the different parts of the application at the top, the content of the page in the center of the screen and, at the bottom of the screen, a navigation bar made up of five parts.

### Dynamic View Rendering

For most of our screens, the backend controls the UI changes through the view models we implemented. The Firebase database facilitates this by providing various collections that we manage. We created the DbServiceImpl class to handle our Firebase operations, and we use its functions across all our view models to update the UI accordingly. We use Hilt and Dagger to inject all Firebase objects in view models.

### Data Management

The frontend will securely store refresh tokens and cache necessary app data. This approach prioritizes the security of sensitive information and the efficiency of the app’s performance.

## Backend

Following the staff's advice, we used Firebase for our backend implementation. Firebase proved to be user-friendly and streamlined our backend processes. By adding a single class to manage database operations, we ensured a consistent and clean database.

### Association scraping

We scraped all the associations from the EPFL Associations API and added them to the Firebase database. By integrating this data throughout our application, we ensured that all EPFL associations were readily available, allowing us to have a fully functional app from the start.

### Authentication

Initially, we considered using Tequila for authentication, but our professor advised against it due to the service's potential discontinuation. Consequently, we implemented email authentication using Firebase Authentication. To obtain the necessary customer information at sign up, we utilized the EPFL People API. This API provides details such as the customer's first name, last name, section, year, and the associations they belong to.

### Offline persistent data

For offline persistent data, we utilized the native functionalities of Firestore who cached all the data at each call. This enabled us to store data locally and access it even when the user is offline. Additionally, to ensure data persistence even after closing the app, we used the Room database to store all associations.

## Security Considerations

### Authentication

Firebase Authentication is a secure and reliable method for authenticating users. By using email authentication, we ensure that only authorized users can access the app. Firebase allows us to also simply verify the user's email address, which adds an extra layer of security. And a two-step verification process is also available to further secure the user's account.

### Data Protection

We store all data in Firestore, which is a secure and reliable database. Firestore provides built-in security rules that allow us to control access to our data. We can define who has access to read or write data, ensuring that only authorized users can access the database.

## Test Plan

To test our application, we employed two primary frameworks: Robolectric, primarily for unit tests, and JUnit. These were used in conjunction with Android Hilt to properly inject our dependencies. We executed our tests on a Firebase emulator, covering end-to-end tests, connected tests, and unit tests.

### Firebase emulator

We utilized a Firebase emulator to replicate Firebase services, which was extremely beneficial for testing and running our application in an isolated environment. By integrating this emulator into our GitHub continuous integration workflow, we ensured that our tests remained consistent and independent of customer data.

### End to end tests

End-to-end tests simulate real user scenarios to ensure that the entire application works seamlessly from start to finish. These tests cover the interaction between multiple components and systems, including user interfaces, databases, and external services and validate that the app's features and workflows function correctly in a real-world environment. By running End-to-end tests, we can identify integration issues, verify the user experience, and ensure that the application meets business requirements.

### Connected Tests

We used connected tests for most of our screens to ensure they behaved as expected. This approach was straightforward, as we had already learned how to implement it during the bootcamp. Connected tests helped us identify various bugs and prompted us to critically evaluate the code we wrote.

### Unit tests

Unit tests are designed to verify the functionality of individual components or units of code in isolation. They ensure that specific functions or methods perform as expected under various conditions. By using unit tests, we can quickly identify and fix bugs, maintain code quality, and ensure that new changes do not break existing functionality.
