Got it ✅ thanks for sharing the full **project scope + README**.

This is a **very strong interview-ready project** because it covers:

* **Backend engineering (Node.js, Express, MongoDB)**
* **Security (JWT, password hashing)**
* **AI integration (Gemini API for categorization & notes)**
* **Background jobs (Inngest for async ticket processing)**
* **Email workflow (Mailtrap for notifications)**
* **System design elements (role-based access, skill-matching, fallback logic)**

---

## 🎯 How to Present This Project in an Interview

### **1. Project One-Liner**

> “I built an **AI-powered ticket management system** that automatically categorizes, prioritizes, and assigns support tickets to the right moderators using Google Gemini AI, skill-based matching, and role-based access control.”

---

### **2. Motivation (Why You Built It)**

* Traditional ticketing systems rely on **manual triage**, which is slow and error-prone.
* My project solves this by using **AI + automation**:

  * AI assigns priority & skills.
  * Moderators get auto-assigned.
  * Admins intervene only if no match found.

---

### **3. System Architecture (High-Level Flow)**

1. **User submits ticket** → saved in MongoDB.
2. **Event triggered** → `on-ticket-created` event sent to Inngest.
3. **AI (Gemini API)** → analyzes description, generates:

   * Related skills
   * Priority
   * Helpful notes
   * Ticket category
4. **Moderator Assignment**:

   * Match skills with available moderators.
   * If no match → assign to admin (fallback).
5. **Notification** → Moderator gets an **email** with AI notes.

---

### **4. Tech Stack Choices**

* **MongoDB** → flexible schema, handles nested data like `relatedSkills`, great for searching/moderator matching.
* **Express.js** → lightweight, easy for REST APIs.
* **JWT** → stateless authentication (scales better than sessions).
* **Inngest** → background job processing (avoids blocking API responses, ensures reliability).
* **Nodemailer + Mailtrap** → reliable and testable email delivery.
* **Gemini API** → advanced NLP for ticket analysis.

---

### **5. Features You Can Demo**

* **Sign up / Login** (with role assignment).
* **Create a Ticket** (simple user flow).
* **Auto AI Processing** (watch ticket get updated with priority, skills, notes).
* **Auto Assignment** (moderator with matching skills gets assigned).
* **Email Notification** (moderator receives details).

---

### **6. Interview Questions You Might Face**

#### 🔹 Schema & Database

* Why did you use `ref: "User"` instead of embedding user info in tickets?
* How do you prevent duplicate emails?
* How would you scale MongoDB if you had millions of tickets?

#### 🔹 Authentication

* How do JWTs work?
* Why do we hash passwords?

#### 🔹 AI Processing

* How does AI determine priority/skills?
* What if AI fails or is too slow? (→ fallback logic with admin).

#### 🔹 Background Jobs

* Why use Inngest instead of running AI in the same API call?
* What happens if the job queue fails?

#### 🔹 Notifications

* How would you handle email failures?
* Can you integrate real SMTP instead of Mailtrap?

---

### **7. Bonus Interview Points**

* **Indexes** → you added indexes on `status`, `priority`, `skills` for fast queries.
* **Validation** → deadline can’t be in the past.
* **Error Handling** → centralized error middleware in Express.
* **Security** → password hashing, role-based access control.
* **Scalability** → AI + event-driven background jobs.

---

✅ With this breakdown, you’ll be ready to **explain the project confidently** from design → code → interview Q\&A.

---

Perfect 👌 let’s stay **simple but sharp** so you can **answer clearly in interview**.

We’ll do **DB (MongoDB with Mongoose)** in **What? Why? How?** format.

---

## 🔹 **User Schema**

### ❓ What?

A collection that stores information about users:

* `email`, `password`
* `role` (user, moderator, admin)
* `skills`
* `createdAt`

### ❓ Why?

* To **authenticate users** (email + password).
* To **control access** (role-based permissions).
* To **match tickets** with moderators (skills).

### ❓ How?

* Use Mongoose schema with validations.
* Hash password before saving.
* Add `unique` on email to prevent duplicates.

👉 Example:

```js
{
  email: "abc@gmail.com",
  password: "hashedPassword",
  role: "moderator",
  skills: ["React", "Node.js"]
}
```

---

## 🔹 **Ticket Schema**

### ❓ What?

A collection that stores details about tickets:

