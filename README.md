# Periodic Tables Capstone Guide
### _Table of Contents_
* [**0 : Introduction**](#0--introduction)
	* [(0.1) Changelog](#01-changelog)
	* [(0.2) My current progress on the capstone](#02-my-current-progress-on-the-capstone)
	* [(0.3) Starter code won't start](#03-starter-code-wont-start)
	* [(0.4) Deploying your app](#04-deploying-your-app)
	* [(0.5) Creating your databases](#05-creating-your-databases)
  
* [**1 : US-01 - Create and list reservations (front end)**](#1--us-01---create-and-list-reservations-front-end)
	* [(1.1) Tests](#11-tests)
	* [(1.2) Form](#12-form)
	* [(1.3) Dipping our toes back into React](#13-dipping-our-toes-back-into-react)
	* [(1.4) Dashboard](#14-dashboard)

* [**2 : US-02 - Create reservation on a future, working date (front end)**](#2--us-02---create-reservation-on-a-future-working-date-front-end)
	* [(2.1) Tests](#21-tests)
	* [(2.2) Tuesdays](#22-tuesdays)
	* [(2.3) Reservation date is in the past](#23-reservation-date-is-in-the-past)
	* [(2.4) Hooking it up](#24-hooking-it-up)

* [**3 : US-03 - Create reservation within eligible timeframe (front end)**](#3--us-03---create-reservation-within-eligible-timeframe-front-end)
	* [(3.1) Tests](#31-tests)
	* [(3.2) Time is in the past](#32-time-is-in-the-past)
	* [(3.3) Time constraints](#33-time-constraints)
	* [(3.X - Optional) Form validation](#3x---optional-form-validation)

* [**4 : US-04 - Seat reservation (front end)**](#4--us-04---seat-reservation-front-end)
	* [(4.1) Tests](#41-tests)
	* [(4.2) Reuse & Recycle](#42-reuse--recycle)
	* [(4.3) Adding to the dashboard](#43-adding-to-the-dashboard)
	* [(4.4) Table row components](#44-table-row-components)
	* [(4.X - Optional) Moving the API calls](#4x---optional-moving-the-api-calls)
	* [(4.5) Seating a reservation](#45-seating-a-reservation)

---

# **0 : Introduction**
Hi everybody! We are SO close to graduating. I am literally SO PROUD of every single one of you. We've (almost) made it through the hell that is Thinkful by Chegg. My hope is that this guide will be able to relieve some of the stress on you and that it pushes you in a comfortable direction. I will be updating this README as I work through the project and will be putting as much here as I can. 

On top of that, you can use the Issues tab if you have ANY (literally any) questions. You can also post suggestions of content to add to the guide for everyone to see. I will try to be as attentive as I can on this repo. If you would ever like to look at [my project repo](https://github.com/itsdotnickscott/periodic-tables), or the [deployed version of my app](https://periodic-tables-frontend-7tiv1r4sx-itsdotnickscott.vercel.app/dashboard), I will be pushing to the repo when I finish checkpoints as frequently as I can. Looking at my code and my process is not cheating! This is software engineering - we don't need to reinvent the wheel. Observe and learn through example! :P Feel free to use that Issues tab to also ask about why I implemented a feature a certain way or how I got around a certain problem.

Of course, I am not proclaiming to be any type of expert at this. I am learning just as much as all of you, and I will make mistakes and blunders. It's all part of the coding experience, baby. I recommend you read the instructions first before reading the sections. They'll make a lot more sense in-context!

If I've been a help to you at all during this cohort, I would greatly appreciate some LinkedIn endorsements? Is this basically me asking you to smash that like button?

> EDIT (5/17): I was asked a question about how I was handling the tests during this capstone. Here was my answer about my current workflow...feel free to adopt the same idea if it suits you.
>
> "im very loosely worrying about the tests right now. i look at them and run them to see what they're generally looking for, but i am not going in-depth into any one test for a bit. im planning on building out the rest of the functionality using just the instructions, and if i pass tests along the way, yay. otherwise, i ignore them, lol. i'll go back and care about the tests when i feel like i have a solid minimum viable product (mvp)"

---

### *(0.1) Changelog*
If I significantly edited a section after it was already written, there's a chance you are missing some updated information. If I ever add a significant chunk to a section, I will put it here so you can stay updated. Also, I will put all edits under an "edit" section so changes are easy to find. Cheers y'all!

**May 17th**
* Included additional workflow information in the introduction.

**May 12th**
* 1.3 at `handleSubmit` function: Removed the use of `formatReservationDate()`.

**May 11th**
* Solution changed in Section 2.

---

### *(0.2) My current progress on the capstone*
Front End:
- [ ] US-01 Create and list reservations
- [X] US-02 Create reservation on a future, working date
- [X] US-03 Create reservation within eligible timeframe
- [ ] US-04 Seat reservation
- [ ] US-05 Finish an occupied table
- [ ] US-06 Reservation Status
- [ ] US-07 Search for a reservation by phone number
- [ ] US-08 Change an existing reservation

Back End:
- [ ] US-01 Create and list reservations
- [ ] US-02 Create reservation on a future, working date
- [ ] US-03 Create reservation within eligible timeframe
- [ ] US-04 Seat reservation
- [ ] US-05 Finish an occupied table
- [ ] US-06 Reservation Status
- [ ] US-07 Search for a reservation by phone number
- [ ] US-08 Change an existing reservation

---

### *(0.3) Starter code won't start*
Surprise! Thinkful starter code will crash when running `npm run start:dev`. If you read my guide for Flashcards, you'll remember the fix.
In `./package.json` (make sure you're looking at the file in the root directory), change the `start:dev` script to: `"npx concurrently \"npm run start:dev --prefix ./back-end\" \"npm start --prefix ./front-end\""`

---

### *(0.4) Deploying your app*
The project recommends you deploy early and often. The EASIEST way to do this is by deploying via GitHub, not the commandline.
1. Initialize and push your app onto a new GitHub repository.
2. If you cloned the project, then it is possible that the project is still connected to Thinkful's repo. We need to delete the `.git` folder in the directory (NOT `.github`). If you can't find the `.git` folder, go to your File Explorer, and view hidden items. You should be able to see it and delete it.
3. [Create a project on Vercel](https://vercel.com/new).
4. Link up your GitHub account if you haven't already.
5. If everything's good up till this point, you should be able to import your capstone project into Vercel.
6. Select your personal account.
7. Select the `back-end` folder, and press 'Continue'.
8. Blah blah blah options. Name the project so you can tell it is the backend, something like `periodic-tables-backend`.
9. Deploy, baby!!
10. After it is deployed, the preview should say something like `{"error":"Path not found: /"}`. Good news: this error is good. It means it deployed correctly.
11. Time to do the same process but for the `front-end` folder. [Create a project on Vercel again](https://vercel.com/new) and import the same GitHub repo. You don't have to do anything special. You'll notice that the final settings page recognizes that it is a React app. That's neat!
12. If everything worked out, you should see the base template of the starter project. The BEST part about deploying via GitHub is that Vercel will automatically update your website **every time you push your project onto your GitHub repo's main branch**. That saves SO MUCH headache from deploying via the command line, at least in my opinion.

---

### *(0.5) Creating your databases*
Here's a refresher on ElephantSQL and DBeaver!
1. [Create a new instance](https://customer.elephantsql.com/instance/create).
2. Select a name and tag. I named one of mine `pt-devlopment` and gave it a `Periodic Tables` tag.
3. Select a region closest to you. I chose US-West because.....west coast best coast. I'm sorry, I don't make the rules.
4. Create instance.
5. Time to do this three more times for `test`, `preview`, and `production`! : ^)

Time to move onto DBeaver.
1. Click on New Connection (it looks like a blue plug with a plus sign).
2. Choose PostgreSQL.
3. Using the information from ElephantSQL:
  * Host will be the "Server"
  * Database and Username will be the "User & Default database"
  * Password can be copied using the clipboard icon
4. If all of that works, the "Test Connection" button should show a successful connection.
5. Rename the connection so they're easily identifiable.
6. Time to do this three more times!!! Don't have too much fun!
7. (Optional) I made a `periodic-tables` folder using the yellow folder icon and moved all of my connections into there. Organization! B)

Last thing to do...
1. Go to your `.env` file in the `./back-end` folder.
2. Update all of those URLs with the corresponding "URL" on ElephantSQL. Like the password, there is a clipboard button for easy pasting.

I hope that was easy for you, but it is okay if it isn't yet. You're going to be a pro in no time.

---

# **1 : US-01 - Create and list reservations (front end)**
The testing for this project is a bit more frustrating than what we've dealt with before. Running `npm run test:1`, firstly, cannot run at the same time as your servers if you ran `npm run start:dev` (they are on the same port...). Secondly...I have a hard time getting `npm run test:1` to work. It just crashes, and I'm guessing it's because I haven't done some part of the code yet. (However, I have been successful with `npm run test:1:frontend`.)

---

### *(1.1) Tests*
You can always look at the test files yourself, but I LOVE having all of the tests in a list for easy reference, so here they are! (tests checked off are tests that are passing for my current code).

`/reservations/new` page
- [ ] filling and submitting form creates a new reservation and then displays the dashboard for the reservation date
- [X] canceling form returns to previous page

---

### *(1.2) Form*
I am going to try my best to be as in-depth as I can about my process as a programmer and how I am personally building my app. I'm going to start by building up the front-end entirely. I'm not working to style it at all. I'm getting what I need to be displayed on each page to create a minimum-viable product (MVP) without focusing on little details. I am a very detail-oriented person, but I know I have to ignore it and save it for later, because it's not going to help right now!

Of course, this is YOUR project and YOUR workflow. YOU decide what to do and when!

Let's make our new component. Here is what I generally do when first creating a React component.
```javascript
// 1. import react
// 2. create component function & export it
// 3. create a return statement (most, if not all react components will return some JSX)

import React from "react";

// i named my component NewReservation:
export default function NewReservation() {
	return (
    		// JSX will be placed here as we build our component
	);
}
```

`/layout/routes.js` - Before we build our page, we need to route it!
```javascript
import NewReservation from "../reservations/NewReservation";

// code ommited for brevity (from now on, this will be represented by ...)

<Route exact={true} path="/reservations/new">
	<NewReservation />
</Route>
```

`/reservations/NewReservation.js` - Let's make our form and our inputs.
```javascript
return (
	<form>
		{ /* use the following as a template for your input fields: */ }
		<label htmlFor="first_name">First Name:&nbsp;</label>
		{ /* &nbsp; is a fancy way for HTML to place a space instead. it stands for "non-breakable space". i used it because i found the label and the input box were too close together. */ }
		
		<input
			name="first_name"
			id=="first_name"
			type="text"
			onChange={} // we will add this in soon!
			value={} // this as well!
			required // this will make the field non-nullable
		/>
        
		{ /* now to make the rest of them! */ }
	</form>
);
```

Let's look at some helpful input types:
* "text" - value is a string
* "number" - value is a number
* "tel" - value is a phone number (i'd suggest looking up the [pattern attribute](https://www.w3schools.com/tags/att_input_pattern.asp) as well)
* "date" - string formatted as YYYY-MM-DD
* "time" - string formatted as HH:MM

Let's make some buttons!
```javascript
<form>
	// ...
	<button type="submit" onClick={}>Submit</button>
	<button type="button" onClick={}>Cancel</button>
</form>
```

Byotiful.

---

### *(1.3) Dipping our toes back into React*
*shudder* It's React...

Let's start by setting up our form data with the `useState` hook.
```javascript
import React, { useState } from "react";

export default function NewReservation() {
	// recall that useState takes the form [state, setState], where setState is an asynchronous function
	const [formData, setFormData] = useState();
}
```

We now want to create an initial, default form that the user will see when first visiting the page.
```javascript
// we get to put this right inside of our useState hook as an object:
const [formData, setFormData] = useState({
	first_name: "",
	last_name: "",
	mobile_number: "",
	reservation_date: "",
	reservation_time: "",
	people: 0,
});

// ??? why did i use underscore_case here instead of camelCase?
// all of our <input> fields have a 'name' attribute that uses underscore case. when we are editing the form fields later, we want to be consistent with the field names.
```

Everytime a user makes a change to an input, we want to record that as a state.
```javascript
function handleChange({ target }) { // i deconstruct the `event` argument
	// we will be using our useState hook to store whatever changes are made.
	// this is why we use underscore case; when we access target, we get the input name in underscore_case.
	setFormData({ ...formData, [target.name]: target.value });
	// remember to use the spread operator `...` so all previous values do not get overwritten.
}
```

Recall that we left some attributes blank on the inputs...`onChange` and `value`. Let's go in and fill it now!
```javascript
// example:
<input
	// ...
    
	onChange={handleChange} // the function we just made! the onChange attribute will automatically pass the `event` argument based off of which input was clicked
	// we can use our useState hook to store the values of each input now
	value={formData.first_name}
/>

```

Both the cancel and submit button will be redirecting people. Let's refresh ourselves with the `useHistory` hook:
```javascript
import { useHistory } from "react-router-dom";

export default function NewReservation() {
	const history = useHistory();

	// example code:
	// recall how to bring back someone back a page:
	// history.go(-1);
    
	// you can also call:
	// history.goBack(); 
	// this is the same as the one above!
    
	// great, let's put this into our onClick handler for cancel!
	<button type="button" onClick={history.goBack}>Cancel</button>
```

As of now, the cancel button test is passing for me.

Let's make our submit handler. As of right now, we're not going to be sending this form anywhere, because there's no where to send it to. We'll come back to this in the future.
```javascript
function handleSubmit(event) {
	event.preventDefault(); // the normal submit refreshes the entire page. we don't want that to happen!
  
	// in the future, we will be editing this submit handler to actually post the request to the database. i'm not worried about it right now though.
  
	// the submit button will be redirecting the user to the dashboard on a specific date.
	// the dashboard will have a URL query with the date. it looks like /dashboard?date=2035-12-30
	// so i will be replicating this here.
	// the push function literally "pushes" the user to whatever path you give.
	history.push(`/dashboard?date=${formData.reservation_date}`);
}

// ...

// time to add our function to the submit button!
<button type="submit" onClick={handleSubmit}>Submit</button>
```

> EDIT (5/12): I took out the use of formatReservationDate() because it wasn't working. You can just use the raw `formData.reservation_date`.

If you run your tests, you'll see that the submit test is still failing. It's an async error, so I think this might be because not everything is set up yet. Great job refreshing yourselves with React. It's been a bit.

Here's what my page looks like now. Ugly and unformatted! :)

![/reservations/new initial screenshot](https://user-images.githubusercontent.com/64234681/117707205-1ff64f00-b183-11eb-8991-188f07d50f97.JPG)

---

## *(1.4) Dashboard*
Thinkful is hiding a lot of information in different files. Keep in mind the starter code that is already written for you because they WILL be helpful...particularly, the `utils` folder. Let's go look at how we can use some of them!

You'll see in `/dashboard/Dashboard` that a lot of it is already set up. It's great because it means we don't have to figure out how to do certain tasks, and it sucks because we don't quite know what it even does right now. Let's go over the existing code together and point out some important bits of code.

```javascript
// at the top of the function, we can see that there are two states being stored. the 'reservations' state is especially important because it is holding the response from our API! (right now the API returns nothing; we haven't made it yet)
const [reservations, setReservations] = useState([]);
const [reservationsError, setReservationsError] = useState(null);

// useEffect review! useEffect(func, depen) - func is a function that is called when the page first renders, and after every time one of the variables in the dependency array changes.
// a dependency array of [] will only be ran once.
// in this case, useEffect will call the loadDashboard function every time the 'date' variable changes
useEffect(loadDashboard, [viewDate]);

function loadDashboard() {
	// recall that the abort controller is used for async calls. it is used to avoid race conditions.
	const abortController = new AbortController();
	
	// no errors
	setReservationsError(null);
	
	// time to make our API call! the first parameter { date } is the search parameter for the database, and also the value of 'date'.
	listReservations({ date }, abortController.signal)
		.then(setReservations)
		.catch(setReservationsError);
		
	// here's where all other abortControllers will dump their async calls - race conditions fixed!
	return () => abortController.abort();
}

// this return statement already has a component that will show errors if something goes wrong. then, it stringifies the response from the API.
// right now, the stringify will still output some javascript-looking strings. we will want to find another way later to format this nicely for the user. however, we don't have to worry about that yet!
return (
	<main>
		<h1>Dashboard</h1>
		<div className="d-md-flex mb-3">
			<h4 className="mb-0">Reservations for {date}</h4>
		</div>
		<ErrorAlert error={reservationsError} />
		{JSON.stringify(reservations)}
	</main>
);
```

Firstly, we have to acknowledge the query in the URL. If there is no date query, today's date will be used. You can see the initial `<Dashboard />` component in `/layout/Routes.js` passes the current date as a prop.

React doesn't have a built in query getter. Luckily, our handy `utils` folder has a custom React hook to grab the query. Let's check it out in `/utils/useQuery.js`:
```javascript
/**
 * useQuery is a custom hook that makes use of the useLocation and the URL class to parse the query parameters.
 *
 * @example
 *
 * const query = useQuery();
 * const date = query.get("date")
 */

import { useLocation } from "react-router-dom";

function useQuery() {
	return new URLSearchParams(useLocation().search);
}
```

We don't need to fully understand how the function works to use it! Let's go implement it in `layout/Routes.js`:
```javascript
// i chose this file because this is where the dashboard is routed from.
import useQuery from "../utils/useQuery";

function Routes() {
	const query = useQuery();
	const date = query.get("date");

// ...

// now we can use this for our Dashboard component:
<Route path="/dashboard">
	{ /* i use a ternary here. if date exists, pass in that date. otherwise, just send in today's date. */ }
	<Dashboard date={date ? date : today()} />
</Route>
```

Let's make some buttons back in `reservations/NewReservation`. The `utils` folder has some helpful functions for us! We will be importing and creating a history variable with the useHistory hook.
```javascript
// these functions will give the day before, the day today, and the next day, respectively.
import { previous, today, next } from "../utils/date-time";
import { useHistory } from "react-router-dom";

function Dashboard({ date }) {
	const history = useHistory();
	
	// ...

	return (
		<main>
			<h1>Dashboard</h1>
			<div className="d-md-flex mb-3">
				<h4 className="mb-0">Reservations for {date}</h4>
			</div>
			<ErrorAlert error={reservationsError} />

			{JSON.stringify(reservations)}

			<button type="button" onClick={() => history.push(`/dashboard?date=${previous(date)}`)}>Previous</button>
			<button type="button" onClick={() => history.push(`/dashboard?date=${today()}`)}>Today</button>
			<button type="button" onClick={() => history.push(`/dashboard?date=${next(date)}`)}>Next</button>
		</main>
	);
```

Notice I edited the `<h4>` element to show the date. If we go to our web page and test out our buttons, we can see the date actually changing!

![dashboard buttons example](https://user-images.githubusercontent.com/64234681/117718994-b7fb3500-b191-11eb-8c2c-a7afcd860419.gif)

---

# **2 : US-02 - Create reservation on a future, working date (front end)**
For this user story, we will be adding some features onto our `NewReservation component`. We will be validating the reservation date after a user tries to submit the form. Let's head on over to `/reservations/NewReservation.js`! (This is where I organized this file - yours might be in a different location / have a different name.)

I'd like to note that for this section, I spent a bit coming up with a solid solution to this problem. The `Date` class CAN be tricky, since dates are treated as if they are a UTC time. However, sometimes JavaScript will use your local time zone at times to interpret them. We have to be careful what "time zone" we are working in (I'm referring to UTC as a time zone even though it technically isn't).

Looking at the [Date class documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) was helpful during this user story.

There are two paths we can go down:
- Work completely in UTC
- Work completely in the user's time zone

I'm deciding to work in the user's time zone so we can base everything off of their local time zone.

I didn't record my whole process in this guide. I'm just giving you my current solutions to the checkpoints. What might seem like a simple solution took a good bit of refactoring and simplifying. If you'd like to take a good shot at this before reading, please do! Otherwise, let's go solve this thing!

> EDIT (5/11): If you read this before it was changed, my old solution worked in UTC. After moving onto the third user story, I realized that working in the user's local time zone might be easier in the long run. Who knows...maybe I'll come back and change this back to UTC. Regardless, the logic remains completely the same no matter which path we choose. Just stay consistent.

---

## *(2.1) Tests*
`/reservations/new` page
- [X] displays an error message if the date of the reservation occurs in the past
- [X] displays an error message if reservation date falls on a Tuesday

---

## *(2.2) Tuesdays*
Tuesdays...second worst only to Mondays. Looks like the restaurant is closed on Tuesdays, and we should display errors to the user if they try to reserve on a Tuesday.

`/layout/ErrorAlert.js` - Before we start writing our validation code, let's take a look at the `ErrorAlert` component that was included with the starter code.
```javascript
/**
 * Defines the alert message to render if the specified error is truthy.
 * @param error
 *  an instance of an object with `.message` property as a string, typically an Error instance.
 * @returns {JSX.Element}
 *  a bootstrap danger alert that contains the message string.
 */

function ErrorAlert({ error }) {
	return (
		error && (
			<div className="alert alert-danger m-2">Error: {error.message}</div>
		)
	);
}

export default ErrorAlert;
```

This component was also used in the `Dashboard` component when there is an error grabbing the reservations. `ErrorAlert` uses a `<div>` with `className="alert alert-danger m-2"`, so this will satisfy the tests.

`reservations/NewReservation.js` - Let's check to see if the reservation date is a Tuesday!
```javascript
// i'm going to create my own function here, specialized to validate the reservation date.
function validateDate() {
	// we will be using the built-in Date class to be comparing our dates
	// previously in this file, we stored the form's input values in a react state called formData
	// we can access that here, and use the Date constructor
	// the string is already stored in the format YYYY-MM-DD, so we don't have to do anything special to the string...at least not yet (we'll touch on this in the next user story).
	const reserveDate = new Date(formData.reservation_date);
	
	// it's possible we can have multiple errors when a date is submitted. i am going to initialize an array to hold these errors.
	const foundErrors = [];
	
	// the Date class has many functions, one of which returns the day (0 is sunday, 6 is saturday)
	if(reserveDate.getDay() === 2) {
		// it's tuesday...let's push in an error object to our array!
		foundErrors.push({ message: "Reservations cannot be made on a Tuesday (Restaurant is closed)." });
	}
}
```

---

## *(2.3) Reservation date is in the past*
Let's keep building on our validation function. I would like to start by grabbing today's date.
```javascript
function validateDate() {
	const reserveDate = new Date(formData.reservation_date);
	
	// we will need to compare the reservation date to today's date.
	// an empty constructor defaults the date to whatever it is right now
	const todaysDate = new Date();

	const foundErrors = [];

	if(reserveDate.getDay() === 2) {  
		foundErrors.push({ message: "Reservations cannot be made on a Tuesday (Restaurant is closed)." });
	}
}
```

Next, we will be comparing dates. After creating a bit of a complex algorithm to check if a certain date is in the past, I realized the `Date` class can be compared normally with <, >, etc. This solution is significantly more elegant. There are some restrictions on comparing dates...if you want to know more about them, [check this out](https://stackoverflow.com/questions/492994/compare-two-dates-with-javascript)!
```javascript
if(reserveDate < todaysDate) {
	foundErrors.push({ message: "Reservations cannot be made in the past." });
}
```

---

## *(2.4) Hooking it up*
We should now successfully be finding these errors, but as of right now, we're not doing anything with them. The reservation will still submit normally, no matter what. We will need to hook it up with the rest of the `NewReservation` component.
```javascript
// my solution involves creating a new state that will contain the errors
const [errors, setErrors] = useState([]);
```

We'll have the validation function set its found errors into the state. If there were no errors, it'll remain an empty array.
```javascript
function validateDate() {
	// ...

	setErrors(foundErrors);
}
```

Now, we'll have the validation be called after every time the submit button is pressed.
```javascript
function handleSubmit(event) {
	event.preventDefault();

	// if there are errors, we don't want to push the user onto a different page, we want them to stay on this page until the issue is resolved.
	// because of this, i'm thinking of adding a return statement to our validation function that will be true when the date is valid and false if it isn't.
	// that way, we only push the user if there are no errors with the reservation date.
	if(validateDate()) {
		history.push(`/dashboard?date=${formData.reservation_date}`);
	}
}
```

Great! I want to go add those return statements I was talking about.
```javascript
function validateDate() {
	// ...

	setErrors(foundErrors);

	// we can use our foundErrors array to check if there were any problems.
	if(foundErrors.length > 0) {
		return false;
	}
	// if we get here, our reservation date is valid!
	return true;
}
```

The last thing we have to do is have the errors display if there are any.
```javascript
// ...
	
// i'm going to create an errors variable that maps every error into an ErrorAlert component
// no errors? returns nothing.
const errors = () => {
	return dateErrors.map((error, idx) => <ErrorAlert key={idx} error={error} />);
}

return (
	<form>
		{ /* we can throw our errors right at the top, so they'll be noticeable to the user */ }
		{errors()}

		<label htmlFor="first_name">First Name:&nbsp;</label>
			
		// ...
	</form>
);
```

All my front-end tests for US-02 are passing! Time to see it in action:

![new reservations date errors example](https://user-images.githubusercontent.com/64234681/117870533-15a28680-b251-11eb-9f0d-a3252f8a1d02.gif)

---

# 3 : **US-03 - Create reservation within eligible timeframe (front end)**
This user story is exactly like the previous one except with the time instead of the date. We'll mostly keep working within the same file with the same validation function. Let's go!

---

## *(3.1) Tests*
`/reservations/new` page
- [X] displays an error message if reservation time is before 10:30 AM
- [X] displays an error message if reservation time is too close to close time
- [X] displays an error message if reservation time is after the close time

---

## *(3.2) Time is in the past*
Let's talk about date strings. They look like this: `2021-05-11T01:48:04.123`. The date YYYY-MM-DD goes first, then a capital letter T, then the time in HH:MM:SS:XXX, where XXX is milliseconds ranging from 000 - 999. Knowing this, we can change how we initialize our `Date` object so we can utilize time in our validation function as well.
```javascript
// i changed the constructor to be a date string with time included
const reserveDate = new Date(`${formData.reservation_date}T${formData.reservation_time}:00.000`);
```

The best part is, this small change still works on this piece of code that compares the dates! If you try to make a reservation for today at 12:00pm when the time is already 12:01pm, this error message will pop up.
```javascript
// this comparison still works, because it is taking account time as well now
if(reserveDate < todaysDate) {
	foundErrors.push({ message: "Reservation cannot be made: Date is in the past." });
}

// ??? how are dates compared?
// every Date is stored as a number that represents the number of milliseconds that have elapsed since January 1, 19-whatever.
// that way, we know if a date is in the past if there are less milliseconds in one date than the other.
```

---

## *(3.3) Time constraints*
The rest of this user story is easy to implement. We set up some conditions and check to see if any of them are triggered.
```javascript
function validateDate() {
	const reserveDate = new Date(`${formData.reservation_date}T${formData.reservation_time}:00.000`);
	const todaysDate = new Date();
	
	const foundErrors = []

	if(reserveDate.getDay() === 2) {  
		foundErrors.push({ message: "Reservation cannot be made: Restaurant is closed on Tuesdays." });
	}

	if(reserveDate < todaysDate) {
		foundErrors.push({ message: "Reservation cannot be made: Date is in the past." });
	}

	// in english: if it is before 10:30am...
	// in code: if the hour is not yet 10 or the hour is 10 but below 30 minutes...
	if(reserveDate.getHours() < 10 || (reserveDate.getHours() === 10 && reserveDate.getMinutes() < 30)) {
		foundErrors.push({ message: "Reservation cannot be made: Restaurant is not open until 10:30AM." });
	}
	
	// in english: if it is after 10:30pm...
	// if the hour is after 22 or the hour is 22 and after 30 minutes...
	else if(reserveDate.getHours() > 22 || (reserveDate.getHours() === 22 && reserveDate.getMinutes() >= 30)) {
		foundErrors.push({ message: "Reservation cannot be made: Restaurant is closed after 10:30PM." });
	}
	
	// in english: if it is after 9:30pm...
	// if the hour is after 21 or the hour is 21 and after 30 minutes...
	else if(reserveDate.getHours() > 21 || (reserveDate.getHours() === 21 && reserveDate.getMinutes() > 30)) {
		foundErrors.push({ message: "Reservation cannot be made: Reservation must be made at least an hour before closing (10:30PM)." })
	}
	
	setErrors(foundErrors);

	if(foundErrors.length > 0) {
		return false;
	}
	return true;
}
```

Errors working as expected!

![new-reservation-time-errors-example](https://user-images.githubusercontent.com/64234681/117885032-2ad3e100-b262-11eb-9a83-064bef47f23b.gif)

---

## *(3.X - Optional) Form validation*
While we're still working on this form, I think it's important for the form to show an error if fields are left blank. I won't go in-depth about my process, since it isn't connected to a certain test, but you can check out how I did it here.
```javascript
function handleSubmit(event) {
	event.preventDefault();

	// i move the foundErrors array in the submit handler so both validation functions can push to the same array
	const foundErrors = [];

	// i created a validateFields function. you can see i now pass foundErrors as an argument
	if(validateFields(foundErrors) && validateDate(foundErrors)) {
		history.push(`/dashboard?date=${formData.reservation_date}`);
	}

	// this also used to be inside of validateDate(), now moved here.
	setErrors(foundErrors);
}

// sparkly new validation function
function validateFields(foundErrors) {
	for(const field in formData) {
		if(formData[field] === "") {
			foundErrors.push({ message: `${field.split("_").join(" ")} cannot be left blank.`})
		}
	}

	if(formData.people <= 0) {
		foundErrors.push({ message: "Party must be a size of at least 1." })
	}

	if(foundErrors.length > 0) {
		return false;
	}
	return true;
}
```

Here's what this looks like:

![new-reservation-field-validation-example](https://user-images.githubusercontent.com/64234681/117885758-147a5500-b263-11eb-9ced-c667421f2fbf.gif)

---

# **4 : US-04 - Seat reservation (front end)**

---

## *(4.1) Tests*
`/tables/new` page
- [ ] filling and submitting form creates a new table
- [X] omitting table_name and submitting does not create a new table
- [X] entering a single character table_name and submitting does not create a new table
- [X] omitting capacity and submitting does not create a new table
- [X] canceling form returns to previous page

`/reservations/:reservation_id/seat` page
- [ ] seating reservation at table #1 makes the table occupied

`/dashboard` page
- [ ] seat button has href with /reservations/${reservation_id}/seat

---

## *(4.2) Reuse & Recycle*
We can easily set up the new table page now that we just worked together on the new reservation page. We can quite literally apply the same logic in a new page. I made a folder called `tables` and a component called `NewTable.js`. I'm not going to go through this step-by-step, but feel free to look at my solution below! You'll probably noticed I did some copy and pasting...
```javascript
import React, { useState } from "react";
import { useHistory } from "react-router-dom";
import ErrorAlert from "../layout/ErrorAlert"

export default function NewTable() {
	const history = useHistory();

	const [error, setError] = useState([]);
	const [formData, setFormData] = useState({
		// initial (default) data
		table_name: "",
		capacity: 1,
	});

	function handleChange({ target }) {
		setFormData({ ...formData, [target.name]: target.value });
	}

	function handleSubmit(event) {
		event.preventDefault();

		if(validateFields()) {
			history.push(`/dashboard`);
		}
	}

	function validateFields() {
		let foundError = null;

		if(formData.table_name === "" || formData.capacity === "") {
			foundError = { message: "Please fill out all fields." };
		}
		else if(formData.table_name.length < 2) {
			foundError = { message: "Table name must be at least 2 characters." };
		}

		setError(foundError);

		return foundError.length !== null;
	}

	return (
		<form>
			<ErrorAlert error={error} />

			<label htmlFor="table_name">Table Name:&nbsp;</label>
			<input 
				name="table_name"
				id="table_name"
				type="text"
				minLength="2"
				onChange={handleChange}
				value={formData.table_name}
				required
			/>

			<label htmlFor="capacity">Capacity:&nbsp;</label>
			<input 
				name="capacity"
				id="capacity"
				type="number"
				min="1"
				onChange={handleChange}
				value={formData.capacity}
				required
			/>

			<button type="submit" onClick={handleSubmit}>Submit</button>
			<button type="button" onClick={history.goBack}>Cancel</button>
		</form>
	);
}
```

Here's a screenshot of my new tables page:

![new-table](https://user-images.githubusercontent.com/64234681/118416222-69eba300-b663-11eb-8ba0-c67abfec796d.png)

---

## *(4.3) Adding to the dashboard*
I haven't migrated or seeded anything yet. It might actually be a good idea to go and do that right now, but I am feeling lazy so I'm going to keep fleshing out the front-end. The problem is, I don't know if it works because there is no data being fetched yet. So, these solutions are relative right now, and they're not going to pass any of the tests (yet).

`/dashboard/Dashboard.js` - I'm going to be creating some HTML tables to organize an area for all of the reservations and then an area for all of the tables. I'm now going to be taking out the `JSON.stringify` that was in the original starter code, since we will now be refactoring it to a more easily-understood format.
```javascript
// although unused right now, i thought it would be important to set up some states for our new "tables" section we will be making
const [tables, setTables] = useState([]);
const [tablesError, setTablesError] = useState(null);

// ...

return (
	<main>
		<h1>Dashboard</h1>

		<h4 className="mb-0">Reservations for {date}</h4>
			
		<ErrorAlert error={reservationsError} />

		{ /* although i'm not caring too much right now about what the table looks like, i'm still utilizing some of the classes from Bootstrap to format it in a nice way. */ }
		<table class="table">
			{ /* "thead" is the table header, meant for the column labels */ }
			<thead>
				{ /* "tr" means table row */ }
				<tr>
					// "th" is a table heading. they all have a scope="col", which is used primarily for Bootstrap. (it will basically <strong> it)
					<th scope="col">ID</th>
					<th scope="col">First Name</th>
					<th scope="col">Last Name</th>
					<th scope="col">Mobile Number</th>
					<th scope="col">Time</th>
					<th scope="col">People</th>
					<th scope="col">Status</th>
					<th scope="col">Seat Table</th>
				</tr>
			</thead>
			
			{ /* "tbody" is the table body. */ }
			<tbody>
				{ /* i am currently planning on creating a special component that will format the reservation information as a table row (<tr>) */ }
			</tbody>
		</table>
      
      		{ /* using the same principles as the code up above, we can make a section for the tables as well: */ }
		<h4 className="mb-0">Tables</h4>

		<ErrorAlert error={tablesError} />

		<table class="table">
			<thead>
				<tr>
					<th scope="col">ID</th>
					<th scope="col">Table Name</th>
					<th scope="col">Capacity</th>
					<th scope="col">Status</th>
				</tr>
			</thead>
				
			<tbody>
				{ /* likewise to the other <tbody>, we will be making a new component that will format the table information. */ }
			</tbody>
		</table>
		
		<button type="button" onClick={() => history.push(`/dashboard?date=${previous(date)}`)}>Previous</button>
		<button type="button" onClick={() => history.push(`/dashboard`)}>Today</button>
		<button type="button" onClick={() => history.push(`/dashboard?date=${next(date)}`)}>Next</button>
    </main>
  );
}
```

Here is what the website looks like:

![dashboard-with-tables](https://user-images.githubusercontent.com/64234681/118416165-314bc980-b663-11eb-88bd-232070fc4744.png)

---

## *(4.4) Table row components*
In the previous section, I mentioned making some new components that will be formatting the information grabbed from the API.

I will start by working on the reservation rows. In `/dashboard`, I made a component called `ReservationRow.js`.
```javascript
import React from "react";

// note that i pass in a reservation object as a prop:
export default function ReservationRow({ reservation }) {
	// returning "null" inside of a react component basically means return nothing. however, we always want to make sure we return null if we intend to return nothing.
	if(!reservation) return null;

	return (
		<tr>
			{ /* because the reservation id is a primary key, i figured i would make this a sort of table header (recall it basically just makes the test bold */ }
			<th scope="row">{reservation.reservation_id}</th>
			
			{ /* for everything else, i use "td", which means table data. */ }
			<td>{reservation.first_name}</td>
			<td>{reservation.last_name}</td>
			<td>{reservation.mobile_number}</td>
			<td>{reservation.reservation_time}</td>
			<td>{reservation.people}</td>
			<td>{reservation.status}</td>
			
			{ /* lastly, the instructions call for a "seat" button. here is where i put it: */ }
			<td>
				<a href={`/reservations/${reservation.reservation_id}/seat`}>
					<button type="button">Seat</button>
				</a>
			</td>
		</tr>
	);
}
```

And now, I want to do the same thing inside of a new component `/dashboard/TableRow.js`. We can just use the same logic as above.
```javascript
import React from "react";

export default function TableRow({ table }) {
	if(!table) return null;

	return (
		<tr>
			<th scope="row">{table.table_id}</th>
			<td>{table.table_name}</td>
			<td>{table.capacity}</td>
			
			{ /* the instructions say the tests are looking for this data-table-id-status, so be sure to include it. */ }
			<td data-table-id-status={table.table_id}>{table.status}</td>
		</tr>
	);
}
```

Lastly, we want to hook these components up inside of `/dashboard/Dashboard.js`. Make sure to import your components first!
```javascript
// if you read my previous sections, i use the same logic of displaying multiple error components here:
const reservationsJSX = () => {
	return reservations.map((reservation) => 
		<ReservationRow key={reservation.reservation_id} reservation={reservation} />);
};

// and here:
const tablesJSX = () => {
	return tables.map((table) => 
		<TableRow key={table.table_id} table={table} />);
};

// and to add them inside of our <tbody> tags:
return (
	{ /* ... */ }
	
	<tbody>
		{reservationsJSX()}
	</tbody>	
	
	{ /* ... */ }
	
	<tbody>
		{tablesJSX()}
	</tbody>
);
```

Like I said, I haven't migrated my tables yet (and I probably won't write a section on it until I'm about done with the front end). So, I can't really test to see if my code is working. I have a feeling they're alright though. ;)

---

## *(4.X - Optional) Moving the API calls*
This section is completely optional, but my code is going to keep building off of the work that I do in this section, so I think it is an important section to read nevertheless.

> *What am I trying to solve?*

Right now, the code that was included in the starter code only makes API calls inside of the `Dashboard` component. I want to move this call up to the dashboard's parent, which happens to be `/layout/Routes.js`.

> *Why am I moving the API call up to the `Dashboard`'s parent?*

It seems like the `Routes` component is the daddy of all the other components (that is, all other components we will be working on. it should be noted that `Routes`' parent component is `/layout/Layout.js`, but we don't need to worry about this file at all). What I want to avoid in the future is, when other components need to make API calls, re-coding what is already written inside of `dashboard/Dashboard.js`. And, unless that component is a child of `Dashboard`, we will be writing redundant and extreneous code.

> *Are there different solutions?*

Of course there are. You could not do this at all...I mean, why do more work than you need to do? Plus, I'm sure Thinkful put the API call in the `Dashboard` for a reason. I'm choosing to move the API call code inside of `Dashboard` into `Routes`, but you could also completely put the API calls into its own file and import it as you wish to your different components. Is there a better solution? Not really. Do whatever you feel comfortable and happy with.

With the boring set-up text out of the way, let's see the snippet of code I am planning on removing from my `Dashbaord` to `Routes`:
```javascript
const [reservations, setReservations] = useState([]);
const [reservationsError, setReservationsError] = useState(null);

const [tables, setTables] = useState([]);
const [tablesError, setTablesError] = useState(null);

useEffect(loadDashboard, [date]);

function loadDashboard() {
	const abortController = new AbortController();

	setReservationsError(null);

	listReservations({ date: date }, abortController.signal)
		.then(setReservations)
		.catch(setReservationsError);

	return () => abortController.abort();
}
```

Now, since all of this information got ripped out of `Dashboard`, we need to pass this information in the form of props. Now, the daddy component (`Routes`) is able to pass the data from the API calls down as props. This is exactly what I wanted to happen. The parent holds all the information and will pass it down as read-only props to its children.
```javascript
<Route path="/dashboard">
	<Dashboard 
		date={date ? date : today()}
		reservations={reservations}
		reservationsError={reservationsError}
		tables={tables}
		tablesError={tablesError}
	/>
</Route>
```

---

## *(4.5) Seating a reservation*
Our next task is to implement a component for seating a reservation at a certain table. Here is me setting up the route in `/layout/Routes.js`:
```javascript
<Route exact={true} path="/reservations/:reservation_id/seat">
	<SeatReservation
		reservations={reservations}
		tables={tables}
		
		{ /* how did I pass the reservations and tables as props? */ }
		{ /* read how I did it in section 4.X! */ }
	/>
</Route>
```

Setting up a new component in `/reservations/SeatReservation.js`:
```javascript
import React from "react";

export default function SeatReservation({ reservations, tables }) {
	return (
		// JSX
	);
}
```

Let's first set up our `form` using `select`:
```javascript
return (
	<form>
		<label htmlFor="table_id">Choose table:</label>
		<select 
			name="table_id" 
			id="table_id"
		>
			{ /* our options will go here soon */ }
		</select>

		<button type="submit" onClick={handleSubmit}>Submit</button>
		<button type="button" onClick={history.goBack}>Cancel</button>
	</form>
);
```

The `select` tag will set up a drop-down for us. The user will be able to choose an `option` from a given list. Let's go ahead and make those options now.
```javascript
// i use the same principles in previous sections in mapping the tables array.
const tableOptionsJSX = () => {
	return tables.map((table) => 
		// make sure to include the value
		// the option text i have here is required for the tests as included in the instructions
		<option value={table.table_id}>{table.table_name} - {table.capacity}</option>);
};
```



We will add our new variable to the `return` statement. You will notice I also added a `value` and `onChange` to the `select`. 
```javascript
<select 
	name="table_id" 
	id="table_id"
	value={tableId}
	onChange={handleChange}
>
	{tableOptionsJSX()}
</select>
```

The value and onChange correspond to the following code:
```javascript
export default function SeatReservation({ reservations, tables }) {
	const history = useHistory();
	
	// here are the states we need to keep track of
	const [tableId, setTableId] = useState(0);
	const [errors, setErrors] = useState([]);

	// in case the props passed in don't exist
	if(!tables || !reservations) return null;

	// change handler sets tableId state
	function handleChange({ target }) {
		setTableId(target.value);
	}

	// submit handler does nothing as of yet
	function handleSubmit(event) {
		event.preventDefault();

		// we will be creating a validation function as well
		if(validateSeat()) {
			history.push(`/dashboard`);
		}
	}
	
	// validation function uses the same principles from my other vaidation functions in previous sections
	function validateSeat() {
		const foundErrors = [];

		// we will need to use the find method here to get the actual table/reservation objects from their ids
		const foundTable = tables.find((table) => table.table_id === tableId);
		const foundReservation = reservations.find((reservation) => reservation.reservation_id === reservation_id);

		if(!foundTable) {
			foundErrors.push("The table you selected does not exist.");
		}
		else if(!foundReservation) {
			foundErrors.push("This reservation does not exist.")
		}
		else {
			if(foundTable.status === "occupied") {
				foundErrors.push("The table you selected is currently occupied.")
			}

			if(foundTable.capacity < foundReservation.people) {
				foundErrors.push(`The table you selected cannot seat ${foundReservation.people} people.`)
			}
		}

		setErrors(foundErrors);

		// this conditional will either return true or false based off of whether foundErrors is equal to 0
		return foundErrors.length === 0;
		
		// if you read my previous sections, you will recall that i programmed it like this previously:
		// if(foundErrors.length > 0) {
		// 	return false;
		// }
		// return true;
		
		// both my new return statement and the old return statement do the same thing. i find the one-liner more elegant.
	}
	
	// ...
```

The final page looks like this...except I haven't set up the back end yet, so there's no tables in the drop-down. Looks like we will be visiting this again in the back end.

![seat-reservation-example](https://user-images.githubusercontent.com/64234681/118546160-6829ea00-b70c-11eb-8340-6e79289a0cab.png)

---

Looks like you got to the bottom. 0_0 I am updating this guide as I build the program, so hopefully some sections get added soon. You're killing it!
