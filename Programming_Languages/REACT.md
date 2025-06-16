
## Initializing a React App
```
npx create-react-app nameofapp
```

## Using props
to use props define your function or module and pass in an argument. After passing an argument, use the argument name e.g prop.data-item-name. Ensure that the data item name is same to what you pass in the `index.js` file.
An example is show below:
```
function TouristComponent(props){
return (
	<section className="touristInfo">
		<div className="imageHolder">
			<img src={prop.imageUrl} alt={prop.altImage}/>
		</div>
		<div className="location-Data">
			<div className="location">
				<p>{prop.locationName}</p>
			</div>
			<h2>{prop.title}</h2>
			<div className="dates">
				<p>{prop.startDate}</p>
				<p>{prop.endDate}</p>
			</div>
			<p>{prop.description}</p>
		</div>

	</section>
	)
}
export default TouristComponent;
```
In the `touristPage.js` file 
```
import TouristComponent from "./component/touristComponent.js";
function TouristPage(){
	return(
		<TouristComponent
			imageUrl="https://images.pexels.com/photos/3408354/pexels-photo-3408354.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
			locationName="United Arab Emirates"
			title="Dubai"
			googleMapsUrl=""
			startDate="13 Dec, 2022"
			endDate="29 Dec, 2022"
			description="Dubai is a city and emirate in the United Arab Emirates             known for luxury shopping, ultramodern architecture and a lively   nightlife scene."
		/>
	)
}
export default TouristPage;
```

## Using Map Function 
Using the map function enables you to pass the data to the App file directly which has imported the components, the data and will be exported to the Main Page.
Example Based on Tourist Project:
Simple sample of our `tourist.js` file
```export default [
{
id:1,
imageUrl: "https://images.pexels.com/photos/3408353/pexels-photo-3408353.jpeg?auto=compress&cs=tinysrgb&w=600",
altImg:"Mount Fuji",
location: "Japan",
title: "Mountain Fuji",
googleMapsUrl: "https...",
startDat: "12 Jan, 2021",
endDat: "24 Jan, 2021",
description:"Mount Fuji is the single most popular tourist site in Japan, for both Japanase and foreign tourists.",
},
```

```
import TouristComponent from "./touristComponent.js";
import TouristData from "./touristDaja.js";

function TouristApp(){
	//javascript
	const touristElements = TouristData.map(function(dataItems){
		return <TouristComponent imageUrl={dataItems.imageUrl} altImg=                    {dataItems.altImg}  locationName={dataItems.location} title={dataItems.title} startDate={dataItems.startDat} endDate={dataItems.endDat} description={dataItems.description}
	})
}
```

## Working with Objects
To work with object pass the argument word on the function() inside the map function. To the Component module. Change the component module elements which have the props to props.argument.name. Ensure that the item in the props.argument.item elements have the same element to that of the data file.
Example based on tourist App:
```
function TouristApp(){
	const touristElements = touristData.map(function(dataItems){
		return <TouristComponent key={dataItems.id} items={dataItems}/>
	})
	return(touristElements)
}
```

## Working with images
To use a local image, provide the file path and assign an alias or a variable and insert it as javascript code in the module/function.
```
import logo from "./images/user_image.jpg";
function Header(){
	<img src={logo} alt="logo">
}
```
If its a link provide directly to the source attribute of the image.

## Add ``css`` file to your ``js`` component folder
Use import statement as shown below:
```
import "../css/profile-main-component.js"
```

## Using react icons 
To use react icons install the following
```
npm  install react-icons --save
```

```
import {FaPhone} from "react-icons/fa6";
function CardComponent()
{
	return (
		<div>
			<FaPhone/>
		</div>
	)
}
```

## Object destructing
Similar to props
```
// object destructuring in React
const person = {
	img: "file_path",
	name: "Mr. whiskerson",
	phone: "(220) 123-977-413",
	email: "whiskerson@gmail.com"
}
function Contact({img, name, phone, email})
{
	<img src={img}/>
	<h3>{name}</h3>
	<p>{phone}</p>
	<p>{email}</p>
}
```

