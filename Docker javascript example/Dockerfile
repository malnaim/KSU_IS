FROM node
LABEL maintaner="Meshari Alnaim <malnaim@safedecision.com.sa>"
LABEL name="dev"
LABEL version="v1"
WORKDIR /app   
COPY server.js .
USER node
EXPOSE 8000
CMD ["node", "server.js"]