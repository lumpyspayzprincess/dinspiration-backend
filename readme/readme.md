# Project 3: "Dinspiration"

## Description

During my time at General Assembly, I’d been learning how to use HTML, CSS, JS and TS, and was given the opportunity to work in a team project with 2 other talented engineers on my course.

In this project, we were tasked with creating a MERN app. This meant that unlike the previous project, we built our own API which was created and managed using MongoDB.
As a team, we decided to build an app for anyone interested in learning about different foods based on their dietary and lifestyle needs and called the app, Dinspiration (which is a portmanteau of the words ‘dinner’ and ‘inspiration’).

The foods available in the app were managed by the team responsible for building the app, while the other content was user-generated.

### Link to the gane

[HERE](https://dinspiration.netlify.app/)

## Getting Started/Code Installation

To get started, we first had to set up the backend, and then set up the frontend.

- Download Backend and Frontend starter code
- Create a folder in the development directory so that it can be linked to your Github
- Read through the documentation relating to TypeScript, JavaScript, React, MongoDB and Mongoose

## Timeframe & Working Team

- I worked with another 2 people, (Pamela Smith and Shkendi Naqellari)
  - The project was split into features, where Pam was responsible for the frontend and backend of the users, I was responsible for the frontend and backend of the foods, and Shkendi was responsible for the frontend and backend of the inspirations
  - As the project progressed, we collaborated with one and another and helped each other with features if we were stuck with debugging or learning how to add a new feature to the project
  - Within the three of us, I also had more responsibility with organising the vote on how we initially decided on which idea we’d work on, designing the Figma prototype, setting up the expectations of how and when we’d work together on Slack as we all had wildly different schedules and managing the sprints in JIRA

- Timeframe: 10 days

## Technologies Used

### Languages, libraries and frameworks

#### Backend:
- TypeScript
- Espress.js

#### Frontend:
- React
- Bulma

#### Database:
- MongoDB

### Tools:

#### Clients:
- Insomnia

#### IDE:
- Visual Studio Code (VSCode)

#### Troubleshooting, Diagnostic and Testing:
- Chrome Dev Tools

#### Design:
- Figma
- Excalidraw

#### Agile product management:
- JIRA
- Slack

We chose to work with JIRA  because it is the industry standard for planning and managing tasks and as we’re working in a group, the features related to assigning, filtering and group tasks were very useful.

[JIRA](https://curiousgrape.atlassian.net/jira/software/projects/P3/boards/1)

![JIRA](https://drive.google.com/uc?id=1VNBeXlt2p9Lvjl9T5zNsIJwjalt6Xp0h)
<img width="1440" alt="jira" src="https://user-images.githubusercontent.com/40352055/229467187-0e71f458-9bf9-45bb-90dc-576bb0f96cb3.png">


## Brief

### Technical Requirements:

I needed to:

- Work in a team, using git to code collaboratively.
- Build a full-stack application by making your own backend and your own front-end
- Use an Express API to serve your data from a Mongo database
Consume your API with a separate front-end built with React
- Be a complete product which most likely means multiple relationships and CRUD functionality for at least a couple of models
- Implement thoughtful user stories/wireframes that are significant enough to help you know which features are core MVP and which you can cut
- Have a visually impressive design to kick your portfolio up a notch and have something to wow future clients & employers. ALLOW time for this.
- Be deployed online so it's publicly accessible.
- Have automated tests for at least one RESTful resource on the back-end. Improve your employability by demonstrating a good understanding of testing principles.

**Necessary Deliverables**

- A working app hosted on the internet
- A link to your hosted working app in the URL section of your - Github repo
- A git repository hosted on Github, with a link to your hosted project, and frequent commits dating back to the very beginning of the project
- A readme.md file with:
  - An embedded screenshot of the app
  - Explanations of the technologies used
  - A couple paragraphs about the general approach you took
  - Installation instructions for any dependencies
  - Link to your user stories/wireframes – sketches of major views / interfaces in your application
  - Link to your pitch deck/presentation – documentation of your wireframes, user stories, and proposed architecture
  - Descriptions of any unsolved problems or major hurdles you had to overcome

## Planning

<img width="1440" alt="figma" src="https://user-images.githubusercontent.com/40352055/229467611-24a2e446-4554-4801-8030-d17174eca7b1.png">


Between the 3 of us, I was the only one who had previous experience with prototyping, so I was given the task of designing and managing the Figma prototype.

The prototype built is clickable, so the user can click through and go through the user journey that we’d designed as if the app had been built.

### [Prototype](https://www.figma.com/proto/xdYnQoCF3twD6HHgIxMOnn/Project-3?node-id=0-1&scaling=min-zoom&page-id=0%3A1&starting-point-node-id=18%3A26)

Figma was also useful to the team, as it helped us visualise what we wanted to build and how each screen would work.

Each screen is ordered as if the user is going through the app, and on top of each screen, there are annotations regarding what functions might need to be built and how state would be managed.

We then separated the screens into our MVP screens and our ideal screens, who we knew what would be built, by whom, and how to prioritise our work.

## Build/Code Process

We decided that each of us would have a flow that would be focussed on. I was working on the ‘Foods’ flow.

We then set up one JIRA project, and created two repos on GitHub (one for the backend and one for the frontend).

Once the repo was set up, we created a branch for each feature that was being worked on, and would meet up regularly to ensure that the code that was committed to main was looked at by all of us before merging.

### Backend

The starter code for the project contained:
- An index.ts file, which was eventually where the app.ts file would be referenced when we were working with Express
- A package.json and a package-lock.json file which managed the packages that were installed and then used within the project
- A tsconfig.json file which set up how I used TypeScript in this project and how the dist folder would be created which managed how TypeScript converted to JavaScript in the dist folder (which was created later)


I then began working on the ‘Foods’ part of the project in the backend, and set up the Models.

```
import mongoose from "mongoose"


const foodSchema = new mongoose.Schema({
 name: {type: String, required: true},
 imageURL: {type: String, required: true},
 options: {type: Array, required: true, default: () => ["anything"]},
 lifestyle: {
   lowGi: {type: Boolean, required: true},
   lowCarb: {type: Boolean, required: true},
   highProtein: {type: Boolean, required: true},
   lowCalorie: {type: Boolean, required: true},
   keto: {type: Boolean, required: true},
   skip: {type: Boolean, default: () => true}
 }
})


export default mongoose.model("Food", foodSchema)
```

As we were working with Models, Views and Controllers in our project, a Models folder was created. This folder contained models that Shkendi, Pam and I created.

I then made my foods.ts file, which contained my food **model**. 

Mongoose was installed by running `npm i mongoose`, and then imported into the file.

Here, I defined that there should be a name, image, array of options and array of lifestyle objects in the model.

We made some changes to the models as time progressed as we found that the use of Booleans was useful to us for determining the lifestyle.

Once the model was defined, I then worked on the food controllers, which are known as the ‘business logic’ and were responsible for making sure that certain functions would run when the API had certain requests. 

I imported the model from foods, and installed Express with `npm i express`. Once Express was installed, the Request and Response methods were imported.

```
import { Request, Response } from "express"
import Foods from "../models/foods"


export async function getFoodByName(req: Request, res: Response) {
 try {
   const name = req.params.name
   console.log(name)
   const food = await Foods.findOne({ "name": [name] })
   console.log(food)
   res.send(food)
 }
 catch (e: any) {
   res.send(e.message)
   console.log(e.message)
 }
```

Here’s an example of a GET request that was created in the controller. As I was working with MongoDB, the function uses ‘FindOne’ to find one food that matches the parameters that were used in the URL of the GET request.

Within the **views**, we created the router.ts file, which was responsible for initiating a function when a particular API request was made.

```
/ FOODS


router.route('/foods')
.get(secureRoute, getFoods)
.post(createFoods)


router.route('/my-foods')
.get(secureRoute, getMyFoods)


router.route('/food/:id')
.get(secureRoute, getFoodById)

```

`getFoods` is a function that was imported into the router which comes from the Foods' controller. It's essentially responsible retrieving the foods in a mapped array. Another function, `secureRoute` is responsible for making sure that the user is logged in before they can access the foods mapped to their user. The functions related to a particular router are chained together so that multiple requests can be made from the same URL.

### Database:

To make sure that the database worked, I had to set up MongoDB and Mongoose in my terminal, and create a connection to the MongoDB database using Mongoose.

Once the database had a URI, I could connect it to my backend in VSCode, in my index.ts file.


```
async function start() {
 await mongoose.connect(MONGODB_URI)
 console.log('Connected to dinspiration-db!')


const serverPromise = app.listen(PORT, () => {
 console.log(`Express API is running on http://localhost:${PORT}`)
})
return serverPromise


 app.listen(8000, () => {
     console.log("The post is listening on http://localhost:8000 ")
   })
}
start()
```

Once that was connected, I could test that it was working in my terminal by using the command line to search for objects that were saved in my database.

![query](https://drive.google.com/uc?id=1kKFcz1IYmY7LQWI_adERrE4ic5euSZLL)

```
with app.app_context():
   try:
     print('Creating...')
     db.drop_all()
     db.create_all()


     print('Seeding...')


     # seeded in order of succession. Everything relies on the user, so user is seeded first
    
     target_area=TargetAreaModel(name="core")
     target_area.save()


     target_area1=TargetAreaModel(name="shoulders")
     target_area1.save()


     #! note to use args, kwargs in seeding for target_areas so there's a full table
     # exercise = ExerciseModel(name="plank")
     exercise = ExerciseModel(name="plank",target_area_id=target_area.id)
     exercise.save()


     # # exercise2 = ExerciseModel(name="shoulder rotations",target_area_id=target_area1.id)

      # exercise2 = ExerciseModel(name="shoulder rotations")
     # exercise 2.save()


     # # exercise3 = ExerciseModel(name="crunches",target_area_id=target_area.id)
     # exercise3 = ExerciseModel(name="crunches")
     # exercise3.save()


     #* target_area -> exercises has been mapped successfully and we can see this in tableplus


     user = UserModel(username="jane",email="jane@jane.co", password="highcupsintegerwow",
     fitcoin=0, target_areas=1, image_url="https://img.icons8.com/color/480/lumpy-space-princess.png")
     user.save()


     #! note to use args, kwargs in seeding for exercises so there's a full table


     print(exercise.id)
    
     # workout = WorkoutModel(warmup=1,exercise1=exercise.id, exercise2=exercise2.id, exercise3=exercise3.id, cooldown=1, rest=1,length_of_workout=10)
     workout = WorkoutModel(user_id=user.id, warmup=1, cooldown=1, rest=1,length_of_workout=10)
     workout.save()


     #! here I make a workout exercise
     workout_exercise = WorkoutExerciseModel(workout_id=workout.id, exercise_id=exercise.id)
     workout_exercise.save()




     reward = RewardModel(name="£10 Sephora voucher", description="£10 to use at Sephora, online and in stores.",fitcoin_cost=900)
     reward.save()
    
     spend = SpendModel(reward_quantity=1,fitcoin_cost=100)
     spend.save()






     print('Completed!')


   except Exception as e:
     print(e)
