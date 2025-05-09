# Step 1: Use an official Node.js runtime as the base image
FROM node:18 AS build

# Step 2: Set the working directory inside the container
WORKDIR /app

# Step 3: Copy package.json and package-lock.json to install dependencies
COPY package*.json ./

# Step 4: Install dependencies
RUN npm install

# Step 5: Copy the rest of the application code
COPY . .

# Step 6: Build the React app
RUN npm run build

# Step 7: Use an Nginx image to serve the app
FROM nginx:alpine

# Step 8: Copy the build directory to Nginx's public directory
COPY --from=build /app/build /usr/share/nginx/html

# Step 9: Expose port 80 for the container
EXPOSE 80

# Step 10: Start Nginx server to serve the React app
CMD ["nginx", "-g", "daemon off;"]
