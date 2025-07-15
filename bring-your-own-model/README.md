# Bring Your Own Azure AI Foundry Model to AI Prompts

{description}

## ⚙️ Prerequisites

- Power Platform environment with access to:
  - AI Builder
- Access to Microsoft Azure / Azure AI Foundry with the same account as the Power Platform environment

## 🚀 Lab Walkthrough

### Create a dedicated Power Platform solution

1. Navigate to [Power Apps](https://make.powerapps.com/) and log in with your credentials.

1. On the left sidebar, select **Solutions**.

    ![Select Solutions](./assets/select-solutions.png)

1. Select **+ New solution**.

    ![Create New Solution](./assets/create-new-solution.png)

1. On the **New solution** page, enter the following details:
    - **Display name**: `Bring Your Own Model Solution`
    - **Name**: `BringYourOwnModelSolution`
    - **Publisher**: _Select the default publisher or create a new one._
    - **Version**: `1.0.0.0`
    - **Set as your preferred solution**: ✅

        > **Note:**
        > Setting a preferred solution ensures that all your custom components go into a dedicated unmanaged solution instead of the generic system solutions, giving you clear separation, consistent publisher settings, and full control.
        >
        > This makes it easy to export your tailored solution for deployment to other Dataverse environments and keeps collaboration with others clean and predictable.

        ![New Solution Details](./assets/new-solution-details.png)

1. Then click **Create**.

    The solution will then be created and you will be redirected to the solution's overview page.

1. While on the solution's overview page, select the **Back to solutions** icon to return to the solutions page.

    ![Back to Solutions](./assets/back-to-solutions.png)

1. On the Solutions page, you should then see the **Current preferred solution** listed as `Bring Your Own Model Solution`.

    ![Preferred Solution](./assets/preferred-solution.png)

### Deploy a model from Azure AI Foundry

Now with the solution created, let's get started on bringing your own model from Azure AI Foundry.

1. Open a new tab in your browser and navigate to [Azure AI Foundry](https://ai.azure.com/). Log in with the same account you use for Power Platform and Microsoft Azure.

1. On the Azure AI Foundry home page, select **+ Create new** to create a new project.

    > **Note:**
    >
    > There are two types of projects you can create - a **hub based project** and a **Foundry project**. We will be creating a Foundry project which is built on an Azure AI Foundry resource. This project type allows for a simple setup, access to agents, and industry leading models from OpenAI, Mistral, Meta, and more. You can learn more [here](https://learn.microsoft.com/en-gb/azure/ai-foundry/what-is-azure-ai-foundry#project-types).

    Select **Azure AI Foundry resource** and then click **Next**.

    ![Create New Project](./assets/create-new-project.png)

1. Give your project a name or use the default name, and then click **Create**.

    ![Project Name](./assets/project-name.png)

    It may take a few minutes for the project to be created.

    Once it has been created, you will be redirected to the project overview page:

    ![Project Overview](./assets/project-overview.png)

1. Now with the project created, we can deploy a model to it. On the left sidebar, select **Model catalog**. In the model catalog, you can browse through the available models.

1. Scroll down to just _below_ the **Model leaderboards** section where there are filter options.

    ![Model Catalog Filters](./assets/model-catalog-filters.png)

1. Here we will filter the models to only show those that are capable of **Chat completion** tasks. Select the **Inference tasks** dropdown and then select **Chat completion**.

    ![Filter Chat Completion Models](./assets/filter-chat-completion-models.png)

    You will now see a list of models that support chat completion tasks. For this lab, we will use the **Phi-4** model as well as the **Mistral-Nemo** model.

1. To deploy the **Phi-4** model, select it from the list and then click the **Use this model** button.

    ![Use Phi-4 Model](./assets/use-phi-4-model.png)

    Then select **Agree and proceed** to accept the terms of use.

1. On the **Deploy Phi-4** pane, configure the following settings:

    - **Deployment name**: `phi-4-ai-prompt`
    - **Deployment type**: `Global Standard`

    Then select **Deploy**.

    This will create a deployment of the Phi-4 model in your Azure AI Foundry project which can take a few minutes. A deployment is your specific instance of a model that you can use in your applications.

1. Once the deployment is complete, you will be redirected to the model deployment overview page. Copy the following details and save them for later use:

    - **Deployment name:** Which can be found at the top of the page
    - **Target URI:** Which can be found in the **Endpoint** section on the left-hand side of the page
    - **Key:** Which can be found in the **Endpoint** section on the left-hand side of the page

    ![Phi-4 Deployment Details](./assets/phi-4-deployment-details.png)

    These are the details you will need to connect the model to AI Builder.

1. Now let's deploy the **Mistral-Nemo** model. Go back to the **Model catalog** and filter the models again to show only those that support chat completion tasks.

    Select the **Mistral-Nemo** model from the list and then select **Use this model** > **Agree and proceed**.

1. On the **Deploy Mistral-Nemo** pane, configure the following settings:

    - **Deployment name**: `mistral-nemo-ai-prompt`
    - **Deployment type**: `Global Standard`

    Then select **Deploy**.

    This will create a deployment of the Mistral-Nemo model in your Azure AI Foundry project which can take a few minutes.

1. Once the deployment is complete, you will be redirected to the model deployment overview page. Copy the following details and save them for later use:

    - **Deployment name:** Which can be found at the top of the page
    - **Target URI:** Which can be found in the **Endpoint** section on the left-hand side of the page
    - **Key:** Which can be found in the **Endpoint** section on the left-hand side of the page

With both models deployed, let's go back to the Power Platform to connect them to AI Builder.

### Connect the model to AI Builder Prompts

1. On the left sidebar in the Power Apps portal, select **AI hub**.

    ![AI Hub](./assets/ai-hub.png)

1. Select **Prompts**.

1. On the Prompts page, under the **Popular Templates** section, select the **Summarize text** template.

    ![Summarize Text Template](./assets/summarize-text-template.png)