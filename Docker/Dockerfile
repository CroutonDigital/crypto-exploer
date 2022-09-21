FROM node:14 as builder

ARG GIT_COMMIT
WORKDIR /app
RUN git clone --depth 1 https://github.com/CroutonDigital/crypto-exploer.git .

RUN yarn && yarn build


FROM nginx:alpine
COPY --from=builder /app/ping.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/dist /usr/share/nginx/html