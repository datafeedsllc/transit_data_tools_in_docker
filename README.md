# transit_data_tools  
  
You can make datatools-server and datatools-ui work locally, and not in the docker (it is necessary that mongo, postgis work).

Or you can collect via docker-compose:
```
docker-compose up
```

Then navigate to [http://localhost:8080/](http://localhost:8080/)

Things are a bit janky, but work. 
Once you’re up and running, the homepage doesn’t show anything and is currently broken. 
This can be fixed in the future if we like. 
You can create and edit projects by going to the /project endpoint

Those. after you have logged in, you need to go to the page -
[http://localhost:8080/project/](http://localhost:8080/project/)