* `title`, `description`
* `status` (TODO, IN\_PROGRESS, DONE)
* `createdBy` (user reference)
* `assignedTo` (moderator reference)
* `priority`, `deadline`, `helpfulNotes`, `relatedSkills`

### ❓ Why?

* To **track issues/tasks** in the system.
* To **assign tickets** to the right moderator.
* To **automate categorization & prioritization** with AI.

### ❓ How?

* Use Mongoose schema with enums and validation.
* `ref: "User"` links tickets with users (normalized data).
* Index fields like `status`, `priority` for faster queries.

👉 Example:

```js
{
  title: "Database error",
  description: "Getting connection timeout",
  status: "TODO",
  createdBy: ObjectId("userId"),
  assignedTo: ObjectId("moderatorId"),
  priority: "high",
  deadline: "2025-09-20",
  helpfulNotes: "Check MongoDB connection pool",
  relatedSkills: ["MongoDB", "Backend"]
}
```

---

## 🔹 **Why MongoDB?**

* **Flexible** → Easy to store dynamic fields like `skills` or `helpfulNotes`.
* **Scalable** → Can handle millions of tickets with sharding.
* **JSON-like** → Easy to map with Node.js objects.

---

✅ This way, if interviewer asks about DB, you can explain:

* **What** schema stores
* **Why** you designed it like that
* **How** you implemented it

---



## Nice ✅ You’ve listed all the strong DB-related questions.
But in an interview, they won’t ask *all of them*. They’ll try to test if you understand **schema design, DB choice, data integrity, queries, and scaling**.

So here’s the **Top 7 Questions (DB-Focus, Interview-Ready):**

---

## 🔹 **Top 7 DB Questions**

### 1. Why did you separate User and Ticket into two collections?

* **What** → User = login/role info, Ticket = task info.
* **Why** → Separation avoids duplication, keeps DB normalized.
* **How** → Link using `ref: "User"` in Ticket.

---

### 2. Why did you choose MongoDB over SQL?

* **What** → MongoDB is a NoSQL, document-based DB.
* **Why** → Flexible schema, fast for unstructured + evolving ticket data, easy scaling.
* **How** → JSON-like docs fit our ticket system (status, skills, deadline) without rigid tables.

---

### 3. How does MongoDB handle scaling when millions of tickets exist?

* **What** → Horizontal scaling with **sharding**.
* **Why** → Splits data across multiple servers → avoids single machine overload.
* **How** → Example: shard by `status` or `assignedTo`.

---

### 4. Why do you hash passwords before storing?

* **What** → Converts password into unreadable form.
* **Why** → Even if DB leaks, attackers can’t read passwords.
* **How** → Use `bcrypt.hash(password, saltRounds)`.

---

### 5. How do you ensure unique emails in User collection?

* **What** → Add **unique index** on email.
* **Why** → Prevents multiple accounts with same email.
* **How** →

  ```js
  email: { type: String, unique: true }
  ```

---

### 6. How would you get all tickets assigned to a specific moderator with details?

* **What** → Query + populate.
* **Why** → Need both ticket info + moderator details in one response.
* **How** →

  ```js
  Ticket.find({ assignedTo: moderatorId }).populate("assignedTo");
  ```

---

### 7. What happens if you delete a User who has tickets assigned? (Orphan problem)

* **What** → Tickets lose their assigned user → become orphan.
* **Why** → Causes incomplete/invalid ticket data.
* **How** → Options:

  * Use **cascade delete** (delete tickets too).
  * Or set `assignedTo: null` (reassign later).

---

👉 These 7 cover **Schema Design, Choice of DB, Scaling, Security, Data Integrity, Querying, and System Design edge case** — the most interview-relevant mix.

---

Great question 👍 — this is one of the **most common interview questions**.
Here’s how you can answer it simply but strongly:

---

## 🔹 Why I chose **MongoDB** for this project

### 1. **Document-Oriented (JSON-like)**

* Tickets and Users have flexible structures (skills, notes, deadlines, roles).
* MongoDB stores them as JSON documents → no need for complex joins.

---

### 2. **Schema Flexibility**

* New fields (e.g., `helpfulNotes`, `relatedSkills`) can be added anytime.
* No need to alter rigid SQL tables → makes development faster.

---

### 3. **Performance & Speed**

* MongoDB is optimized for **read-heavy + write-heavy workloads**.
* Queries like "all TODO tickets" or "all tickets by moderator" are very fast.

