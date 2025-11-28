# Stage 1: Build Stage - Compile the Angular application
FROM node:20-alpine AS build
WORKDIR /usr/src/app
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build -- --output-path=./dist

# Stage 2: Production Stage - Serve with Nginx
FROM nginx:alpine
# Check the exact folder name created by your Angular build (e.g., 'frontend' or 'app-name')
COPY --from=build /usr/src/app/dist/frontend /usr/share/nginx/html
COPY nginx/default.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
