# *************************
# -----Stage 1---------

FROM node:21 AS backend-builder

#setup working directory
WORKDIR /app

#code
COPY . .

RUN npm i


#*********************************

#------ Stage 2--------

FROM node:21-slim

#setup working directory
WORKDIR /app

#copy thr above stage as compressed
COPY --from=backend-builder /app .

COPY .env.docker .env

#port
EXPOSE 5000

#app
CMD ["npm", "start"]