---

### 4. **Scaling**

* MongoDB supports **horizontal scaling (sharding)** → data can be distributed across servers.
* Useful if the system grows to **millions of users and tickets**.

---

### 5. **Developer Productivity**

* Works natively with **JavaScript/Node.js** (our stack = MERN).
* Less mapping overhead compared to SQL.

---

### 6. **Community & Ecosystem**

* Huge community, well-tested libraries (like Mongoose).
* Easier to find solutions, docs, and support.

---

✅ **One-liner interview answer**:
*"I chose MongoDB because it fits well with the MERN stack, allows flexible schema for tickets and users, supports fast queries, and can scale horizontally if the system grows to millions of records."*

Exactly 👍 You got it — in MongoDB we are essentially **parsing and storing data as JSON-like documents**.

---

## 🔹 So what type of data am I parsing?

* **User data** → JSON document (structured)

  ```json
  {
    "email": "john@example.com",
    "password": "hashed_value",
    "role": "moderator",
    "skills": ["database", "networking"],
    "createdAt": "2025-09-14T12:30:00Z"
  }
  ```

---

* **Ticket data** → JSON document (semi-structured + AI-enhanced)

  ```json
  {
    "title": "Database Connection Issue",
    "description": "Experiencing intermittent database timeouts",
    "status": "TODO",
    "priority": "high",
    "deadline": "2025-09-30T00:00:00Z",
    "helpfulNotes": "Check MongoDB connection pooling settings",
    "relatedSkills": ["database", "backend"],
    "createdBy": "ObjectId(abc123)",
    "assignedTo": "ObjectId(xyz789)",
    "createdAt": "2025-09-14T12:35:00Z"
  }
  ```

---

* **AI processing** → starts with raw **text (unstructured)** but outputs **structured JSON** fields like `priority`, `helpfulNotes`, `relatedSkills`.

---

✅ **One-liner interview answer**:
*"Yes, MongoDB stores data as JSON-like documents (BSON internally). In our project, both users and tickets are stored as JSON objects — structured and semi-structured — while AI helps convert unstructured descriptions into structured JSON fields."*

---

"Yes, MongoDB stores data as JSON-like documents (BSON internally). In our project, both users and tickets are stored as JSON objects — structured and semi-structured — while AI helps convert unstructured descriptions into structured JSON fields."












# User.js (auth ) cotrollers

Got it 👍 Let’s break this **auth workflow** into simple steps, only the important points you should remember for interview:

---

## 🔹 Workflow in Auth Controller

### 1. **Signup**

* User sends `{ email, password, skills }`.
* Password is **hashed** with bcrypt before saving → security.
* User is saved in DB (Mongo).
* Fires an **Inngest event** → useful for background jobs like sending a welcome email.
* Creates a **JWT token** with user’s `_id` and `role`.
* Returns `{ user, token }`.

👉 **Key points:** Hashing, JWT, event-driven design with Inngest.

---

### 2. **Login**

* User sends `{ email, password }`.
* Find user by email.
* Compare plain password with **hashed password** using bcrypt.
* If match → create new **JWT token** and return `{ user, token }`.
* If not → return error.

👉 **Key points:** Secure password comparison, no plain text storage.

---

### 3. **Logout**

* Gets token from `Authorization` header.
* Verifies token with `jwt.verify`.
* If invalid → error.
* If valid → just responds `"Logout successfully"`.

👉 **Note:** No blacklist here → token remains valid until expiry.

---

### 4. **Update User (Admin Only)**

* Requires `req.user.role === "admin"`.
* Finds user by email.
* Updates `skills` (if provided) and/or `role`.
* Saves changes.

👉 **Key points:** Role-based access control (RBAC).

---

### 5. **Get All Users (Admin Only)**

* Only admins allowed.
* Fetch all users but **exclude password** using `.select("-password")`.
* Return list.

👉 **Key points:** Security → never return password hashes.

---

## 🔑 Interview-Ready Highlights

1. **Passwords always hashed with bcrypt.**
2. **JWT used for stateless authentication.**
3. **Role-based access control (user/mod/admin).**
4. **Event-driven signup (Inngest).**
5. **Security best practices:** exclude passwords, token verification, forbid non-admins.

---

✅ One-liner summary:
*"The auth workflow ensures security by hashing passwords, issuing JWTs for authentication, restricting admin actions, and triggering background events like signup notifications via Inngest."*

