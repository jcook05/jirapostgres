README

The docker-compose.yml currently creates 2 containers.   

  jira container:   name = jira_seven_postgres
  postgres container:  name = my_postgres_for_jira


Images:

Jira image:  name jirapostgres (may change)

Build jira image using the included DockerFile.   Update as needed to ensure the latest versions are used. 

Postgres Image:   using postgres image stored on Dockerhub repository.   Adjust image path/name to use a custom postgres image. 



It uses the JiraHome folder as the base JiraHome

To setup:

1.  Download Jira
2.  Install Jira into a JiraHome directory in the same directory as the docker-compose.yml
3.  Replace the dbconfig.xml with the included dbconfig.xml



Running:  


To run using existing containers do: 

docker-compose up -d --no-recreate

** You can also simply run the launchjira.bat file


to rebuild containers and run

docker-compose up -d


Stopping:

To stop

docker-compose stop


To remove containers and volumes

*** Ensure to backup Jira before doing this


docker-compose rm -v 



Backup:


1.  In jira admin peform system backup

2.  cp generated file from container     docker cp <container>:/var/atlassian/jira/export/filename  <targetsourcedirectory>


To Restore

1.  copy backup file from source to container   docker cp dbmigration.zip <container>:/var/atlassian/jira/import
2.  In Jira Admin perform restore
