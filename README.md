1. What is the difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll?


getElementById – This selects only ONE element using its ID. Since ID is unique, it returns a single element directly. It's fast but limited.
# Example : const total = document.getElementById('total-count');


getElementsByClassName – This selects ALL elements with the same class name. It returns a live HTMLCollection (updates automatically if DOM changes).
# Example : const cards = document.getElementsByClassName('job-card');

querySelector / querySelectorAll – These are more flexible. querySelector returns the FIRST match, querySelectorAll returns ALL matches as a static NodeList. It can use any CSS selector like .class, #id, or tag.
# Example : const firstBtn = document.querySelector('.btn');
            const allBtns = document.querySelectorAll('.btn');

Special Note : In my assignment, I used getElementById for dashboard counters because each one has a unique ID.


2. How do you create and insert a new element into the DOM?

There are 3 simple steps:

i. Create the element
: const card = document.createElement('div');

ii. Add content or classes
: card.className = 'job-card';
  card.innerHTML = '<h3>Frontend Developer</h3>';

iii. Insert it into the page
: jobsContainer.appendChild(card);


3. What is Event Bubbling? And how does it work?
Event Bubbling means when you click on a child element, the event travels UP to its parent elements.

Example:

<div onclick="parentClick()">     - Event reaches here last
  <button onclick="childClick()"> - Event starts here
</div>

---If anyone click the button, first childClick() runs, then parentClick() runs. The event "bubbles up" from inside to outside.
In my assignment, when I click the "Interview" button inside a card, the click event could bubble up to the card or container. That's why I added specific onclick handlers on buttons only.


4. What is Event Delegation in JavaScript? Why is it useful?
Event Delegation means instead of adding event listeners to every single child element, you add ONE listener to the parent and check which child was clicked using event.target.

Example:

// Instead of this (bad for many items):
buttons.forEach(btn => btn.addEventListener('click', handleClick));

// Do this (better):
container.addEventListener('click', (e) => {
    if(e.target.classList.contains('btn')) {
        handleClick(e);
    }
});

# Why it's useful:
1. Better performance (fewer listeners)
2. Works on new elements added later (like my job cards)
3. Less memory usage

#Special note : In my assignment, I used onclick directly in HTML for simplicity, but event delegation would be better if I had 100+ job cards.

5. What is the difference between preventDefault() and stopPropagation() methods?


Ans- 

*preventDefault()* stops the browser's default behavior. For example, stopping a form from submitting or a link from opening a new page.
*stopPropagation()* stops the event from bubbling up to parent elements. It keeps the event contained within the specific element.

In this assignment, I didn't need preventDefault() because I am not using forms, but I learned that it is essential for form handling.*