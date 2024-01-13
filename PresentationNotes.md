# Large ETL Pipeline for a Hospital Network

## Purpose

- Brought on to build a large scala based ETL pipeline to automate medical coding and to Digitise the Electronic Healthcare Records (EHR) for a network of hospitals. The data in turn would be given to insurance companies to pay and process the claims correctly. The data itself was scanned documents that went through many processed to be stored in a Postgres database. The data was purely EHR data and the goal was to transform several through the following menthods:
  - Mapping data onto each other datasets
  - Performing regex checks
  - Performing filtering logic

Here is an overview

![Inital Pipeline](Initial_pipeline.drawio.png)

## Situation

- There was a requirement to build out logic and filtering to rank ICD 10 Codes in order of importance to medical insurance companies. This was initially done in Spark Scala and Spark SQL.
- There were a lot of edge cases that had to be accounted for and the amount of data would only add to the space and time required to process the data, this was not going to be sustainable.
- For reference there were three people on the team, including myself.
- I voiced this concern and advocated for an alternative solution using a [Learning to Rank Model built in TensorFlow](https://www.tensorflow.org/ranking).

## Task

- The task then was to build this model and figure out how to make it interact with the Scala ETL pipeline in an asynchronos manor.

## Action

- Given that we had a source of truth, A custom Learning To Rank Model was created via Medical Coders from the Network of Hospitals.

- I am more familiar with Keras/TensorFlow than PyTorch and using the Keras Tuner was used to Fine tune the model later on.

- Worked on this with a Senior Engineer who helped guide me in the right engineering direction whilst I helped him understand the ML side of things.

- This model was deployed into a Dockerised FastAPI Server that was Monitored by Kibana. This server interacted with the Scala Pipeline in a Bidirectional manor, sending data via JSON.

- The reason for this is that we were working with a Scala pipeline, the on-prems system had Python 3.6 installed (TensorFlow LTR needed Python 3.8)

- Here is the updated pipeline.

![Inital Pipeline](pipeline_with_LTR_model.drawio.png)

## Result

- Decreased medical coding errors by 40%.

- The rankings of the codes per patient were enhanced by 80%.

- Uptime of the API was stable 99% of the time, monitored by Kibana.

- Established home grown Machine Learning models in the company.

- Used Machine Learning as a Helper for a complex ETL processes.

## Reflection

- Understand where upper management is coming from.

- Asking clarifying questions to understand the gaps in knowledge in upper management.

- Demo my updates in each meeting.

- Generally, being more confident in voicing my concerns.
