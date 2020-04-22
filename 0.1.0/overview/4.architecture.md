## ARCHITECTURE (roadmap)

The FAST approach proposes two different alternatives for deploying the underlying architecture. These alternatives are: Cloud based and Self-deployed

1.	Cloud based deployment

The cloud based deployment takes advantage of different cloud providers to provide a highly scalable, highly available, low maintenance platform.

The process of data collection starts with the use of any of the tools that FAST provides for this purpose, whether is a mobile application, web application or a single embedded form in a webpage, they all share the same technology: Form.io
Once the data has been uploaded to the Form.io cloud platform, it will be extracted using AWS Glue data crawler and taken to Amazon S3 to be used as a long term Data Lake storage.

From S3, the data can be published again to AWS Glue or other services like EMR or even tools like pentaho to process it and then move it back to and S3 bucket, Amazon Redshift or queried by Amazon Athena.
Finally, once the data is ready to be published visualizations can be built using Tableau, Amazon Quicksight or Power BI.
The complete process is shown on Figure 7.


2.	Self-deployed (on premise)

The on premise deployment is built considering country requirements on Data Access and Data confidentiality, the proposed architecture emulates the Cloud architecture using different Open Source projects, to leverage a powerful and customizable solution without the need to pay licenses.

![alt text](https://dl.dropboxusercontent.com/s/ur9dmyklt9hi0jc/FAST%20-%20ARCHITECTUREv2.png?dl=1 'THE FULL PICTURE')
