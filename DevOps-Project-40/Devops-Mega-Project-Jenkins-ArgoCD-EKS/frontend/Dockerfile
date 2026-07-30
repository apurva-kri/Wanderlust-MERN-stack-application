ARG NODE_VERSION=22

FROM node:${NODE_VERSION} AS builder

# LABEL is used in a Dockerfile to add metadata to an image, such as the author, version, description, or project information.
LABEL stage="builder"  

WORKDIR /app

COPY package-lock.json package.json ./

RUN npm ci

COPY . .

RUN npm run build

FROM nginx:alpine

LABEL stage="production"
# copy an image which is build above and save it in destination - /usr/share/nginx/html folder
COPY --from=builder /app/dist /usr/share/nginx/html

LABEL maintainer="Apurva"

EXPOSE 80

HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \
CMD wget --no-verbose --tries=1 --spider http://localhost/ || exit 1

# nginx - start the nginx server, -g - it will passes the global configuration directive to Nginx , daemon off tells nginx not to run in the background
CMD ["nginx", "-g", "daemon off;"]










