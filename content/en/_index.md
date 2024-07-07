---
title: Goldydocs
---

{{< blocks/cover title="Welcome to KRS - Kubernetes Recommender System." image_anchor="top" height="full" >}}
<a class="btn btn-lg btn-primary me-3 mb-4" href="/docs/">
  Learn More <i class="fas fa-arrow-alt-circle-right ms-2"></i>
</a>
<a class="btn btn-lg btn-secondary me-3 mb-4" href="https://github.com/kubetoolsca/krs">
  Github <i class="fab fa-github ms-2 "></i>
</a>
<p class="lead mt-5">Empower your Kubernetes cluster management with the help of <strong>AI</strong></p>
{{< blocks/link-down color="info" >}}
{{< /blocks/cover >}}


{{% blocks/lead color="primary" %}}
Krs is here to change the game! This project utilizes GenAI technology to recommend the perfect Kubernetes tools for your unique environment. 

Say goodbye to endless searches and hello to a streamlined, efficient workflow.


{{% /blocks/lead %}}



{{% blocks/section color="dark" type="row" %}}
{{% blocks/feature icon="fa-magnifying-glass" title="Scanning the Kubernetes cluster" %}}
The tool scans the cluster to identify the deployed pods, services, and deployments. It retrieves information about the tools used in the cluster and their rankings.
{{% /blocks/feature %}}


{{% blocks/feature icon="fa-screwdriver-wrench" title="Detecting tools from the repository"  %}}
The tool detects the tools used in the cluster by analyzing the names of the pods and deployments.
{{% /blocks/feature %}}


{{% blocks/feature icon="fa-arrow-up-9-1" title="Extracting rankings"  %}}
The tool extracts the rankings of the detected tools based on predefined criteria. It categorizes the tools into different categories and provides the rankings for each category.
{{% /blocks/feature %}}

{{% /blocks/section %}}


{{% blocks/section color="light" type="row" %}}
{{% blocks/feature icon="fa-list" title="Generating recommendations" %}}
The tool generates recommendations for Kubernetes tools based on the detected tools and their rankings. It suggests the best tools for each category and compares them with the tools already used in the cluster.
{{% /blocks/feature %}}


{{% blocks/feature icon="fa-notes-medical" title="Health check"  %}}
The tool provides a health check for a selected pod in the cluster. It extracts logs and events from the pod and analyzes them using a language model (LLM) to identify potential issues and provide recommendations for resolving them.
{{% /blocks/feature %}}


{{% blocks/feature icon="fa-info" title="Exporting pod information"  %}}
The tool exports the information about the pods, services, and deployments in the cluster to a JSON file.
{{% /blocks/feature %}}

{{% /blocks/section %}}

