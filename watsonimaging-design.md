## Watsonx

{: #ai-products-watsonx}

Watsonx is IBM’s AI and data platform with three core components and a set of AI assistants designed to help to scale and accelerate the impact of AI with trusted data across businesses.

Core components include watsonx.ai, watsonx.data and watsonx.governance.

Watsonx.ai - a studio for new foundation models, generative AI and machine learning; : It comprises of Watson Studio and Watson Machine Learning services that are extended with features for working with foundation models and generative AI.

Watsonx.data - a fit-for-purpose data store built on an open data lakehouse architecture; : It comprises of a single unified data platform based on open lakehouse architecture, open data formats and opensource Presto engine for querying.

Watsonx.governance - a toolkit, to accelerate AI workflows that are built with responsibility, transparency and explainability. : It comprises of Open Scale, AI Factsheets and Open Pages services that are integrated and enhanced with features for working with foundation models and generative AI. Services will be rebranded with current focus on integrating and Open Scale, AI Factsheets with Open Pages integration to follow.

AI assistants are pre-built applications powered by watsonx. They enable automating customer service, generating code, and automating key workflows in departments such as HR.

* watsonx Assistant: Designed to create exceptional customer service experiences, watsonx Assistant empowers everyone in the organization to build and deploy AI-powered virtual agents without writing a line of code.
* watsonx Orchestrate: With an expanding catalog of capabilities, business users can use watsonx Orchestrate to delegate common and complex talent management tasks such as creating a job description, pulling a report in Salesforce or SAP SuccessFactors, sourcing candidates and more using natural language.
* watsonx Code Assistant: Empower developers of all experience levels to write code with AI-generated recommendations. Purpose-built for targeted use cases such as application modernization and IT automation, watsonx Code Assistant leverages generative AI to increase developer productivity, reduce coding complexity, and accelerate developer onboarding.
* Watsonx Orders: AI-powered voice agent that accurately takes orders from your drive-thru guests and speeds them to the pay window. It supports a multitude of use cases, including loyalty programs and mobile orders. It knows the customization options of every menu item. It’s aware of what’s available and what’s not. And it works every shift, every day.

## Types of Gen AI workloads

{: #concepts-types-gen-ai-workloads}

Generative AI workloads typically fall into these following categories:

* Inferencing: The process of using a trained machine learning model to make predictions on new data.
* Prompt Tuning: An efficient, low-cost way of adapting a pre-trained model to new tasks without retraining the model or updating its weights. Prompt tuning involves learning a small number of new parameters that are appended to a model’s prompt, while freezing the model’s existing parameters.
* Fine Tuning: The process of adapting a pre-trained model to perform a specific task by conducting additional training. Fine tuning may involve (1) updating the model’s existing parameters, known as full fine tuning, or (2) updating a subset of the model’s existing parameters or adding new parameters to the model and training them while freezing the model’s existing parameters, known as parameter-efficient fine tuning.
* Model Training: The initial stage of model building, involving a subset of the source data. The model learns by example from the known data. The model can then be tested against a further, different subset for which the outcome is already known.

Given the current state of technology, we think that most IBM Cloud clients will be focusing on using/creating solutions that involve Inferencing, Prompt Tuning and Fine Tuning. A much smaller set of clients may be interested in doing the Model Training for Gen AI by themselves.

## Watsonx aaS on IBM Cloud

{: #deployment-watsonx-aas}

Customers can use the IBM Cloud watsonx-aaS service without the need to deploy any generative AI software. IBM Cloud IaaS, PaaS services provide the supporting/surround environment for a secure and regulatory compliant development and deployment of the generative AI workloads/solutions for inferencing, prompt tuning and fine tuning.

## References

https://www.ibm.com/docs/en/mas-cd/maximo-manage/continuous-delivery?topic=SSLPL8_cd/com.ibm.mam.doc/upgrade/c_mas_architecture.htm

visual inspection

https://www.ibm.com/docs/en/mas-cd/maximo-vi

https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=configuring

supported models

https://www.ibm.com/docs/en/mas-cd/maximo-vi/8.5.0?topic=overview-models-supported-functions

https://www.ibm.com/docs/en/mas-cd/maximo-vi/8.5.0?topic=overview-use-cases

https://www.ibm.com/docs/en/mas-cd/maximo-vi/8.5.0?topic=planning

https://www.ibm.com/docs/en/mas-cd/maximo-vi/continuous-delivery?topic=planning
