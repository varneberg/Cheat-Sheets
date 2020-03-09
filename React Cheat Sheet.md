# React Cheat Sheet

## What is React?

* Code runs on client
* Build UIs
* Framework

## Why use it?

* Uses self contained, independent components with their own state
* Virtual DOM
	* Only update what’s needed, not update everything not touched
* JSX 
	* Javascript with HTML like syntax

## React State

 * Components can have sate which is an object that determines how that component renders and behaves
 
 ```js
 state = {
 	title: ‘xxx’
 	body:’xxx’
 	isFeatured:true
 }

 ```
 
## Create React App

* npx create-react-app .
* CLI Tool for creating React apps
* Uses web pack
* Comes with hot reload
* **npm run build** - compiles so browser can read

## Anatomy of a Component
* Render is required life cycle method
	* JSX

```js
Class Post extends React.Component {
	state = {
		title:’post one’,
		body:’This is a post’
	}
	render() {
	return{
	<div>
		<h3>{ this.state.title }</h3>
		<p>{ this.state.body }</p>
		}
	}
}
```

## Default Files and Folders

* **index.html**
	* Everything on React runs from this page
	* <div id=”root></div> - Everything runs from this div
* **index.js**
	* Entry point of react
 
 