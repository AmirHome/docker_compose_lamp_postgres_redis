FROM node:16.17.0-alpine3.15

RUN apk add --no-cache libc6-compat

EXPOSE 3000

ENV PORT 3000
ENV NODE_ENV production

WORKDIR /app

RUN rm -rf node_modules
RUN rm -rf .next
# RUN rm -rf package-lock.json

# COPY package.json .
# COPY package-lock.json .D

RUN npm install --omit=optional
RUN npx browserslist@latest --update-db
RUN npx next telemetry disable

# need to install linux specific swc builds
RUN npm install -D @swc/cli @swc/core

COPY . .

RUN npm run build

RUN addgroup -g 1001 -S nodejs
RUN adduser -S nextjs -u 1001

USER nextjs

CMD [ "npm", "start" ]
