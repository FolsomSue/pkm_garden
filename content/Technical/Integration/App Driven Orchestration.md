#Technology #definition #Integration #Oracle #Patterns 
# App Driven Orchestration
Create an integration that uses an event or a business object to trigger the integration. For example, you create an integration with an Oracle RightNow Adapter as a trigger and an Oracle Engagement Cloud Adapter as an invoke. The Oracle RightNow Adapter subscribes to an event from the Oracle RightNow application to trigger the integration. Orchestration integrations include features such as the following:

-   Switch activities to create multiple routing expressions.
-   For-each activities for looping over repeating elements.
-   Assign activities for assigning values to scalar variables.
-   Ad-hoc mappings on switch branches.
-   Callback activities (to end a process and respond back to the sender) and end activities (to end a process without responding back to the sender) in asynchronous integrations.

See [Create Application-Driven Orchestrated Integrations](https://docs.oracle.com/en/cloud/paas/integration-cloud/integrations-user/create-application-driven-orchestrated-integrations.html "You can create business object- or event-based orchestrated integrations. Orchestrated integrations can be synchronous, asynchronous, or fire-and-forget types. Orchestrated integrations use Oracle BPEL Process Manager capabilities. Oracle BPEL Process Manager enables you to define how a business process that involves web services is executed. BPEL messages invoke remote services and orchestrate process execution. When designing integrations, you can create multiple routing expressions.").