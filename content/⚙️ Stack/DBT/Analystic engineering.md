# Analystic engineering

[https://docs.getdbt.com/community/resources/viewpoint](https://docs.getdbt.com/community/resources/viewpoint)

We believe that analytics teams have a workflow problem. Too often, analysts operate in isolation, and this creates suboptimal outcomes. Knowledge is siloed. We too often rewrite analyses that a colleague had already written. We fail to grasp the nuances of datasets that we’re less familiar with. We differ in our calculations of a shared metric.

We have convinced ourselves after hundreds of conversations that these conditions are by and large the status quo for even sophisticated analytics teams. As a result, organizations suffer from reduced decision speed and reduced decision quality.

Analytics doesn’t have to be this way. In fact, the playbook for solving these problems already exists — on our software engineering teams. The same techniques that software engineering teams use to collaborate on the rapid creation of quality applications can apply to analytics. We believe it’s time to build an open set of tools and processes to make that happen.

## Analytics workflows require automated tools[](https://docs.getdbt.com/community/resources/viewpoint#analytics-workflows-require-automated-tools)

Frequently, much of an analytic workflow is manual. Piping data from source to destination, from stage to stage, can eat up a majority of an analyst’s time. Software engineers build extensive tooling to support the manual portions of their jobs. In order to implement the analytics workflows we are suggesting, similar tools will be required.

Here’s one example of an automated workflow:

- models and analysis are downloaded from multiple source control repositories,
- code is configured for the given environment,
- code is tested, and
- code is deployed.

Workflows like this should be built to execute with a single command.

**Analytics is collaborative**

I would recommend using `--full-refresh` if you are able to. since `--full-refresh` rebuilds the table, it takes care of the schema changes and the historical values of the new column.