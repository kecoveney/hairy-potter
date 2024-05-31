# The Hairy Potter

In this project, your task to build a workflow for making, and firing pottery, and then determining if it should be sold at a craft show. Then you will display the pottery to be sold in the DOM.

> 🧨 Make sure you answer the vocabulary and understanding questions at the end of this document before notifying your coaches that you are done with the project

## Setup

1. Open a new terminal window, copy pasta the following command into the terminal and hit enter to run it. It will create a basic file structure for you and create some starter code in the `~/workspace/hairy-potter-project` directory.

   ```sh
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/nashville-software-school/course-bash-scripts/main/client/hairy-potter.sh)"
   ```

1. Navigate to the project directory
   ```sh
   cd ~/workspace/hairy-potter-project
   ```
1. Create a Github repository for this project and run the use the suggested `git remote add origin` command to connect your local repository with the Github repository. The setup script runs `git init` for you.
1. Open the project for editing with the `code .` command.
1. Run the following command in your terminal. This is the directory where all of your code will be written.

   ```sh
   cd src
   ```

1. Run the `serve` command to start the web server.
1. Open the URL provided by `serve` in your browser.
1. Open another new terminal session _(yes, there will be two terminal sessions needed for this project)_ and make sure you are in the the `hairy-potter-project` directory and not in the `src` sub-directory.

   ```sh
   cd ~/workspace/hairy-potter-project
   ```

## Requirements

### Making Pottery at the Wheel

1. Create a `scripts/PotteryWheel.js` module.
1. Define a variable in the module to have the value of the primary key for each piece of pottery. It should have an initial value of 1.
1. Define and export a function named `makePottery`.
1. The `makePottery` function must accept the following values as input _(i.e. it needs parameters)_, in the following order.
   1. Shape of the piece of pottery (e.g. "Mug", "Platter")
   1. Weight of the piece (e.g. 1, 5)
   1. Height of the piece (e.g. 3, 7)
1. The `makePottery` function must return an object with the following properties on it.
   1. `shape`
   1. `weight`
   1. `height`
   1. `id` _(increment this value each time the function is invoked)_

#### Checking Your Work

In the `main.js` module, invoke the `makePottery` function and provide the required values as arguments. Store the object that gets returned into a variable, and then use `console.log()` to view the object.

Once you have it working, make 5 pieces of pottery in `main.js`.

**THEN PUSH YOUR CODE TO GITHUB**

### Firing the Pottery in the Kiln

1. Define a `scripts/Kiln.js` module.
1. Define and export a function named `firePottery` that is responsible for acting as a kiln.
1. The function must accept the following values as input _(i.e. it needs parameters)_, in the following order. If you don't remember, you can easily [add new properties to objects in JavaScript](https://www.dyn-web.com/tutorials/object-literal/properties.php).
   1. An object representing a piece of pottery that was made at the wheel in the `makePottery` function.
   1. A number specifying the firing temperature of the kiln.
1. The function must add a new property of `fired` with the value of `true` to the object.
1. The function must add a new property of `cracked` to the object.
   1. If the temperature of the kiln is above 2200 degrees then `cracked` property must have a value of `true`.
   1. If the temperature of the kiln is at, or below, 2200 degrees then `cracked` property must have a value of `false`.
1. After both of the new properties have been added, return the augmented object.

#### Checking Your Work

In the `main.js` module, invoke the `firePottery` function for each of the 5 pieces of pottery you created. Ensure you provide the required values as arguments. Store the object that gets returned into a variable, and then use `console.log()` to view the objects and make sure it has the right properties on each.

To check your work, make sure that at least one of your pieces of pottery is fired at a temperature that is too high.

**THEN PUSH YOUR CODE TO GITHUB**

### Pricing Uncracked Pottery

1. Create a `scripts/PotteryCatalog.js` module.
1. Define a variable in the module with a value of an empty array. This array will store pottery that will be sold. Do not export this array.
1. Define and export a function named `toSellOrNotToSell` that is responsible for determining if a piece of pottery should be sold.
1. The `toSellOrNotToSell` function must accept a pottery object as input.
1. If the weight of the piece of pottery is greater than, or equal to, 6 then the function must add a `price` property with a value of 40.
1. If the weight of the piece of pottery is less than 6 then the function must add a `price` property with a value of 20.
1. If the piece of pottery is cracked, do not add a `price` property to it.
1. If the pottery is **not** cracked, add the object to the module-level array of items to be sold.
1. Return the augmented object.
1. Define and export a function named `usePottery` returns a copy of the array of items to be sold. Recall which array method creates a copy of the array.

