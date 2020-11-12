## MVP

- Users can add bird pictures to database
- Users can create an account
- Users can login to website
- Users can view bird pictures from our database
- Users can edit/delete their own posts

## Icebox

- Users can comment on other users' posts
- Users can update/like posts
- Users can view locations of bird sightings using Google Maps API

## Database

- Schemas

users

```SQL
CREATE TABLE bird_users (
    user_id SERIAL PRIMARY KEY,
    email VARCHAR(60) NOT NULL,
    username varchar(20) not NULL,
    password TEXT
);
```

posts

```SQL
CREATE TABLE posts (
    post_id SERIAL PRIMARY KEY,
    img TEXT,
    species_name VARCHAR(32),
    location TEXT,
    user_id INT REFERENCES bird_users(user_id)
)

```

comments

```SQL
CREATE TABLE comments (
comment_id SERIAL PRIMARY KEY,
body TEXT,
user_id INT REFERENCES bird_users(user_id),
post_id INT REFERENCES posts(post_id)
);

```

## Server

- Dependencies:

  - express
  - massive
  - dotenv
  - express-session
  - bcrypt

- File Structure
- server/
- index.js
- controllers/
- authController.js
- postController.js

- Endpoints:

  - auth endpoints:

    - register => '/auth/register'
    - login => '/auth/login'
    - logout => '/auth/logout'
    - getUserSession => '/api/get_user

  - post endpoints:
    - read posts => 'api/posts'
    - delete => '/api/post/:id'
    - edit => '/api/post/:id'
    - create => '/api/post'

## Frontend

- Dependencies:

  - axios
  - react-router-dom
  - redux
  - react-redux
  - redux-promise-middleware

- File Structure
  - src/
    - App.js
    - App.css
    - reset.css
    - redux/
      - store.js
      - reducer.js
    - routes.js
      - '/' => Auth.js
      - '/createpost' => Form.js
      - '/Feed' => Feed.js
    - components/
      - Header.js
      - Auth.js
      - Form.js
      - Feed.js
