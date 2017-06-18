# AContent
==========

docker rm -v -f mysqladmin; \
docker rm -v -f mysql; \
docker rm -v -f acontent

docker image rmi acontent; \
docker image build -t acontent .

docker run --network=atnet -e MYSQL_ROOT_PASSWORD=rootpwd --name mysql -d mysql:5.6; \
docker run --network=atnet -p80:80 --name acontent -d acontent ; \
docker run --network=atnet -p8080:80 --name mysqladmin -e PMA_HOST=mysql -d phpmyadmin/phpmyadmin