#### Checking Your Work

In the `main.js` module, invoke the `toSellOrNotToSell` function for each of the 5 pieces of pottery you created. Ensure you provide the required value as an argument.

**THEN PUSH YOUR CODE TO GITHUB**

### Display the Catalog

Your next task is to create HTML representations of the pottery you want to sell at the craft fair and display them on the DOM. Then you will track which ones you sell.

#### Define DOM Target

1. Create an `<article>` element in the `index.html` file.
1. The article element must have a class of `potteryList`.

#### Create Pottery HTML

1. Create a `scripts/PotteryList.js` module.
1. Define and export a `PotteryList` function.
1. The `PotteryList` function must get the items to be sold from the `PotteryCatalog.js` module.
1. The `PotteryList` function must convert each object in the array to an HTML representation string. Use the following template to generate the representations.
   ```html
   <section class="pottery" id="pottery--1">
     <h2 class="pottery__shape">Mug</h2>
     <div class="pottery__properties">
       Item weighs 3 grams and is 6 cm in height
     </div>
     <div class="pottery__price">Price is $20</div>
   </section>
   ```
1. The `PotteryList` function must then return a single string that contains ALL of the pottery HTML representation.

#### Checking Your Work

In the `main.js` module, invoke the `PotteryList` component function. Take its return value and update the inner HTML of the article element you created above. When you start your web server, you should see your non-cracked pottery list appear (_example below_).

![example output](./src/images/pottery.png)

**THEN PUSH YOUR CODE TO GITHUB**


## Vocabulary and Understanding

> 🧨 Before you click the "Assessment Complete" button on the Learning Platform, add your answers below for each question and make a commit. It is your option to request a face-to-face meeting with a coach for a vocabulary review.

1. Explain how you got the HTML, with the correct data, displayed in the browser?
   > The article element with the class potteryList in the index.html file serves as the target where the pieces of pottery will be displayed. The PotteryList.js module contains the PotteryList function, which is responsible for generating the HTML representation for each object that is an uncracked piece of pottery. This function retrieves the pottery items to be sold from the PotteryCatalog module, constructs the HTML for each item using template literals, and inserts the generated HTML into the potteryList element using the innerHTML property.
2. In the **PotteryList** module, when you iterate your pottery, you need to show the evidence of what the **weight** property's value is for the 2nd piece of pottery. Use [Loom](https://www.loom.com/) to record your browser window with the developer tools open and show those values.
   > https://www.loom.com/share/741389e6f88d45a9ad98b97bcef58b66?sid=e0057cbe-2118-4755-92b1-2741447dd9bd
3. The **PotteryWheel** module has a single function named `makePottery`. Why doesn't that module have all of the other code in it?
   > The PotteryWheel module only includes the makePottery function to follow the principle of separation of concerns, making the code more maintainable, reusable, and scalable. Each module focuses on a specific task: PotteryWheel for creating pottery, Kiln for firing, PotteryCatalog for determining sale eligibility and pricing, and PotteryList for displaying items. This modular approach ensures easier updates, independent testing, and better organization.
4. The pottery shop has learned that there is a set of customers that are willing to buy cracked pottery at a discounted price of $2.50. That means that the cracked pottery should now be displayed in the catalog. Explain the changes that this new business strategy would cause to your algorithm.
   > To accommodate the new business strategy of selling cracked pottery at a discounted price of $2.50, several changes need to be made to the existing algorithm. The toSellOrNotToSell function will need to be updated to include cracked pottery in the potteryToSell array and would then assign a price of $2.50 to these items. If the pottery is not cracked, the function will continue to determine the price based on weight using if else statements, setting it to $40 if the weight is 6 or more and $20 if it is less. All pottery, whether cracked or not, will be added to the potteryToSell array. The PotteryList function, which generates HTML for each piece of pottery in the array, will automatically include cracked pottery in the catalog displayed on the web page, ensuring that all items are represented accurately with their respective prices.
5. In the **Kiln** module, you have a `firePottery()` function. You need to demonstrate how to use the debugger to verify the values of the parameters for that function when your code runs. Use [Loom](https://www.loom.com/) to record your browser window with the developer tools open and show those values.
   > https://www.loom.com/share/883ac2e2d1d84dea9accf70cfd29d550?sid=e92e96c9-99ff-4177-9bf8-2bd26cd2d372
