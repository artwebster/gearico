# Gearico
A Wearable Technology E-commerce Site

## Description
Created by a small, 3 person team, this was a 5-day project as part of the Concordia Web Development bootcamp. We were given a .json file of wearable technology items (names, prices, and thumbnails), and instructions that the MVP had to allow users to browse and purchase those items, updating their stock in the backend via a RESTful server. Everything else was up to us, provided we stuck to the MERN stack and didn't use any extra libraries/dependencies to cut corners.

## Homepage:

![homepage_full](https://user-images.githubusercontent.com/97937045/167347569-1343bcd4-43d5-4091-ad7c-613edbb7ee11.png)

The landing page, with the navigation bar fixed on the top. If you scroll down, you see the **Category** links. Clicking on the "Products" link at the top will let you browse _all_ of the items, whereas clicking on a category here will take you to the appropraite item sub-category within the Products page.

Underneath that, there are a handful of **Featured Products** - ideally items that are overstocked and you want to push.

## Products:

![categories](https://user-images.githubusercontent.com/97937045/167344690-8d4a35be-cbd0-455f-bfec-b314541a8133.png)

Products are limited to 10 per page, with the pagination being handled in the backend. Clicking on an item here, or from the "Featured Items" section of the homepage, will open the item details in a modal:

![product_page](https://user-images.githubusercontent.com/97937045/167347214-495f213e-dae4-4d89-9113-5842b1ff333c.png)

Listed here is all the information we were given for each product - the name, price, company that produces it and category. All of the item details were imported from the given .json file into our Mongo database, which is where the backend pulls the information from on request. We wanted to add a description, but with close to 400 items that wasn't realistic given our timeline. Users can change the quantity (dependent on the # in stock), and either add it to the cart or click anywhere outside the modal to close the details and return to the product page.

## Shopping Cart:

![shoppingcart](https://user-images.githubusercontent.com/97937045/167350250-62b6f5a6-c549-49b1-942a-3aff424f2bb1.png)

The shopping cart displays all items added, giving the user the ability to remove items or change their quantities here as well (number of items are reflected in the Cart link in the top right, in the nav bar). Clicking the "Guest Checkout" button will go directly to the checkout page, but if the user is not signed in yet they will see the "Sign In/Create Account" button, giving them that option.

## Sign In

![signin](https://user-images.githubusercontent.com/97937045/167347900-943927e9-6c2e-4982-b6cd-0d289328ae4d.png)

Signing in/out can be done at any time from the "Sign In" link in the nav bar. Using an email address and a created password, the backend validates this info and utilizes a Mongo database to sign the user in. Now the user can save their address and/or billing info, so they don't have to enter it during the checkout process, as well as see their order history (which is also saved in the database).

## Checkout

![cart](https://user-images.githubusercontent.com/97937045/167348774-a3f5b3d7-3194-47f6-93dc-e3b94e7f8b6d.png)

Finally, the checkout page. Since there's a lot of information we need to collect, we divided the fields into two categories - shipping, and billing. Users get cycled through once they've completed all the input in a section (or, once they've confirmed the inputs if they've signed in and saved their info previously). We used a pretty robust set of input validations in the backend, to ensure the addresses are actual street addresses, postal codes are formatted properly, etc. The final component on this page is the "Review" section, where the user sees all their info and has one last chance to cancel out of the order process. This is also when the "Place Order" button becomes active. Clicking that button does a few things: updates the stock numbers and creates a new order entry in the database in the backend, and opens up a modal in the frontend displaying the order confirmation message.
