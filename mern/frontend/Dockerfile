# 1. Use a specific, stable version of Node.
# Using 'node:lts' is a good balance between stability and features.
FROM node:lts 

# Set the working directory
WORKDIR /app

# 2. Copy both package.json and package-lock.json (if it exists)
# This is crucial for consistent builds and is what Docker's caching relies on.
COPY package*.json ./

# Install dependencies
# This is placed here to utilize Docker's build cache. If only source code changes, 
# this step won't rerun.
RUN npm install 

# 3. Copy the rest of the application source code AFTER installing dependencies
COPY . .
 
# Expose the application port. 5173 is common for Vite/frontend dev.
EXPOSE 5173 

# 4. Define the command to start the application.
# If you are running a development server (like 'npm run dev'), ensure it binds to '0.0.0.0'.
CMD ["npm", "run", "dev"]
