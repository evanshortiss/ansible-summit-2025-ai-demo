## Installation

### Prerequisites

* Cluster admin access to an OpenShift cluster (the installation was successfully tested with OpenShift 4.18).
* API key(s) for access to AI model(s).
* [oc](https://github.com/openshift/oc) and [Ansible](https://docs.ansible.com) installed on your workstation.

### Models

All the AI services in this project use the OpenAI API.

The following models have been successfully used with this demo:
* moderation: OpenAI omni-moderation-latest
* structured output: OpenAI gpt-4o-mini
* router: OpenAI gpt-4o-mini
* finance: OpenAI gpt-4o-mini
* website: OpenAI gpt-4o-mini
* support: OpenAI gpt-4o-mini
* embedding: OpenAI text-embedding-3-small

### Installation

* Clone this project to your workstation.
* Copy the `inventories/inventory.template` file to `inventories/inventory`.
* For each of the AI services, add the model name and the base URL and API Key to access the model.
* Open a terminal, and login to your OpenShift cluster as admin.
* Change directory to the root of the project.
* Run the Ansible playbook:
  ```
  ansible-playbook -i inventories/inventory playbooks/ocp4_workload_ai_summit2025.yml -e ACTION=create
  ```

The project uses ArgoCD to install the different components of the demo. You can use `oc` or the Argocd console to ensure all components are successfully deployed. 

## Running the demo

The [intake-python](https://github.com/summit2025-ai-demo/intake-python) project contains a Python script to send input messages into the Kafka cluster. Refer to the `README.md` of the project for instructions to run the script.