## Working with forms in React
When working with forms in React, we use ``useState()`` and each time the user types in  into the input, the const variable is updated.
Example:
```
function Forms(){
	const [formData, setFormData] = React.useState();
	function handleChange(event){
		console.log(event);
	}
	return (
		<form>
			<input type="text" onChange={handleChange}/>********
		</form>
	)
}
```

The **``onChange``** is a input handler that takes in a function. Mostly used to update an object or string stateObject.  This will be shown in the following examples:
Example 1: A form with a single input
```
function Form1(){
	const [firstName, setFirstName] = React.useState("");
	function handleChange(event){
		setFirstName(()=>{
			const newUserName = event.target.value;
			return newUserName;
		})
		//or 
		setFirstName(event.target.value);
	}
	return (
		<div>
			<form>
				<input type="text" onChange={handleChange}/>
			</form>
		</div>
	)
}
```
Example 2: A form with multiple input
```
function Form2(){
	const [firstName, setFirstName] = React.useState("");
	const [secondName, setSecondName] = React.useState("");

	function firstNameHandle(){
		setFirstName(event.target.value);
	}
	function secondNameHandle(){
		setSecondName(event.target.value);
	}
	return (
		<div>
			<form>
				<input type="text" onChange={firstNameHandle}/>
				<input type="text" onChange={secondNameHandle}/>
			</form>
		</div>
	)
}
```

Example 3:
Working with ``textarea`` input. The ``textarea`` input is a self closing element in React and it takes on the ``value={} ``  which is used to tell the input element what to display and name property that has to be similar to that in the object and ``onChange={}``  function for handling input when data is entered.

```
function CollectData(){
	const [formData, setFormData] = React.useState({
		firstName: "",
		secondName: "",
		age: "",
		comment: ""
	});

	return (
		<div>
			<form>
				<input type="text" name="firstName" value={formData.firstName} onChange={handleChange}/>
				<input type="text" name="secondName" value={formData.secondName} onChange={handleChange}/>
				<input type="number" name="age" value={formData.age} onChange={handleChange}/>
				<textarea value={formData.comment} name="comment" onChange={handleChange} /> 
			</form>
		</div>
	)
}
```

## **Links in React**
In React in order to link pages we use the Link Component. 

### **NavLink component**
The NavLink component is used for setting the NavBar link which is active. 
Example: this is shown below:
```
import {NavLink} from "react-router-dom"


function Header()
{
	<ul className="flex flex-row">
		<NavLink
			to="/"
			className={({isActive})=>
				isActive ? "text-black" : "text-white"
			}
		>
		Home
		</NavLink>
		<NavLink
			to="/about"
			className={({isActive})=>
				isActive = "text-black" : "text-white"
			}
		>
		About
		</NavLink>
	</ul>
}
```

### Styling link component
To style the link component assign it a ``className`` and apply the styles to the class in your css file.
Example:
```
<ul className="relative">
	<li><Link className="myLinks" to="/">Home</Link></li>
</ul>
```

my Css file: using tailwind css framework
```
.myLinks{
	@apply text-[17px] text-red-400;
}
.myLinks::after{
	content: "",
	position:absolute;
	bottom:0;
	height:3px;
	background-color:aqua;
	
	
}
```


## Creating Multiple Routes for Multiple Pages 
To create more than a single page web app in React, we use the`` react-router-dom`` module. 
Also remember the ``Outlet`` . 
It provides with the following and it will be explain below:
```
import {BrowserRouter, Routes, Route} from "react-dom-router";

// in app.js file do the following:
function App()
{
	return (
		<main>
			<BrowserRouter>
				{/* create a nested router in which header and footer will be displayed in each page*/}
				<Routes>
					<Route path="/" element={<div> <Header/> <Footer/> </div>}>
						<Route index element={<Users/>}/>
					</Route>
				</Routes>
			</BrowserRouter>
		</main>
	)
}
```

