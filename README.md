# NEXT.js - Deployment to AWS

Cheapest way to deploy a React app using NextJS SSR on AWS.

Next Js is a Node framework that requires server capabilities and therefore, using if for servier-side rendering could not be hosted on an S3 only. However we can host entire app on an EC2 - which is significantly more expensive.

Following architecture is a solution to our problem.

## Architecture - SSR + Serverless framework + AWS Lambda

For deploying our Next.js SSR App, instead of following a traditional approach of managing and running a whole AWS EC2 instance which keeps running 24x7. There is actually one more cost effective and modern approach which uses AWS lambda and Serverless framework.

**Q. What is  [AWS lambda](https://aws.amazon.com/lambda/)?**  
AWS Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume.

**Q. What is  [Serverless framework](https://www.serverless.com/open-source/)?**  
Serverless Framework Open Source lets you develop applications with serverless architectures and deploy using AWS Lambda, Azure Functions, Google CloudFunctions & more.

**Q. What is  [Serverless-Next.js](https://github.com/danielcondemarin/serverless-next.js)?**  
This is a Serverless component built just for deploying Next.js app. Also any of your assets in the static or public folders are uploaded to S3 and served from CloudFront automatically, so I think this is what you are exactly looking for.

Below is the architecture explaining how it serves your app to the user.
![enter image description here](https://i.stack.imgur.com/uXgjX.png)

> If you are new to serverless framework, I will suggest you to go thru a free course by Serverless community called [Serverless for Frontend Developers](https://www.serverless.com/learn/courses/serverless-for-frontend-developers/)


Thankfully there are few ways to keep the Lambda function warm. This is the act of sending scheduled ping events to your functions to keep them alive and idle, ready to serve requests.

You will find various methods and plugins to achieve this, if you just search "How to keep lambda functions warm?" on google.

Below are some links which I'm attaching for reference.

[How to keep your lambda functions warm?](https://acloudguru.com/blog/engineering/how-to-keep-your-lambda-functions-warm)

[How to Minimize AWS Lambda Cold Starts](https://epsagon.com/development/how-to-minimize-aws-lambda-cold-starts/)

[Keep your lambdas warm](https://www.serverless.com/blog/keep-your-lambdas-warm)
