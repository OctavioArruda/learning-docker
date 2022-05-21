FROM node:16-alpine as builder

WORKDIR '/app'
COPY package.json .
RUN npm install
# Copy over all of the source code
COPY . .
RUN npm run build

# Next stage - nginx server - 110% production appropriate
FROM nginx
# I want to copy over something over something already done in a different phase
COPY --from=builder /app/build /usr/share/nginx/html
