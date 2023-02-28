# Welcome to your new bot

This bot project was created using the Empty Bot template, and contains a minimal set of files necessary to have a working bot. Added certain triggers, dialogs and skills to make the bot integrated with several LLMs services from OpenAI and Azure OpenAI, working on Microsoft Teams Platform. You can configure the triggers in the project to use one or more LLMs services based on your needs. 


<img width="600" alt="image" src="https://user-images.githubusercontent.com/8623897/221474676-847cfaa9-fb1c-4a1f-9a48-e987c7242c58.png">


## ChatGPT responses in Teams Conversation

<img width="958" alt="image" src="https://user-images.githubusercontent.com/8623897/221471351-0bebf072-ceb5-49ed-a3cb-2837916e0cbb.png">

<img width="807" alt="image" src="https://user-images.githubusercontent.com/8623897/221471644-ce9e1ead-7c19-4cda-8d3f-53a26927b581.png">

## Interactive in Teams Message Extension

<img width="321" alt="image" src="https://user-images.githubusercontent.com/8623897/221473432-b50434be-e103-4143-b89e-5e532af7aa77.png">

<img width="936" alt="image" src="https://user-images.githubusercontent.com/8623897/221473604-f5f16c53-d682-48db-bce2-4300232d168f.png">

## "Act As" ChatGPT with preset prompts in Adaptive Cards

<img width="934" alt="image" src="https://user-images.githubusercontent.com/8623897/221474204-243488e6-1974-4ecf-aeda-1cdce57bb80d.png">

<img width="439" alt="image" src="https://user-images.githubusercontent.com/8623897/221474514-81ca299b-d417-42e8-8cea-359a754f52f1.png">

## DALLE in in Teams Message Extension (DALL-E SKill Bot is not required, DALL-E for Teams ME logic is included in the project)

<img width="318" alt="image" src="https://user-images.githubusercontent.com/8623897/221493090-d2b3abab-6191-430a-b159-1c94c18be5c8.png">

<img width="918" alt="image" src="https://user-images.githubusercontent.com/8623897/221492795-fb8de08a-b7e8-4ff3-8e26-1d9c00ae1e68.png">

## DALLE in Conversation (DALL-E SKill Bot is required)

<img width="956" alt="image" src="https://user-images.githubusercontent.com/8623897/221476733-659305ce-5201-4a0f-9316-6de497a36923.png">

<img width="381" alt="image" src="https://user-images.githubusercontent.com/8623897/221493362-843cfed2-7182-4e59-bd22-0df211a6eb87.png">

# Rootbot Building Guide

1. Clone the root bot

2. Open the folder in Bot Framework Composer
   
   Note: If BFC is not installed, please go through **Environment Preparation** of this article https://techcommunity.microsoft.com/t5/modern-work-app-consult-blog/create-a-weather-forecast-bot-with-azure-luis-and-maps-services/ba-p/3261135 on how to use Bot Framework Composer.
   
   Building this project requires expereinces on building and publishing Bot App to Teams Platform in Bot Framework Composer. If not quite certain, can refer to below articles to get quick ideas on important concepts and steps before bullding this project:
   
   https://techcommunity.microsoft.com/t5/modern-work-app-consult-blog/create-a-weather-forecast-bot-with-azure-luis-and-maps-services/ba-p/3261135
   
   https://techcommunity.microsoft.com/t5/modern-work-app-consult-blog/improve-the-weather-forecast-bot-app-using-language-generation/ba-p/3262350
   
   https://techcommunity.microsoft.com/t5/modern-work-app-consult-blog/publish-bot-app-to-teams-channel-with-bot-framework-composer-and/ba-p/3341876
   
   
3. BFC will promote "Project Convert", confirm it. After a while, it may give error about Null Reference, ignore it.
4. Add Teams Package to the root bot

   <img width="878" alt="image" src="https://user-images.githubusercontent.com/8623897/221361118-3157a492-222e-492b-9f8b-d1bf759b1d23.png">

5. Provision root bot (setup publish profile)
6. Set Azure Luis Authoring key, and AppID/PWD (refer to steps 15~19 of https://techcommunity.microsoft.com/t5/modern-work-app-consult-blog/create-a-weather-forecast-bot-with-azure-luis-and-maps-services/ba-p/3261135 for more details)
 
   ![image](https://user-images.githubusercontent.com/8623897/221360395-33faeba5-44f2-4b92-8584-db0b94e2d9c0.png)
   
   ![image](https://user-images.githubusercontent.com/8623897/221360529-b2154401-5853-46d9-8196-3ae26ddc4c60.png)

    
7. Remove unnecessary skills (based on the error hints, for example, remove DALLE skill). 

8. Add necessary configuration keys in root bot configuration json:

     ```json

    "GPT3key": "Your Azure Open AI key for GPT-3",
    
    "GPT3Url" : "Your Azure Open AI Endpoint Url"
 
    "promoterUrl": "Azure Function Endpoint of Act As Prompoter",
  
    "chatgptUrl": "Azure Function Endpoint of OpenAI ChatGPT Wrapper",
  
    "openAIKey": "Bearer sk-your OpenAI API Key",
  
    "taskmoduleurl": "https://flstaticweb.azurewebsites.net/",
    ```

     Note: promoterUrl and chatgptUrl are the two endpoints after publishing the two Azure Functions from here: https://github.com/freistli/chatgpt-api/tree/main/demos/demo-azurefunction . Also need to configure your OpenAI Key there after publishing them: https://github.com/freistli/chatgpt-api/blob/main/demos/demo-azurefunction/Readme.md

     The BFC JSON configuration UI is similar to:
     
     ![image](https://user-images.githubusercontent.com/8623897/221360271-6ca877b4-ac93-4dea-aa08-5ed0f1126c6d.png)

9. Publish root bot.

10. Enalbe Teams Channel, create App Package for teams. The Teams App Manifest can refer to .\settings\manifest.sample.json

## Next steps

### Start building your bot

Composer can help guide you through getting started building your bot. From your bot settings page (the wrench icon on the left navigation rail), click on the rocket-ship icon on the top right for some quick navigation links.

Another great resource if you're just getting started is the **[guided tutorial](https://docs.microsoft.com/en-us/composer/tutorial/tutorial-introduction)** in our documentation.

### Connect with your users

Your bot comes pre-configured to connect to our Web Chat and DirectLine channels, but there are many more places you can connect your bot to - including Microsoft Teams, Telephony, DirectLine Speech, Slack, Facebook, Outlook and more. Check out all of the places you can connect to on the bot settings page.

### Publish your bot to Azure from Composer

Composer can help you provision the Azure resources necessary for your bot, and publish your bot to them. To get started, create a publishing profile from your bot settings page in Composer (the wrench icon on the left navigation rail). Make sure you only provision the optional Azure resources you need!

### Extend your bot with packages

From Package Manager in Composer you can find useful packages to help add additional pre-built functionality you can add to your bot - everything from simple dialogs & custom actions for working with specific scenarios to custom adapters for connecting your bot to users on clients like Facebook or Slack.

### Extend your bot with code

You can also extend your bot with code - simply open up the folder that was generated for you in the location you chose during the creation process with your favorite IDE (like Visual Studio). You can do things like create custom actions that can be used during dialog flows, create custom middleware to pre-process (or post-process) messages, and more. See [our documentation](https://aka.ms/bf-extend-with-code) for more information.