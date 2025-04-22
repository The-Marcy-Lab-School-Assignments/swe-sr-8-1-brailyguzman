# swe-sr-8-1

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Prompt

![Fullstack Diagram](./client-server-database-diagram.svg)

You’ve been given a diagram (see above) showing the three core layers of a fullstack application:

- Frontend – a React application that users interact with
- Backend – an Express server that handles logic and communication
- Database – a PostgreSQL database that stores persistent data

Imagine you’re explaining how these layers work together by using a real-world example: Instagram.

Your task:

1. Explain how Instagram works using the three-layer diagram.

<!-- - What happens when a user opens the app, scrolls through their feed, likes a post, or uploads a new photo?
- Walk through how data flows from the frontend to the backend and to the database—and back again. -->

- When a user loads Instagram's frontend application (website, mobile app), a request is made to the backend (server)\*\* to check if the token the user currently has is a valid one. It verifies this by checking if the user to which the token belongs exists in the database and the token has not expired.
- As the user loads up the feed and scrolls through it, the app requests the backend for more posts to show the user. It does this by following an algorithm developed by Instagram to determine which posts to show, which are gathered from the database.
- When a user likes a post, a request is made to the **server** to add a new like to that post. The server adds the like to the post by communicating with the database and updating the users who have liked the post.
- When a user uploads a new photo, a request to the server is made so that the photo is created. The server then communicates those details to the database to create the new post.
- As we can see, the frontend allows a user to make interactions, which are then handled by the server. In certain interactions with the server, the server would have to communicate with the database to do CRUD (Create, Read, Update, Delete) operations.

2. Come up with an analogy to help someone new to coding understand these layers.

<!-- - You might compare the system to something like a restaurant, a library, or even a post office—anything that helps make the roles of each layer intuitive.
- Make sure your analogy maps clearly to the roles of the frontend, backend, and database. -->

**Frontend (React App) = The Waiter & Menu**

- This is what you would see and interact with when you walk into the restaurant. You browse the menu, tell the waiter what you want, and get your food delivered to your table. You're not involved in how the good gets made or where the ingredients come from; you just place your order and see the results.

**Backend (Express Server) = The Kitchen Staff & Order System**

- The waiter takes your order and sends it to the kitchen. The kitchen staff (backend) understands the order, prepares the dish according to instructions, and makes sure everything is done correctly. It may also do things like check for dietary restrictions (validation) or decide what to prioritize based on what's happening in the kitchen (routing, processing).

**Database (PostgreSQL) = The Pantry & Recipe Book**

- The kitchen relies on the pantry and recipe book to make your food. The pantry holds all the ingredients (data), and the recipe book ensures things are made the right way. If the kitchen needs to know how to make lasagna or check if there's still cheese in stock, it checks the pantry (reads from the database). When new ingredients arrive or something runs out, the pantry gets updated (writes to the database).

3. Reflect on the value of this separation.

<!-- - Why do we separate concerns into these layers?
- What would go wrong if we tried to do everything in one layer?

Audience: Imagine you're writing this for someone who's just starting out in web development and wants to understand how modern apps work.

Length: Around 400–600 words. -->

## Why We Separate Things in a Fullstack App

When you're first learning how websites and apps work, it can feel like a lot is going on. But one of the most important ideas in modern web development is **separating responsibilities**, or breaking up a big job into smaller, focused parts. That's what we do when we build apps with three layers: the **frontend, backend, and database**. Each part has a job, and by keeping those jobs separate, we make things easier to build, fix, and grow.

Let's break it down.

### What Each Layer Does

- The **Frontend** is what users see and interact with. It's the buttons, images, text, and forms you use in an app like Instagram. It's built with things like HTML, CSS, and JavaScript (often with a framework like React).

- The **Backend** it's like the "brain" of the app. It handles the logic. When the frontend sends a request like, "Hey, show me new posts" or "I want to like this photo", the backend decides what to do next. It's usually built using tools like Node.js and Express.

- The **Database** is where the app stores information: users, posts, likes, comments, and more. It keeps everything saved, even after someone closes the app. Instagram, for example, might use PostgreSQL for this.

### Why Separate Them?

Imagine trying to cook, serve food, take orders, wash dishes, and run the cash register all at the same time. That would be overwhelming. But if you work as part of a team, one person in the kitchen, one at the front counter, one at the register, it's much easier to do each job well.

The same idea applies here. Separating the layers gives us a few big benefits:

- **Clarity**: Each part has a clear job. That makes the code easier to understand and work on.
- **Flexibility**: You can change or update one layer without breaking everything else. For example, you could redesign the frontend without touching the database.
- **Teamwork**: In a team, developers can focus on different parts. One person can work on the frontend, another on the backend, and another on the database.
- **Security**: Sensitive stuff like passwords or private data should only be handled in the backend and database. Keeping that separate from the frontend helps protect it.

### What Happens If We Don't Separate?

If you tried to do everything in one layer, for example, having your frontend also talk directly to the database, you'd run into problems fast.

- **Too much going on**: The code would get messy and hard to keep track of.
- **Hard to update**: Changing one thing might accidentally break something else.
- **Unsafe**: If your frontend talks directly to the database, users could easily mess with or see data they shouldn't

In conclusion, it would be like trying to run an entire restaurant by yourself, from cooking to cleaning to serving guests. It might work at first, but as things grow, it's going to fall apart.