---

Do you want me to also give you the **important fixes** in your code (like missing `await bcrypt.hash` and `await User.findOne`) so you don’t get caught if asked?
Got it 👍 Keeping it simple:

This code is an **authentication middleware**.

* It checks if a request has a **JWT token** in the `Authorization` header.
* If the token is missing or invalid → it blocks access (`401 Unauthorized`).
* If the token is valid → it **decodes the user info** and attaches it to `req.user`, then lets the request continue.

👉 In short: **It protects routes so only logged-in users with a valid token can access them.**
This file is your **Express Router** — it defines the API endpoints for user-related actions.

---

## 🔹 What it does

1. **Imports controllers**

   * `signup`, `login`, `logout`, `updateUser`, `getUsers` → actual logic lives in `controllers/user.js`.

2. **Imports middleware**

   * `authenticate` → checks if the user has a valid JWT before accessing protected routes.

3. **Creates routes**

   ```js
   router.post("/signup", signup);      // new user registration
   router.post("/login", login);        // login user + get token
   router.post("/logout", logout);      // logout user

   router.post("/update-user", authenticate, updateUser);  // admin only
   router.get("/users", authenticate, getUsers);           // admin only
   ```

   * `/signup`, `/login`, `/logout` → **public routes** (no auth needed).
   * `/update-user` and `/users` → **protected routes**, require `authenticate` middleware (only logged-in users with valid JWT can access).

4. **Exports the router**

   * `export default router;` → so this can be used in `server.js` or `app.js` like:

     ```js
     app.use("/api/auth", userRoutes);
     ```

---

## ✅ One-liner summary

*"This file defines user-related API routes. Public routes handle signup, login, and logout, while protected routes (update-user, getUsers) require authentication with a valid JWT."*

---

Do you want me to also make you a **diagram of the flow** (Request → Middleware → Controller → Response) so you can visualize how signup/login/auth works together?
Perfect 👍 Let’s map the **flow** of your `userRoutes` step by step.

---

## 🔹 Request → Middleware → Controller → Response

### 1. **Public Routes (No Auth Needed)**

* **Signup (`POST /signup`)**

  ```
  Client → /signup → signup controller
         → hash password + save user + fire event + return JWT
  ```
* **Login (`POST /login`)**

  ```
  Client → /login → login controller
         → check user + compare password + return JWT
  ```
* **Logout (`POST /logout`)**

  ```
  Client → /logout → logout controller
         → verify token (if any) → return "logout success"
  ```

---

### 2. **Protected Routes (Need JWT in Authorization Header)**

* **Update User (`POST /update-user`)**

  ```
  Client → /update-user
         → authenticate middleware
             - check Authorization: Bearer <token>
             - verify JWT
             - attach decoded user to req.user
         → updateUser controller
             - only admin allowed
             - update skills / role
             - return success message
  ```

* **Get Users (`GET /users`)**

  ```
  Client → /users
         → authenticate middleware
             - check token, verify, attach user
         → getUsers controller
             - only admin allowed
             - fetch all users (exclude password)
             - return users list
  ```

---

## 🔑 Flow Summary

1. Client sends request.
2. If route is protected → `authenticate` middleware runs first.
3. If token valid → `req.user` is set → controller runs.
4. Controller does business logic (DB ops, JWT issue, updates).
5. Response sent back to client.

---

✅ **One-liner interview answer**:
*"Public routes like signup/login go directly to controllers, while protected routes first pass through the `authenticate` middleware that verifies JWT, attaches user info, and then allows the controller to execute."*

---

Do you want me to also explain **where this `router` fits in the bigger app** (like in `app.js/server.js`)?











# now tickets

Nice — here’s a clear, complete **end-to-end scenario** for your system, explained in detail and in plain language. I’ll cover the normal (happy) path, every important intermediate step, all failure cases you should expect, and concrete fixes/improvements you can apply.

# 1) System components (who does what)

