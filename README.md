# Azure Logic App for Automated Employee Onboarding

## Overview

This project demonstrates how to automate the employee onboarding process using Azure Logic Apps. The workflow automates user creation in Azure Entra ID / AD, assigns roles, and provisions necessary resources for new hires.

![logic app](https://github.com/Harbim001/Employee-Onboarding-Automation/assets/98036782/42a379ea-5474-4989-9cb8-f1857808c212)

## Workflow Steps

1. **Trigger and Initialize Variables**
    - Triggered by an email indicating a new hire.
    - Initializes variables to store email content.

2. **Parsing Email Content**
    - Parses the email body to extract the new hire's details.

3. **Creating User in Entra ID**
    - Creates a new user in Entra ID with the parsed information.

4. **Assigning User to Groups**
    - Uses conditional logic to assign the user to the appropriate group based on their job position.

5. **Provisioning Resources and Sending Welcome Email**
    - Provisions necessary Azure resources.
    - Sends a welcome email to the new hire with login credentials.

6. **Monitoring and Review**
    - Monitors the workflow execution and reviews logs for troubleshooting.
  
   ![Blank diagram (1)](https://github.com/Harbim001/Employee-Onboarding-Automation/assets/98036782/0ceb26aa-d6c0-41ca-a89d-e98d7d5c4439)

## Getting Started

### Prerequisites

- Azure Subscription
- Access to Entra ID / AD
- Azure Logic Apps

### Setup

1. **Clone the Repository**

    ```sh
    git clone https://github.com/yourusername/azure-logic-apps-onboarding.git
    cd azure-logic-apps-onboarding
    ```

2. **Import Logic App Definition**

    - Navigate to the Azure Portal.
    - Create a new Logic App.
    - Import the `logic-app-definition.json` file from this repository.

3. **Configure Connections**

    - Set up connections for Entra ID and Outlook within the Logic App.

4. **Run the Workflow**

    - Test the workflow by sending an email with the new hire details.

## Example Email Body

```plaintext
First Name: John
Last Name: Doe
Email: john.doe@example.com
Job Position: Cloud Engineer
Department: IT
```
## Configuration

Before deploying this logic app, replace the following placeholders in the `logic-app-definition.json` file with the actual values from your Azure environment:

- `{client-id}`
- `{tenant-id}`
- `{group-id-cloud-engineer}`
- `{group-id-data-analyst}`
- `{subscription-id}`
- `{resource-group-name}`
- `{client-secret}`

## Challenges and Solutions

1. **Parsing HTML Email Content:**
   - **Challenge:** Azure Logic Apps read email content as HTML, making it difficult to parse plain text information.
   - **Solution:** Use string manipulation functions to extract necessary details from the HTML content.

2. **Authorization Issues:**
   - **Challenge:** Facing "Authorization Denied" errors when attempting to add users to groups or assign roles.
   - **Solution:** Ensure that the service principal used by the logic app has the necessary permissions, such as `Group.ReadWrite.All` and `Directory.ReadWrite.All`.

3. **Role Assignment via HTTP Call:**
   - **Challenge:** Configuring HTTP actions to assign roles and permissions.
   - **Solution:** Use the `HTTP` action to get an OAuth token and make API calls to Azure Resource Manager (ARM).

[Full Project documentation](https://medium.com/@abimbolaibis/azure-administrator-project-1-automating-employee-onboarding-with-azure-logic-apps-5c0c7ac0cdfe)

## Acknowledgements

- Project was inspired by [@madebygps](https://github.com/madebygps)
- [Original repository](https://github.com/madebygps/projects)
