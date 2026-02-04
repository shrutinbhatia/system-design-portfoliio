## High-Level Architecture

### Clients
Since the users will use an application for everything we need a - 

- iOS & Android mobile app
- Web app (employees)

### Backend services

The backend services need to be divided into sections with separate business capabilities, following the approach of domain driven design - DDD. 

<img width="6116" height="6987" alt="image" src="https://github.com/user-attachments/assets/33aa8d3d-b176-4ab3-b19a-b7c8fb03c88c" />

- User Management Service: This will manage user registration, authentication and personal data. Also integrate with billing 

- Attendance Service : This will allow users to check in and checkout 

- Class Booking Service  
  - Will allow users to view class schedules and book a slot.
  - Will allow employees to post and modify schedules

- Workout Tracking Service
- The service will allow user's to select and log their workouts, add details like weight and repitations. It will also integrate with user's fitness device to gather heart rate information.
- This requires access to 3rd party APIs

- Personalization Service
- Based on the workouts logged and the user's data this 

- Community Service

- Billing Service

### External integrations

- Fitness devices APIs

- Payment provider
 