* **Client / User**: submits tickets via API (title + description).
* **Express API**: receives ticket create request and stores a ticket document in MongoDB.
* **Inngest**: receives `ticket/created` event and runs `onTicketCreated` function asynchronously.
* **AI agent (Gemini)**: `analyzeTicket()` — reads ticket text and returns JSON: `{ summary, priority, helpfulNotes, relatedSkills }`.
* **MongoDB (Ticket & User collections)**: stores tickets, AI results, and user/moderator data.
* **Assignment logic**: finds a moderator whose `skills[]` match AI `relatedSkills` (fallback → admin).
* **Emailer (Nodemailer / Mailtrap)**: notifies assigned moderator.
* **Client / Moderator dashboard**: polls or requests ticket data to show AI fields & assignment.

---

# 2) Happy-path (step-by-step sequence)

1. **Client** calls `POST /api/tickets` with:

   ```json
   { "title": "DB timeouts", "description": "Intermittent Mongo connection timeouts" }
   ```
2. **API** creates a Ticket in MongoDB:

   ```json
   {
     "_id": "T1", "title": "...", "description": "...",
     "status": "CREATED", "createdAt": "...", "assignedTo": null
   }
   ```
3. API fires Inngest event:

   ```js
   await inngest.send({ name: "ticket/created", data: { ticketId: "T1" }});
   ```
4. **Inngest** triggers `onTicketCreated` function with event data.
5. **Fetch ticket**: `Ticket.findById(ticketId)` → returns ticket object.
6. **Set initial status** (optional): update ticket to `status: "TODO"`.
7. **AI analysis**: `analyzeTicket(ticket)` calls Gemini with a strict prompt requesting raw JSON. AI returns:

   ```json
   {
     "summary": "Intermittent DB timeouts",
     "priority": "high",
     "helpfulNotes": "Check connection pool & network; see link...",
     "relatedSkills": ["MongoDB", "Node.js", "Networking"]
   }
   ```
8. **Save AI results**, update ticket:

   * `priority`, `helpfulNotes`, `relatedSkills`, `status: "IN_PROGRESS"`.
   * Optionally also save the **rawAIResponse** for audit.
9. **Find moderator**: query `User` for role `moderator` with skills matching `relatedSkills`.

   * Example query uses `$elemMatch` + `$regex` with `relatedSkills.join("|")`.
10. **If moderator found** → update `ticket.assignedTo = moderator._id`.
    **If not** → find admin and assign admin, or leave unassigned.
11. **Send email** to assigned moderator with ticket title & AI notes.
12. **Done** — API/clients can now fetch the ticket with populated `assignedTo` and see AI fields.

---

# 3) Important code/logic details & small bugs you must fix (practical)

* In `analyzeTicket` parsing: you expect raw JSON, but code still looks for triple-backtick JSON. Be consistent: either prompt AI to return *only* JSON (best) and parse `response.output[0].context` as the full JSON string, or build a robust parser that finds JSON in arbitrary text.
* In `onTicketCreated` there are real typos/bugs:

  * `if (!ticket) {` inside fetch-step should check the fetched variable (`ticketObject`).
  * `await setp.run(...` should be `await step.run(...` (typo).
* Concurrency: current assignment uses `findOne` then `findByIdAndUpdate` — race condition possible if multiple workers try to assign the same ticket. Use an atomic update like:

  ```js
  const user = await User.findOne(...);
  const updated = await Ticket.findOneAndUpdate(
    { _id: ticket._id, assignedTo: null }, // ensure unassigned
    { assignedTo: user._id },
    { new: true }
  );
  ```

  or use a single `findOneAndUpdate` with a filter to set `assignedTo` only if currently null.
* AI parsing errors: if `JSON.parse` fails (AI returned invalid JSON), handle gracefully — set defaults, mark ticket `status: "AI_FAILED"`, and push to manual triage queue.

---

# 4) Failure modes (what can go wrong) and how to handle each

### A. Ticket not found in DB

* **Symptom**: `Ticket.findById(ticketId)` returns `null`.
* **Action**: throw `NonRetriableError` (already present), log the event, and stop processing.

### B. AI returns invalid/non-JSON or times out

* **Symptom**: parsing fails or response is empty.
* **Action**:

  * Mark ticket `status: "AI_FAILED"`.
  * Save `rawAIOutput` for debugging.
  * Notify a human triage queue (email or admin dashboard).
  * Optionally retry once or twice with exponential backoff.

### C. No moderator matches the skills

* **Symptom**: `User.findOne({role: "moderator", ...})` returns null.
* **Action**:

  * Fallback to admin (already implemented).
  * If admin not found, mark ticket `assignedTo: null` and send to manual assignment queue.

### D. Email sending fails

