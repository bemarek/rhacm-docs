---
layout: page
title: Troubleshooting guidance
permalink: /troubleshooting
horizontal: false
---

Learn the basic format and elements of a troubleshooting topic, as well as other considerations.

**Note:** The format for RHAMC troubelshooting doc comes from feedback from developers and support focals.

## Location and basic format

- Troubleshooting files are located in the _Troubleshooting_ folder.
- For MCE, which is the _Cluster lifeycle_ feature for RHACM, there is a separate Troubleshooting guide.
- When placing the new file, writers need to know if the issue is for ACM (MCH operator with the MCE operator), or for MCE-only (cluster only, without MCH).
- Create the files with the same format:
  - **Title:** Ensure the title is specific and concise.
  - **Symptom:** Explain what the user sees or experiences that indicates there is a problem.
  - **Identifying the problem:** Write how the user further completes a procedure to find the specific problem.
  - **Resolving the problem:** Write the user action to work around or resolve the issue.
  - Title the files in a similar format as all the other files.

## Considerations

- _Identifying the problem_ is not needed if the symptom gives enough detail. It is needed if the user completes an action to find more about the problem. 

  See the following examples:
  
  **Example Symptom: Cluster with pending import status**
  
    Your cluster is stuck in `pending import` status with no error.

  **Example Identifying the problem: Cluster with pending import status**

  Run the following command on the managed cluster to view the Kubernetes pods that have the issue:

  `kubectl get pod -n open-cluster-management-agent | grep klusterlet-registration-agent`

  Run the following command on the managed cluster to find the log entry for the error:

  `kubectl logs <registration_agent_pod> -n open-cluster-management-agent`

  Search the returned results for text that indicates there was a networking connectivity problem. Example includes: `no such host.`

- When you build a `.adoc` file, you do not have to repeat the title in the ID. You can keep the ID short. 

  `[#trouble-grafana-timeout]`
  `= Troubleshooting Grafana explorer gateway timeout`

- You should have a verification step from the tech leads that tells the user how to check for success. 

- If you do not, don't assume the result. For example, don't write: `The import issue is resolved`. 

  Example of a verification step:

  `Refresh the Grafana page and try to query the metrics again.`

- It is understood that if this doesn't work, users should contact support or check for other problems.

- We do not link to these files in the main documentation. Sometimes we will be asked and the response is usually that if so many customers need this, the procedure should change rather than interrupting the user with a fix or scenario.

- There is an option to put them in related links at the bottom, but keep in mind when we do that, we have to maintain that link and remove it when the scenario is no longer valid.