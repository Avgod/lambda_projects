Automate ec2 instance to stop and start
Use case "schedule ec2 instance of multiple regions using lambda functions and bridge event scheduler”.
i used event Scheduler as a trigger for lambda function to start and stop the ec2 instance for billing reduction in an organisation.
schedule is like from Monday to Friday from 9 to 24 i.e. from morning 9 O’clock to midnight 12 the instance should be running after that all instance will be stopped all over the weekend for cost optimizing 
Here Bridge event scheduler will be used as cron tab for a serverless lambda.
  
First thing you need to create proper IAM role with correct permissions for event bridge and lambda and Ec2. 
Step 1: Create iam role as given in example IAM policy file make sure that you given for specific regions permission.
Step 2: After this we can now create Lambda function with the same iam role attached cerate 2 lambda functions one is to start and stop.
Step 3: Create Amazon Bridge event scheduler by attaching the created iam role, depend on your requirements referring crontab guru you can get one, I have created 2 bridge events for start and stop, I have given “ 0 9 ? * 2-6 * “
Another with “ 0 21 ? * 2-6 * “ and target will be given as lambda function 

 

Step 4: Create a test event and confirm there is no errors. Now start and stop instance will be done automatic.