Header.js file:
```
// do the following
import {Outlet} from "react-router-dom";
function Header()
{
	return (
		<div>
			<header>
				<ul>
					<Link to="/"><li>Home</li></Link>
					<Link to="/about"><li>About</li></Link>
					<Link to="/services"><li>Services</li></Link>
				</ul>
			</header>
			<Outlet/>
		</div>
	
	)
}
```
## setting dark mode in React
To set dark mode in your web application or website use the following:
install tailwind framework: go to [link](https://tailwindcss.com/docs/installation)
Add the custom class in t``ailwind.config.css`` file:
```
darkMode: 'class'
```

In app.js do the following:
```
import React from "react";
function App()
{
	const [darkMode, setDarkMode] = React.useState(false);
	function handleChange()
	{
		setDarkMode((prevalue)=>{
			return !prevValue;
		})
	}
	const answer = darkMode ? "dark" : ""
	return (
		<div className={`${answer}`}>
			<header className="dark:bg-slate-400">
				<button onClick={handleChange}>Dark</button>
			</header>
		</div>
	)
}
```

```
function Header()
{
		const [menuStyle, setMenuStyle] = React.useState({display: "none"})

	function toggleNav()
	{
	setMenuStyle((prevStyle)=>({
	display: prevStyle.display === "none" ? "flex" : "none"
	}))
	}

return (
	<header>
		<ul className="max-[630px]:hidden >
		<li>Home</li>
		<li>About</li>
		<li>Contact</li>
		<li>Service</li>
		</ul>
		<ul style={menuStyles}>
		<li>Home</li>
		<li>About</li>
		<li>Contact</li>
		<li>Service</li>
		</ul>
		<button onClick={toggleNav}>NavBtn</button>
	</header>
)
}
```


## **Complex data props and mapping**
FileName : ``data.js``
```
Given the following data

const games = {
	"shooter": [
		{
			name: "Call of Duty",
			description: "Best gun fighting games"
		},
		{
			name: "Ghost Recod",
			description: "Explore all ways"
		}
	],
	"Powers": [
		{
			name: "Devil May Cry 4",
			description: "Sword and Powers"
		},
		{
			name: "Prototype",
			description: "Run Fast, strenght, Hijack Helicopters"
		}
	]
}
export default games;
```

FileName: gameViewComponent.js
```
function GaveViewComponent(props)
{
	return(
		<div>
			<p>{props.item.name}</p>
			<p>{props.item.description}
		</div>
	)
}
export default GameViewComponent;
```

FileName: gameCategoryView.js
```
import GameViewComponent from "";
function GameCategoryView(props)
{
	const {gameType, gameData} = props;
	return (
		<div>
			<h2>{gameType}</h2>
			<GameViewComponent key={gameData.id} item={gameData}/>
		</div>
	
	)
}
export default GameCategoryView;
```

FileName: gameProject.js
```
import GameCategoryView from "./";
import data from "./data.js";
function GameMainView()
{
	return (
		<div>
			{Object.keys(data).map((gameItem)=>(
				<GameCategoryView gameType={gameItem} gameData={data[gameItem]}/>
			))}			
		</div>
	)

}
```



## **cross origin resource sharing**
when fetching data using ``fetch()`` 


## **React Preloader**
to set up a preloader for your website, use the following steps:
Step 1. Create a preloader.js file:
```
export default function Preloader()
{
	return (
		<div className="prelaoder">
			<div className="preloader">
			</div>
		</div>
	)
}
```

Step 2: in index.css give the following styles:
```
.prelaoder{
	height:100vh;
	width:100wv;
	background:red;
	display:flex;
	justify-content:center;
	align-item:center;
}
```

In your mains.js file do the following:
```
import React from "react";
function App()
{
	const [isLoading, setIsLoading] = React.useState(true);
	return (
		{isLoading ? (<Prelaoder>) : (
			<main>
				<BrowseRouter></
			</main>
		)}
	)
}
```

### **conditional Rendering**
to perform conditional rendering in React we use the following:
note the html code must be in parenthesis and will displayed if the condition evaluates to true
Example:
```
return (
	{formData.details === "Referall" && (
		<div>
			<label>Enter username:inappropriate</label>
			<input type="text" value={formData.referallUser} name="referallUser"/>
		</div>
	)}
)
```