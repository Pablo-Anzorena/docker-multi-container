# docker-multi-container

docker network create -d bridge asp-example
docker run -d --network asp-example --network-alias mysql -v todo-mysql-data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=secret -e MYSQL_DATABASE=todos mysql:5.7
docker build -t app_node_mysql:0.0.1 .
docker run -dp 3000:3000 --network asp-example -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=secret -e MYSQL_DB=todos app_node_mysql:0.0.1
