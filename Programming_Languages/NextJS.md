Go to [Link](https://nextjs.org/docs/app/getting-started/installation) to get started.
To create a nextjs application use the following command:
```
npx create-next-app@latest 
```

appName = event_app
``npx create-next-app@latest event_app``


tsconfig.json : configuration file for typescript, defines what should be type checked, ignored and the rules to follow
postcss.config.mjs : used to process CSS with different plugins
next.config.ts : configure nextjs
public folder: static assets such as images 
app folder: file for source code 


## architecture in NextJS
2 types of components:
- Server side components : default (any component you make will by default be a SSC(server side component)).  These are components that are rendered on the server. Therefore they can access resources on the server such as database and fileSystem reducing the size of the javascript code sent to the browser 

- Client side components : components that require user interactions such as clicking forms, entering data. They're rendered on the client side(browser).    

To use them in nextjs one must add ``"use client";`` directive in your file. client side components are pre-rendered on the server side and create a static shell that is then sent to the client. 

```
"use client";

export default Hello()
{
    console.log("Client side component");
    return (
        <h1>Lets See</h1>
    )
}
```


## Routing
file based routing System
In nextjs routing is performed by creating a new folder and adding a page.tsx withing the folder. 

**nested routes**
In cases whereby you want to have nested routes: 
e.g :      ``domain.name/dashboard/users``  ||   ``domain.name/darshboard/analytics``
Create folder: 
dashboard
Add: 
./analystics/page.tsx
./users/page.tsx

One can also add a page.tsx file in the dashboard folder, for the route: ``domain.name/dashboard``

**Dynamic Routing**
Lets say we want to have a page where there are mutliple users in which each can be clicked
``domain.name/users/[user]`` : [user] === user-1 , user-2, user-3
In such a case we use dynamic routing by placing the changing url element.  
Create an dynamic route:
create ``id`` folder wrapped with ``[]``

```
[id]
    page.tsx
```

To provide links in nextjs we use the ``Link`` component
``<Link href="/route">Text</Link>``

Complex Object destructuring:
```
const peter = {name: "Swaelee", song: "just to save you", movie: "spiderman", lesson: {Subject: "javascript", Support: "nav"}};
const {lesson: {Subject, Support}} = peter;
console.log(Subject);
console.log(Support);
```

**``Layout.tsx file``**
The layout.tsx file is used as the parent file whereby each file/route is displayed a child component. Useful for placing headers,footers or user interface elements.

If you want to specify a specific navbar or user interface element for specific pages we use the following:
Example: specific navbar for dashboard pages:
Always ensure that this file is called page.tsx;

```
- dashboard
    - layout.tsx
    - analytics
    - users
```
In the above code, the ``layout.tsx`` file will be used.
the layout.tsx file should have the following:
```
import React from "react"
const Layout = ({children}: {children: React.ReactNode})=>{
    return (
        <div>
            <h1>Dashboard</h1>
            {children}
        </div>
    )
}
```
or:
```
import React from "react"
const Layout = ({children}: {children: React.ReactNode})=>{
    return (
        <div>
            <h1>Dashboard</h1>
            {children}
        </div>
    )
}
```
## Route Groups
or better if you want to group several route pages to have a specific navBar do the following: 
Create 2 folders in paranthesis:
(root) : add layout.tsx file
(dashboard) : add layout.tsx

## data fetching
in react/traditional way we use useEffect:

```
async function Home(){
    const response = awaity fetch("https://jsonplaceholder.typicode.com/albums");
    if (!response.ok) throw new Error("Failed to fetch data");


    const albums = await response.json();
    return (
        <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols">
            {albums.map((album: {id: number, title: string}))} =>{
                <div  key={album.id} className="bg-white shadow-md rounded-lg p-4 transition t..">
                   <h3>{album.title}</h3>
                   <p>Album ID: {album.id}</p>
                </div>
            }
        </div>
    )}

```

## Server Side Strategies:
- Static site generation (SSG): the site is generated once deployed
, not suitable for websites that update frequently. Documentation and marketing pages, blogs

- Incremental Static Generation (ISG):

 
## Routing in NextJS
In the src/app file, to create a new page or a route one must:
Create a folder containing the name of the page:
Example: About page == about folder
within each of the folder create a file for the page, source code file. The file should be named ``page.tsx``
```
src/app/
	about/page.tsx
	event/page.tsx
	contact/page.tsx
```


## Fetching data in NextJS
```
type Post = [
	id: string;
	title: string;
	category: string;
]

export default async funciton Page()
{
	const data = await fetch("httsp://api.vercel.app/blog");
	const posts : Post[] = await data.json();
	return (
		<ul>
			{posts.map((post L)=>{
			<li key={post.id}>{post.title{</li>})}
		</ul>
	)
}
```

The example above shows a basic server-side data fetch using the fetch API in an Asynchronous  React Server [Component](https://nextjs.org/docs/app/building-your-application/data-fetching/fetching)

## fetching data from an api

```
const data = await import("/data/data.json");
const res = await fetch("URL");
const data = await res.json();
```