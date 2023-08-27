# Trivia Titans

Trivia Titans is a multi-cloud serverless online trivia game that allows users to form teams, compete against other
teams in real-time, and track their progress on global and category-specific leaderboards. The game will provide a
personalized experience by adapting to users' preferences and offering a diverse mix of questions tailored to their interests
and skill levels. Additionally, administrators will have access to analytics tools for monitoring the game's performance and
user engagement, enabling them to make data-driven decisions to improve the overall gaming experience

### Technologies
 - AWS
 - GCP
 - Firebase
 - React 


### Modules
Trivia titans has 10 modules which are as follows: 

- **User Authentication:** Multi factor authentication implemented with GCP Firebase for first factor authentication and 2nd factor authentication with AWS DynamoDB and AWS Lambda.
- **Profile Management:** Implemented with AWS S3, Lambda and API Gateway.
- **Team Management:** Creating, updating, and deleting a team developed with the help of AWS DynamoDB, Lambda Functions, SQS ,SNS, ChatGPT (Open AI).
- **Trivia Game Lobby:** Game Lobby which displays all the live games created by the admin. Implemented with AWS DynamoDB, Lambda Functions,  SQS, SNS. 
- **In game Experience:** On joining the game, team will need to wait in the waiting lobby till the designated game start time. The waiting lobby displays all the teams which joined the game. After that game will start where team can compete with each others and team members can talk among themselves with the help of in game chat. Implemented with AWS DynamoDB, Lambda Functions and Firestore.
- **Leaderboards:** Implemented with AWS Lambda, Amazon DynamoDB, Amazon SNS and Amazon SQS. 
- **Trivia Content Management by Admin:** Web dashboard providing comprehensive control for managing and monitoring trivia games. This dashboard lets administrators control game settings, trivia questions, and analytics. Implemented with Google Cloud, Auth, Firestore, Cloud Functions, and retool.
- **Notifications and Alerts:** Implemented with AWS Lambda, Amazon DynamoDB, Amazon SNS and Amazon SQS.
- **Automated Question Tagging:** Tagging question so as to filter the question based on the category of the question. Implemented with Google Cloud, Natural Language API, Google Cloud Function, Firestore, and Node.js.
- **Virtual Assistance:** Game Chatbot Implemented with AWS Lex and AWS Lambda. Integrated to frontend with the help of Lex Runtime Client.

### Architecture Diagram

![Architecture for Trivia Titans](https://github.com/sarthak3136/Multi-Cloud-Serverless-Trivia-Quiz-Game/blob/main/Architecture.png)

User signup in the game, multi factor authentication has been used to make it more robust. First Factor is email address and password, which will be stored in Firebase. Second factor authentication is three question answers, set by the user. After the user has created the accoun and signed in, then the user will have the choice to join the game as a solo player or as a team. If a team is selected then the user will create a team and invite other members through their email. When the user clicks to send an invitation, it will publish an SNS message in the SNS topic. As the SQS is subscribed to the same
SNS topic, it will receive that printed message and store all the invites until they are acknowledged. When an invited user goes inside the View Invite page, it will be displayed if invites contain his/her email in the message attributes of all the messages stored in SQS. The invited member can accept or reject the invitation. If accepted then the team admin has the authority to select the game from the game lobby. All the games has designated time at which they start. Till then the team can wait in the waiting lobby where the other teams who are also waiting for the same game can be seen. Game starts and the team will have to answer the questions of quiz created by the admin. Team members can communicate within each other through in game chat feature implemented with firestore. Game ends and the leader board is updated with the final scores. 

This trivia game employs a multi-cloud architecture, harnessing the capabilities offered by both AWS and GCP. It has been meticulously crafted to ensure scalability and fault tolerance, capable of effortlessly accommodating a substantial influx of concurrent users.

Within the AWS ecosystem, several key services have been leveraged, including:

- AWS Lambda: Utilized for executing serverless functions.
- DynamoDB: Serving as the primary database for the storage of game-related data.
- SQS and SNS: Employed for facilitating messaging and event-driven communication among various components.
- S3: Actively utilized for the storage of profile images.
- Lex: Employed to power the virtual assistance feature.

Similarly, in the GCP domain, essential services have been harnessed, such as:

- Firestore: Serving as a secondary database for the storage of user data, game logs, and in-game chats.
- Chat GPT: Employed for generating random team name.
- Cloud Functions: Utilized for executing serverless functions.
- Natural Language API: Applied for the tagging of questions based on content.

Furthermore, on the admin side, Retool has been integrated for efficient data analytics pertaining to the game's content.

### Contributing

Contributions are always welcome! Follow these steps to contribute:

1. **Fork** the repository.
2. Create a new branch:
```bash
git checkout -b new-feature
```
3. Make your changes and commit them:
```bash
git commit -m "Commit name"
```
4. Push to the new branch:
```bash
git push origin new-feature
```
5. Create a pull request on GitHub.
  

