# Application properties
- By default, SpringBoot will load properties from : application.properties
- It is created by default
- We can different properties like : 

                    server-port= 8585
Or some custom properties 

                    mickey-house= clubhouse

## how to read properties
![img.png](../image/appprop.png)

## Static directory 
- It stores the static data for the application
![img.png](../image/static.png)


### Warning : Don't use the src/main/webapp directory if your application is packaged as JAR
### Although it is standard Maven directory , it only works with WAR
### It is silently ignored if it is JAR.


## Different properties for logging
- Log level security mapping

      logging.level.org.springframework=DEBUG
      logging.level.org.hibernate=TRACE
      logging.level.com.luv2code=INFO


- You can even store logs in a file

logging.file.name = my-crazy-stuff.log
logging.file.path = c:/myapps/demo
