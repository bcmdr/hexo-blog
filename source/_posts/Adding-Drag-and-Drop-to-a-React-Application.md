---
title: Adding Drag and Drop to a React Application
categories:
  - Tutorials
tags:
  - Development
date: 2020-01-02 18:38:43
---

My goal this morning was to add drag and drop reordering to my habit tracker, Orchard. Between [react-dnd](https://react-dnd.github.io/react-dnd/) and [dragula](https://github.com/bevacqua/dragula), I couldn't resist the simplicity of Dragula. The idea of declaring my parent GoalList element as a container in which all the child GoalItem elements would suddenly become draggable was seemingly too good to be true. 

Amazingly, initial installation along with the CSS from [this JSFiddle by Shen Huang Huang](https://jsfiddle.net/wellwind/nxp1yxpu/) gave me the outcome I was looking for: I created a react ref with `useRef` tied to my GoalList, passed this ref to Dragula and the cards inside were now reorder-able through drag and drop! 

My next task was to ensure this reordered state persisted among page reloads. Here, I aim to summarize the gotchas I encountered and provide an explanation of my solutions. 

To get Dragula working, I needed to pass it a DOM node to use as the parent for the draggable container. React's `useRef` allowed me to essentially label my GoalList component with a ref and pass this variable name as the DOM node to Dragula. 

```
function GoalList(props, listRef) {
  return (
    <div className="GoalList" ref={listRef}>
      {props.items.map((goalItem, index) => ( goalItem &&
        <GoalItem 
          key={index}
					...
        ></GoalItem>
      ))}
    </div>
  ) 
}

export default React.forwardRef(GoalList);
```

Since you apparently can't apply refs to function components, Reacts `forwardRef` provided a way to raise this variable to the parent App component which handles all of the state manipulation. 

The relevant code inside my `App` component looks like this: 

```
const [drake, setDrake] = useState(null)
const listRef = useRef();
const scrollable = useRef();
const goalListRef = useRef();

function handleTouchMove(event) {
	if (! scrollable.current) {
	  event.preventDefault();
	}
}

useEffect(() => {
	scrollable.current = true;
	document.addEventListener('touchmove', handleTouchMove, { passive:false });
	if (drake) return;
	let drakeInit = Dragula([listRef.current], {
	  moves: (el, source, handle, sibling) => {
	    return handle.classList.contains('drag-handle');
	  }
	});
	drakeInit.on('drag', (el, source) => {
	  scrollable.current = false;
	})
	drakeInit.on('drop', (el, target) => {
	  scrollable.current = true;
	  let currentGoalList = goalListRef.current;
	  let indices = []
	  let newGoalList = [];
	  for (let i = 0; i < target.children.length; i++) {
	    let child = target.children[i];
	    indices.push(child.dataset.index);
	  }
	  for (let index of indices) {
	    newGoalList.push(currentGoalList[index]);
	  }
	  localStorage.setItem("goalList", JSON.stringify(newGoalList));
	});
	setDrake(drakeInit);
}, [drake, goalListRef]);
```

We can see I've saved the Dragula instance (or `drake`) in state. This was to avoid creating multiple Dragula instances resulting in a bug with multiple layered `.gu-transit` nodes created (we just want the one). This node is the floating copy of our dragged item that follows the cursors thanks to the above JSFiddle CSS. 

The moves function in the Dragula options ensures dragging only occurs when the `.drag-handle` element is touched. (I've applied this className to the title heading text of the draggable goals). 

`scrollable.current` is where I've decided to keep the global boolean that determines whether the page the scrollable during a `touchmove` event, a solution I found in [this github issue](https://github.com/bevacqua/dragula/issues/487), to the problem of drag-and-dropping also scrolling the page on mobile.  This is ultimately solved via the `touchmove` event handler declared in the beginning of the effect. 

The Dragula `drop` event handler contains an algorithm I whipped up for sorting the goal list based on the new position of the dragged item. It references the current goalList via a ref, which to my understanding provides an up-to-date goalList where my `useState` reference would provide the goalList as of the initial render (this was no good since the drag event would update the goalList without triggering a total re-render). 

To summarize, the biggest gotchas I encountered were needing to `useRef`, needing to declare a single instance of Dragula via `useState` and needing to overcome the default `touchmove` event with a custom event listener. In retrospect the solution is relatively simple and can hopefully serve as a reference for future drag-and-droppers. 



