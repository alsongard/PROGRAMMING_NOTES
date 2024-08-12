
## Initializing a React App



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
 