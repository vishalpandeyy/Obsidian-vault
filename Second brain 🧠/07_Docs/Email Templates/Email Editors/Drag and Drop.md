
Dnd editor is part of the https://dev.azure.com/ClickDimensionstfs/CRM/_git/SPA [[SPA]] monorepo project.

Build pipeline: https://dev.azure.com/ClickDimensionstfs/CRM/_build?definitionId=2659

Release:  [https://dev.azure.com/ClickDimensionstfs/CRM/_release?_a=releases&view=mine&definitionId=60](https://dev.azure.com/ClickDimensionstfs/CRM/_release?_a=releases&view=mine&definitionId=60)


description: Kicks of process of running unit tests and build dnd-editor application artifact. This script automatically creates a [release entry](https://dev.azure.com/ClickDimensionstfs/CRM/_release?_a=releases&view=mine&definitionId=60 "https://dev.azure.com/ClickDimensionstfs/CRM/_release?_a=releases&view=mine&definitionId=60"), where a developer can deploy to different environments in the proper order. For non /release prefixed branches, artifact is deployed to Dev and QA. For /release prefixed branches, this goes to pre-prod, and various prod environments.


Reference: https://clickdimensions.atlassian.net/wiki/spaces/CTO/pages/1704755482/Email+and+Messaging+-+Release+Pipelines
