


## DOCKER CHALLENGE

#### Step 1: Create Two Isolated Networks

Create two entirely separate custom networks named `network-alpha` and `network-beta`.

#### Step 2: You need to spin up two containers:

- `Container A` (postgres-db): A standard PostgreSQL database container.

- Ensure this container run inside `network-alpha`.

- `Container B` (data-fetcher): You need to write a script that reads mock data from any public API and attempts to write it to a database.

- Write a Dockerfile, package this script into an Image and run it in a container.

- Ensure this container run inside `network-beta`.

#### Step 3: Fix the Network Issue

- You should experience an issue as you launch `Container B`, as both containers cannot talk to each other, 
please fix the issue.
- You should be able to see the data you read from the API in the database table if all is fixed.

Good Luck !!!!!!
