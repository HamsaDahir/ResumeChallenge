# ResumeChallenge

![image](https://github.com/HamsaDahir/ResumeChallenge/assets/121874724/5302ea54-5585-48bb-93cf-5cbbda0e2407)



The Plan

The plan is to facilitate user access to the website. Upon entering the website URL in the browser, the user will interact with the Domain Name System (DNS). In the backend, DNS servers, specifically utilizing Route 53, will be engaged as I have procured the domain name through AWS/Route 53.

Subsequently, it is anticipated that the DNS will contain records redirecting to CloudFront distributions. These CloudFront distributions will be responsible for hosting a static website sourced from an S3 bucket. The S3 bucket, housing the website files, necessitates an automated deployment process. Consequently, any changes committed by a developer to the index file should be automatically deployed to the S3 bucket.

S3 Bucket

I have established an S3 bucket bearing the same name as my domain. To enhance security, all public access to the bucket has been restricted. Access is exclusively granted through CloudFront using an Origin Access Identity (OAI), ensuring that users cannot directly access the bucket via the internet.

CloudFront

A CloudFront distribution has been created to host the aforementioned S3 bucket. The distribution has OAI enabled, and only HTTPS is permitted for enhanced security. Following the creation of the CloudFront distribution, a URL is generated to access the website. However, this URL needs to be configured to align with my domain name.

SSL Certificate

To secure the connection between the DNS and CloudFront with HTTPS, I have generated an SSL certificate.

Route 53

Route 53 serves a dual purpose – it is utilized for both domain name acquisition and as a tool for validation. Additionally, Route 53 is employed to add CNAME records, redirecting the CloudFront distribution URL to align with my domain name.


AWS codepipeline

Finally, I have implemented an AWS CodePipeline to automate the deployment of any changes committed to the index file in the GitHub repository. This ensures a streamlined and efficient process for updating the website content, maintaining synchronization with the version-controlled codebase on GitHub. The AWS CodePipeline orchestrates the necessary steps, from source code retrieval to deployment, allowing for seamless updates to the S3 bucket and, consequently, the CloudFront-hosted website.
 