```

The seed data was important for me as it enabled me to double check that the contents of my models were correct, allowed me to work with some data while I was trying to create the logic in the controllers to generate data in my API without needing the seed.

With Insomnia, I was then able to see if I had correctly seeded my data and if the controllers including the logic for my app were correct.

### Frontend:

I was given starter code to work with my frontend, similar to the starter code that was used in previous projects.  This included:
- the root folder, which has:
- a .gitignore file that tells us which files should be ignored when I’m committing and pushing code 
- an index.html which contains an element with an id of ‘root’, which is where the react code is rendered
- package.json and package-lock.json files which show which packages (frameworks and libraries) which have been installed, what their versions are and other information related to the packages
- tsconfig.json and tsconfig.node.json files which are related to how Typescript is set up in the project
- and the src folder, that lives within the root, which is where the code that I would write existed

To work on JS locally, I had to install Node.js, referencing this documentation (https://nodejs.org/en/docs/).

I then went to the package.json file and made sure that the following scripts are included:

```
"scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview"
}
```

Once node was installed, I was then able to use the terminal in VSCode with the keyword ‘npm’ (node package manager) to make changes to run the code. Running `npm run dev` would start the website in my browser, and would hot reload when any changes were made.

### Testing:

To ensure that the database was working as expected, I was testing with Insomnia and the command line.

Insomnia is a client that’s used to manage API requests, so I could use this to check that the requests were being made correctly. Using Mongoose with the command line enabled me to use queries to search for objects with parameters to check if seeding had worked as expected, the controllers were working and that any changes to the database were saved.

## Challenges

Most of the challenges came from working in a team where we had different strengths, and had to figure out where the best use of time was.

Initially, I did have a bit of trouble linking the Inspirations to the Foods. Essentially, when a Food is clicked on, a list of inspirations is populated. This means that one Food has many Inspirations that it is associated with.

As I wasn’t responsible for the Inspirations, a big part of my work was dependent on the the Inspiration Cards, and subsequently, the Inspiration pages being built, so at the last leg of the project, many of my efforts were spent resolving commits in multiple branches and testing Inspirations.

Ultimately, the project we created wasn’t aesthetically as great as we would have hoped initially, but I’m personally very proud of the work as we completed the project and presented something.

## Wins

For me, my biggest win was managing to build a project that I’m proud of after working with someone whose confidence in their coding ability was very low. During the project, there were points where me and another member were progressing with the code, while the other was struggling, and we had to take on more coding than initially expected. At the end of the project, I had a conversation with the teammate that had trouble with the code, and she told me that by working with us, she’d learned a lot and believed she could keep going with the course. That’s something I’m very proud of!

My biggest tangible contribution that can be seen comes from the Figma prototype. As the person who designed and built that by themselves, it was good to show just how much forethought had gone into the design and presenting a clickable prototype also was useful to showcase what else we would have built if we decided to add more to the MVP.

Code-wise, I’d spent a few hours using LiveShare, which is an integration on VSCode which allows people to share their code online, and edit their code as if they’re using the same computer.

At the end of the project, I was given the task of unravelling some of the code that has conflicted across 4 different branches related to the Inspirations, and was able to clean up the code before pushing it, and map the Inspirations linked to Foods. This took a long time as I was reluctant to push code that would conflict with the code on the Main branch that we knew worked before. Finishing at 2am before the presentation was due and knowing that everything worked was a massive relief for us.

## Key Learnings/Takeaways

Pairing was very useful to me, and others around me! I learned a lot, and feel progressively confident in my own skills as I could see first-hand that I could contribute to other people’s growth as coders.

I also learned that working in branches is useful when building features, but it’s best not to use multiple branches at the same time. Unfortunately, I repeated this mistake in another project, but this time, I’ve learned my lesson!

I’d potentially have organised the team’s workload differently knowing what I know now. Although I wanted everyone in the team to shine and work on what piqued their interests, the team might have presented a project at the end that was more aesthetically pleasing had all of us been expected to work on the things that would have challenged them without the potential of getting overwhelmed.

## Bugs

There are no bugs in this project, although there is a lot of redundant code that might cause bugs in the future

## Future Improvements

- ### I would like to be able to make my controllers more streamlined. 

I’ve noticed that in a few places, I have created code that could be redundant and would benefit from refactoring.

An improvement for later projects would be to use variables in the controller where table names, model names etc could be imported into the controller files and then used as variables which would then require some degree of logic to assign in different scenarios.

- ### CSS

Improving the look of the app would be great as the CSS was done quite quickly since there were so many issues with the frontend before the project was due.
