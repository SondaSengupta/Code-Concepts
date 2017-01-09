**Resource Link:** https://app.pluralsight.com/library/courses/modern-software-architecture-domain-models-cqrs-event-sourcing/table-of-contents

## The difference between Spaghetti Code and Lasagna Code
- **Spaghetti Code** - a tangled mess that is difficult to break up 
- **Lasagna Code** - layered code that has clear modules and pieces that are easy to replace vertically or horizontally.

## The Presentation Layer
- The presentation layer is what the user sees and interacts with in the application.
- This layer sends input data and accepts view model data to show on the screen.

## The Application Layer
- The application layer is in charge of giving the presentation layer or infrastructure layer the data model it needs to present properly coming out of the domain layer
- This layer is concerned with the real-world use cases of the data being presented and how your software will handle them. 
- It houses the business logic concerned with how the data will be seen to the outside world.This could be through HTTP requests, an API or through an automated messaging service.
- These data models are called Data Transfer Objects or DTOs. And the actions done are the application services.
- A typical application service would be make a call to the repository and use or change that aggregate for the presentation layer.
- For example, if your presentation layer always needs the datetime to be converted to a specific format, then it needs to be done here.

## Domain Logic Layer
- The domain layer is concerned with business rules that are modeled from the real world. It is not concerned with how the software will handle it, but only how your business users see the data through business processes or policies.
- For example, if business users know that in order to set an appointment, they must have a first name and a time, then those requirements are reflected here.
