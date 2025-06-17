Doctor appointment system
This is a mern stack project uses reactJS,redux toolkit,HTML,CSS javascript to make simple and smooth UI, express JS, Node js is used to handle request and responses in backend, Mongo DB is used to store users details permanantly in database, JWT(javascript webtoken) and bycrpt is used to ensure authenication and authorization.

Website Entitles

Admin:  Admin user is the head user of this website. He is the person who can Approve the 
Doctor’s and Reject the Doctor, When the User applied as doctor . Admin will get the 
notification to approve or reject.

Doctor: This person should 1st register to the website as a normal user, after that he can 
apply as a doctor. There is a from where he need to fill his all details later it is approved or 
rejected by the Admin. If approved then interface is according to doctor and his details are 
shown in the doctors list

 Users: These users are patients or the people who are looking to book an appointment to 
consult a doctor. They can book appointment at the flexible time when Doctor is available , 
and the same person cannot book the appointment at the same time. 

Tech Stack

Frontend: React JS, Redux Toolkit, React Router, Axios, React Toastify, Tailwind CSS

Backend: Node.js, Express.js, Mongoose (MongoDB), JWT, bcrypt, dotenv, CORS

1. Backend Architecture & API Routing  
The server entry point (server.js) initializes Express, connects to MongoDB via a dbConfig module, and applies middleware (JSON parsing, CORS, environment variables). Three main route groups handle functionality:  
- User Routes (/api/users): registration, login, profile fetch.  
- Doctor Routes (/api/doctors): fetching doctor lists, individual profiles, and doctor-specific bookings.  
- Admin Routes (/api/admin): user and doctor management (view, update, delete).  
Each route uses controllers that interact with Mongoose models, returning standardized JSON responses and HTTP status codes.

2. Data Models & Persistence  
Three Mongoose schemas enforce data structure and validation:  
- User Model: fields for name, email, hashed password, role (patient/admin/doctor).  
- Doctor Model: specialization, availability slots, profile details.  
- Appointment Model: references to user and doctor IDs, appointment date/time, and status.  
MongoDB’s flexible schema lets us quickly evolve requirements, while Mongoose ensures relations are maintained and queries remain efficient.

3. Authentication & Authorization Logic  
Users authenticate via JWT:  
- On login or registration, the server hashes passwords with bcrypt and issues a signed token.  
- The frontend stores this JWT in localStorage.  
- A custom Express middleware (authMiddleware) verifies the token on protected routes, attaching the decoded user object to req.user.  
- Role-based checks in route handlers prevent unauthorized access (e.g., only admins can hit /api/admin/*).

4. Frontend Structure & Component Flow  
The React app is organized into:  
- Pages: Login, Register, Patient Dashboard, Book Appointment, Doctor Dashboard, Admin Panels (Users List, Doctors List).  
- Components: Navbar, AppointmentCard, ProfileCard, ProtectedRoute.  
Redux Store:  
- userSlice for auth state (login/logout, user info).  
- alertsSlice for global notifications (success/error toasts).  
On app start, the Redux store hydrates from localStorage if a token exists. Routing (via React Router) wraps protected views so only logged-in users of the correct role can enter.

5. API Integration & State Management  
All HTTP calls use a centralized Axios instance configured with a base URL and an interceptor to attach the JWT header. Redux async thunks dispatch actions to:  
- Fetch available doctors and appointments.  
- Create, update, or cancel appointments.  
- Manage users and doctor data (admin).  
After each API call, success or error payloads trigger alertsSlice actions, displaying toast notifications site-wide.

6. Form Logic & Validation  
Booking and profile forms are built as controlled components with inline validation:  
- Dates cannot be in the past.  
- Required fields display immediate error messages.  
- On valid submit, data is sent to the backend and the view updates without full page reload.

7. Notifications & User Experience  
React Toastify (wrapped in Redux) handles feedback:  
- notifySuccess("Booked successfully!") on positive responses.  
- notifyError("Time slot unavailable") for failures.  
This ensures users receive clear, contextual messages after each action.

8. Styling & Responsiveness  
Tailwind CSS provides a utility-first approach:  
- Mobile-first layouts collapse gracefully on small screens (hamburger menu under 768px).  
- Consistent color palette, spacing, and rounded corners maintain a modern, cohesive UI.  
- Reusable class combinations power cards, buttons, and forms across the app.



![image](https://github.com/user-attachments/assets/264bfd2b-487c-4a60-af31-536d7fab1b62)
![image](https://github.com/user-attachments/assets/bbeaf6b5-aa38-45bc-9ef0-a655da91cfe0)
![image](https://github.com/user-attachments/assets/aaab47a3-817d-4b61-8187-2987565257dc)
![image](https://github.com/user-attachments/assets/21f51432-3012-4a33-90b3-4eb70475ecb9)
![image](https://github.com/user-attachments/assets/caa171ea-b19d-4d18-be1c-78a96e06984c)
![image](https://github.com/user-attachments/assets/e971d3ad-093b-4c82-aa5d-2f2972c1a754)
![image](https://github.com/user-attachments/assets/ecb0e3f4-a16a-4ffb-90a8-d12b2e4e2a1f)
![image](https://github.com/user-attachments/assets/b424e81a-ca0e-4983-b5a5-0dfc77f093f6)

Project PPT: [Presentation1.pdf](https://github.com/manojkadali/Doctor-Appointment-System/files/15210637/Presentation1.pdf)



