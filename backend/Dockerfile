FROM node:22
WORKDIR /app
COPY . /app
RUN npm install
COPY .env .env
EXPOSE 5000
CMD ["npm","start"]
