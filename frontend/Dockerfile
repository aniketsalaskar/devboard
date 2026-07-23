#-----------------Stage 1--------------------

FROM node:24 AS builder 

WORKDIR /app

COPY . .

RUN npm install --legacy-peer-deps

RUN npm run build 

#-----------------Stage 2--------------------

FROM node:24-alpine AS runner

WORKDIR /app

COPY package.json .

RUN npm install -g vite


COPY --from=builder /app/dist ./dist 

EXPOSE 5173

CMD ["npm","run","preview", "--", "--host", "0.0.0.0", "--port", "5173"]

