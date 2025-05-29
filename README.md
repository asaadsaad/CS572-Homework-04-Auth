### CS572-Homework-07-Auth
### Question 1
Explain how each of these security attacks work and how we prevent them:
* Brute-Force attack
* DDoS attack
* XSS attack
* Data Injection attack
### Question 2
You will build a backend application for a personal diary application. 
  
Given the following Mongoose Models, create a backend API endpoints to perform signup + signin + all necessary routes to perform CRUD operations on the given entities. 
  
Users can only remove or update their own entries.
```typescript
import { Schema, model, InferSchemaType, pluralize } from 'mongoose';

pluralize(null);

const userSchema = new Schema({
    fullname: String,
    email: { type: String, unique: true },
    password: String,
    picture_url: String
})

const diarySchema = new Schema({
    user_id: Schema.Types.ObjectId,
    title: String,
    description: String,
}, {
    timestamps: true
})

export type User = InferSchemaType<typeof userSchema>;
export type Diary = InferSchemaType<typeof diarySchema>;

export const DiaryModel = model<Diary>('diary', diarySchema);
export const UserModel = model<User>('user', userSchema);
```
Use the following packages:
* `cors` to allow AJAX communication between client and server applications
* `express` to build the backend application
* `morgan` to log all incoming requests on the server
* `mongoose` to persist data into MongoDB
* `bcrypt` to hash and compare passwords
* `jsonwebtoken` to generate and verify JWT at the server
* `multer` to upload pictures to the server
  
You may need to configure express application with `express.static()` middleware to serve the user picture.
### Question 3 (optional)
* Implement additional API endpoints for changing the password, amd password reset.
* Implement additional API endpoints for token refresh.
