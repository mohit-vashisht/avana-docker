services:
  app:
    build:
      context: .
      dockerfile: docker/php/Dockerfile
    container_name: avana
    working_dir: /var/www
    volumes:
      - .:/var/www
    

  web:
    image: nginx:alpine
    container_name: avana_web
    ports:
      - "8010:80"
    volumes:
      - .:/var/www
      - ./docker/nginx/default.conf:/etc/nginx/conf.d/default.conf
    depends_on:
      - app
