# STEPS TO RUN

cd /lnd2020

docker build -t lnd2020 .

docker run -p 8080:80 --name lnd2020 lnd2020

docker run -d -p 8080:80 --name lnd2020 lnd2020

