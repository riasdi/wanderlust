# Stage 1
FROM node:21 AS frontend-builder

#set the working directory to /app
WORKDIR /app

#Copy the package.json and package-lock.json for dependency installation
COPY package*.json ./

#install dependency
RUN npm install


#Copy the rest of the application
COPY . .

# Stage 2
FROM node:21-slim

#set the working directory to /app
WORKDIR /app

#copy built assets and dependencies from frontend-builder stage
COPY --from=frontend-builder /app .

#copy the .env.sample file to .env.local
COPY .env.sample .env.local

#expose the port
EXPOSE 5173

#define th default command run the app in development
CMD ["npm","run","dev", "--","--host"]
