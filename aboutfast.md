> FAST - FAO SURVEY TECHNOLOGY

FAO SURVEY TECHNOLGY (FAST) is the Food and Agriculture Organization's approach to handle corporate Data Collection and Data Management projects in a scalable and reusable fashion. Rather than just going for a single provider approach, we separated every step of the Data Collection process to allow the use of pluggable/interchangeable Open Source solutions that will work the same way whether you are using them on a Cloud or On-premise environment (No internet access)

## Why we built it?

The complexity of data collection projects is often underestimated. Even when the problematics faced on those projects can be very similar from one and other, there is no consensus on the best approach to cover them all. Managing multiple tools or customize solutions for every project will only increase the burden of developing and maintaining them over time, therefore a common platform that defines a standard approach to face this scenario could substantially benefit the organization through the use of a secure, highly available, reliable and replicable solution that could speed up the projects and therefore, the decision making.

#### Reducing corporate data collection complexity

In some cases, the required data to be collected may seem simple, as a single online form that could potentially be easily handled by a custom development or using online tools, but even when those approaches could solve the current problem, there is no certainty of the repercussions that these solutions could bring in the future in terms of data segregation and software standardization.

Before starting any type of development, there are underlying technology related decisions that have to be considered that could potentially affect the entire organization.

##### 1. Survey and data collection tools.

Currently there is a wide range of possible solutions to choose from. From Google Docs, Survey Monkey, Survey Solutions, EPI Collect, Smart Forms or CommCare, the variety of alternatives can be overwhelming.
Even when it’s feasible to use any of this providers, there is still the option to create custom developments, generating more questions:

- Which front end and backend framework should be used?

- Which front end and backend library for validation should be used?

- Which type of database should use?

- How should the schema of our database be?

- How is going to be the API structured?

- Where is the project going to be deployed?

- Is the project going to have Dev and QA environments?

- Who is going to maintain all the project in the long term?

##### 2. Complex data collection scenarios.

There are also cases where the assumption of simplicity disappears, the initial simple survey quickly starts to require complex logic on top to decide whether to ask or not a question, jump to a certain section of the survey, validate or not a certain field and so forth. Is at this point when not all of the listed providers may work, or where the teams realize that the so called “simple custom development” has become a large project with thousands of lines of code.

##### 3. Data regulation.

In other cases, due to organization or country based regulations, it is not possible to share the collected data or in some others, the data cannot even reside outside the country. Is in these case where most of the SaaS tools that initially worked must be discarded. Some of this regulations can be so strict that will immediately discard any kind of cloud-based solutions or SaaS.

Given this two possible scenarios (online and on premise) only the software with the highest flexibility should be considered to avoid having different tools for every possible case, thus standardizing the data collection process throughout the organization. Even when the tool under consideration may have the ability to be deployed locally, other concerns arise, closely related to the ones that appear when having custom developments.

- Does the project have a team with knowledge of the programming language that the tool was developed?
- Does the project have a team with experience administrating the DB that the tool uses?
- Who is going to maintain all the project in the long term?
  In these scenarios, the analysis of the tool should be detailed, and focused on having the less possible moving components to reduce the overall maintenance cost of the application.

##### 4. Long term application support.

There are three assertions that we can make on IT related projects: requirements will increase or change, people will move in or out of the organization and technology will eventually change.
Having a clear vision over these assertions will help understanding that even small decisions made at some point can have big consequences if an approach that is not easily extendable or tools that are not easy to understand or with scarce documentation is chosen.
If these elements are not considered, it is likely that after a few years the chosen collection tool will lose momentum and with time will be outdated, putting in risk the availability and security of the collected data.
Another important consideration is that if the collected data and services to be available should run for a long period, long term support to the underlying architecture will be required: upgrading and maintaining servers, paying server bills and of course, having a team to do the job.

##### 5. Data storage, parsing, backup and analyzing.

If a SaaS provider is chosen, the development process will be considerably reduced, as the provider will probably handle most of the tasks of the data collection process. But once the collection is done and it is time start working with the collected data, some other problems may appear.
Does the chosen tool provide the ability to export/extract the data or manipulate it in a way that is differently from the format they offer? Is it possible to extend the functionalities of the tool?
For some projects, CSV or JSON export formats could be enough but for others, there is need to have a more robust solution in place that will allow working a processing the data to retrieve information. Depending on the provider, considerations will have to be taken to address backups of the information given the committed availability level. In this scenario, more complex architectural solutions come in place, as the software may need database clusters, different availability zones or disaster recovery plans.

##### 6. Data sharing.

Lastly is important to consider that the collected data is there to be used. Perhaps, in the beginning, will only be used by internal teams but on time others will want to access it. Having a clear and consistent method to give access to these resources is important. Not just because the data is exportable it means that it has the flexibility to be shared, as in some occasions we are not going to share the data to users but to other software (machine to machine) or between other data collection projects.

## Environment Configuration

The file `env-example` is provided as template for setting up the environment variables. Once ready, save it as `.env` to start the full stack
FAST consist of two main componets.

1.  Form.io
2.  Mobile Application

Form.io is used as the main API and form builder resource. It takes care
of handeling all form submissions and storing the data.

The mobile application is a Vue.js mobile/offline first application
that connects to Form.io and pulls the form's definition to later
be used for data collection in the field.
