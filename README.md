# YelpCamp

## Description

YelpCamp is a full-stack web application designed for campground enthusiasts to discover, create, edit, and review campgrounds. Built with Node.js, Express, MongoDB, and EJS, it offers a robust platform with user authentication, session management, and review functionality. Integrated with Mapbox for location visualization and Cloudinary for image uploads, it ensures a dynamic user experience. Security features like MongoDB injection prevention and Content Security Policy (CSP) enhance safety, making it an ideal tool for sharing and exploring campground information.

## Features

- **Browse Campgrounds**: View a list of campgrounds with details like name, location, price, and images.
- **Create & Manage Campgrounds**: Authenticated users can add, edit, and delete campgrounds.
- **Post Reviews**: Users can leave reviews for campgrounds, fostering community engagement.
- **User Authentication**: Secure login and registration using Passport.js with local strategy.
- **Session Management**: Persistent user sessions with MongoDB-backed session storage.
- **Flash Messages**: Display success and error messages for user actions.
- **Security Enhancements**:
  - Input sanitization with `express-mongo-sanitize` to prevent MongoDB injection.
  - Content Security Policy (CSP) via `helmet` to mitigate XSS attacks.
  - Secure cookies with `httpOnly` and expiration settings.
- **Map Integration**: Displays campground locations using Mapbox APIs.
- **Image Uploads**: Supports image uploads via Cloudinary integration.

## Tech Stack

- **Backend**: Node.js, Express
- **Database**: MongoDB with Mongoose ODM
- **Frontend**: EJS with `ejs-mate` for templating
- **Authentication**: Passport.js (Local Strategy)
- **Session Management**: `express-session` with `connect-mongo` for session storage
- **Security**: `helmet`, `express-mongo-sanitize`
- **Static Assets**: Served from `/public` directory
- **External APIs**: Mapbox for maps, Cloudinary for image storage
- **Dependencies**:
  - express
  - mongoose
  - ejs-mate
  - express-session
  - connect-flash
  - passport
  - passport-local
  - helmet
  - express-mongo-sanitize
  - connect-mongo
  - dotenv

## Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/yelp-camp.git
   cd yelp-camp
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set up environment variables**:
   - Create a `.env` file in the root directory.
   - Add the following variables:
     ```env
     DB_URL=mongodb://localhost:27017/yelp-camp
     SECRET=your-session-secret
     CLOUDINARY_CLOUD_NAME=your-cloudinary-cloud-name
     CLOUDINARY_KEY=your-cloudinary-key
     CLOUDINARY_SECRET=your-cloudinary-secret
     MAPBOX_TOKEN=your-mapbox-token
     ```

4. **Set up MongoDB**:
   - Ensure MongoDB is running locally or provide a cloud-based MongoDB URL (e.g., MongoDB Atlas) in `DB_URL`.
   - The app connects to a database named `yelp-camp`.

5. **Run the application**:
   ```bash
   node app.js
   ```
   The app will be served at `http://localhost:3000` (or the port specified in `PORT`).

## Usage

- **Home Page**: Access the landing page at `/`.
- **Campgrounds List**: View all campgrounds at `/campgrounds`.
- **Create Campground**: Authenticated users can add a new campground at `/campgrounds/new`.
- **View Campground**: See details of a specific campground at `/campgrounds/:id`.
- **Edit Campground**: Modify a campground at `/campgrounds/:id/edit` (requires ownership).
- **Post Review**: Add a review at `/campgrounds/:id/reviews` (requires login).
- **User Authentication**: Register at `/register` or log in at `/login`.

## Project Structure

- `app.js`: Main application file with Express setup, middleware, routes, and MongoDB connection.
- `models/`:
  - `user.js`: Mongoose schema for users.
  - `campground.js`: Mongoose schema for campgrounds.
  - `review.js`: Mongoose schema for reviews.
- `routes/`:
  - `users.js`: Routes for user registration, login, and logout.
  - `campgrounds.js`: Routes for CRUD operations on campgrounds.
  - `reviews.js`: Routes for creating and deleting reviews.
- `views/`: EJS templates for rendering pages using `ejs-mate` for layout support.
- `public/`: Static assets (CSS, JavaScript, etc.).
- `utils/ExpressError.js`: Custom error handling class.

## Security Features

- **MongoDB Injection Prevention**: `express-mongo-sanitize` replaces prohibited characters in query strings.
- **Content Security Policy**: `helmet` restricts sources for scripts, styles, and images to trusted domains (e.g., Mapbox, Cloudinary, FontAwesome).
- **Secure Sessions**: Sessions stored in MongoDB with a 7-day cookie expiration.
- **Input Validation**: Custom error handling with `ExpressError` for consistent error responses.

## Future Enhancements

- Add support for password reset functionality.
- Implement campground search and filtering.
- Add user profiles and campground favoriting.
- Integrate additional map features (e.g., geolocation-based search).
- Enhance accessibility compliance for the frontend.
- Deploy to a cloud platform like Render, Heroku, or AWS.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request with improvements, bug fixes, or new features.

## License

This project is licensed under the MIT License.
