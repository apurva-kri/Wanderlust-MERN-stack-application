FROM node:20-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci --omit=dev

COPY . .

EXPOSE 5000

CMD ["npm", "start"]



# FROM node:21 AS build

# WORKDIR /app

# COPY package*.json .

# RUN npm ci

# COPY . .

# RUN npm run build

# # 2nd stage

# FROM node:21-alpine 

# WORKDIR /app

# COPY --from=build /app/dist ./dist

# EXPOSE 8080 

# CMD ["npm","start"]



