
## **Automation Scenarios of Attended and Unattended Robots**

* **Attended robots** are software robots that work alongside human employees and assist them with their tasks in real-time. 

    * Attended robots are typically **triggered by a user** and operate on the user's workstation.
    * Attended robots are used for tasks like **data entry, data validation, customer support, and document processing** that require human judgment and interaction.
    * **Attended bots have limited autonomy** since they typically work under the guidance and control of a user. 
    * Attended robots can be **triggered by events** such as hotkeys, system tray icons, notification icons, and dialog boxes. 

* **Unattended robots** are software robots that operate independently without human intervention. 

    * Unattended robots are typically **scheduled to run** at specific times or in response to certain events. 
    * Unattended robots work in the background, often on remote servers or virtual machines, and **can perform tasks 24/7** without human supervision. 
    * Unattended robots are used for tasks like **invoice processing, data migration, server maintenance, and batch data processing** that do not require human intervention. 
    * Unattended robots are suitable for automating **high-volume, repetitive tasks** that do not require human judgment or real-time decision-making.

## **Bot Models**

* **Task Bots:** These are the most basic RPA bot models that automate individual, repetitive tasks according to a set of predefined rules and instructions.
* **Process Bots:** These are more advanced than task bots and automate entire end-to-end processes, handling a series of tasks, decisions, and interactions across multiple systems.
* **Attended Bots:** are software robots that work alongside human employees and assist them with their tasks in real-time. Attended robots are typically **triggered by a user** and operate on the user's workstation. 
* **Unattended Bots:** are software robots that operate independently without human intervention.Unattended robots are typically **scheduled to run** at specific times or in response to certain events.  
* **Hybrid Bots:** These combine attended and unattended capabilities, allowing them to collaborate with humans when necessary and operate autonomously when needed.
* **Cognitive Bots:** These bots use artificial intelligence (AI) and machine learning (ML) capabilities to perform tasks involving natural language processing, sentiment analysis, image recognition, and decision-making.
* **Meta Bots:** These are reusable automation components that can be deployed across multiple processes and projects, promoting consistency and reducing development time.
* **Citizen Bots:** These are designed for non-technical business users with limited coding skills, providing a user-friendly interface for creating simple automation tasks.
* **Discovery Bots:** These are used in the initial phase of automation projects to analyze and identify automation opportunities by monitoring user activities.
* **Einstein Bots:** Used in Salesforce's RPA platform, these leverage AI and chatbot capabilities to automate customer service tasks.
* **Process Discovery Bots:** These capture and analyze user interactions to identify automation opportunities and bottlenecks.
* **Email Bots:** Specialized bots for automating email tasks like sorting, filtering, and extracting information from emails and attachments.
* **Chatbots:** Conversational bots that interact with users through chat interfaces, handling customer inquiries, providing information, and performing transactions.
* **Integration Bots:** Focused on automating data transfer and communication between different applications and systems.
* **Analytics Bots:** Designed to automate data analysis and reporting tasks, generating reports, dashboards, and insights.


## **Creating a Provision Robot from Server**

Provisioning a robot from a server in an RPA environment typically involves setting up a new robot instance on a designated machine or virtual machine (VM) to execute automation tasks. Here are the general steps:

1.  **Install RPA Software:** Install the necessary RPA software on the server. This includes the RPA platform’s runtime or agent, which allows the robot to execute automation workflows. 
2.  **Configure Server and Environment:** Ensure the server environment meets the RPA platform's requirements, which might include configuring network settings, firewall rules, and access permissions. 
3.  **Define Robot Configuration:** Define the robot's configuration in the RPA platform's control center or orchestrator, specifying its name, machine ID, environment variables, credentials, and asset mappings.
4.  **Install Dependencies:** If your automation workflows have dependencies, such as specific software applications, libraries, or browser extensions, make sure these dependencies are installed on the server. 
5.  **Register the Robot:**  Register the robot with the RPA orchestrator or control center, associating it with the machine or VM it will run on, and provide the necessary authentication credentials. 
6.  **Configure Environments and Queues:** Set up environments and queues in the orchestrator to organize and manage automation tasks. Environments define the runtime settings for robots, while queues handle task distribution.
7.  **Assign Work to the Robot:** Assign tasks or workflows to the provisioned robot either manually or programmatically through API calls. 
8.  **Test Automation Workflows:** Before using the robot, test the workflows to ensure they work correctly in the server environment. 
9.  **Set Up Monitoring and Logging:** Implement monitoring and logging mechanisms to track the robot’s performance. Set up error handling and alerts for unexpected issues.
10.  **Start the Robot:** Initiate automation tasks through the orchestrator or schedule- or event-based triggers. 


## **Connecting a Robot to a Server**

Connecting a robot to an RPA server, also called an orchestrator or control center, is essential for setting up and managing automation tasks. Here's how:

1.  **Install RPA Software:** Install the appropriate RPA software, including the RPA runtime or agent, on the machine where the robot will run. 
2.  **Obtain Server URL and Credentials:** You'll need the RPA server’s URL or endpoint and authentication credentials (username and password or API token) to connect the robot. 
3.  **Robot Configuration:** Configure the robot in the RPA platform's control center, specifying the robot's name, machine ID, and any specific settings needed for your automation tasks. Also, set up environment variables, credentials, and asset mappings. 
4.  **Register the Robot:** Register the robot with the orchestrator using the server URL and authentication credentials to establish a connection. 
5.  **Machine Association:** Associate the robot with the specific machine where it's installed so the orchestrator can communicate with it. 
6.  **Authentication and Permissions:** Ensure the authentication credentials used for robot registration have the necessary permissions for interacting with the orchestrator, executing tasks, and accessing resources. 
7.  **Configure Execution Environments:** Set up execution environments in the orchestrator to define the robot's runtime settings, specifying what processes or automation tasks it's allowed to execute. 
8.  **Task Assignment:** Assign automation tasks or workflows to the robot through the orchestrator, either manually, on a schedule, or through event triggers. 
9.  **Connectivity Testing:** Before using the robot, test the connection to ensure it can communicate with the server and receive instructions.
10.  **Start the Robot:** Initiate tasks through the orchestrator manually or using predefined schedules.


## **Deploying the Robot to Server**

While the sources provide information on publishing an automation solution using a publish utility and mention deploying robots, they lack specific details on deploying a robot to a server. 

Here are some general steps involved in deploying a robot to a server:

1.  **Package the Robot:** Create a deployment package containing all the necessary files, dependencies, and configurations for the robot.
2.  **Transfer the Package:** Transfer the deployment package to the target server environment where the robot will be deployed.
3.  **Install and Configure:** Install the robot software on the server and configure it according to your RPA platform's guidelines.
4.  **Connect to Orchestrator:** Establish a connection between the deployed robot and the UiPath Orchestrator.
5.  **Test and Validate:** Conduct thorough testing to ensure the robot functions correctly in the server environment.
6.  **Monitor and Maintain:** Monitor the robot's performance and implement necessary maintenance tasks, including updates and security patches. 

