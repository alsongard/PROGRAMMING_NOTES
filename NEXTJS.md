
#### **Adding sticky navbar using nextjs and classx**
```
'use client';
import React from 'react';
import clsx from 'clsx';
function Header()
{
	const [stickyVar, setStickyVar] = React.useState(false);
	React.useEffect(()=>{
		const header = document.getElementById("header");
		if (!header) return;
		# get position
		const headerPosition = header.offsetTop;
		window.addEventListener("scroll", ()=>{
			// changes the value to true if condition == true
			setStickyVar(window.scrollY > headerPosition);
		})
		
	}, [])
	return (
		<header id="header" className={clsx(stickyVar ? "true execute": "false execute", "w-[100vw] flex flex-row py-[5px])}>
			<ul className="">
				<li>Home<li>
				<li>About<li>
			</ul>
		</header>
	)
}
```