* **Symptom**: `sendMail` throws or SMTP rejected.
* **Action**:

  * Retry sending (with limited retries).
  * Persist email attempt and push to a DLQ (dead-letter) if persistently failing.
  * Also update ticket with `notificationStatus: "FAILED"` for operators.

### E. Race conditions / double assignment

* **Symptom**: two workers assign the same ticket to different people.
* **Action**: use atomic DB updates (see previous atomic `findOneAndUpdate` pattern). Optionally add an `assignedAt` and `assignedByJobId` fields to detect concurrent updates.

### F. Unauthorized access to protected endpoints

* **Symptom**: missing/invalid JWT.
* **Action**: `authenticate` middleware returns 401 — ensure tokens have reasonable expiry and use HTTPS.

---

# 5) Robustness & reliability improvements (recommended)

* **Save raw AI response** in ticket for audit and debugging.
* **Validate AI output**: check `priority` ∈ `{"low","medium","high"}` and `relatedSkills` is an array. If invalid, fallback.
* **Idempotency** for `ticket/created` handler: detect duplicate events (store `eventId` in DB) and ignore repeats.
* **Retries & DLQ**: use Inngest retries but also a dead-letter mechanism for events that repeatedly fail.
* **Metrics & Logging**: record counts for `ai_succeeds`, `ai_fails`, assignment success, email failures (use Prometheus + Grafana or similar).
* **Monitoring & Alerts**: alert on high error rates or AI latency spikes.
* **Rate-limiting**: prevent abuse of ticket creation endpoint.
* **Testing**: mock AI in tests; add unit tests for parsing, assignment logic, and failure conditions.

---

# 6) Security & privacy considerations

* **Passwords**: always hash (bcrypt) and never return password field in API responses (`.select("-password")`).
* **JWT**: set expiry, use HTTPS, consider refresh tokens for long sessions, and optionally a token blacklist for logout if needed.
* **Sensitive data**: avoid including secrets in AI prompts if ticket descriptions may contain PII; redact if necessary.
* **Access control**: ensure only admins can call `update-user` and `get-users` (you do that check in controllers).

---

# 7) Example payloads you can show in interview

**Ticket creation request**

```json
POST /api/tickets
{ "title":"DB timeouts", "description":"Multiple errors: connection pool exceeded..." }
```

**AI output (stored)**

```json
{
  "rawAIResponse": "{ \"summary\":\"...\",\"priority\":\"high\",... }",
  "priority": "high",
  "helpfulNotes": "...",
  "relatedSkills": ["MongoDB","Node.js"]
}
```

**Ticket after processing**

```json
{
  "_id":"T1",
  "title":"DB timeouts",
  "priority":"high",
  "relatedSkills":["MongoDB","Node.js"],
  "helpfulNotes":"Check connection pool...",
  "assignedTo":"U123",
  "status":"IN_PROGRESS"
}
```

---

# 8) Quick checklist for immediate next steps (code-level)

1. Fix typos:

   * `setp.run` → `step.run`
   * Check `ticketObject` vs `ticket` variable after fetching.
2. Make AI parsing robust:

   * Enforce raw JSON in prompt and parse response accordingly.
   * Validate fields before saving.
3. Add `await` where missing (e.g., `await bcrypt.hash(...)`, `await User.findOne(...)` in auth code).
4. Make assignment atomic (`findOneAndUpdate` with `assignedTo: null` filter).
5. Add logging and save `rawAIResponse` to ticket.
6. Add error paths: `AI_FAILED`, `UNASSIGNED`, email retries.

---

# 9) Short interview summary (how to explain the whole scenario)

* "User creates a ticket → API saves it and emits an Inngest `ticket/created` event. Inngest runs an async function that fetches the ticket, sets an initial status, calls Gemini to extract summary, priority, notes and skills, saves the AI results, then finds a moderator whose `skills[]` match the AI-suggested skills. If none match, it falls back to an admin. The ticket is updated with `assignedTo` and the moderator receives an email. Failure cases (AI parse error, missing moderator, email fail) are handled by marking the ticket for manual triage, retrying, or using fallbacks."

---

If you want, I can now:

* show a **sequence diagram** (textual) of the flow, or
* give **exact code snippets** for the fixes (atomic assignment, robust JSON parsing, saving rawAIOutput),
* or write **tests** (unit + integration) for the pipeline.

Which of those would you like next?
