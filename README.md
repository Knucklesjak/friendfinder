# Friend Finder - Node and Express Servers

### Overview

Live Link

In this activity, I built a compatibility-based "FriendFinder" application -- basically a dating app. This full-stack site will take in results from users' surveys, then compare their answers with those from other users. The app will then display the name and picture of the user with the best overall match. 

I used Express to handle routing. The app is deployed to Heroku so other users can fill it out.



###

1. Mysurvey should have 10 questions. Each answer is on a scale of 1 to 5 based on how much the user agrees or disagrees with a question.

2. My `server.js` file requires the basic npm packages we've used in class: `express`, `body-parser` and `path`.

3. My `htmlRoutes.js` file includes two routes:

   * A GET Route to `/survey` which displays the survey page.
   * A default, catch-all route that leads to `home.html` which displays the home page. 

4. My `apiRoutes.js` file contains two routes:

   * A GET route with the url `/api/friends`. This displays a JSON of all possible friends.
   * A POST routes `/api/friends`. This handles incoming survey results. This route will also handles the compatibility logic. 

5. Mya application's data inside of `app/data/friends.js` is saved as an array of objects:

```json
{
  "name":"Ahmed",
  "photo":"https://media.licdn.com/mpr/mpr/shrinknp_400_400/p/6/005/064/1bd/3435aa3.jpg",
  "scores":[
      5,
      1,
      4,
      4,
      5,
      1,
      2,
      5,
      4,
      1
    ]
}
```

6. The app determines the user's most compatible friend using the following as a guide:

   * Converts each user's results into a simple array of numbers (ex: `[5, 1, 4, 4, 5, 1, 2, 5, 4, 1]`).
   * With that done, compares the difference between current user's scores against those from other users, question by question. Adds up the differences to calculate the `totalDifference`.
     * Example: 
       * User 1: `[5, 1, 4, 4, 5, 1, 2, 5, 4, 1]`
       * User 2: `[3, 2, 6, 4, 5, 1, 2, 5, 4, 1]`
       * Total Difference: **2 + 1 + 2 =** **_5_**
   * The closest match will be the user with the least amount of difference.

7. Once the current user's most compatible friend is found, the result is displayed as a modal pop-up.
    

- - -

