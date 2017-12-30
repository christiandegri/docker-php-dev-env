INSTALLATION

- Copy env.example file to .env

- Set environment variables in .env file

- In each service, copy <configuration_file.example> to <configuration_file> 
  and edit parameters in the copies

- Edit mysql/Dockerfile to set mysql version you want to use

- If you want to setup a websiste, copy nginx/sites-examples/myproject.dev.conf 
  to nginx/sites-available/myproject.dev.conf.
  You will notice that this file contains the following line :
  fastcgi_pass php7-fpm:9000.

  It means that PHP scripts of your site will be run by 
  php7-fpm Docker service on port 9000 (container port).
  Do not remove it if you want your application work properly.

  You can customize other parameters of your site configuration.

- Add your site server name to /etc/hosts file of your host machine

- Build services (Run sudo docker-compose build)

- Create and run containers (Run sudo docker-compose up -d)

- Test your installation by calling a valid url of your site
