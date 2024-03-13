# AWS creating CD Pipeline for Web Application

I will be constructing a continuous delivery pipeline tailored for a basic web application. In this project, the source code will reside on my local machine, and the continuous delivery pipeline will be designed in such a way as to automatically deploy our web application each time modifications are made to our source code, whether it's on our Git repository or directly on the web application itself.

## Intermediary Goal

1. Adding a review stage in my pipeline.
2. By doing this, I can manually approve/disapprove a change before the web application is deployed.


# Pipeline Architecture

This Architecture provided the visual representation of the services used in building the pipeline and how they are connected.

![image](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/f0e21f0c-d6d7-4a7a-a111-4c3f7ba13791)


# Services and technologies used

1. GitHub
2. AWS Elastic Beanstalk
3. AWS CodeBuild
4. AWS CodePipeline
5. EC2
6. IAM
7. Python


# Process

1. Setting up a Git respotory: 
  - Logg in/create Github account and install git in our local machine.
  - Open [AWS Elastic bean Repo](https://github.com/aws-samples/aws-elastic-beanstalk-express-js-sample).
  - Fork the repo in your account.

2. Pushing change to my GitHub repository:
  - Open Gitbash on your local machine and make the changes that you want to display on the web application.
      ![Screenshot 2024-03-12 195851](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/079925d7-f40a-444d-bd2a-fc41167c39cc)

  - Finalise the changes using Git Push command and GitHub Repository will be update.

    ![Screenshot 2024-03-12 200438](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/35050de6-7448-4970-bbe2-ba4d1f4f507f)

    ![Screenshot 2024-03-12 201659](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/a0e87e2b-a6e2-4a3c-bf1d-77677d85b683)

  - Changes updated in repository.

    ![Screenshot 2024-03-12 201842](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/0b531763-3409-4aab-bf9a-8909f4287446)

  - Current Architecture after this step.

    ![image](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/218843c8-64db-4332-b79e-b9ed9f0e71f7)

3. Deploying Web Application
  - First is to login to our AWS account and going to AWS Elastic Beanstalk and configure Elastic Beantstalk according to
    our
    current requirements.

      ![Screenshot 2024-03-12 202232](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/15541bf1-4b85-441d-ab1a-2a0695ae7ba0)

  - Choose Node.js as our Platform branch and instance as Single instance (free tier).

       ![Screenshot 2024-03-12 202248](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/98cd47c4-3ac5-43c5-b423-347e03aaceea)

      ![Screenshot 2024-03-12 202833](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/dcc67e69-6986-4982-9a7d-9dcace8877fa)

  - Create a new IAM policy with Elastic BeanStalk permission and add in the IAM policies for creating Elastic Beanstalk
  environment.

      ![Screenshot 2024-03-12 202956](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/fa7ded25-8653-435f-aa82-2f489859b3ac)

      ![Screenshot 2024-03-12 203129](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/7d7a27a6-14d3-41e0-8718-4365e2da386c)

  - Choosing the role which we created.

      ![Screenshot 2024-03-12 203303](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/4c4f2197-b59a-448e-b5cc-9aebde89003d)

  - Launch the environment

      ![Screenshot 2024-03-12 203527](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/6161bd9a-7705-4d61-86e8-179417c4a39a)

  - Web application

      ![Screenshot 2024-03-12 203649](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/c99d1e42-27f7-4414-81ad-dabe41eb6bc9)

  - Current Architecture after this step

      ![image](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/1e35f048-14ba-4b03-8786-292be908885e)

4. Creating a Build Project
   - I will be using AWS CodeBuild to build source code that is present in our GitHub repository.

     ![Screenshot 2024-03-12 203930](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/8dd2d9cf-b010-44be-8c4f-3b7585787c8e)

   - Connecting my GitHub using OAuth

       ![Screenshot 2024-03-12 203944](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/2e531fc4-9986-4581-a026-d80ced43fd25)

       ![Screenshot 2024-03-12 204046](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/b1002f28-20e3-44fb-bed0-74eaa8594e6d)

   - Configuring the CodeBuild

        ![Screenshot 2024-03-12 204157](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/98a0a742-33ed-4e97-acc3-38462bbe099d)

       ![Screenshot 2024-03-12 204436](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/1b553f06-3445-4c51-8c51-a2c90d29f0e2)

    - Current Architecture

         ![image](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/485ca8a9-65b2-46fe-9a6d-0f3f797b1b65)


5. Creating a Delivery Pipeline
   - I will set up a continous delivery piepe on AWS CodePipeline.
   - Editing Buildspec with our custom command

     ![Screenshot 2024-03-12 204645](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/73a41fc3-739a-492c-a320-14161f2d54bb)

   - Update

     ![Screenshot 2024-03-12 204719](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/70746490-4353-4011-acf8-d203637e2a97)

   - Start the CodeBuild code.
  
     ![Screenshot 2024-03-12 204750](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/c82fdf85-eb60-43d2-be09-2f5aabfc7e32)

   - Now choosing pipeline setting under CodePipelin Console

     ![Screenshot 2024-03-12 205101](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/3e97c619-4bab-4020-84f1-6b91e7aef0a3)

   - Connect GitHub again using OAuth
  
     ![Screenshot 2024-03-12 205158](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/43b9bd11-d3be-4307-b9f5-f8f67b0fb122)

   - Configure the pipeline
  
     ![Screenshot 2024-03-12 205234](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/8670186e-972b-4cba-962c-d0394cbe4c1e)

    - Deploy options as Elastic Beanstalk
  
      ![Screenshot 2024-03-12 205313](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/2aec834e-26fc-46a3-9834-756188f086ac)

     - Create the pipeline
  
       ![Screenshot 2024-03-12 205400](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/20970fb5-3e2f-4f38-9302-62b2b594791c)

       ![Screenshot 2024-03-12 205635](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/83efa8eb-5c73-4f96-80c2-eb5751a65b4b)

       ![Screenshot 2024-03-12 205651](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/8474d305-367a-4efb-a797-fba5d5b580e1)

     - Checkout the website after the deployment of environment
  
       ![Screenshot 2024-03-12 205605](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/3ecd494d-e4d7-4e9c-a7eb-852c892b6acb)

     - Application Architecture after this step.
  
       ![image](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/41dd46c1-ab04-4984-bf54-2659d51f5939)


6. Adding a Manual Review stage to the CD pipeline
   - In thee AWS CodePipeline Console select our pipeline and click on Edit button.
   - Add stage buttong between the Build and Deploy stage.
     ![Screenshot 2024-03-12 210041](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/ec0fa3c9-6c5e-4dbf-b9f9-d5c260ab6b82)

   - After adding the buttong.

     ![Screenshot 2024-03-12 210103](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/55841652-dbc0-4257-9ae9-2ad474e85380)

     ![Screenshot 2024-03-12 210157](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/1db004aa-fa42-4951-9a32-b8243a0553b3)

   - Pushing a commit from our repo from our local machine.
  
     ![Screenshot 2024-03-12 210401](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/6c3ee6e6-5a0e-40ed-9ba6-f26f66a9eee1)

   - After committing the Git push, the pipeline will deploy again and will stop at review stage for our approval.
  
     ![Screenshot 2024-03-12 210719](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/2039350a-c5c7-4319-b47a-b1a3d0b4f6b8)


     ![Screenshot 2024-03-12 210740](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/9d48d21f-72e2-4f87-b70b-afff0792c4a1)

   - After Approval, it get deployed.
  
     ![Screenshot 2024-03-12 210823](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/22026f5e-509b-41ff-9b21-c653afb05d12)

   - Changes to Web application relected as changes are made from repository.
  
     ![Screenshot 2024-03-12 210848](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/6ecaaae2-d338-4b00-9d39-ca5ade1dc4b7)

     - Final Architecture of the application
    
       ![Screenshot 2024-03-12 214243](https://github.com/ankurcyb/aws-elastic-beanstalk-express-js-sample/assets/141453942/06e3bff9-cd39-49dc-9c62-24bce8eeb160)



# Conclusion

Developing this continuous delivery pipeline for the web application, we witness real-time updates as we synchronize changes directly from our local machine or GitHub repository. Additionally, integrating a manual review approval process ensures the security of our pipeline, enabling us to approve or disapprove content before it's published on the web application. Moreover, this pipeline's versatility allows deployment on complex architectures while maintaining the same mechanism, accommodating the addition of more stages seamlessly.


#Acknowledgment

This Project is sourced from AWS Resource center - [Create Continous Delivery Pipeline](https://aws.amazon.com/getting-started/hands-on/create-continuous-delivery-pipeline/)




  
     


     




  




       



       











